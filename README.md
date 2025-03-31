## TRABALGO DE CALC 2
---
## ALUNO: GABRIEL FERRARI
---
## TURMA : V01
---
**OBJETIVO:** COMPLETAR AS ATIVIDADES "A)" E "B)" DO EXERCÍCIO 1 , SEÇÃO 3.1 
---
```
import pandas as pd
import sympy as sp
import numpy as np
import matplotlib.pyplot as plt

def menu():
    while True:
        print("\nA constante 'e' pode ser provada de 3 formas principais:\n")
        print("1 - Economicamente")
        print("2 - Binômio de Newton")
        print("3 - Limite")
        print("4 - Estatisticamente")
        print("0 - Sair")
        
        try:
            resp = int(input("Indique a abordagem que deseja abaixo: "))
            if resp <4 and resp>=0:
                return resp
            else:
                print("Opção inválida, tente novamente.")
        except ValueError:
            print("Entrada inválida! Digite um número entre 0 e 4.")

# ----------------------------------------------------------------------------------------------------

def Eco():
    print("\t\tJuros Compostos\t\t")
   
  
    print("Jacob Bernoulli descobriu esta constante em 1683, enquanto estudava uma questão sobre juros compostos:\n\n")
    print("Uma conta começa com $ 1,00 e paga 100% de juros ao ano. Se os juros forem creditados uma vez, no final do ano, o valor da conta no final do ano será de $ 2,00.")
    print("O que acontece se os juros forem calculados e creditados com mais frequência durante o ano?")
    print("Jacob Bernoulli descobriu esta constante em 1683 enquanto estudava juros compostos.\n")
    
    # Simulação de crescimento de juros compostos
    P = float(input("Valor do investimento: "))
    r = float(input("Taxa de juros anual (em decimal, ex: 0.05 para 5%): "))
    t = int(input("Tempo (em anos): "))

    n_values = [1, 4, 12, 52, 365, 1000]  # Diferentes frequências de capitalização
    valores_finais = [P * (1 + r/n)**(n*t) for n in n_values]

    plt.plot(n_values, valores_finais, marker='o', label="Montante final")
    plt.xlabel("Frequência de capitalização")
    plt.ylabel("Valor final do investimento")
    plt.title("Crescimento do investimento com diferentes capitalizações")
    plt.legend()
    plt.grid()
    plt.show()

    print("Bernoulli observou que essa sequência se aproxima de um limite à medida que n aumenta e, assim, intervalos de rendimento diminuem")
    print("Com rendimento semanal (n = 52), o valor atinge $ 2,692596..., enquanto com rendimento diário (n = 365) atinge $ 2,714567... (aproximadamente dois centavos a mais). O limite à medida que n cresce é o número que ficou conhecido como e. Ou seja, com rendimentos contínuos, o valor da conta atinge $ 2,718281828... ")
    print("De maneira mais geral, uma conta que começa com um dólar e oferece uma taxa de juros anual de R, após t anos, resultará em eRt dólares com capitalização contínua. Aqui, R é a equivalência decimal da taxa de juros expressa em porcentagem, de modo que, para 5% de juros, R = 5/100 = 0,05.")

# ----------------------------------------------------------------------------------------------------

def Bi():
    
    print("Os primeiros registros de uso da letra e para a constante, por Leonhard Euler, são de 1727 ou 1728, em um artigo não publicado sobre forças explosivas em canhões, e em uma carta para Christian Goldbach em 25 de novembro de 1731. A primeira aparição de e em uma publicação impressa foi em Mechanica de Euler (1736).É desconhecido o motivo pelo qual Euler escolheu a letra e.")
    print("Embora alguns pesquisadores tenham usado a letra c nos anos subsequentes, a letra e era a mais comum e tornou-se a padrão.")
    print("Com isso, Euler provou que 'e' é a soma da série infinita \n")
    print("\nEuler provou que 'e' é a soma da série infinita:\n")
    print("e = 1 + 1/1! + 1/2! + 1/3! + 1/4! + ...\n")

    n = int(input("Digite o número de termos para a aproximação de e: "))
    e_aprox = sum([1/np.math.factorial(i) for i in range(n)])

    print(f"Aproximação de 'e' com {n} termos: {e_aprox:.6f}")

    # Gráfico da série
    x = np.arange(1, n+1)
    y = [sum([1/np.math.factorial(i) for i in range(j)]) for j in x]

    plt.plot(x, y, marker='o', label="Aproximação de e")
    plt.axhline(y=np.e, color='r', linestyle='--', label="Valor real de e")
    plt.xlabel("Número de termos")
    plt.ylabel("Valor aproximado de e")
    plt.title("Aproximação de e pela série de Euler")
    plt.legend()
    plt.grid()
    plt.show()

# ----------------------------------------------------------------------------------------------------

def Limit():
    print("\nO número e pode ser definido pelo limite:\n")
    print("e = lim (1 + 1/n)^n à medida que n -> infinito\n")
    print("sendo essa expressão oriunda da análise de juros compostos.")

    n_vals = [1, 10, 100, 1000, 10000]
    e_vals = [(1 + 1/n)**n for n in n_vals]

    for n, e_aprox in zip(n_vals, e_vals):
        print(f"Para n = {n}, e ≈ {e_aprox:.6f}")

    # Plotando gráfico
    plt.plot(n_vals, e_vals, marker='o', linestyle='-', label="Aproximação de e")
    plt.axhline(y=np.e, color='r', linestyle='--', label="Valor real de e")
    plt.xscale("log")
    plt.xlabel("Valor de n")
    plt.ylabel("Valor aproximado de e")
    plt.title("Aproximação de e pelo limite (1 + 1/n)^n")
    plt.legend()
    plt.grid()
    plt.show()

# ----------------------------------------------------------------------------------------------------

def Estat():
    
     print("Outra aplicação de 'e', também descoberta em parte por Jacob Bernoulli junto com Pierre Rémond de Montmort, está no problema de desarranjos:\n\n")
        
     print("'n' convidados são convidados para uma festa 'e', à entrada, os convidados entregam seus chapéus ao mordomo, que por sua vez coloca os chapéus em 'n' caixas, cada uma rotulada com o nome de um convidado. ")
     print("No entanto, o mordomo não perguntou as identidades dos convidados 'e's', portanto, coloca os chapéus em caixas selecionadas aleatoriamente.\n\n") 
     print("O problema de Montmort é encontrar a probabilidade de nenhum dos chapéus ser colocado na caixa certa.") 
     print("Essa probabilidade, denotada por pn, é dada por:\n\n")
  
     print("pn= (-1)^n/n!\n\n")
  
     print("Quando n tende a infinito, pn se aproxima de 1/e.")
     print("Além disso, o número de maneiras que os chapéus podem ser colocados nas caixas de forma que nenhum fique na caixa correta é o inteiro mais próximo de n!/e, para todo n positivo")
  
     print("\nO número e aparece em probabilidades e estatísticas:\n")
     print("Exemplo: A probabilidade de nenhum chapéu estar na caixa correta é aproximadamente 1/e.\n")

     n = int(input("Digite um valor para n: "))
     p_n = (-1)**n / np.math.factorial(n)
     print(f"Para n = {n}, a probabilidade aproximada é {p_n:.6f}")

     # Gráfico
     x = np.arange(1, n+1)
     y = [(-1)**i / np.math.factorial(i) for i in x]

     plt.plot(x, y, marker='o', label="Probabilidade p_n")
     plt.axhline(y=1/np.e, color='r', linestyle='--', label="1/e")
     plt.xlabel("Valor de n")
     plt.ylabel("Probabilidade p_n")
     plt.title("Probabilidade de nenhum chapéu estar na caixa correta")
     plt.legend()
     plt.grid()
     plt.show()

# ----------------------------------------------------------------------------------------------------

def LIMITES():
    print("\n\t\tCalculadora de Limites\t\t\n")
 
    print("É preciso calcular esses dois limites e dizer o que acontece com a constante e:\n\n")
  
    print("lim 2,7^h -1/ h")
    print("h->0\n\n")
    
    print("lim 2,8^h -1/ h")
    print("h->0\n\n")
 

    h = sp.symbols('h')
    limite_27 = sp.limit((2.7**h - 1) / h, h, 0)
    limite_28 = sp.limit((2.8**h - 1) / h, h, 0)

    print(f"lim (2.7^h - 1) / h quando h -> 0 = {limite_27}")
    print(f"lim (2.8^h - 1) / h quando h -> 0 = {limite_28}")

    # Gráfico ilustrativo
    h_vals = np.linspace(-0.1, 0.1, 100)
    y_27 = (2.7**h_vals - 1) / h_vals
    y_28 = (2.8**h_vals - 1) / h_vals

    plt.plot(h_vals, y_27, label="(2.7^h - 1)/h", color="blue")
    plt.plot(h_vals, y_28, label="(2.8^h - 1)/h", color="green")
    plt.axhline(y=limite_27, color='r', linestyle='--', label="Limite de 2.7^h")
    plt.axhline(y=limite_28, color='purple', linestyle='--', label="Limite de 2.8^h")
    plt.xlabel("h")
    plt.ylabel("Valor da função")
    plt.title("Comportamento dos limites")
    plt.legend()
    plt.grid()
    plt.show()

# ----------------------------------------------------------------------------------------------------

def main():

 resp=menu()
 while resp<4 or resp>0:
    match resp:
     case 0:
       print("Saindo...")
       break

     case 1:
        Eco()
        break
     case 2:
       Bi()
       break
     case 3:
       Limit()
       break
     case 4:
       Estat()
       break
    print("\nQuestão 1 / b)")
    LIMITES()
 

main()
```
--
