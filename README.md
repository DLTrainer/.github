# DLTrainer

DLTrainer é uma organização dedicada a criar uma suíte de ferramentas de código aberto para democratizar e otimizar o fluxo de trabalho de experimentação em Machine Learning. Nosso principal projeto é um aplicativo de desktop e servidor que atua como um estúdio de treinamento de redes neurais, projetado para ser flexível, intuitivo e poderoso.

## 💡 A Grande Ideia
O ciclo de vida do desenvolvimento de modelos de Deep Learning é complexo e fragmentado. Envolve a preparação de dados, definição de arquiteturas, um longo e custoso processo de treinamento, monitoramento e, finalmente, a implantação. O DLTrainer nasceu da necessidade de unificar essas etapas em uma única aplicação coesa e interativa.

Nossa visão é criar um ambiente onde pesquisadores, estudantes e engenheiros possam:
- **Projetar e Configurar**: Selecionar ou construir visualmente arquiteturas de modelos, conectar fontes de dados de maneira simplificada e ajustar todos os hiperparâmetros de treinamento através de uma interface gráfica intuitiva.
- **Treinar com Controle Total**: Iniciar, monitorar, pausar e retomar sessões de treinamento a qualquer momento, liberando o desenvolvedor da necessidade de monitorar constantemente processos de longa duração.
- **Analisar e Iterar em Tempo Real**: Realizar inferências e testes com a melhor versão do modelo enquanto o treinamento ainda está em andamento, permitindo uma validação rápida e um ciclo de iteração muito mais ágil.
- **Manter a Organização Profissional**: Integrar-se nativamente com ferramentas de rastreamento de experimentos de ponta, como MLflow e Neptune.ai, para registrar cada detalhe dos seus projetos, garantindo reprodutibilidade e análise comparativa.

## 🚀 Funcionalidades Principais
- **Interface de Controle Unificada**: Gerencie todos os seus experimentos de um só lugar.
- **Seleção Flexível de Componentes**: Escolha entre modelos, otimizadores, funções de perda e métricas pré-configuradas ou defina as suas próprias.
- **Conectores de Datasets**: Suporte para carregar e pré-processar dados de diversos formatos padrão.
- **Checkpointing Avançado**: Capacidade de pausar e continuar treinamentos, salvando não apenas os pesos do modelo, mas todo o estado do otimizador e do treinamento.
- **Inferência "On-the-Fly"**: Teste o melhor checkpoint do seu modelo em uma interface de inferência dedicada, sem interromper o processo de treinamento.
- **Rastreamento de Experimentos (Experiment Tracking)**: Logging automático de hiperparâmetros, métricas e artefatos para plataformas como MLflow e Neptune.
  
## 🏛️ Visão da Arquitetura
O DLTrainer está sendo construído com uma filosofia de modularidade e flexibilidade, consistindo em um **backend robusto em Python** e uma interface de usuário reativa.
### Backend: O Coração Agnóstico a Frameworks
O núcleo da nossa aplicação é projetado para ser **agnóstico ao framework de Deep Learning**. Reconhecemos que tanto o **PyTorch** quanto o **TensorFlow** possuem ecossistemas e vantagens únicas. Em vez de forçar o usuário a escolher um, nosso backend é construído sobre uma **Camada de Abstração de Treinamento (Training Abstraction Layer - TAL)**.

**Como funciona?**

- **Interface Comum**: A lógica de negócio da aplicação (iniciar, pausar, logar) se comunica com a TAL através de um conjunto definido de comandos (`tal.train()`, `tal.pause()`, `tal.get_best_model()`).
- **Adaptadores de Framework**: A TAL, por sua vez, utiliza "adaptadores" específicos para cada framework. Quando um usuário inicia um treinamento em PyTorch, a TAL delega a execução para o `PyTorchAdapter`, que traduz os comandos para a sintaxe do PyTorch e do PyTorch Lightning. Se o usuário escolher TensorFlow, o `TensorFlowAdapter` entra em ação, utilizando as APIs do Keras.

Essa abordagem nos permite:
- **Máxima Flexibilidade**: Permitir que o usuário utilize o framework com o qual se sente mais confortável ou que seja mais adequado para um projeto específico.
- **Manutenção Simplificada**: Isolar a lógica específica de cada framework, facilitando a atualização para novas versões do PyTorch ou TensorFlow sem quebrar a aplicação principal.
- **Extensibilidade**: Facilitar a adição de suporte para novos frameworks de ML no futuro (como o JAX).

### Frontend: Uma Interface Web Moderna e Local
A interface do usuário será desenvolvida para ser intuitiva e informativa. As tecnologias em consideração incluem:
- **Prototipagem Rápida**: Streamlit ou Gradio para as fases iniciais e para criar demos rapidamente.
- **Frontend hospedado localmente**: Um servidor web leve será executado em sua máquina, tornando a interface acessível através do seu navegador preferido (ex: `http://localhost:8501`).

## 🛠️ Pilha de Tecnologia
- **Linguagem Principal**: Python 3.9+
- **Frameworks de ML**: PyTorch, TensorFlow/Keras
- **Estruturas de Treinamento**: PyTorch Lightning, Keras Callbacks
- **Rastreamento de Experimentos**: MLflow, Neptune.ai
- **Manipulação de Dados**: Pandas, NumPy, Scikit-learn
- **Interface (Potencial)**: Streamlit, Gradio, PyQt

## 🗺️ Roteiro do Projeto (Roadmap)
- **Fase 1 (Núcleo)**: Desenvolvimento do backend com a Camada de Abstração de Treinamento (TAL). Implementação das funcionalidades de treinamento, checkpointing e logging para PyTorch e TensorFlow através de scripts de linha de comando.
- **Fase 2 (Interface Inicial)**: Criação de uma interface web básica com Streamlit/Gradio para validar o fluxo de trabalho de ponta a ponta de forma interativa.

## 🤝 Como Contribuir
O DLTrainer é um projeto de código aberto e damos as boas-vindas a contribuições de todos os tipos. Seja você um desenvolvedor, um engenheiro de ML ou um designer, há um lugar para você aqui. Por favor, consulte nosso guia `CONTRIBUTING.md` (a ser criado) para mais detalhes sobre como se envolver.
