modificador
Os modificadores são usados ​​para executar operações de modificação, incluindo solicitações de modificação e retornos de modificação

candidato
Dependendo da localização do conteúdo que precisa ser modificado, os modificadores são divididos nas seguintes categorias:

Cabeçalho(MapModify)
Cookie(MapModify)
Corpo (TextoModificar)
Modificador de texto TextModify
TextModifyModifique principalmente o texto, atualmente suporta duas maneiras:

Definir conteúdo de texto diretamente
Substituição normal ou substituição regular
definir diretamente
Para a configuração direta do tipo simples, o conteúdo será redefinido diretamente para o texto especificado

- name: "modify response body plain"
  filter:
    domain: '126.com'
  action:
    modify-response:
      body: "Hello 126.com, from Good-MITM"
Copiar para área de transferênciaerrocopiado
substituir
Substituição suporta substituição simples e substituição regular

substituição simples
- name: "modify response body replace"
  filter:
    domain-suffix: '163.com'
  action:
    modify-response:
      body:
        origin: "网易首页"
        new: "Good-MITM 首页"
Copiar para área de transferênciaerrocopiado
substituição regular
- name: "modify response body regex replace"
  filter:
    domain-suffix: 'zu1k.com'
  action:
    - modify-response:
        body:
          re: '(\d{4})'
          new: 'maybe $1'
Copiar para área de transferênciaerrocopiado
Modificador de Dicionário MapModify
MapModifyO modificador de dicionário modifica principalmente a posição do tipo de dicionário, como headerecookies

keyRepresenta a chave do dicionário, deve ser especificado

valueSim TextModifyDigite , escrito de acordo com o método acima

Se especificado removecomo true, o par chave-valor será excluído

- name: "modify response header"
  filter:
    domain: '126.com'
  action:
    - modify-response:
        header:
          key: date
          value:
            origin: "2022"
            new: "1999"
    - modify-response:
        header:
          key: new-header-item
          value: Good-MITM
    - modify-response:
        header:
          key: server
          remove: true
Copiar para área de transferênciaerrocopiado
Modificação do cabeçalho
veja MapModifyalguns métodos

Modificação de cookies
Igual ao método de modificação do cabeçalho

Se especificado removecomo truetambém removerá o set-cookieitem correspondente ao mesmo tempo

Modificação corporal
veja TextModifya seção
