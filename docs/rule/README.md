Regras

RuleUsado para controlar Good-MITM

Uma regra de qualificação precisa conter o seguinte:

Nome da Regra: Usado para distinguir diferentes regras, conveniência e manutenção

filtro: Usado para filtrar o conteúdo que precisa ser processado de muitos enviar e receber

ação: Usado para executar o comportamento desejado, incluindo redirecionar, bloquear, modificar e etc.

Especifique nomes de domínio que requerem MITM, se necessário

- name: "Yutube"
  mitm: "*.youtube.com"
  filter:
    url-regex: '^https?:\/\/(www|s)\.youtube\.com\/(pagead|ptracking)'
  action: reject
  
Copiar para área de transferência erro copiado

Ao mesmo tempo, uma regra qualificada precisa atender aos seguintes requisitos:

Foco: Uma regra é usada apenas para fazer uma coisa

Simples: use um método simples para manusear, conveniente e manter

Eficiente: Tente usar métodos eficientes, como usar sufixos de nome de domínio e prefixos de nome de domínio para substituir expressões regulares de nome de domínio
