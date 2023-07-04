from estrutura_elementar import estrutura_elementar


class No:
    def __init__(self, valor):
        self.valor = valor
        self.proximo = None

    def set_proximo(self, no):
        self.proximo = no

    def get_proximo(self):
        return self.proximo


class LinkeList(estrutura_elementar):
    def __init__(self):
        self.inicio = None

    def inserir_inicio(self, valor):
        if self.inicio is None:
            self.inicio = No(valor)
        else:
            novoNo = No(valor)
            novoNo.set_proximo(self.inicio)
            self.inicio = novoNo

    def inserir_fim(self, valor):
        if self.inicio is None:
            self.inicio = No(valor)
        else:
            novoNo = No(valor)
            aux = self.inicio
            while aux.get_proximo() is not None:
                aux = aux.get_proximo()
            aux.set_proximo(novoNo)

    def esta_vazio(self) -> bool:
        return self.inicio is None

    def remove(self, item):
        if self.inicio is None:
            return

        if self.inicio.valor == item:
            self.inicio = self.inicio.get_proximo()
            return

        atual = self.inicio
        while atual.get_proximo() is not None:
            if atual.get_proximo().valor == item:
                atual.set_proximo(atual.get_proximo().get_proximo())
                return
            atual = atual.get_proximo()

    def tamanho(self) -> int:
        if self.inicio is None:
            return 0
        else:
            contador = 0
            aux = self.inicio
            while aux is not None:
                contador += 1
                aux = aux.get_proximo()
            return contador

    def limpa(self):
        self.inicio = None

    def procura(self, item) -> bool:
        aux = self.inicio
        while aux is not None:
            if aux.valor == item:
                return True
            aux = aux.get_proximo()
        return False

    def indice_de(self, item):
        indice = 0
        atual = self.inicio
        while atual:
            if (atual.valor == item):
                return indice
            indice += 1
            atual = atual.get_proximo()
        return -1

    def recupera_indice(self, index):
        if index < 0:
            return None
        
        atual = self.inicio
        indice = 0
        
        while atual:
            if (indice == index):
                return atual.valor
            indice += 1
            atual = atual.get_proximo()
        
        return None
