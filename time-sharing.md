import time

def process_task(task_id, time_slice, remaining_time):
    """
    Processa a tarefa por um determinado tempo e retorna o tempo restante.
    """
    print(f"Tarefa {task_id} processando por {time_slice} segundos...")
    time.sleep(time_slice)
    remaining_time -= time_slice
    print(f"Tarefa {task_id} parcialmente concluída. Tempo restante: {max(remaining_time, 0)} segundos.")
    return remaining_time

tasks = [(1, 5), (2, 5), (3, 5)]  # Lista de tarefas com seu tempo total necessário

time_slice = 2  # Tempo alocado por vez (2 segundos)

while any(remaining_time > 0 for _, remaining_time in tasks):
    for i, (task_id, remaining_time) in enumerate(tasks):
        if remaining_time > 0:
            tasks[i] = (task_id, process_task(task_id, min(time_slice, remaining_time), remaining_time))
        if tasks[i][1] <= 0 and remaining_time > 0:
            print(f"Tarefa {task_id} concluída.")
