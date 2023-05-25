preparação de certificado

Para implementar o tráfego MITM para HTTPS e impedir que os navegadores exibam avisos de segurança, um certificado CA autoassinado precisa ser gerado e confiável

Gerar certificado CA

Por motivos de segurança, os usuários devem gerar seus próprios certificados de CA. O uso aleatório de certificados de CA não confiáveis ​​deixará sérios riscos de segurança

Usuários experientes podem usar o OpenSSL para executar operações relacionadas por conta própria. Considerando usuários sem experiência relevante, eles podem usar os seguintes comandos para gerar conteúdo relevante diretamente. O certificado gerado e a chave privada serão armazenados no cadiretório

./firewallapp genca

Copiar para área de transferênciaerrocopiado

Depois que o navegador usar o proxy fornecido pelo FirewallApp, você poderá baixar diretamente o certificado visitando http://cert.mitm.plus , o que é muito útil ao fornecer serviços para outros dispositivos

Confiar no certificado gerado

Você precisa confiar no certificado recém-gerado no navegador ou sistema operacional, o método específico será adicionado posteriormente
