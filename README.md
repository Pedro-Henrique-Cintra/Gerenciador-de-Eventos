from PyQt5 import QtCore, QtGui, QtWidgets
from PyQt5.QtWidgets import QMessageBox

dc_cafe = list()
lpessoas = list()
lsalas = list()
lpessoa_sala = list()


class Ui_MainWindow(object):
    def setupUi(self, MainWindow):
        MainWindow.setObjectName("MainWindow")
        MainWindow.resize(805, 531)
        self.centralwidget = QtWidgets.QWidget(MainWindow)
        self.centralwidget.setObjectName("centralwidget")
        self.tabela_main = QtWidgets.QTabWidget(self.centralwidget)
        self.tabela_main.setGeometry(QtCore.QRect(0, 0, 801, 531))
        self.tabela_main.setObjectName("tabela_main")
        self.inicio = QtWidgets.QWidget()
        self.inicio.setObjectName("inicio")
        self.consulta = QtWidgets.QLineEdit(self.inicio)
        self.consulta.setGeometry(QtCore.QRect(20, 440, 201, 21))
        self.consulta.setText("")
        self.consulta.setObjectName("consulta")
        self.btn_pesquisa_pessoa = QtWidgets.QPushButton(self.inicio)
        self.btn_pesquisa_pessoa.setGeometry(QtCore.QRect(230, 440, 111, 21))
        self.btn_pesquisa_pessoa.setObjectName("btn_pesquisa_pessoa")
        self.btn_pesquisa_pessoa.clicked.connect(lambda: self.consultar())
        self.tabela_etapa1 = QtWidgets.QTableWidget(self.inicio)
        self.tabela_etapa1.setGeometry(QtCore.QRect(20, 70, 381, 331))
        self.tabela_etapa1.setObjectName("tabela_etapa1")
        self.tabela_etapa1.setColumnCount(3)
        self.tabela_etapa1.setRowCount(0)
        item = QtWidgets.QTableWidgetItem()
        self.tabela_etapa1.setHorizontalHeaderItem(0, item)
        item = QtWidgets.QTableWidgetItem()
        self.tabela_etapa1.setHorizontalHeaderItem(1, item)
        item = QtWidgets.QTableWidgetItem()
        self.tabela_etapa1.setHorizontalHeaderItem(2, item)
        self.str_Etapa1 = QtWidgets.QLabel(self.inicio)
        self.str_Etapa1.setGeometry(QtCore.QRect(60, 40, 251, 21))
        self.str_Etapa1.setObjectName("str_Etapa1")
        self.tabela_etapa2 = QtWidgets.QTableWidget(self.inicio)
        self.tabela_etapa2.setGeometry(QtCore.QRect(410, 70, 381, 331))
        self.tabela_etapa2.setObjectName("tabela_etapa2")
        self.tabela_etapa2.setColumnCount(3)
        self.tabela_etapa2.setRowCount(0)
        item = QtWidgets.QTableWidgetItem()
        self.tabela_etapa2.setHorizontalHeaderItem(0, item)
        item = QtWidgets.QTableWidgetItem()
        self.tabela_etapa2.setHorizontalHeaderItem(1, item)
        item = QtWidgets.QTableWidgetItem()
        self.tabela_etapa2.setHorizontalHeaderItem(2, item)
        self.str_Etapa2 = QtWidgets.QLabel(self.inicio)
        self.str_Etapa2.setGeometry(QtCore.QRect(440, 40, 251, 21))
        self.str_Etapa2.setObjectName("str_Etapa2")
        self.str_consulta = QtWidgets.QLabel(self.inicio)
        self.str_consulta.setGeometry(QtCore.QRect(90, 410, 71, 20))
        self.str_consulta.setObjectName("str_consulta")
        self.str_treinamento = QtWidgets.QLabel(self.inicio)
        self.str_treinamento.setGeometry(QtCore.QRect(360, 10, 101, 16))
        self.str_treinamento.setObjectName("str_treinamento")
        self.rb_pessoa = QtWidgets.QRadioButton(self.inicio)
        self.rb_pessoa.setGeometry(QtCore.QRect(20, 470, 71, 20))
        self.rb_pessoa.setObjectName("rb_pessoa")
        self.rb_sala = QtWidgets.QRadioButton(self.inicio)
        self.rb_sala.setGeometry(QtCore.QRect(100, 470, 51, 20))
        self.rb_sala.setObjectName("rb_sala")
        self.rb_cafe = QtWidgets.QRadioButton(self.inicio)
        self.rb_cafe.setGeometry(QtCore.QRect(160, 470, 51, 20))
        self.rb_cafe.setObjectName("rb_cafe")
        self.btn_limpar_dados = QtWidgets.QPushButton(self.inicio)
        self.btn_limpar_dados.setGeometry(QtCore.QRect(700, 478, 93, 20))
        self.btn_limpar_dados.setObjectName("btn_limpar_dados")
        self.tabela_main.addTab(self.inicio, "")
        self.cadastro_de_salas = QtWidgets.QWidget()
        self.cadastro_de_salas.setObjectName("cadastro_de_salas")
        self.janela_cadastro_salas = QtWidgets.QScrollArea(self.cadastro_de_salas)
        self.janela_cadastro_salas.setGeometry(QtCore.QRect(270, 110, 241, 291))
        self.janela_cadastro_salas.setWidgetResizable(True)
        self.janela_cadastro_salas.setObjectName("janela_cadastro_salas")
        self.scrollAreaWidgetContents_2 = QtWidgets.QWidget()
        self.scrollAreaWidgetContents_2.setGeometry(QtCore.QRect(0, 0, 239, 289))
        self.scrollAreaWidgetContents_2.setObjectName("scrollAreaWidgetContents_2")
        self.btn_inscrever_sala = QtWidgets.QPushButton(self.scrollAreaWidgetContents_2)
        self.btn_inscrever_sala.setGeometry(QtCore.QRect(70, 190, 101, 21))
        self.btn_inscrever_sala.setObjectName("btn_inscrever_sala")
        self.btn_inscrever_sala.clicked.connect(lambda: self.adicionar_sala())
        self.cadastro_sala = QtWidgets.QLineEdit(self.scrollAreaWidgetContents_2)
        self.cadastro_sala.setGeometry(QtCore.QRect(60, 110, 121, 16))
        self.cadastro_sala.setObjectName("cadatro_sala")
        self.str_nome_da_sala = QtWidgets.QLabel(self.scrollAreaWidgetContents_2)
        self.str_nome_da_sala.setGeometry(QtCore.QRect(80, 90, 91, 16))
        self.str_nome_da_sala.setObjectName("str_nome_da_sala")
        self.str_lotacao = QtWidgets.QLabel(self.scrollAreaWidgetContents_2)
        self.str_lotacao.setGeometry(QtCore.QRect(100, 140, 51, 16))
        self.str_lotacao.setObjectName("str_lotacao")
        self.cadastro_lotacao_sala = QtWidgets.QLineEdit(self.scrollAreaWidgetContents_2)
        self.cadastro_lotacao_sala.setGeometry(QtCore.QRect(60, 160, 121, 16))
        self.cadastro_lotacao_sala.setObjectName("cadastro_lotacao_sala")
        self.str_cadastro = QtWidgets.QLabel(self.scrollAreaWidgetContents_2)
        self.str_cadastro.setGeometry(QtCore.QRect(60, 40, 131, 31))
        font = QtGui.QFont()
        font.setFamily("Arial")
        font.setPointSize(18)
        font.setItalic(True)
        font.setUnderline(False)
        self.str_cadastro.setFont(font)
        self.str_cadastro.setObjectName("str_cadastro")
        self.janela_cadastro_salas.setWidget(self.scrollAreaWidgetContents_2)
        self.tabela_main.addTab(self.cadastro_de_salas, "")
        self.cadastro_do_espaco_do_cafe = QtWidgets.QWidget()
        self.cadastro_do_espaco_do_cafe.setObjectName("cadastro_do_espaco_do_cafe")
        self.janela_cadastro_cafe = QtWidgets.QScrollArea(self.cadastro_do_espaco_do_cafe)
        self.janela_cadastro_cafe.setGeometry(QtCore.QRect(270, 110, 241, 291))
        self.janela_cadastro_cafe.setWidgetResizable(True)
        self.janela_cadastro_cafe.setObjectName("janela_cadastro_cafe")
        self.scrollAreaWidgetContents_3 = QtWidgets.QWidget()
        self.scrollAreaWidgetContents_3.setGeometry(QtCore.QRect(0, 0, 239, 289))
        self.scrollAreaWidgetContents_3.setObjectName("scrollAreaWidgetContents_3")
        self.btn_inscrever_cafe = QtWidgets.QPushButton(self.scrollAreaWidgetContents_3)
        self.btn_inscrever_cafe.setGeometry(QtCore.QRect(70, 190, 101, 21))
        self.btn_inscrever_cafe.setObjectName("btn_inscrever_cafe")
        self.btn_inscrever_cafe.clicked.connect(lambda: self.adicionar_cafe())
        self.cadatro_cafe = QtWidgets.QLineEdit(self.scrollAreaWidgetContents_3)
        self.cadatro_cafe.setGeometry(QtCore.QRect(60, 110, 121, 16))
        self.cadatro_cafe.setObjectName("cadatro_cafe")
        self.str_nome_do_cafe = QtWidgets.QLabel(self.scrollAreaWidgetContents_3)
        self.str_nome_do_cafe.setGeometry(QtCore.QRect(80, 90, 91, 16))
        self.str_nome_do_cafe.setObjectName("str_nome_do_cafe")
        self.str_lotacao_cafe = QtWidgets.QLabel(self.scrollAreaWidgetContents_3)
        self.str_lotacao_cafe.setGeometry(QtCore.QRect(100, 140, 51, 16))
        self.str_lotacao_cafe.setObjectName("str_lotacao_cafe")
        self.cadastro_lotacao_cafe = QtWidgets.QLineEdit(self.scrollAreaWidgetContents_3)
        self.cadastro_lotacao_cafe.setGeometry(QtCore.QRect(60, 160, 121, 16))
        self.cadastro_lotacao_cafe.setObjectName("cadastro_lotacao_cafe")
        self.str_cadastro_cafe = QtWidgets.QLabel(self.scrollAreaWidgetContents_3)
        self.str_cadastro_cafe.setGeometry(QtCore.QRect(60, 40, 131, 31))
        font = QtGui.QFont()
        font.setFamily("Arial")
        font.setPointSize(18)
        font.setItalic(True)
        font.setUnderline(False)
        self.str_cadastro_cafe.setFont(font)
        self.str_cadastro_cafe.setObjectName("str_cadastro_cafe")
        self.janela_cadastro_cafe.setWidget(self.scrollAreaWidgetContents_3)
        self.tabela_main.addTab(self.cadastro_do_espaco_do_cafe, "")
        self.cadastro_de_pessoas = QtWidgets.QWidget()
        self.cadastro_de_pessoas.setObjectName("cadastro_de_pessoas")
        self.janela_cadastro_participante = QtWidgets.QScrollArea(self.cadastro_de_pessoas)
        self.janela_cadastro_participante.setGeometry(QtCore.QRect(270, 110, 241, 291))
        self.janela_cadastro_participante.setWidgetResizable(True)
        self.janela_cadastro_participante.setObjectName("janela_cadastro_participante")
        self.scrollAreaWidgetContents_4 = QtWidgets.QWidget()
        self.scrollAreaWidgetContents_4.setGeometry(QtCore.QRect(0, 0, 239, 289))
        self.scrollAreaWidgetContents_4.setObjectName("scrollAreaWidgetContents_4")
        self.btn_inscrever_participante = QtWidgets.QPushButton(self.scrollAreaWidgetContents_4)
        self.btn_inscrever_participante.setGeometry(QtCore.QRect(70, 200, 101, 21))
        self.btn_inscrever_participante.setObjectName("btn_inscrever_participante")
        self.btn_inscrever_participante.clicked.connect(lambda: self.adicionar_pesssoa())
        self.cadatro_participante = QtWidgets.QLineEdit(self.scrollAreaWidgetContents_4)
        self.cadatro_participante.setGeometry(QtCore.QRect(60, 130, 121, 16))
        self.cadatro_participante.setObjectName("cadatro_participante")
        self.str_nome_do_participante = QtWidgets.QLabel(self.scrollAreaWidgetContents_4)
        self.str_nome_do_participante.setGeometry(QtCore.QRect(60, 100, 131, 16))
        self.str_nome_do_participante.setObjectName("str_nome_do_participante")
        self.str_cadastro_pessoa = QtWidgets.QLabel(self.scrollAreaWidgetContents_4)
        self.str_cadastro_pessoa.setGeometry(QtCore.QRect(60, 40, 131, 31))
        font = QtGui.QFont()
        font.setFamily("Arial")
        font.setPointSize(18)
        font.setItalic(True)
        font.setUnderline(False)
        self.str_cadastro_pessoa.setFont(font)
        self.str_cadastro_pessoa.setObjectName("str_cadastro_pessoa")
        self.cadastro_sobrenome_pessoa = QtWidgets.QLineEdit(self.scrollAreaWidgetContents_4)
        self.cadastro_sobrenome_pessoa.setGeometry(QtCore.QRect(60, 180, 121, 16))
        self.cadastro_sobrenome_pessoa.setObjectName("cadastro_sobrenome_pessoa")
        self.str_sobrenome = QtWidgets.QLabel(self.scrollAreaWidgetContents_4)
        self.str_sobrenome.setGeometry(QtCore.QRect(60, 160, 81, 16))
        self.str_sobrenome.setObjectName("str_sobrenome")
        self.janela_cadastro_participante.setWidget(self.scrollAreaWidgetContents_4)
        self.tabela_main.addTab(self.cadastro_de_pessoas, "")
        MainWindow.setCentralWidget(self.centralwidget)
        self.retranslateUi(MainWindow)
        self.tabela_main.setCurrentIndex(0)
        QtCore.QMetaObject.connectSlotsByName(MainWindow)

    def adicionar_sala(self):
        nlotacao = self.cadastro_lotacao_sala.text()
        try:
            int(nlotacao)
            if int(nlotacao) < 0:
                nlotacao = 'Sou negativo'
            int(nlotacao)
        except:
            QMessageBox.about(self.centralwidget, 'ERRO', 'Lotação Inválida')
        else:
            lpessoa_sala.clear()
            lista_sala = [self.cadastro_sala.text(), self.cadastro_lotacao_sala.text()]
            lsalas.append(lista_sala)
            if len(lpessoas) != 0:
                cont = 0
                if len(lsalas) >= len(lpessoas):
                    n = int(len(lsalas)) / int(len(lpessoas))
                else:
                    n = int(len(lpessoas)) / int(len(lsalas))
                if len(lsalas) * int(n) < len(lpessoas):
                    d = len(lpessoas) - len(lsalas) * int(n)
                    if d == 1:
                        for c in lsalas:
                            if cont == 0:
                                p = cont + int(n)
                                lpessoa_sala.append(c + lpessoas[cont:p+1])
                                cont += int(n)+1
                            else:
                                p = cont + int(n)
                                lpessoa_sala.append(c + lpessoas[cont:p])
                                cont += int(n)
                    else:
                        n += 1
                        for c in lsalas:
                            p = cont + int(n)
                            lpessoa_sala.append(c + lpessoas[cont:p])
                            cont += int(n)
                else:
                    for c in lsalas:
                        p = cont + int(n)
                        lpessoa_sala.append(c + lpessoas[cont:p])
                        cont += int(n)
            print(lpessoa_sala)


    def adicionar_cafe(self):
        nlotacao = self.cadastro_lotacao_cafe.text()
        try:
            int(nlotacao)
            if int(nlotacao) < 0:
                nlotacao = 'Sou negativo'
            int(nlotacao)
        except:
            QMessageBox.about(self.centralwidget, 'ERRO', 'Lotação Inválida')
        else:
            if len(dc_cafe) < 2:
                dc_cafe.append(self.cadatro_cafe.text() + self.cadastro_lotacao_cafe.text())
            else:
                QMessageBox.about(self.centralwidget, 'ERRO', f'Números de espaços cadastrados no limite: 2 ')


    def adicionar_pesssoa(self):
        if len(lsalas) == 0:
            p = self.cadatro_participante.text() + ' ' + self.cadastro_sobrenome_pessoa.text()
            lpessoas.append(p)
        else:
            lpessoa_sala.clear()
            p = self.cadatro_participante.text() + ' ' + self.cadastro_sobrenome_pessoa.text()
            lpessoas.append(p)
            cont = 0
            if len(lsalas) >= len(lpessoas):
                n = int(len(lsalas)) / int(len(lpessoas))
            else:
                n = int(len(lpessoas)) / int(len(lsalas))
            if len(lsalas) * int(n) < len(lpessoas):
                d = len(lpessoas) - len(lsalas) * int(n)
                if d == 1:
                    for c in lsalas:
                        if cont == 0:
                            p = cont + int(n)
                            lpessoa_sala.append(c + lpessoas[cont:p+1])
                            cont += int(n)+1
                        else:
                            p = cont + int(n)
                            lpessoa_sala.append(c + lpessoas[cont:p])
                            cont += int(n)
                else:
                    n += 1
                    for c in lsalas:
                        p = cont + int(n)
                        lpessoa_sala.append(c + lpessoas[cont:p])
                        cont += int(n)
            else:
                for c in lsalas:
                    p = cont + int(n)
                    lpessoa_sala.append(c + lpessoas[cont:p])
                    cont += int(n)
            print(lpessoa_sala)

    def consultar(self):
        if self.rb_pessoa.isChecked():
            rowCount = self.tabela_etapa1.rowCount()
            self.tabela_etapa1.insertRow(rowCount)
            rowCount = self.tabela_etapa2.rowCount()
            self.tabela_etapa2.insertRow(rowCount)
            for c in lpessoa_sala:
                print(c)
                for b in c[2:]:
                    print(b)
                    if str(b) == str(self.consulta.text() + ' '):
                        self.tabela_etapa1.setItem(0, 0, QtWidgets.QTableWidgetItem(str(b)))
                        self.tabela_etapa1.setItem(0, 1, QtWidgets.QTableWidgetItem(str(c[0])))
                        self.tabela_etapa1.setItem(0, 2, QtWidgets.QTableWidgetItem(str(dc_cafe[0])))
                        self.tabela_etapa2.setItem(0, 0, QtWidgets.QTableWidgetItem(str(b)))
                        self.tabela_etapa2.setItem(0, 1, QtWidgets.QTableWidgetItem(str(c[0])))
                        self.tabela_etapa2.setItem(0, 2, QtWidgets.QTableWidgetItem(str(dc_cafe[1])))
            print(self.consulta.text())
        if self.rb_cafe.isChecked():
            pass
        if self.rb_sala.isChecked():
            pass



    def retranslateUi(self, MainWindow):
        _translate = QtCore.QCoreApplication.translate
        MainWindow.setWindowTitle(_translate("MainWindow", "MainWindow"))
        self.consulta.setAccessibleName(_translate("MainWindow", "consulta"))
        self.btn_pesquisa_pessoa.setText(_translate("MainWindow", "Pesquisar "))
        item = self.tabela_etapa1.horizontalHeaderItem(0)
        item.setText(_translate("MainWindow", "Pessoa"))
        item = self.tabela_etapa1.horizontalHeaderItem(1)
        item.setText(_translate("MainWindow", "Sala"))
        item = self.tabela_etapa1.horizontalHeaderItem(2)
        item.setText(_translate("MainWindow", "Espaço do Café"))
        self.str_Etapa1.setText(_translate("MainWindow", "                         Etapa 1"))
        item = self.tabela_etapa2.horizontalHeaderItem(0)
        item.setText(_translate("MainWindow", "Pessoas"))
        item = self.tabela_etapa2.horizontalHeaderItem(1)
        item.setText(_translate("MainWindow", "Sala"))
        item = self.tabela_etapa2.horizontalHeaderItem(2)
        item.setText(_translate("MainWindow", "Espaço do Café"))
        self.str_Etapa2.setText(_translate("MainWindow", "                         Etapa 2"))
        self.str_consulta.setText(_translate("MainWindow", "CONSULTA"))
        self.str_treinamento.setText(_translate("MainWindow", "TREINAMENTO"))
        self.rb_pessoa.setText(_translate("MainWindow", "Pessoa"))
        self.rb_sala.setText(_translate("MainWindow", "Sala"))
        self.rb_cafe.setText(_translate("MainWindow", "Café"))
        self.btn_limpar_dados.setText(_translate("MainWindow", "Limpar Dados"))
        self.tabela_main.setTabText(self.tabela_main.indexOf(self.inicio), _translate("MainWindow", "Início"))
        self.btn_inscrever_sala.setText(_translate("MainWindow", "Inscrever"))
        self.str_nome_da_sala.setText(_translate("MainWindow", "Nome da Sala"))
        self.str_lotacao.setText(_translate("MainWindow", "Lotação"))
        self.str_cadastro.setText(_translate("MainWindow", "Cadastro"))
        self.tabela_main.setTabText(self.tabela_main.indexOf(self.cadastro_de_salas), _translate("MainWindow", "Cadastro de Salas"))
        self.btn_inscrever_cafe.setText(_translate("MainWindow", "Inscrever"))
        self.str_nome_do_cafe.setText(_translate("MainWindow", "Nome do Café"))
        self.str_lotacao_cafe.setText(_translate("MainWindow", "Lotação"))
        self.str_cadastro_cafe.setText(_translate("MainWindow", "Cadastro"))
        self.tabela_main.setTabText(self.tabela_main.indexOf(self.cadastro_do_espaco_do_cafe), _translate("MainWindow", "Cadastro do espaço do café"))
        self.btn_inscrever_participante.setText(_translate("MainWindow", "Inscrever"))
        self.str_nome_do_participante.setText(_translate("MainWindow", "Nome do Participante"))
        self.str_cadastro_pessoa.setText(_translate("MainWindow", "Cadastro"))
        self.str_sobrenome.setText(_translate("MainWindow", "Sobrenome"))
        self.tabela_main.setTabText(self.tabela_main.indexOf(self.cadastro_de_pessoas), _translate("MainWindow", "Cadastro de Pessoas"))

import sys
app = QtWidgets.QApplication(sys.argv)
MainWindow = QtWidgets.QMainWindow()
ui = Ui_MainWindow()
ui.setupUi(MainWindow)
MainWindow.show()
sys.exit(app.exec_())
