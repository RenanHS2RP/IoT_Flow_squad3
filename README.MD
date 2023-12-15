# Projeto de IoT integrado com Mecatrônica.

## Índice
- [Descrição](#descrição)
- [Projetos](#projetos)
- [Capturas de Tela](#capturas-de-tela)
- [Pré-requisitos](#pré-requisitos)
- [Instalação](#instalação)
- [Inicialização](#inicialização)
- [Uso](#uso)

## [Video Pitch](https://drive.google.com/file/d/1j4uJrHLrrpB4-vBhnNiWlpJUyzlEzYYj/view?usp=sharing)

## Descrição
Este é um projeto realizado pela turma de ADS da Escola e Faculdade Técnica SENAI Gaspar Ricardo Jr. com o objetivo de criar uma integração com dois projetos da turma de Mecatrônica. Isso resultou na criação de uma interface, uma API e uma integração específica para cada projeto.

## Projetos:
- ### **[Sensor de Combustível](https://github.com/RenanHS2RP/IoT_Flow_squad3/):**
    - *Descrição do Projeto:*
        - O projeto "Sensor de Combustível" tem como finalidade considerar o preço pago e a quantidade de combustível emitido pela bomba, comparando com o que foi realmente recebido e o preço correto de acordo com o posto.
        - O preço e a quantidade emitida pela bomba serão informados pelo cliente, também terão os dados conferidos pelo sensor, estes são enviados para uma API, que esta, calculará e enviará o valor correto para o aplicativo mobile.

### Projetos relacionados:

- **[Janela Automática](https://github.com/RenanHS2RP/IoT_Window_squad3/):**
    - *Descrição do Projeto:*
        - O projeto "Janela Automática" tem como objetivo automatizar uma janela, tomando ações com base nas condições climáticas. Se a previsão indicar alta probabilidade de chuva e ela realmente ocorrer, a janela será fechada; caso contrário, ela será aberta.
        - Para isso, sensores de umidade e dados de previsão do tempo de uma API externa serão utilizados. Um painel no ThingsBoard exibirá gráficos relacionados à probabilidade de chuva, histórico de aberturas e fechamentos, além de alertas sobre o estado da janela.

## Pré-requisitos
Para executar nosso projeto, é recomendado:
- Acesso à um computador ou laptop
- Uma IDE como Visual Studio Code
- Conhecimento básico em terminais
- Conhecimento básico em envio de JSON
- Ter um celular com Expo Go instalado

## Instalação
- Copie este repositório com o comando `git clone --recurse-submodules https://github.com/RenanHS2RP/IoT_Flow_squad3.git` em uma pasta que desejar usando o terminal.

### Frontend
1. No terminal, navegue até o repositório com o comando `cd /IoT_Flow_squad3/codigo/front/flow_app_mobile`.
2. Execute o comando `npm install` ou `npm i` para instalar todas as dependências do projeto.
3. Seu Frontend de IoT_Flow_squad3 estará instalado e pronto para rodar.

### Backend
- *Nota: O Backend está hospedado em: [Xquad3.pythonanywhere.com](Xquad3.pythonanywhere.com), em dezembro de 2023, não é efetivamente necessário rodar a API localmente para interagir com ela.*
1. No terminal, navegue até o repositório com o comando `cd /IoT_Flow_squad3/codigo/back/FlowAPIProject`.
2. Execute o comando `python manage.py makemigrations` para criar migrações.
3. Execute o comando `python manage.py migrate` para migrar.

## Inicialização
### Frontend
- Para iniciar a interface, execute o comando npx expo start. Um código QR será gerado, e ao escaneá-lo com a câmera, a página da interface será aberta utilizando o Expo Go.
### Backend
- Execute o comando `python manage.py runserver` para iniciar a API em: [http://127.0.0.1:8000/](http://127.0.0.1:8000/).

## Uso
### Frontend

Ao acessar o QR code com um celular e com o Expo Go instalado, você será direcionado para a página principal:

<img src="/assets/imgMob1.jpeg" alt="Tela inicial/root Mobile" width="40%">

Nesta página, você encontrará dois campos para inserir os valores, que serão fornecidos pela bomba de combustível: o montante total pago pela gasolina e a quantidade informada pela bomba. Dessa forma, o valor pago por litro será calculado e exibido.

Ao clicar no ícone do painel de controle, localizado na parte inferior da página, você será redirecionado para a segunda tela:

<img src="/assets/imgMob2.jpeg" alt="Tela inicial/root Mobile" width="40%">

Nessa página, serão apresentados os litros captados pelo sensor, uma resposta com base nos valores inseridos anteriormente e um gráfico que mostra a quantidade de litros inserida a cada segundo.

### Backend
- Tanto no host [local](http://127.0.0.1:8000/) ou [online](Xquad3.pythonanywhere.com), ao acessar a página será exibido dois caminhos:

![Tela inicial/root API](/assets/img1.png)

1. **Pump** [[local]](http://127.0.0.1:8000/pump/) [[online]](http://xquad3.pythonanywhere.com/pump/): Nestas URLs serão exibidos métodos para listar (GET) e inserir (POST). Se desejar deletar (DELETE) ou atualizar (PUT), será necessário uma busca específica, basta adicionar o ID do JSON escolhido no final da URL, exemplo: `http://xquad3.pythonanywhere.com/pump/1` ou `http://127.0.0.1:8000/pump/`.
2. Para adicionar um JSON ao banco de dados, pode-se ser adicionado pela interface gráfica. Na parte inferior, os campos: Litros totais (litros totais adicionados na bomba de combustível) e Preço por litro (preço pago por cada litro).
3. Também há outros dois modos de envio, ambos por JSON. Na aba Raw data, pode ser enviado um JSON ou, caso já tenha um maior conhecimento sobre ferramentas auxiliares como Postman, pode ser feita esta inserção com JSON. Um exemplo de inserção através deste método:
```JSON
{
    "litros_totais": 60,
    "preco_por_litro": 5.19
}
```

![Tela Pump input da API](/assets/img2.0.png)
![Tela Pump input da API](/assets/img2.png)
![Tela Pump input da API](/assets/img2.1.png)

1. **Sensor** [[local]](http://127.0.0.1:8000/sensor/) [[online]](http://xquad3.pythonanywhere.com/sensor/): Nestas URLs serão exibidos métodos para listar (GET) e inserir (POST). Se desejar deletar (DELETE) ou atualizar (PUT), será necessário uma busca específica, basta adicionar o ID do JSON escolhido no final da URL, exemplo: `http://xquad3.pythonanywhere.com/sensor/1` ou `http://127.0.0.1:8000/sensor/1`.
2. Para adicionar um JSON ao banco de dados, pode-se ser adicionado pela interface gráfica. Na parte inferior (em cao de muitos dados use a barra de rolagem lateral), os campos: Tempo operacao (Tempo em que o sensor captou fluidos), Litros totais (litros totais adicionados) e Litros por minuto (mostra quantos litros a bomba inseriu por minuto).
3. Também há outros dois modos de envio, ambos por JSON. Na aba Raw data, pode ser enviado um JSON ou, caso já tenha um maior conhecimento sobre ferramentas auxiliares como Postman, pode ser feita esta inserção com JSON. Um exemplo de inserção através deste método:
```JSON
{
  "tempo_operacao": "2023-12-07T12:30:00",
  "litros_totais": 50.5,
  "litros_por_minuto": 2.3
}
```

![Tela Sensor input da API](/assets/img3.0.png)
![Tela Sensor input da API](/assets/img3.png)
![Tela Sensor input da API](/assets/img3.1.png)