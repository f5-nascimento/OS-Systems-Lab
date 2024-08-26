import time
import threading

def primary_task(task_id):
    print(f"Processador principal executando TAREFA {task_id} crítica de I/O...")
    time.sleep(2)
    print(f"Processador principal completou a TAREFA {task_id} de I/O.")

def secondary_task(id, master, task_id):
    print(f"Processador secundário {id} aguardando autorização do processador principal para TAREFA {task_id}...")
    master.join()  # Espera o processador principal completar sua tarefa
    print(f"Processador secundário {id} executando TAREFA {task_id}.")

# Criação da tarefa do processador principal
master_task_id = 1
master_thread = threading.Thread(target=primary_task, args=(master_task_id,))

# Criação das tarefas dos processadores secundários
secondary_task_ids = [2, 3, 4]
secondary_threads = [threading.Thread(target=secondary_task, args=(i, master_thread, task_id)) for i, task_id in enumerate(secondary_task_ids)]

# Início da execução
master_thread.start()
for thread in secondary_threads:
    thread.start()

# Aguarda a conclusão de todas as threads
master_thread.join()
for thread in secondary_threads:
    thread.join()

print("Todas as tarefas foram concluídas.")
