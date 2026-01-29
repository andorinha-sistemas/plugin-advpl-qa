# ADVPL QA Analyzer

Extensão para Visual Studio Code que oferece análise de qualidade de código ADVPL/Protheus em tempo real.

## 📋 Sobre o Projeto

O **ADVPL QA Analyzer** é uma extensão desenvolvida para ajudar desenvolvedores ADVPL/Protheus a identificar e corrigir problemas de qualidade de código diretamente no Visual Studio Code. A extensão fornece feedback visual imediato, destacando problemas no editor e gerando relatórios detalhados.

## 📢 Publicação

**Em breve** estaremos publicando esta extensão na Visual Studio Code Marketplace para facilitar a instalação e atualização automática.

Por enquanto, a extensão está disponível através do arquivo `.vsix` para instalação manual.

---

## 🎯 Funcionalidades

### Análise de Código
- Análise em tempo real de arquivos `.prw`, `.prx` e `.tlpp`
- Suporte completo para encoding Windows-1252 (CP1252)
- Codificação automática em Base64 para envio seguro

### Visualização de Resultados
- **Problems Panel** - Integração nativa com o VS Code
- **Destaque visual** - Linhas problemáticas destacadas com cores por severidade
- **Informações detalhadas** - Regra, mensagem e localização exata de cada problema
- **Navegação rápida** - Clique para ir direto à linha problemática

### Relatório Detalhado
- Documento virtual em Markdown com visualização rica
- Estatísticas resumidas em tabela
- Agrupamento por severidade (Erros, Avisos, Informações)
- Links clicáveis para navegação até as linhas
- Nome dinâmico baseado no arquivo analisado
- Atualização automática

### Múltiplas Formas de Uso
- Atalho de teclado: `Cmd+F8` (Mac) / `Ctrl+F8` (Windows/Linux)
- Botão na toolbar do editor
- Menu de contexto no Explorer
- Menu de contexto no Editor
- Command Palette

## 🏗️ Estrutura do Projeto

```
extensao-vscode-qa/
├── src/
│   └── extension.ts          # Código principal da extensão
├── scripts/
│   ├── install.js             # Script de instalação automática
│   └── version-bump.js        # Script para incrementar versão
├── out/                        # Código compilado (gerado)
├── package.json               # Manifesto da extensão
├── tsconfig.json              # Configuração TypeScript
├── .vscodeignore              # Arquivos ignorados no pacote
├── .gitignore                 # Arquivos ignorados no Git
├── build-and-install.sh       # Script shell para build e instalação
├── README.md                  # Este arquivo
└── RELEASE.md                 # Notas de release
```

## 🛠️ Tecnologias Utilizadas

- **TypeScript** - Linguagem de programação
- **VS Code Extension API** - API oficial do Visual Studio Code
- **Node.js** - Runtime environment
- **HTTP/HTTPS** - Comunicação com serviços externos

## 🚀 Como Desenvolver

### Pré-requisitos

- **Node.js** 16.x ou superior
- **Visual Studio Code** 1.74.0 ou superior
- **npm** ou **yarn**

### Configuração do Ambiente

1. **Clone o repositório**:
   ```bash
   git clone <url-do-repositorio>
   cd extensao-vscode-qa
   ```

2. **Instale as dependências**:
   ```bash
   npm install
   ```

3. **Compile o projeto**:
   ```bash
   npm run compile
   ```

### Executar em Modo de Desenvolvimento

1. **Abra o projeto no VS Code**:
   ```bash
   code .
   ```

2. **Pressione F5** para iniciar uma nova janela do VS Code com a extensão carregada

3. **Teste a extensão** na nova janela:
   - Abra um arquivo `.prw`, `.prx` ou `.tlpp`
   - Execute o comando de análise
   - Verifique os resultados

### Scripts Disponíveis

- `npm run compile` - Compila o TypeScript para JavaScript
- `npm run watch` - Compila e observa mudanças (modo watch)
- `npm run version-bump` - Incrementa a versão automaticamente
- `npm run package` - Incrementa versão + gera pacote `.vsix`
- `npm run install-extension` - Instala a extensão automaticamente
- `npm run build-and-install` - Compila + empacota + instala (tudo em um)

### Debugging

1. Abra o projeto no VS Code
2. Pressione `F5` para iniciar o debug
3. Uma nova janela do VS Code será aberta com a extensão carregada
4. Use `console.log()` no código para debug
5. Os logs aparecerão no **Debug Console** da janela original

### Estrutura do Código

#### `src/extension.ts`

Arquivo principal contendo toda a lógica da extensão:

- **Interfaces TypeScript**: Definições de tipos para resposta da API
- **ReportProvider**: Classe que gera relatórios em Markdown
- **Função `activate()`**: Ponto de entrada da extensão
- **Função `analyzeFile()`**: Lógica principal de análise
- **Função `sendToApi()`**: Comunicação com serviço externo
- **Função `displayResults()`**: Exibição de problemas no Problems Panel

#### `package.json`

