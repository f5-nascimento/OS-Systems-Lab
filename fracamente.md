import time
import threading

def node_task(id, task_id):
    print(f"Nó {id} iniciando processamento da TAREFA {task_id} independente...")
    time.sleep(2)
    print(f"Nó {id} completou a TAREFA {task_id}.")

task_ids = [1, 2, 3, 4]
nodes = [threading.Thread(target=node_task, args=(i, task_id)) for i, task_id in enumerate(task_ids)]

for node in nodes:
    node.start()

for node in nodes:
    node.join()

print("Todas as tarefas distribuídas foram concluídas.")
