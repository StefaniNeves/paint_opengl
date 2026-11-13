🎨 Paint OpenGL - Editor Gráfico Interativo

Um editor gráfico 2D completo desenvolvido em C com OpenGL/GLUT, implementando criação, seleção e transformação de objetos geométricos com sistema avançado de undo/redo.

📋 Funcionalidades

🎯 Objetos Primitivos

- Pontos - Criação com clique simples
- Linhas - Definidas por dois pontos
- Polígonos - Lista circular de vértices com fechamento automático

🖱️ Sistema de Seleção Inteligente

- Pontos: Distância euclidiana com tolerância ajustável
- Linhas: Distância mínima ponto-segmento
- Polígonos: Algoritmo Ray Casting para formas côncavas e complexas

🔄 Transformações Geométricas (Matrizes 3x3)

- Translação - Movimento em X/Y
- Rotação - Em torno do centro (linhas/polígonos) ou origem (pontos)
- Escala - Redimensionamento proporcional
- Reflexão - Espelhamento em eixos X/Y
- Cisalhamento - Deformação controlada

Todas as transformações utilizam matrizes homogêneas 3x3 com composição matemática.

⏪ Sistema Undo/Redo Avançado

- Stack de 50 operações com histórico detalhado
- Cálculo automático de matrizes inversas
- Validação de objetos existentes
- Suporte a todas as transformações

💾 Persistência de Dados

- Salvar/Carregar objetos em formato texto
- Validação robusta de arquivos
- Tratamento de erros e corrupção
- Limpeza automática ao carregar

🎬 Sistema de Animação

- Movimento contínuo de todos os objetos
- Controle de direção e velocidade
- Atualização suave em tempo real

🎮 Controles

Criação de Objetos

Tecla| Função
"P"| Modo Ponto
"L"| Modo Linha
"G"| Modo Polígono
"Enter"| Fechar Polígono

Seleção e Transformação

Tecla| Função
"S"| Modo Seleção
"R" / "r"| Rotação ±15°
"T"| Translação (20px)
"E"| Escala (1.2x)
"F"| Reflexão (eixo X)
"C"| Cisalhamento
"Setas"| Movimento preciso (10px)
"Scroll"| Escala variável

Sistema Undo/Redo

Tecla| Função
"U"| Desfazer (Undo)
"Y"| Refazer (Redo)
"Z"| Limpar histórico
"Q"| Status do histórico

Arquivo e Outros

Tecla| Função
"V"| Salvar objetos
"W"| Carregar objetos
"I"| Iniciar animação
"A"| Parar animação
"D"| Deletar selecionado
"+" / "-"| Ajustar tolerância
"H"| Mostrar/ocultar ajuda

🏗️ Arquitetura

Estruturas de Dados

- Listas Ligadas para flexibilidade dinâmica
- Listas Circulares para vértices de polígonos
- Stack de Transformações para undo/redo
- Matrix Stack hierárquico (32 níveis)

Módulos Principais

📁 src/
├── main.c              # Inicialização e loop principal
├── objetos.c/h         # Estruturas e criação de objetos
├── render.c/h          # Sistema de renderização OpenGL
├── eventos.c/h         # Gerenciamento de entrada
├── selecao.c/h         # Algoritmos de seleção
├── transformacoes.c/h  # Sistema de matrizes e transformações
├── undo_system.c/h     # Sistema avançado de undo/redo
├── animacao.c/h        # Sistema de animação
└── arquivo.c/h         # Persistência de dados

Algoritmos Implementados

- Ray Casting para seleção de polígonos
- Cálculo de matriz inversa para undo
- Composição de matrizes para transformações
- Detecção de colisão ponto-linha otimizada

🚀 Como Executar

Pré-requisitos

# Ubuntu/Debian
sudo apt-get install build-essential freeglut3-dev

# Fedora/CentOS
sudo dnf install gcc freeglut-devel

# Windows (MinGW)
# Instalar FreeGLUT manualmente

Compilação

# Clone o repositório
git clone https://github.com/ViniRamon1/paint-opengl.git
cd paint-opengl

# Compile usando Makefile
make

# Execute
./paint

Makefile

CC = gcc
CFLAGS = -Wall -Wextra -std=c99
LIBS = -lGL -lGLU -lglut -lm

OBJS = main.o render.o objetos.o eventos.o selecao.o transformacoes.o \
       animacao.o arquivo.o undo_system.o

paint: $(OBJS)
	$(CC) -o paint $(OBJS) $(LIBS)

%.o: %.c %.h
	$(CC) $(CFLAGS) -c $<

clean:
	rm -f *.o paint

📊 Especificações Técnicas

- Linguagem: C (C99)
- Gráficos: OpenGL 2.1 + GLUT
- Resolução: 1000x800 pixels
- Coordenadas: Sistema 2D homogêneo
- Memória: Alocação dinâmica com listas ligadas
- Performance: 60 FPS com centenas de objetos

🧪 Funcionalidades Avançadas

Matrix Stack Hierárquico

Sistema profissional similar ao OpenGL com 32 níveis de transformações aninhadas:

MATRIX_PUSH(stack);
    TRANSLATE(stack, 100, 50);
    ROTATE(stack, 45);
    SCALE(stack, 2.0, 2.0);
    aplicarMatrixStack(stack, objeto, tipo);
MATRIX_POP(stack);

Sistema Undo Robusto

- Validação automática de objetos deletados
- Histórico com descrições ("Rotação 15°", "Translação (10, 5)")
- Proteção contra overflow com deslocamento inteligente

Algoritmos Otimizados

- Ray Casting com proteção contra casos extremos
- Cálculo de centro geométrico para formas complexas
- Detecção de loops infinitos em listas circulares

🎓 Contexto Acadêmico

Desenvolvido em equipe para a disciplina de Computação Gráfica na UFCA (Universidade Federal do Cariri), este projeto demonstra a implementação de conceitos fundamentais:

- Transformações geométricas 2D
- Algoritmos de seleção e colisão
- Estruturas de dados para gráficos
- Sistemas de desfazer/refazer
- Persistência de dados gráficos

👩‍💻 Minha Contribuição

Stéfani Rodrigues Neves

Projeto desenvolvido em equipe, no qual fui responsável pela implementação de funcionalidades importantes do editor gráfico:

- Criação de objetos primitivos: desenvolvimento das funções responsáveis pela criação dos elementos geométricos do Paint, incluindo pontos, linhas e polígonos.
- Salvar e carregar arquivos: implementação das funções de persistência de dados, permitindo salvar os objetos criados em arquivos e carregá-los posteriormente.

Minha participação envolveu o desenvolvimento dessas funcionalidades, contribuindo para a construção e o funcionamento do editor gráfico.

📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo "LICENSE" para mais detalhes.

🤝 Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para:

1. Fazer fork do projeto
2. Criar uma branch para sua feature ("git checkout -b feature/AmazingFeature")
3. Commit suas mudanças ("git commit -m 'Add some AmazingFeature'")
4. Push para a branch ("git push origin feature/AmazingFeature")
5. Abrir um Pull Request

---

⭐ Se este projeto te ajudou, considere dar uma estrela!
