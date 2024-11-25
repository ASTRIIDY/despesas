# python-calculador_despesas.py
def main():
    print("Bem-vindo ao Calculador de Despesas!")
    
    # Entrada de renda
    renda = float(input("Digite sua renda mensal: R$ "))
    
    despesas = []  # Lista para armazenar as despesas
    categorias = {}  # Dicionário para resumir por categoria
    
    while True:
        print("\nAdicione uma despesa:")
        descricao = input("Descrição: ")
        valor = float(input("Valor (R$): "))
        categoria = input("Categoria (ex.: alimentação, transporte): ").lower()
        
        # Adiciona a despesa à lista
        despesas.append({"descricao": descricao, "valor": valor, "categoria": categoria})
        
        # Atualiza o total da categoria
        if categoria in categorias:
            categorias[categoria] += valor
        else:
            categorias[categoria] = valor
        
        # Pergunta se deseja adicionar mais despesas
        continuar = input("Deseja adicionar outra despesa? (s/n): ").lower()
        if continuar != "s":
            break
    
    # Calcula o total de despesas
    total_despesas = sum(despesa["valor"] for despesa in despesas)
    saldo = renda - total_despesas
    
    # Saída dos resultados
    print("\n--- Resumo ---")
    print(f"Renda Mensal: R$ {renda:.2f}")
    print(f"Total de Despesas: R$ {total_despesas:.2f}")
    print(f"Saldo Restante: R$ {saldo:.2f}")
    
    print("\nDespesas por Categoria:")
    for categoria, total in categorias.items():
        print(f"  - {categoria}: R$ {total:.2f}")
    
    print("\nObrigado por usar o Calculador de Despesas!")

if __name__ == "__main__":
    main()
