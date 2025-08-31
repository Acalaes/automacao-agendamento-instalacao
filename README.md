# automacao-agendamento-instalacao
Workflow n8n que captura solicitações de instalação via formulário e notifica a equipe no Slack, priorizando agendamentos para os próximos 7 dias.`
# Automação de Agendamento de Instalação

Este repositório contém o código-fonte de um workflow desenvolvido na plataforma n8n, projetado para gerenciar e priorizar solicitações de instalação de serviços.

## Resumo da Solução

O objetivo deste software é automatizar o processo de recebimento de pedidos de instalação. Ele utiliza um formulário web como ponto de entrada, avalia a urgência do pedido com base na data de preferência do cliente e notifica a equipe interna através do Slack para uma ação rápida.

## Como Funciona

O fluxo de trabalho segue uma lógica clara e sequencial para garantir que nenhuma solicitação seja perdida e que os pedidos urgentes sejam tratados com prioridade.

1.  **Gatilho: Recebimento de Formulário (`On form submission`)**
    *   O processo é iniciado quando um cliente preenche e envia o formulário "Solicite uma Instalação".
    *   Os dados capturados são o **E-mail** do cliente e a **Data de preferência para Instalação**.

2.  **Condição: Análise de Urgência (`Esta dentro de 7 dias?`)**
    *   O sistema verifica se a data de preferência informada pelo cliente está dentro de um intervalo de 7 dias a partir da data atual.
    *   Esta é a principal regra de negócio para determinar a prioridade do atendimento.

3.  **Ação (Caso Verdadeiro): Notificação no Slack (`Send a message`)**
    *   Se a data solicitada for para os próximos 7 dias, uma mensagem de alta prioridade é enviada para o canal `#social` no Slack.
    *   A notificação inclui o e-mail de contato e a data sugerida, permitindo que a equipe de agendamento atue imediatamente.

4.  **Ação (Caso Falso): A Fazer (`Fazer`)**
    *   Se a data solicitada for para depois de 7 dias, o workflow atualmente termina neste ponto. A lógica para agendamentos de baixa prioridade será implementada em versões futuras.

## Próximos Passos / Melhorias Futuras

A estrutura atual permite expansões futuras, como:
*   Enviar um e-mail de confirmação para o cliente.
*   Adicionar o agendamento a um Google Calendar.
*   Para solicitações com mais de 7 dias, adicionar os dados a uma planilha do Google Sheets para contato futuro.

## Como Usar

1.  Faça o download do arquivo `My workflow.json` deste repositório.
2.  Em sua instância do n8n, vá em `Import > From File` e selecione o arquivo.
3.  Configure as credenciais do nó do Slack para conectar à sua conta.
4.  Ative o workflow.

## Propriedade Intelectual

Este software foi desenvolvido por Alexandre P Calaes. O histórico de versões e o resumo hash de cada alteração estão registrados nos commits deste repositório Git, servindo como prova de anterioridade para fins de registro de propriedade intelectual junto ao INPI.
