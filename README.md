# Portfólio · PCP, dados e automação na indústria

Aqui descrevo os projetos que desenvolvo como Analista de PCP. Também há uma **demonstração navegável** do hub de indicadores, montada só com **dados fictícios**.

🔗 **Demo:** https://guicollalincoln-glitch.github.io/portfolio-pcp/

> Os sistemas reais rodam dentro da empresa e usam dados internos. Por isso, este repositório não tem código, planilhas, nomes de máquinas nem números reais. A demo gera dados aleatórios no próprio navegador.

---

## 1. Hub de Indicadores da Produção

**Problema:** os indicadores da produção ficavam espalhados em planilhas e relatórios diferentes, e cada área olhava um número diferente.

**Solução:** um app único, aberto no navegador e no celular, que reúne:

- **Programado × Realizado:** quanto do sequenciamento do dia foi feito, medido pelas peças boas de cada OP.
- **Hora x Hora:** a linha do tempo do programado contra o apontado, com justificativa das OPs não feitas.
- **Carga Máquina:** demanda contra capacidade por máquina, célula e B.U, mês a mês.
- **Controle de Horas e WIP**, além de uma **Fábrica 3D** com a planta colorida pelo status de cada máquina.
- **Visão por perfil:** gerência, coordenador, líder e turno. Cada líder vê só as máquinas e o turno dele.
- **Assistente de IA:** responde perguntas usando os dados do próprio indicador.

**Tecnologias:** Python (pandas) para tratar os dados · HTML/JavaScript · Three.js · Cloudflare Workers · Workers AI

## 2. Automação da Coleta de Dados de Produção

**Problema:** atualizar os indicadores dependia de exportar relatórios do ERP manualmente.

**Solução:** um robô agendado que, a cada 30 minutos:

1. coleta os apontamentos do ERP;
2. trata e valida os dados, desconta apontamentos esquecidos abertos e horas sobrepostas;
3. recalcula todos os indicadores e publica o app;
4. envia alertas ao Teams quando há OPs atrasadas.

**Tecnologias:** Python · RPA · Agendador de Tarefas do Windows · webhooks do Teams

## 3. Análise de Carga Máquina

- Cruza OPs firmes e a projeção do MRP com a capacidade de cada máquina.
- Usa calendário por B.U, feriados e sábados trabalhados.
- Guarda "fotos" do relatório ao longo do mês para comparar o que entrou, saiu, foi antecipado ou postergado.
- Corrige automaticamente fotos que vêm sem data limite, usando as fotos vizinhas.

## 4. Indicador de WIP

Mostra as peças paradas entre processos, há quantos dias estão paradas e quanto desse WIP está sequenciado. Mantém um histórico diário para acompanhar a tendência.

## 5. Implantação do Siemens Opcenter APS · key user

Participei da construção, dos testes e da validação do sequenciamento junto ao time de projetos até o go-live.

---

### Sobre a demo

`index.html` é um arquivo único, sem bibliotecas, que gera uma fábrica fictícia com 21 máquinas e mostra:

- visão geral do cumprimento do programa;
- carga máquina por mês;
- programado × realizado com filtro por líder e turno;
- um "assistente" simples que responde a partir dos dados fictícios.

Feito por **Guilherme Lincoln** · [LinkedIn](https://www.linkedin.com/in/guilherme-henrique-colla-lincoln-0361a01b9)
