filtro filtro
FilterUsado para filtrar solicitações e devoluções que precisam ser processadas

candidato
FilterAtualmente inclui os seguintes tipos:

todos
Domínio(String)
DomainKeyword (String)
DomainPrefix(String)
DomainSuffix(String)
UrlRegex(fancy_regex::Regex)
Observe que
na versão atual, domaino tipo relevante corresponde a host, e geralmente não afetará o resultado.
Quando um site usa uma porta não convencional, a regra precisa indicar a porta.
Versões subsequentes otimizarão esse comportamento

tudo tudo
allQuando o filtro é especificado, ele atingirá todas as solicitações e retornará, geralmente usado para executar o comportamento de registro

- name: "log"
  filter: all
  action:
    - log-req
    - log-res
Copiar para área de transferênciaerrocopiado
Nome de domínio de domínio
domainCorrespondência completa no nome de domínio

- name: "redirect"
  filter:
    domain: 'none.zu1k.com'
  action:
    redirect: "https://zu1k.com/"
Copiar para área de transferênciaerrocopiado
Palavra-chave do domínio Palavra-chave do domínio
domain-keywordCorrespondência de palavras-chave para nomes de domínio

- name: "reject CSDN"
  filter:
    domain-keyword: 'csdn'
  action: reject
Copiar para área de transferênciaerrocopiado
Prefixo do nome de domínio DomainPrefix
domain-prefixCorrespondência de prefixos em nomes de domínio

- name: "ad prefix"
  filter:
    domain-prefix: 'ads' // example: "ads.xxxxx.com"
  action: reject
Copiar para área de transferênciaerrocopiado
DomainSuffix sufixo do nome de domínio
domain-suffixCorrespondência de sufixos em nomes de domínio

- name: "redirect"
  filter:
    domain-suffix: 'google.com.cn'
  action:
    redirect: "https://google.com"
Copiar para área de transferênciaerrocopiado
UrlRegex Regularização de url
url-regexCorrespondência regular em todo o URL

- name: "youtube追踪"
  mitm: "*.youtube.com"
  filter:
    url-regex: '^https?:\/\/(www|s)\.youtube\.com\/(pagead|ptracking)'
  action: reject
Copiar para área de transferênciaerrocopiado
vários filtros
filtersO campo suporta um único filtro e vários filtros, e a relação entre vários filtros é或

- name: "youtube-2"
  mitm:
    - "*.youtube.com"
    - "*.googlevideo.com"
  filters:
    - url-regex: '^https?:\/\/[\w-]+\.googlevideo\.com\/(?!(dclk_video_ads|videoplayback\?)).+(&oad|ctier)'
    - url-regex: '^https?:\/\/(www|s)\.youtube\.com\/api\/stats\/ads'
    - url-regex: '^https?:\/\/(www|s)\.youtube\.com\/(pagead|ptracking)'
    - url-regex: '^https?:\/\/\s.youtube.com/api/stats/qoe?.*adformat='
  action: reject
Copiar para área de transferênciaerrocopiado
Várias regras com a mesma ação podem ser agregadas em uma regra para facilitar a manutenção
