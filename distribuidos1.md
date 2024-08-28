import time

class Servidor:
    def __init__(self, nome):
        self.nome = nome
        self.carga = 0 

    def processar_tarefa(self, tarefa_id, tempo_processamento):
        print(f"{self.nome} está processando a tarefa {tarefa_id}...")
        time.sleep(tempo_processamento) 
        self.carga += tempo_processamento
        print(f"Tarefa {tarefa_id} concluída pelo {self.nome}.")

    def obter_carga(self):
        return self.carga

def balancear_carga(servidores, tarefa_id, tempo_processamento):
  
    servidor_disponivel = min(servidores, key=lambda s: s.obter_carga())
    
 
    print(f"Servidor {servidor_disponivel.nome} está disponível e com a menor carga ({servidor_disponivel.obter_carga()} segundos).")
    
   
    servidor_disponivel.processar_tarefa(tarefa_id, tempo_processamento)


servidores = [Servidor("Servidor A"), Servidor("Servidor B"), Servidor("Servidor C")]


tarefas = [(1, 3), (2, 2), (3, 5), (4, 1), (5, 4), (6, 2), (7, 3), (8, 1), (9, 4), (10, 2)]


for tarefa_id, tempo_processamento in tarefas:
    print(f"\nIniciando a tarefa {tarefa_id} com tempo de processamento de {tempo_processamento} segundos...")
    balancear_carga(servidores, tarefa_id, tempo_processamento)
    print()
