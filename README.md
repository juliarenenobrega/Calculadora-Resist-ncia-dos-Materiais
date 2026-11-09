Calculadora Estrutural Interativa (Resistência dos Materiais I)

 Uma aplicação desktop desenvolvida em Python com interface gráfica em Tkinter e visualizações em tempo real via Matplotlib, criada para resolver, analisar e visualizar o comportamento mecânico de sistemas estruturais na disciplina de Resistência dos Materiais I.
 Principais Funcionalidades:
 - Esquema Estrutural Dinâmico: Visualização gráfica da viga principal apoiada por barras verticais (BD e CE), com suporte a carregamento pontual configurável.
 - DEIS e Deformação em Tempo Real: Geração automática de gráficos de Esforço Cortante (DEC), Momento Fletor (DMF), Tensão de Flexão e Linha Elástica.
 - Banco de Materiais Integrado: Catálogo com ligas metálicas, madeira e polímeros (com limites de escoamento e módulos de elasticidade tabelados), além de opção de material personalizado.
 - Conversor de Unidades Flexível: Sistema independente de conversão por campo para forças, comprimentos, dimensões geométricas e tensões.

Guia de Uso da InterfaceA interface da aplicação é dividida em três painéis principais:
- Painel Esquerdo (Controles e Entradas):Carregamento e Geometria: Permite ajustar o valor da força concentrada (P), a posição de aplicação (x_P), o comprimento total da viga (L) e as coordenadas das barras de sustentação (x_B e x_C).
- Seções Transversais: Configuração geométrica (Retangular com largura b e altura h, ou Circular com diâmetro d) para a viga principal e para as barras verticais.Pinos e Ligações: Definição dos diâmetros e tipos de cisalhamento (simples ou duplo) nos nós de ligação.
- Seleção de Materiais: Escolha do material em um banco de dados estrutural ou inserção de um módulo de elasticidade (E) customizado.

Painel Central (Visualizações Gráficas - Abas):
- Aba 1 - Esquema Estrutural: Desenho esquemático em escala do modelo mecânico. Permite fazer um duplo clique sobre a tela para alterar rapidamente o valor da carga P.
- Aba 2 - DEIS e Deformação: Exibição empilhada dos quatro gráficos fundamentais da análise estrutural (DEC, DMF, Tensão de Flexão e Linha Elástica).


Painel Direito (Dashboard de Resultados):Apresenta um relatório textual atualizado instantaneamente a cada alteração de parâmetro, exibindo valores de reações de apoio, esforços axiais, alongamentos, momentos máximos e verificação de segurança contra escoamento (\sigma \le \sigma_y).


Fundamentação Teórica: O sistema calcula o comportamento mecânico utilizando os princípios fundamentais da Estática e da Mecânica dos Sólidos 1.

Equilíbrio Estático e Reações de ApoioPara uma viga submetida a uma carga concentrada P e sustentada por duas barras elásticas em B e C, aplicam-se as equações de equilíbrio de corpo rígido:\sum M_B = 0 \implies R_C \cdot (x_C - x_B) - P \cdot (x_P - x_B) = 0 Dessa forma, determinam-se as reações axiais nas barras (F_A e F_B):F_A = P \cdot \frac{x_C - x_P}{x_C - x_B}, \quad F_B = P - F_A2. 

Esforços Internos na Viga (DEC e DMF)O Esforço Cortante (V) e o Momento Fletor (M) ao longo da coordenada longitudinal x da viga são obtidos pelo método das seções (integração das cargas aplicadas):V(x) = \sum F_y, \quad M(x) = \int V(x) dx3. 
Tensões Normais e de Flexão nas barras axiais (Tração/Compressão pura):\sigma = \frac{\vert{}F\vert{}}{A} onde A é a área da seção transversal.Na viga principal (Flexão Pura/Simples):\sigma_{flex} = \frac{\vert{}M\vert{} \cdot y_{max}}{I}onde I é o momento de inércia da seção transversal e y_{max} é a distância da linha neutra à fibra mais externa.4. 
Linha Elástica e DeformaçõesO deslocamento vertical da viga (v) é governado pela equação diferencial da linha elástica:E I \frac{d^2v}{dx^2} = M(x).
A solução numérica é integrada passo a passo a partir da curvatura, impondo as condições de contorno de compatibilidade geométrica com o deslocamento das barras de sustentação em B e C.


Para executar o projeto, é necessário se certificar de ter o Python está instalado.

Instale as dependências necessárias executando no terminal:
pip install numpy matplotlib

Execute o script principal:
python main.py
