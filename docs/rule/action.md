ação ação
ActionUsado para operar em pedidos ou retornos

candidato
ActionAtualmente, as seguintes opções estão incluídas:

Rejeitar
Redirecionar(String)
ModifyRequest(Modify)
ModifyResponse(Modify)
LogRes
LogReq
Rejeitar
rejectO tipo é retornado diretamente 502, usado para rejeitar determinadas solicitações e pode ser usado para rejeitar rastreamento e publicidade

- name: "reject CSDN"
  filter:
    domain-keyword: 'csdn'
  action: reject
Copiar para área de transferênciaerrocopiado
redirecionar redirecionar
redirectDigite 302redirecionamento de retorno direto

- name: "youtube-1"
  filter:
    url-regex: '(^https?:\/\/(?!redirector)[\w-]+\.googlevideo\.com\/(?!dclk_video_ads).+)(ctier=L)(&.+)'
  action:
    redirect: "$1$4"
Copiar para área de transferênciaerrocopiado
Solicitação de modificação ModifyRequest
modify-requestUsado para modificar a solicitação, consulte Modificador

ModifyResponse modificar retorno
modify-responseUsado para modificar o retorno, consulte Modificador

Registro de registro de registro
log-reqUsado para registrar pedidos, log-resusado para registrar devoluções

várias ações
actionsO campo suporta ação única e várias ações, quando várias ações precisam ser executadas, uma matriz deve ser usada

- name: "youtube-1"
  filter:
    url-regex: '(^https?:\/\/(?!redirector)[\w-]+\.googlevideo\.com\/(?!dclk_video_ads).+)(ctier=L)(&.+)'
  actions:
    - log-req:
    - redirect: "$1$4"
