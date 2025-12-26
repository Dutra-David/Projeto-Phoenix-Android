

AGENTS.md# ⚡️ PROJECT PHOENIX – DOUTRINA OFICIAL DE AGENTES ⚡️

Comandante Supremo: General David Dutra  
Aplicativo: Project Phoenix (Android, Kotlin, Jetpack Compose)  
Função: Agente Autônomo Multi-Função, Multi-Agente e Auto-Evolutivo

---

## 1. VISÃO GERAL

Project Phoenix não é "só um app".  
É um SISTEMA MULTI-AGENTE rodando no Android, projetado para:

- Automatizar tarefas no dispositivo (via AccessibilityService).
- Responder dúvidas técnicas (programação, IA, engenharia de prompt, linguagens).
- Interagir por voz (fala e escuta).
- Usar câmera de forma controlada.
- Auto-melhorar código, arquitetura e experiência com apoio de IAs avançadas (Gemini Agent Mode, etc.), sempre sob comando do General.

---

## 2. PAPÉIS DOS AGENTES INTERNOS

### 2.1 PhoenixOrchestrator (Orquestrador)

- Função: "Cérebro tático".
- Recebe requisições de alto nível do General (ex.: "automatiza X", "explica Y", "melhora Z").
- Decide quais agentes internos devem atuar:
  - ActionAgent
  - KnowledgeAgent
  - VoiceAgent
  - OptimizationAgent
- Consolida o resultado e reporta ao General em linguagem simples.

### 2.2 PhoenixActionAgent

- Interface com o sistema via AccessibilityService.
- Tarefas:
  - Observar a tela (hierarquia de UI).
  - Entender elementos clicáveis, campos de texto, listas, etc.
  - Executar ações (click, preencher texto, rolar).
- Toda ação é:
  - Autorizada pelo usuário.
  - Registrada em log para auditoria.
- Obedece estritamente às políticas de acessibilidade do Android (nada de comportamento de malware).

### 2.3 PhoenixKnowledgeAgent

- Responsável pelo NÚCLEO DE CONHECIMENTO.
- Usa:
  - Banco local (Room) com conhecimento sobre:
    - Programação
    - IA
    - Engenharia de Prompt
    - Linguagens de programação
  - Módulo opcional de sincronização online (para atualizar/expandir conteúdo quando autorizado).
- Atende:
  - Perguntas feitas via texto.
  - Perguntas ditadas por voz (quando VoiceAgent está ativo).

### 2.4 PhoenixVoiceAgent

- Interface de VOZ do Phoenix.
- Tarefas:
  - Falar (Text-to-Speech – TTS) respostas importantes.
  - Ouvir (Speech-to-Text – STT) comandos do General.
- Sempre:
  - Pede permissão de microfone com explicação.
  - Só grava/processa áudio quando há ação explícita do usuário.

### 2.5 PhoenixOptimizationAgent

- "Engenheiro residente" de auto-melhoria.
- Observa:
  - Logs de erros.
  - Métricas de performance.
  - Uso de recursos (CPU, memória, bateria).
  - Freqüência de uso de funcionalidades.
- Em modo conectado com IA externa (como Gemini Agent Mode), é usado para:
  - Sugerir refatorações.
  - Aplicar melhorias de código e arquitetura.
  - Validar se as mudanças realmente melhoram o sistema (build, testes, análise).

### 2.6 PhoenixVisionAgent (Futuro / Câmera)

- Usa CameraX + Compose para:
  - Mostrar preview da câmera.
  - Tirar fotos sob comando.
- Toda captura é:
  - Visível ao usuário.
  - Armazenada de forma controlada.
- Preparado para, no futuro, processar imagens com IA (quando o General autorizar).

---

## 3. PRINCÍPIOS DE ARQUITETURA

- Base: Recomendações oficiais da arquitetura Android (camadas claras: UI, Domain, Data).
- DI: Hilt ou equivalente para injeção de dependência.
- Banco local: Room, offline-first.
- Tarefas em background: WorkManager, com foco em bateria.
- Segurança:
  - Permissões em tempo de execução com explicação clara.
  - Dados sensíveis (logs, perfil do General, chaves) protegidos com criptografia.

---

## 4. PERFIL DO GENERAL (PERSONALIZAÇÃO)

O app mantém um "Perfil do General" local para personalizar o comportamento:

- Preferências:
  - Modo de interação (voz, texto, misto).
  - Estilo de resposta (mais técnico, didático, militar).
- Padrões de uso:
  - Quais módulos são mais usados (automação, conhecimento, voz, etc.).
- Uso:
  - Orquestrador ajusta quais agentes priorizar com base nesse perfil.
  - UI adapta o que destacar primeiro.

Tudo isso é guardado localmente, com possibilidade de criptografia, sem envio automático para servidores.

---

## 5. FLUXOS TÍPICOS

### 5.1 Automação de tarefa

1. General dá um comando (texto ou voz).
2. Orquestrador identifica que é uma ação no dispositivo.
3. Aciona PhoenixActionAgent:
   - Lê a tela.
   - Encontra elementos relevantes.
   - Propõe ou executa a sequência de ações.
4. Logs são registrados para auditoria (e para PhoenixOptimizationAgent aprender).

### 5.2 Pergunta técnica (programação, IA, prompt, linguagens)

1. General faz uma pergunta.
2. Orquestrador passa a consulta ao PhoenixKnowledgeAgent.
3. KnowledgeAgent:
   - Busca no banco local Room.
   - Usa IA on-device (se disponível) para melhorar resposta/resumo.
4. VoiceAgent (se ativo) pode ler a resposta em voz alta.

### 5.3 Ciclo de auto-melhoria

1. General ordena um "ciclo de auto-melhoria Phoenix".
2. PhoenixOptimizationAgent:
   - Coleta métricas, logs, pontos fracos.
   - Monta diagnóstico.
3. Em conjunto com IA externa (Gemini Agent Mode, etc.), são:
   - Propostas mudanças de código/arquitetura.
   - Aplicadas refatorações.
   - Rodados testes.
4. Resultado é documentado:
   - O que mudou.
   - Por que é melhor.
   - Próximos passos.

---

## 6. REGRAS PARA QUALQUER IA QUE EDITAR ESTE PROJETO

1. Sempre respeitar a hierarquia de agentes (Orquestrador → agentes especializados).
2. Nunca introduzir:
   - Auto-modificação do APK em runtime.
   - Coleta/envio de dados sem autorização explícita do General.
3. Para mudanças grandes:
   - Propor um plano antes.
   - Executar em passos pequenos, com validação (build/teste) entre eles.
4. Sempre explicar ao General em linguagem simples:
   - O que foi feito.
   - Por que foi feito.
   - Como usar.

---

## 7. MENSAGEM AO ENGENHEIRO DE PROMPT (GENERAL DAVID DUTRA)

Você não precisa ser programador.  
Sua função é:

- Definir MISSÕES (prompts) claras.
- Dizer o que você quer que o Phoenix faça:
  - Automatizar.
  - Ensinar.
  - Conversar.
  - Melhorar-se.
- Deixar as IAs (Gemini, etc.) executarem dentro destas regras.

Qualquer agente de IA que ler este AGENTS.md deve:
- Tratar você como comandante.
- Respeitar a doutrina acima.
- Entregar código compilável, limpo e explicável.

> **Estado atual: Phoenix em operação.**  
> **Pronto para novas ordens do General.**
