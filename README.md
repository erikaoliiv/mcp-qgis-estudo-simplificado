# Miniguia de Estudos: MCP no QGIS 🗺️🤖

Este repositório contém o Caderno Temático desenvolvido para o desafio de projeto da DIO, explorando o uso da Inteligência Artificial como ferramenta de aprendizagem ativa. O tema escolhido foca na integração do **Model Context Protocol (MCP)** com o **QGIS**, permitindo que modelos de IA (como o Claude) interajam diretamente com o software de geoprocessamento.

---

## 🎯 Contexto e Objetivos

A área de Sistemas de Informação Geográfica (SIG) tradicionalmente exige uma curva de aprendizado acentuada, especialmente quando se trata de automação via scripts (PyQGIS). O **Model Context Protocol (MCP)** surge como uma ponte revolucionária, permitindo que assistentes de IA se conectem a ferramentas locais. 

Ao configurar um servidor MCP no QGIS, é possível instruir a IA em linguagem natural para que ela execute comandos complexos, adicione camadas, aplique simbologias e realize geoprocessamentos diretamente na interface do usuário.

**Objetivos de Estudo:**
1. Compreender a arquitetura básica do Model Context Protocol (MCP).
2. Aprender a configurar a comunicação entre o Claude Desktop e o QGIS.
3. Explorar as capacidades de automação de tarefas geoespaciais utilizando prompts em linguagem natural.
4. Documentar o processo de instalação e os desafios encontrados (troubleshooting).

---

## 📚 Curadoria de Fontes

Para a construção deste caderno temático no NotebookLM, foram selecionadas fontes técnicas e práticas que abordam desde a teoria até a implementação do MCP no QGIS:

| Fonte | Descrição | Link |
| :--- | :--- | :--- |
| **Vídeo Tutorial (YouTube)** | *QGIS MCP - Model Context Protocol Integration*. Demonstração visual e prática da conexão entre o Claude Desktop e o QGIS, mostrando a execução de comandos em tempo real. | [Acessar Vídeo](https://www.youtube.com/watch?v=Uyj6HUcQ6AA) |
| **Repositório Oficial (GitHub)** | *jjsantos01/qgis_mcp*. Repositório contendo o código-fonte do servidor MCP em Python e o plugin necessário para habilitar a escuta no QGIS. | [Acessar Repositório](https://github.com/jjsantos01/qgis_mcp) |
| **Artigo Técnico (El blog de franz)** | *Cómo Configurar un MCP en QGIS con Claude Desktop*. Guia detalhado em texto com o passo a passo da instalação, configuração do arquivo JSON do Claude e requisitos do sistema. | [Acessar Artigo](https://acolita.com/como-configurar-un-mcp-en-qgis-con-claude-desktop/) |

---

## 🛠️ Engenharia de Prompts e "Cicatrizes"

Durante a exploração do tema, diversos prompts foram testados no NotebookLM para extrair resumos, guias de instalação e exemplos de uso. Abaixo estão documentados os testes, resultados e as "cicatrizes" (dificuldades) do processo.

### Teste 1: Compreensão Básica
- **Prompt:** *"Com base nas fontes fornecidas, explique de forma simples o que é o MCP no contexto do QGIS e qual o seu principal benefício."*
- **Resultado:** A IA gerou uma explicação clara, destacando que o MCP atua como um "tradutor" entre a linguagem natural do usuário (via Claude) e os comandos Python (PyQGIS) que o QGIS entende.
- **Cicatriz (Troubleshooting):** Inicialmente, a IA confundiu o MCP com um plugin comum de processamento. Foi necessário refinar o prompt pedindo para focar na *comunicação entre a IA e o software local*.

### Teste 2: Guia de Instalação
- **Prompt:** *"Crie um passo a passo detalhado de como instalar e configurar o QGIS MCP, incluindo a configuração do arquivo JSON no Claude Desktop."*
- **Resultado:** Um tutorial estruturado em 4 passos: Instalação do UV, Instalação do Plugin no QGIS, Configuração do Claude Desktop e Verificação.
- **Cicatriz (Troubleshooting):** A IA omitiu a necessidade de reiniciar o QGIS e o Claude após a configuração do JSON. O prompt precisou ser ajustado para: *"Liste o passo a passo de instalação, dando ênfase aos momentos em que é necessário reiniciar os softwares para evitar erros de conexão."*

### Teste 3: Geração de Casos de Uso
- **Prompt:** *"Quais são 3 exemplos práticos de comandos que posso dar ao Claude para ele executar no QGIS usando essa integração?"*
- **Resultado:** A IA forneceu exemplos excelentes, como: carregar um projeto, adicionar uma camada vetorial e aplicar uma simbologia específica, e executar um algoritmo de geoprocessamento (ex: centroide).

---

## 📖 Miniguia de Estudo (Entrega Final)

### Resumo Estruturado do Assunto

A integração do MCP com o QGIS transforma a maneira como interagimos com dados espaciais. O sistema funciona através de dois componentes principais:
1. **O Plugin QGIS:** Cria um servidor de socket local (geralmente na porta 9876) que fica "escutando" comandos.
2. **O Servidor MCP (Python):** Roda em segundo plano (gerenciado pelo UV) e traduz as intenções do Claude Desktop em scripts PyQGIS válidos, enviando-os para o plugin.

Essa arquitetura permite que tarefas repetitivas, como carregar dezenas de camadas, aplicar estilos padronizados ou rodar rotinas de processamento em lote, sejam feitas com um simples pedido no chat.

### Glossário de Conceitos

| Termo | Definição |
| :--- | :--- |
| **MCP (Model Context Protocol)** | Um padrão de código aberto que permite que assistentes de IA se conectem de forma segura a fontes de dados locais e ferramentas de software. |
| **PyQGIS** | A biblioteca Python do QGIS. É a linguagem usada por baixo dos panos para automatizar tarefas e criar plugins no software. |
| **UV** | Um gerenciador de pacotes e projetos Python extremamente rápido, escrito em Rust. É utilizado para rodar o servidor MCP de forma isolada e eficiente. |
| **Socket Server** | Uma tecnologia de rede que permite a comunicação bidirecional entre dois programas (neste caso, o servidor MCP e o QGIS). |
| **Claude Desktop** | O aplicativo de computador da Anthropic que possui suporte nativo para integrações via MCP. |

### Prompts Reutilizáveis para Revisão

Para futuras revisões ou para expandir o estudo no NotebookLM, utilize os seguintes prompts:

1. *"Aja como um especialista em SIG. Explique como o uso do MCP no QGIS pode reduzir o tempo de treinamento de novos analistas em uma empresa."*
2. *"Gere um script PyQGIS de exemplo que o Claude poderia enviar para o QGIS via MCP para criar um buffer de 50 metros em uma camada selecionada."*
3. *"Quais são as limitações de segurança ao permitir que uma IA execute código Python diretamente no meu ambiente QGIS local?"*
4. *"Crie um quiz de 5 perguntas de múltipla escolha sobre a arquitetura de comunicação entre o Claude Desktop e o plugin QGIS MCP."*

---
*Projeto desenvolvido para o Desafio de Projeto da DIO.*
