# 🔢 Seletor de Números Interativo (6/60)

Este é um projeto de aplicação web simples, mas altamente interativa, desenvolvido em HTML, CSS (Tailwind CSS) e JavaScript puro, com foco em acessibilidade e múltiplas formas de interação (voz e clique). O objetivo principal é simular a seleção de jogos, onde o usuário escolhe 6 números de um total de 60, com a particularidade de tornar os números usados permanentemente indisponíveis.

## ✨ Funcionalidades

A aplicação foi refinada para oferecer uma experiência de usuário fluida, especialmente para interação por voz:

* **Seleção Híbrida (Voz & Clique):** O usuário pode selecionar números diretamente na grade (clique) ou usando o microfone (Web Speech API).

* **Controle de Repetição:** Possui um contador persistente para repetições de números já selecionados.

  * **Usabilidade Aprimorada:** A repetição imediata por voz do último número selecionado toca o bipe de confirmação (feedback), mas **não** incrementa o contador de repetições, evitando penalidades por falha no feedback sonoro.

* **Assistente de Voz (TTS Contínuo):** Se o limite de repetições for atingido, a aplicação entra em modo de assistência, usando o TTS para verbalizar em *loop* aleatório os números que *ainda estão disponíveis* para seleção.

* **Interrupção Inteligente:** Ao selecionar um número por voz enquanto o TTS está ativo, a fala é imediatamente interrompida, o número é registrado e a fala recomeça com o novo conjunto de números disponíveis.

* **Feedback Sonoro Distinto (Tone.js):**

  * 1 Bipe: Seleção de número.

  * 2 Bipes: Registro de um jogo completo (6 números).

  * 3 Bipes (tom grave): Sinaliza o **encerramento total** do jogo.

* **Regras do Jogo:** Números registrados são marcados como permanentemente **Usados** e são visualmente desabilitados.

* **Encerramento Automático:** Se restarem exatamente 6 números disponíveis, eles são automaticamente selecionados, registrados como o último jogo, o microfone e o TTS são desativados, e os 3 bipes de encerramento são tocados.

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Propósito | 
 | ----- | ----- | 
| **HTML5** | Estrutura da aplicação. | 
| **Tailwind CSS** | Estilização responsiva e moderna. | 
| **JavaScript (Puro)** | Lógica do jogo, controle de estado e DOM. | 
| **Web Speech API** | Reconhecimento de Voz (`SpeechRecognition`) e Síntese de Voz (`SpeechSynthesis` - TTS). | 
| **Tone.js** | Geração precisa e agendada de sons de feedback. | 

## 🚀 Como Usar

1. **Grade de Números:** A grade exibe 60 números em um layout 10x6.

2. **Modo Clique:** Clique em qualquer número disponível para selecioná-lo.

3. **Modo Voz:**

   * Clique em **"🎙️ Ativar Microfone"**.

   * Diga o número que deseja selecionar (ex: "cinco", "vinte e três").

4. **Lista de Jogos:** A lista "Jogos Registrados" cresce à medida que conjuntos de 6 são completados.

## ⚠️ Observações Técnicas

* O reconhecimento de voz exige a permissão do microfone e funciona melhor em navegadores baseados em Chromium (Chrome, Edge).

* O código JavaScript inclui lógica robusta de tratamento de erros e *timeouts* para garantir a estabilidade do ciclo de escuta contínua do microfone, minimizando o `InvalidStateError`.
