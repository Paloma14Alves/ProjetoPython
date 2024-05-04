from sqlalchemy import create_engine, Column, Integer, String, Float
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.orm import sessionmaker

Base = declarative_base()

class Produto(Base):
    __tablename__ = 'produtos'
    id = Column(Integer, primary_key=True)
    nome = Column(String)
    quantidade = Column(Integer)
    preco = Column(Float)

    def __repr__(self):
        return f"<Produto(nome={self.nome}, quantidade={self.quantidade}, preco={self.preco})>"

# Conectar ao banco de dados
engine = create_engine('sqlite:///inventario.db')
Base.metadata.create_all(engine)

Session = sessionmaker(bind=engine)
session = Session()

# Funções de manipulação de dados
def adicionar_produto(nome, quantidade, preco):
    novo_produto = Produto(nome=nome, quantidade=quantidade, preco=preco)
    session.add(novo_produto)
    session.commit()

def listar_produtos():
    produtos = session.query(Produto).all()
    for produto in produtos:
        print(produto)

# Interface de usuário
def main():
    while True:
        print("1. Adicionar Produto")
        print("2. Listar Produtos")
        print("3. Sair")
        opcao = input("Escolha uma opção: ")
        if opcao == '1':
            nome = input("Nome do Produto: ")
            quantidade = int(input("Quantidade: "))
            preco = float(input("Preço: "))
            adicionar_produto(nome, quantidade, preco)
        elif opcao == '2':
            listar_produtos()
        elif opcao == '3':
            break

if __name__ == "__main__":
    main()
