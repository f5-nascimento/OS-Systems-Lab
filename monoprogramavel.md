import time

def tarefa_1():
    print("Iniciando Tarefa 1...")
    for i in range(5):
        print(f"Tarefa 1 em execução: Passo {i + 1}/5")
        time.sleep(1)  # Simula um tempo de execução longo
    print("Tarefa 1 concluída.")

def tarefa_2():
    print("Iniciando Tarefa 2...")
    for i in range(3):
        print(f"Tarefa 2 em execução: Passo {i + 1}/3")
        time.sleep(1)  # Simula um tempo de execução longo
    print("Tarefa 2 concluída.")

# Simulação de um sistema monoprogramável
tarefa_1()  # Executa a Tarefa 1
tarefa_2()  # Executa a Tarefa 2 somente após a conclusão da Tarefa 1
