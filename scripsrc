import pymongo
from faker import Faker
from tqdm import tqdm
from datetime import datetime

# Conexão com o MongoDB Atlas (substitua os placeholders)
client = pymongo.MongoClient("mongodb+srv://seu_usuario:sua_senha@seu_cluster.mongodb.net/")
db = client["seu_banco_de_dados"]
collection = db["sua_colecao"]

# Configuração do Faker (localização)
fake = Faker('pt_BR')

# Quantidade de documentos a serem inseridos
num_documents = 10000  # Ajuste conforme necessário

# Barra de progresso
with tqdm(total=num_documents, desc="Populando MongoDB", unit="doc") as pbar:
    for _ in range(num_documents):
        document = {
            "nome": fake.name(),
            "email": fake.email(),
            "endereco": fake.address(),
            "data_nascimento": datetime.combine(fake.date_of_birth(), datetime.min.time()),
            "profissao": fake.job()
        }
        collection.insert_one(document)
        pbar.update(1)  # Atualiza a barra de progresso
