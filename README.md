# miniature-doodle
## Python - showing  a students grades in a bar chart
import numpy as np
import matplotlib.pyplot as plt

alunos = []
notas = []
medias = []
legenda = []

valid_incluir_alunos = False

while valid_incluir_alunos == False:
    incluir_alunos = input('Quantos alunos deseja incluir? ')
    try:
        incluir_alunos = int(incluir_alunos)
        if incluir_alunos <= 0:
            print('Valor valores positivos.')
        else:
            valid_incluir_alunos = True
    except:
        print('Valor inválido. Apenas números inteiros.')

num_alunos = 1



while num_alunos <= incluir_alunos:
    nome = input('Insira nome do aluno: ')
    
    valid_nota1 = False
   

    while valid_nota1 == False:
        nota1 = input('Primeira nota do aluno: ')
        try:
            nota1 = float(nota1)
            if nota1 < 0 or nota1 > 10:
                print('Valores precisam estar entre 0 e 10')
            else:
                break
        except:
            
            print('Valor inválido. Algarismos e decimais separados por ponto.')

          
    valid_nota2 = False
    
    while valid_nota2 == False:
        nota2 = input('Segunda nota do aluno: ')
        try:
            nota2 = float(nota2)
            
            if nota2 < 0 or nota2 > 10:
                print('Valores precisam estar entre 0 e 10')
            else:
                break
        except:
            print('Valor inválido. Algarismos e decimais separados por ponto.')
   

    num_alunos += 1
    alunos.append(nome)
    notas.append(nota1)
    notas.append(nota2)
    seq_nome = nome
    legenda.append(seq_nome)
    
    media = (nota1 + nota2) / 2
    
    medias.append(media)

   
plt.rcParams.update({'font.size': 14})


x = np.arange(incluir_alunos)
y = np.random.rand(incluir_alunos)
plt.xlabel('Alunos')
plt.ylabel('Médias')
plt.title('Média dos alunos do 6º ano')
plt.xticks(x,legenda)
plt.grid(True)
plt.ylim(0,10)
plt.yticks([0,0.5,1,1.5,2,2.5,3,3.5,4,4.5,5,5.5,6,6.5,7,7.5,8,8.5,9,9.5,10])
plt.bar(alunos,medias,color='blue')
plt.show()
