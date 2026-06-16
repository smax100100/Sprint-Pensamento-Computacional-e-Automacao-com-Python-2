ChargeGrid Intelligence da GoodWe

Gestão inteligente de frotas e estações de recarga de veículos elétricos em ambientes Comercial & Industrial
Sobre o projeto
O ChargeGrid Intelligence é a camada de inteligência da GoodWe para o gerenciamento de infraestrutura de carregamento de VEs em ambientes C&I. Ele conecta o hardware de recarga (inversores + carregadores) ao sistema de gestão de energia (SEMS+), permitindo operação otimizada, tarifação automática e integração com fontes renováveis.
Este repositório documenta a Prova de Conceito desenvolvida na Sprint 2 do GoodWe Challenge, com foco em demonstração funcional das soluções propostas na Sprint 1.

Problema resolvido
Ambientes C&I com múltiplos carregadores de VE enfrentam quatro desafios críticos:
ProblemaImpactoSobrecarga de demanda elétricaMultas por ultrapassagem do limite contratadoFalta de padronização de protocolosLock-in tecnológico, frotas mistas sem gestão unificadaCobrança manual fragmentadaInconsistências financeiras e perda de receitaUX comprometida do motoristaFilas, falhas de autenticação, falta de visibilidade

Soluções implementadas

1 — Controle de Demanda (Solução Central)
Monitoramento em tempo real do consumo total (prédio + VEs). Quando a demanda se aproxima de 90% do limite contratado, o sistema reduz automaticamente a potência dos carregadores ativos via lógica condicional.
SE demanda_total > 90% × limite_contratado
   ENTÃO reduzir potência dos carregadores (throttling)
SE excedente_solar > 0
   ENTÃO priorizar recarga com energia fotovoltaica
2 — Billing Automatizado (Middleware)
Cada sessão de recarga é rastreada por RFID. Ao término, o sistema aplica a tarifa vigente (ponta/fora ponta via tabela ANEEL) e gera o faturamento automaticamente, sem intervenção humana.
SE sessão encerrada ∧ usuário autenticado via RFID
   ENTÃO calcular custo = kWh × tarifa_horária
   ENTÃO acionar gateway de pagamento
3 — IA Preditiva
Análise de padrões históricos (horários de chegada/partida, consumo por rota, tarifas ANEEL) para gerar recomendações diárias de horário ideal de recarga. Prioriza janelas com maior geração solar e menor tarifa de rede.
4 — Gateway OCPP
Tradução dos dados proprietários do ecossistema GoodWe para o padrão aberto OCPP 1.6J, permitindo integração com qualquer plataforma corporativa de back-office de carregadores.


Prova de Conceito — Dashboard Interativo

A PoC é um dashboard web em HTML/CSS/JavaScript que simula em tempo real o funcionamento do ChargeGrid Intelligence.
Funcionalidades demonstradas:
Monitoramento de demanda com atualização a cada 2 segundos
6 pontos de recarga com status dinâmico (ativo, throttled, livre, manutenção)
Cálculo automático de custo por sessão com tarifa ponta/fora ponta
Geração solar simulada com excedente calculado dinamicamente
Recomendações da IA atualizadas em tempo real
Status do Gateway OCPP
Botões para simular pico de demanda e injeção de solar

   
Pensamento computacional aplicado

PrincípioAplicaçãoDecomposição4 pilares independentes: Demanda, Protocolos, Tarifação, IAReconhecimento de padrõesPicos simultâneos como causa raiz de todos os problemasAbstraçãoAPI SEMS+ como interface única; hardware tratado como caixa pretaDesign de algoritmosEstruturas condicionais (SE/ENTÃO) implementadas na PoC

GoodWe Challenge — Sprint 2

Integrantes:
Josué Franco Braga RM569174
Andrei Henrique Santos RM569440
Heitor Maxímus Mucha RM571407
Enrico Marinho de Aquino RM569338
Fernando Lobato Rodrigues RM569377
Manoel da Silva Ferreira RM572045

Links

Vídeo de apresentação Sprint 2:
Quadro Kanban do projeto:
