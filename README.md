triatlon = []
atleta = []
listanatacao = []
listacorrida = []
listaciclismo = [] 

atletas = 0

print ('MENU')
print('1: INSERIR ATLETA')
print("2. Relatório - Melhores Tempos")
print("3. Relatório - Melhor Atleta")
print("4. Relatório - Abaixo da Média")
print("0. Sair")

while True:
  try:
    opcao = int(input("Escolha uma opção: "))
    if opcao == 0:
      print('saindo do programa')
      break
    elif opcao < 0 or opcao > 4:
      print('Opção inválida')
    # Fazer cadastro
    elif opcao == 1:
      print(f'Atleta {atletas + 1}:')
      nome = input('Nome:')
      patrocinador = input('Patrocínio:')
      temponatacao = float(input('Tempo na natação:'))
      listanatacao.append(temponatacao)
      tempocorrida = float(input('Tempo na corrida:'))
      listacorrida.append(tempocorrida)
      tempociclismo = float(input('Tempo no ciclismo:'))
      listaciclismo.append(tempociclismo)
      dia = int(input('Dia:'))
      mes = int(input('Mês:'))
      ano = int(input('Ano:'))
      atleta = [nome, patrocinador, temponatacao,  tempocorrida,tempociclismo,  dia, mes, ano]
      triatlon.append(atleta)
      atletas += 1
      print('Atleta cadastrado com sucesso!')
    elif opcao == 2:
      # Relatório de melhor tempo
      melhornatacao = min(listanatacao)
      melhorescorrida = min(listacorrida)
      melhoresciclismo = min(listaciclismo)
      print(f'Melhor tempo na natação: {melhornatacao}')
      print(f'Melhor tempo na corrida: {melhorescorrida}')
      print(f'Melhor tempo no ciclismo: {melhoresciclismo}')
    elif opcao == 3:
      # Relatório do melhor atleta
      tempo_total = []
      for atleta in triatlon:
        tempo_total.append(atleta[2] + atleta[3] + atleta[4])
      indice_melhor_tempo = tempo_total.index(min(tempo_total))
      melhor_atleta = triatlon[indice_melhor_tempo]
      print(f'Melhor atleta: {melhor_atleta[0]}')
      print(f'Patrocinador: {melhor_atleta[1]}')
    elif opcao == 4:
      # ralatório abaixo da média
      tempo_total = []
      for atleta in triatlon:
        tempo_total.append(atleta[2] + atleta[3] + atleta[4])
      media_tempo = sum(tempo_total)/len(tempo_total)
      for atleta in triatlon:
        if atleta[2] + atleta[3] + atleta[4] < media_tempo:
          print(f'Atleta abaixo da média: {atleta[0]}')
          print(f'Patrocínio de {atleta[0]}: {atleta[1]}')
  except ValueError:
    print('Opção inválida')
