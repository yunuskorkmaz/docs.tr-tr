---
title: WSDL ve İlke
ms.date: 03/30/2017
ms.assetid: cea87440-3519-4640-8494-b8a2b0e88c84
ms.openlocfilehash: 330a48989e9d6ca3cee0d11bf4b3fce38a25fa3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="wsdl-and-policy"></a>WSDL ve İlke
Bu konu, Windows Communication Foundation (WCF) WSDL 1.1, uygulama ayrıntılarını, WS-Policy ve WS-PolicyAttachment yanı sıra ek WS-Policy onaylar ve WCF tarafından sunulan WSDL 1.1 uzantılar içerir.  
  
 WCF kısıtlamaları ve bu belgede açıklanan açıklamalar için W3C gönderilen WS-Policy ve WS-PolicyAttachment belirtimleri uygular.  
  
 Bu belgede, aşağıdaki tabloda gösterilen ad alanlarını ve önekleri kullanır.  
  
|önek|Ad Alanı|  
|------------|---------------|  
|WSP (WS-Policy 1.2)|http://schemas.xmlsoap.org/ws/2004/09/policy|  
|WSP (WS-Policy 1.5)|http://www.w3.org/ns/ws-policy|  
|http|http://schemas.microsoft.com/ws/06/2004/policy/http|  
|MSMQ|http://schemas.microsoft.com/ws/06/2004/mspolicy/msmq|  
|MSF|http://schemas.microsoft.com/ws/2006/05/framing/policy|  
|mssp|http://schemas.microsoft.com/ws/2005/07/securitypolicy|  
|msc|http://schemas.microsoft.com/ws/2005/12/wsdl/contract|  
|CDP|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="wcf-wsdl11-extensions"></a>WCF WSDL1.1 uzantıları  
 WCF sözleşmesi oturum gereksinimleri açıklamak için aşağıdaki WSDL1.1 uzantıları kullanır.  
  
 wsdl:portType/wsdl:operation/@msc:isInitiating  
 xs:Boolean, bu işlem bir WCF oturumunu başlatan gösterir; Varsayılan değer `false`.  
  
 wsdl:portType/wsdl:operation/@msc:isTerminating  
 xs:Boolean, gösteren bir WCF oturumu bu işlemi sonlandırır; Varsayılan değer `false`.  
  
 wsdl:portType/wsdl:operation/@msc:usingSession  
 xs:Boolean, gösterir bu sözleşmenin oturum kurulmasını gerektirir.  
  
### <a name="soap-1x-http-binding-transport-uris"></a>SOAP 1.x HTTP bağlama taşıma URI'ler  
 WCF WSDL 1.1, SOAP 1.1 ve SOAP 1.2 bağlama uzantısı öğeleri için kullanılacak taşımaları belirtmek için aşağıdaki URI'ler kullanır.  
  
|Taşıma|URI|  
|---------------|---------|  
|HTTP|http://schemas.xmlsoap.org/soap/http|  
|TCP|http://schemas.microsoft.com/soap/tcp|  
|MSMQ|http://schemas.microsoft.com/soap/msmq|  
|Adlandırılmış Kanallar|http://schemas.microsoft.com/soap/named-pipe|  
  
## <a name="policy-assertions-implemented-by-wcf"></a>WCF tarafından uygulanan ilke onaylamalarını  
 Web hizmetleri belirtimleri sunulan ilke onaylamalarını yanı sıra (WS-*) ve bu belgenin diğer bölümlerinde belirtildiği gibi WCF aşağıdaki ilke onaylamalarını uygular.  
  
|İlke onaylama|İlke konu|Açıklama|  
|----------------------|--------------------|-----------------|  
|http:HttpBasicAuthentication|Uç Noktası|Uç nokta HTTP temel kimlik doğrulaması kullanır.|  
|http:HttpDigestAuthentication|Uç Noktası|Uç nokta HTTP Digest kimlik doğrulaması kullanır.|  
|http:HttpNegotiateAuthentication|Uç Noktası|Uç nokta HTTP anlaşması kimlik doğrulaması kullanır.|  
|http:HttpNtlmAuthentication|Uç Noktası|Uç nokta HTTP NTLM kimlik doğrulaması kullanır.|  
|MSF: akışı|Uç Noktası|Uç nokta akış ileti sınırlandırmasını kullanır. Bu onay TCP ve adlandırılmış kanallar gibi taşıma için sağlanan ileti çerçeveleme protokolü ile kullanılır.|  
|msf:SslTransportSecurity|Uç Noktası|Uç nokta Aktarım Katmanı Güvenliği (TLS) ile ileti sınırlandırmasını kullanır.|  
|MSF:WindowsTransportSecurity|Uç Noktası|Uç nokta ileti sınırlandırmasını ile güvenlik sağlayıcısı anlaşma (SPNEGO) kullanır.|  
|MSMQ:MsmqBestEffort|Uç Noktası|MSMQ en yüksek çaba garanti ile.|  
|MSMQ:MsmqSession|Uç Noktası|MSMQ Oturumu ile güvence altına alır.|  
|MSMQ:MsmqVolatile|Uç Noktası|MSMQ geçici.|  
|MSMQ: kimlik doğrulaması|Uç Noktası|Kimlik doğrulaması ile MSMQ taşıma kullanılır.|  
|MSMQ:WindowsDomain|Uç Noktası|MSMQ Windows etki alanı kimlik doğrulaması kullanır.|  
|cdp:CompositeDuplex|Uç Noktası|Uç nokta iki ayrı ters aktarım bağlantıları için giriş ve çıkış iletileri kullanır.|  
|mssp:RsaToken|İç içe geçmiş|RSA anahtar belirteci onayı. Bu gereksinim, doğrudan bir onaylama imzada anahtar bilgilerinin bir parçası olarak serileştirilmiş bir RSA anahtarı tarafından genellikle uyulmuş olur.|  
|mssp:SslContextToken|İç içe geçmiş|WS-Trust kullanarak ikili TLS anlaşması kullanılarak edinilen SecurityContextToken kullanılmasını gerektirir. İç içe geçmiş onayları içerir: sp:RequireDerivedKeys, mssp:MustNotSendCancel, mssp:RequireClientCertificate.|  
|mssp:MustNotSendCancel|İç içe geçmiş|İstek bir güvenlik belirteci (RST) iletileri iptal bağlama [WS-Trust, WS-SC] kullanarak [WS-Trust] isteyin gereksinimi belirttiğinden verilen SecurityContextToken vereni gönderilmez. Bu onaylama işlemi varsa, ardından bu tür istek iletilerini vereni gönderilmemesi gerekir. Bu onay mevcut değilse, bu tür istek iletilerini vereni gönderilebilir.|  
|mssp:RequireClientCertificate|İç içe geçmiş|Bu isteğe bağlı öğe TLSNEGO protokolünün bir parçası sağlanacak bir istemci sertifikası gereksinimi belirtir. Bu onaylama işlemi varsa, bir istemci sertifikası sağlanmalıdır. Bu onay mevcut değilse, sonra bir istemci sertifikası sağlanmalıdır değil. Bu onay mssp:SslContextToken dışında kullanılmamalıdır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel WSDL Yayımı](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
 [Nasıl yapılır: Özel WSDL Dışarı Aktarma](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)  
 [Nasıl yapılır: Özel WSDL İçe Aktarma](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
