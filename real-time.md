import time

def process_task(task_id, priority):
    """
    Processa a tarefa. Se a tarefa tiver prioridade, ela será processada com urgência.
    """
    if priority:
        print(f"Processando TAREFA CRÍTICA {task_id} com prioridade...")
    else:
        print(f"Processando tarefa {task_id}...")
    
    time.sleep(1)  # Simula o tempo de processamento (1 segundo)
    print(f"Tarefa {task_id} concluída.")

tasks = [(1, False), (2, False), (3, True), (4, False), (5, True)]


for task_id, priority in sorted(tasks, key=lambda x: x[1], reverse=True):
    process_task(task_id, priority)
