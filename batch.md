import time

def process_task(task_id):
    print(f"Processando tarefa {task_id}...")
    time.sleep(2)
    print(f"Tarefa {task_id} concluída.")

tasks = [1, 2, 3, 4, 5]

for task in tasks:
    process_task(task)
