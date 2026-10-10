---
name: notas-fiscais
description: Emitir, consultar e cancelar notas fiscais de serviço (NFS-e) pelo iNotaFiscal. Use quando a pessoa pedir para emitir nota, ver notas, saber o saldo do plano ou cancelar uma nota da empresa dela no Simples Nacional.
---

# Notas fiscais de serviço com o iNotaFiscal

O iNotaFiscal emite NFS-e no sistema nacional para empresas do Simples Nacional (MEI incluído). As tools vêm do conector iNotaFiscal.

## Antes de emitir

1. Se a pessoa tem mais de uma empresa, pergunte por qual emitir (listar_empresas mostra as empresas e o CNPJ). Nunca escolha por ela.
2. Ache o cliente: listar_clientes com parte do nome. Cliente que não está lá entra pelo CNPJ (o nome vem da Receita) ou pelo CPF com o nome da pessoa.
3. O valor é o que a pessoa disse, em reais. Não arredonde, não calcule imposto e não invente valor.
4. O serviço padrão é o da nota mais recente. Se a pessoa falar de outro serviço, use listar_servicos e pergunte qual.

Nunca invente campo fiscal (valor, cliente, serviço, alíquota, código). Na dúvida, pergunte.

## Emitir

1. preparar_nota devolve o resumo. Mostre o resumo inteiro para a pessoa, do jeito que veio, inclusive avisos ("Atenção: já existe...") e a marca de demonstração.
2. Só chame emitir_nota depois de a pessoa confirmar aquele resumo. Repita o valor e o nome do cliente exatamente como o resumo mostrou.
3. Se a resposta vier "Em emissão" ou "Conferindo com o sistema nacional", diga isso. Não peça a nota de novo: o mesmo pedido continua valendo. Para saber depois, use consultar_nota.
4. Nota recusada: explique o motivo que veio na resposta e o que fazer.

## Cancelar

1. listar_notas para achar a nota (número, cliente, valor).
2. preparar_cancelamento com o motivo: 1 erro na emissão, 2 serviço não prestado, 9 outro (com uma frase de justificativa).
3. Mostre o resumo e avise que a nota cancelada não volta. Só chame cancelar_nota depois da confirmação, com o número da nota do resumo.

## PDF e XML

consultar_nota devolve os links do PDF e do XML, que valem 24 horas. Se a pessoa quiser a nota no WhatsApp (para encaminhar ao cliente, por exemplo), use enviar_nota_whatsapp: ela vai para o WhatsApp da própria pessoa, nunca para outro número. Repita o que a resposta disser que foi enviado.

## Saldo e plano

consultar_saldo diz quantas notas restam. Quando as notas acabam, a resposta diz onde estão as informações dos planos; a assinatura é feita fora daqui, pelo WhatsApp do iNotaFiscal.

## Dados

CPF de cliente aparece mascarado nas respostas. Não peça para a pessoa repetir documentos que já estão salvos.
