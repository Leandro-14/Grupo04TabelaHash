# Grupo04TabelaHash
Trabalho realizado visando desenvolver conhecimento sobre algoritmos, nosso grupo escolheu o tema Tabela de Espalhamento.
def _init_(self, tamanho):
        self.tamanho = tamanho
        self.tabela = [None] * tamanho

    def _hash(self, chave):
        return hash(chave) % self.tamanho

    def adicionar_elemento(self, chave, valor):
        indice = self._hash(chave)
        if self.tabela[indice] is None:
            self.tabela[indice] = [(chave, valor)]
        else:
            for i, (ch, val) in enumerate(self.tabela[indice]):
                if ch == chave:
                    self.tabela[indice][i] = (chave, valor)
                    break
            else:
                self.tabela[indice].append((chave, valor))

    def obter_valor(self, chave):
        indice = self._hash(chave)
        if self.tabela[indice] is not None:
            for ch, val in self.tabela[indice]:
                if ch == chave:
                    return val
        return None
