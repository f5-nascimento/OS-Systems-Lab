import time

class Servidor:
    def __init__(self, nome, falhas=[]):
        self.nome = nome
        self.falhas = falhas  

    def processar_tarefa(self, tarefa_id):
        if tarefa_id in self.falhas:
            print(f"Servidor {self.nome} falhou ao processar a tarefa {tarefa_id}!")
            return False
        else:
            print(f"Servidor {self.nome} está processando a tarefa {tarefa_id}...")
            time.sleep(1)  
            print(f"Tarefa {tarefa_id} concluída pelo servidor {self.nome}.")
            return True

o
servidor_a = Servidor("A")
servidor_b = Servidor("B", falhas=[2, 5, 8, 10])  
servidor_c = Servidor("C", falhas=[5, 10])         


tarefas = range(1, 11)  # 10 tarefas


for tarefa_id in tarefas:
    print(f"\nProcessando tarefa {tarefa_id}...")
    
    if not servidor_b.processar_tarefa(tarefa_id):
        print(f"Tarefa {tarefa_id} atribuída ao servidor C.")
        if not servidor_c.processar_tarefa(tarefa_id):
            print(f"Tarefa {tarefa_id} atribuída ao servidor A.")
            servidor_a.processar_tarefa(tarefa_id)
        else:
            print(f"Tarefa {tarefa_id} concluída pelo servidor C.")
    else:
        print(f"Tarefa {tarefa_id} concluída pelo servidor B.")
