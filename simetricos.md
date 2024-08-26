import time
import threading

def task(id, task_id):
    print(f"Processador {id} executando TAREFA {task_id}...")
    time.sleep(2)
    print(f"Processador {id} completou TAREFA {task_id}.")

# Criação das tarefas para os processadores
task_ids = [1, 2, 3, 4]
threads = [threading.Thread(target=task, args=(i, task_id)) for i, task_id in enumerate(task_ids)]

# Início da execução
for thread in threads:
    thread.start()

# Aguarda a conclusão de todas as threads
for thread in threads:
    thread.join()

print("Todas as tarefas foram concluídas.")
