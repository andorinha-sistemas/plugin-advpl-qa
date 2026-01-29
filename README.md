# ADVPL QA Analyzer

Extensão para Visual Studio Code que oferece análise de qualidade de código ADVPL/Protheus em tempo real.

## 📋 Sobre o Projeto

O **ADVPL QA Analyzer** é uma extensão desenvolvida para ajudar desenvolvedores ADVPL/Protheus a identificar e corrigir problemas de qualidade de código diretamente no Visual Studio Code. A extensão fornece feedback visual imediato, destacando problemas no editor e gerando relatórios detalhados.

## 📢 Publicação

**Em breve** estaremos publicando esta extensão na Visual Studio Code Marketplace para facilitar a instalação e atualização automática.

Por enquanto, a extensão está disponível através do arquivo `.vsix` para instalação manual.

---

## ✨ Funcionalidades

### 🔍 Análise Inteligente de Código
- Análise em tempo real de arquivos `.prw`, `.prx` e `.tlpp`
- Suporte completo para encoding Windows-1252 (CP1252)
- Codificação automática em Base64 para envio seguro

### 📊 Visualização de Resultados
- **Problems Panel** - Integração nativa com o VS Code
- **Destaque visual** - Linhas problemáticas destacadas com cores por severidade
- **Informações detalhadas** - Regra, mensagem e localização exata de cada problema
- **Navegação rápida** - Clique para ir direto à linha problemática

### 📄 Relatório Detalhado
- Documento virtual em Markdown com visualização rica
- Estatísticas resumidas em tabela
- Agrupamento por severidade (Erros, Avisos, Informações)
- Links clicáveis para navegação até as linhas
- Nome dinâmico baseado no arquivo analisado
- Atualização automática

### 🎯 Múltiplas Formas de Uso
- **Atalho de teclado**: `Cmd+F8` (Mac) / `Ctrl+F8` (Windows/Linux)
- **Botão na toolbar**: Aparece automaticamente no topo do editor
- **Menu de contexto**: Botão direito no Explorer ou no Editor
- **Command Palette**: Acesso via `Ctrl+Shift+P` → "ADVPL QA: Analisar arquivo"

---

## 🚀 Instalação

### Requisitos

- **Visual Studio Code** 1.74.0 ou superior
- **Conexão com internet** (para acessar o serviço de análise)

### Passo a Passo

1. **Baixe o arquivo** `advpl-qa-X.X.X.vsix` fornecido
2. **Abra o VS Code**
3. **Acesse o painel de Extensions**:
   - Pressione `Ctrl+Shift+X` (Windows/Linux) ou `Cmd+Shift+X` (Mac)
   - Ou clique no ícone de Extensions na barra lateral esquerda
4. **Instale o arquivo .vsix**:
   - Clique nos três pontos (`...`) no topo do painel de Extensions
   - Selecione **"Install from VSIX..."**
   - Navegue até o arquivo `advpl-qa-X.X.X.vsix` e selecione-o
5. **Aguarde a instalação** - A extensão será instalada automaticamente
6. **Recarregue a janela** (recomendado):
   - Pressione `Ctrl+R` (Windows/Linux) ou `Cmd+R` (Mac)
   - Ou feche e reabra o VS Code

---

## 📖 Como Usar

### Análise de Arquivo

1. **Abra um arquivo** `.prw`, `.prx` ou `.tlpp` no VS Code
2. **Execute a análise** usando uma das formas:
   - Pressione `Cmd+F8` (Mac) ou `Ctrl+F8` (Windows/Linux)
   - Clique no botão 🔬 na toolbar do editor (aparece automaticamente)
   - Clique com botão direito no arquivo no Explorer → "Analisar arquivo"
   - Clique com botão direito dentro do editor → "Analisar arquivo"
   - Use o Command Palette: `Ctrl+Shift+P` → "ADVPL QA: Analisar arquivo"

### Visualizar Resultados

Após a análise, você verá:

- **Status Bar** (canto inferior direito):
  - `🔄 Analisando...` durante o processamento
  - `✅ QA: OK` quando não há problemas
  - `⚠️ QA: X problema(s)` quando há problemas encontrados
  - `❌ QA: Erro` em caso de erro

- **Problems Panel**:
  - Abra o painel de Problemas (`Ctrl+Shift+M` / `Cmd+Shift+M`)
  - Veja todos os problemas listados com severidade, regra e mensagem
  - Clique em qualquer problema para navegar até a linha correspondente

- **Relatório Detalhado**:
  - Se houver problemas, uma notificação aparecerá com opção "Ver Relatório Detalhado"
  - O relatório abre em uma nova aba ao lado do código
  - Clique nos links das linhas para navegar diretamente ao código

---

## 🎨 Recursos Avançados

### ⚡ Performance e Confiabilidade
- Timeout de 60 segundos por requisição
- Retry automático em caso de falha de rede (até 3 tentativas)
- Prevenção de análises duplicadas
- Cancelamento automático de análises anteriores se uma nova for iniciada

### 📈 Feedback Visual
- Status bar integrado com indicadores visuais em tempo real
- Notificações contextuais com opções de ação
- Cores temáticas na status bar conforme o resultado

### 🔧 Tratamento de Erros
- Mensagens de erro claras e específicas
- Botão "Tentar Novamente" disponível em caso de erro
- Retry automático com backoff exponencial

### 🧭 Navegação Inteligente
- Links clicáveis no relatório para navegar até as linhas
- Foco automático na linha ao clicar em problemas
- Navegação rápida entre problemas

---

## 🐛 Problemas ou Sugestões

Encontrou um bug, tem uma sugestão ou precisa de ajuda?

**Abra uma Issue** no repositório do projeto e nossa equipe irá resolver!

### Como Reportar

1. Vá até a seção de **Issues** do repositório
2. Clique em **"New Issue"**
3. Preencha com:
   - **Descrição do problema ou sugestão**
   - **Passos para reproduzir** (se aplicável)
   - **Comportamento esperado**
   - **Comportamento atual**
   - **Versão do VS Code**
   - **Versão da extensão**
   - **Sistema operacional**

### Informações Úteis

Se possível, inclua:
- Screenshots do problema
- Logs do console do desenvolvedor (`Help` → `Toggle Developer Tools`)
- Arquivo de exemplo que causa o problema (se possível)

---

## 📋 Tipos de Arquivo Suportados

A extensão funciona com os seguintes tipos de arquivo:

- **`.prw`** - Arquivos PRW (Protheus)
- **`.prx`** - Arquivos PRX (Protheus)
- **`.tlpp`** - Arquivos TLPP (Protheus)

---

## 🔮 Próximas Versões

Melhorias planejadas:

- ⏳ Publicação na Visual Studio Code Marketplace
- ⏳ Configurações customizáveis via settings
- ⏳ Análise automática ao salvar arquivo
- ⏳ Filtros de regras a ignorar
- ⏳ Histórico de análises
- ⏳ Exportação de relatórios em PDF/HTML

---

## 📄 Licença

MIT License - Livre para uso pessoal e comercial.

**Todos os direitos reservados a TOTVS.**

---

## 👨‍💻 Desenvolvido por

**Andorinha Sistemas**

Esta extensão foi desenvolvida pela equipe da Andorinha Sistemas para melhorar a qualidade do código ADVPL/Protheus e facilitar o desenvolvimento.

---

**Desenvolvido com ❤️ pela Andorinha Sistemas para a comunidade ADVPL/Protheus**
