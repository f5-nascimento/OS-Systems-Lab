import time

def process_task(task_id):
    print(f"Processando tarefa {task_id}...")
    time.sleep(2)  # Simula o tempo de processamento da tarefa
    print(f"Tarefa {task_id} concluída.")

# Lista de tarefas
tasks = [1, 2, 3, 4, 5]

# Processamento em batch
for task in tasks:
    process_task(task)