Manifesto da extensão contendo:
- Metadados (nome, versão, descrição)
- Comandos registrados
- Menus e keybindings
- Definições de linguagens
- Scripts de build

## 📝 Arquitetura

### Fluxo de Análise

1. Usuário aciona a análise (atalho, botão ou menu)
2. Extensão valida o arquivo (extensão `.prw`, `.prx` ou `.tlpp`)
3. Conteúdo do arquivo é codificado em Base64
4. Requisição HTTP POST é enviada
5. Resposta é processada e convertida para diagnósticos
6. Problemas são exibidos no Problems Panel
7. Relatório detalhado é gerado e disponibilizado

### Componentes Principais

- **DiagnosticCollection**: Gerencia problemas exibidos no Problems Panel
- **StatusBarItem**: Exibe status da análise na barra de status
- **ReportProvider**: Gera conteúdo do relatório virtual
- **Debounce Timer**: Previne análises duplicadas
- **Request Cancellation**: Cancela requisições pendentes

## 🔧 Configurações e Constantes

### Constantes Principais

```typescript
const DEFAULT_TIMEOUT = 60000;      // 60 segundos
const MAX_RETRIES = 3;              // Máximo de tentativas
const DEBOUNCE_DELAY = 500;         // 500ms de debounce
```

### Encoding

A extensão utiliza **Windows-1252 (CP1252)** via `latin1` para compatibilidade total com ADVPL/Protheus, garantindo que caracteres acentuados sejam exibidos corretamente.

## 🧪 Testes

Para testar a extensão:

1. Compile o projeto: `npm run compile`
2. Execute em modo debug: `F5`
3. Na nova janela, abra um arquivo de teste
4. Execute a análise e verifique:
   - Problemas aparecem no Problems Panel
   - Status bar mostra o resultado
   - Relatório pode ser visualizado
   - Navegação até linhas funciona

## 📦 Empacotamento

Para criar um pacote `.vsix` para distribuição:

```bash
npm run package
```

Isso irá:
1. Incrementar a versão automaticamente
2. Compilar o código
3. Gerar o arquivo `.vsix`

O arquivo será criado na raiz do projeto com o nome `advpl-qa-X.X.X.vsix`.

## 🐛 Reportar Problemas

Encontrou um bug ou tem uma sugestão? Abra uma **Issue** no repositório!

### Como Reportar

1. Vá até a seção de **Issues** do repositório
2. Clique em **"New Issue"**
3. Preencha o template com:
   - **Descrição do problema**
   - **Passos para reproduzir**
   - **Comportamento esperado**
   - **Comportamento atual**
   - **Versão do VS Code**
   - **Versão da extensão**
   - **Sistema operacional**

### Informações Úteis para Debug

Se possível, inclua:
- Logs do console do desenvolvedor (`Help` → `Toggle Developer Tools`)
- Screenshots do problema
- Arquivo de exemplo que causa o problema (se possível)

## 🤝 Contribuindo

Contribuições são bem-vindas! Para contribuir:

1. Faça um **Fork** do repositório
2. Crie uma **branch** para sua feature (`git checkout -b feature/MinhaFeature`)
3. Faça suas alterações
4. **Commit** suas mudanças (`git commit -m 'Adiciona MinhaFeature'`)
5. **Push** para a branch (`git push origin feature/MinhaFeature`)
6. Abra um **Pull Request**

### Padrões de Código

- Use **TypeScript** com tipos explícitos
- Siga as convenções do VS Code Extension API
- Adicione comentários para código complexo
- Mantenha funções pequenas e focadas

## 📚 Recursos e Documentação

### Documentação Oficial

- [VS Code Extension API](https://code.visualstudio.com/api)
- [Extension Guidelines](https://code.visualstudio.com/api/references/extension-guidelines)
- [Contribution Points](https://code.visualstudio.com/api/references/contribution-points)

### Conceitos Utilizados

- **Text Document Content Provider**: Para relatórios virtuais
- **Diagnostic Collection**: Para problemas no Problems Panel
- **Status Bar API**: Para feedback visual
- **Command API**: Para comandos da extensão
- **Menu Contributions**: Para menus de contexto

## 📄 Licença

MIT License - Livre para uso pessoal e comercial.

**Todos os direitos reservados a TOTVS.**

## 👨‍💻 Desenvolvido por

**Andorinha Sistemas**

Esta extensão foi desenvolvida pela equipe da Andorinha Sistemas para melhorar a qualidade do código ADVPL/Protheus e facilitar o desenvolvimento.

---

## 🔮 Roadmap

Melhorias planejadas para futuras versões:

- ⏳ Configurações customizáveis via settings
- ⏳ Análise automática ao salvar arquivo
- ⏳ Filtros de regras a ignorar
- ⏳ Histórico de análises
- ⏳ Exportação de relatórios em PDF/HTML
- ⏳ Suporte para múltiplos arquivos simultâneos
- ⏳ Cache de resultados

---

**Desenvolvido com ❤️ pela Andorinha Sistemas para a comunidade ADVPL/Protheus**
