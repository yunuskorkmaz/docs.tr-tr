---
title: WSDL ve İlke
ms.date: 03/30/2017
ms.assetid: cea87440-3519-4640-8494-b8a2b0e88c84
ms.openlocfilehash: 1e6b315c1830602e72b4b498cd38eed8428bc5ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741437"
---
# <a name="wsdl-and-policy"></a>WSDL ve İlke
Bu konu, Windows Communication Foundation (WCF) WSDL 1.1, uygulama ayrıntıları, WS-Policy ve WS-PolicyAttachment yanı sıra ek WS-Policy onaylar ve WCF tarafından sunulan WSDL 1.1 uzantılar içerir.  
  
 WCF için W3C kısıtlamaları ve bu belgede açıklanan açıklamalar ile gönderilen WS-Policy ve WS-PolicyAttachment belirtimleri uygular.  
  
 Bu belge, aşağıdaki tabloda gösterilen ad alanlarını ve önekleri kullanır.  
  
|Ön eki|Ad Alanı|  
|------------|---------------|  
|WSP (WS-Policy 1.2)|http://schemas.xmlsoap.org/ws/2004/09/policy|  
|WSP (WS-Policy 1.5)|http://www.w3.org/ns/ws-policy|  
|http|http://schemas.microsoft.com/ws/06/2004/policy/http|  
|msmq|http://schemas.microsoft.com/ws/06/2004/mspolicy/msmq|  
|msf|http://schemas.microsoft.com/ws/2006/05/framing/policy|  
|mssp|http://schemas.microsoft.com/ws/2005/07/securitypolicy|  
|msc|http://schemas.microsoft.com/ws/2005/12/wsdl/contract|  
|CDP|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="wcf-wsdl11-extensions"></a>WCF WSDL1.1 uzantıları  
 WCF sözleşmesi oturumu gereksinimlerini tanımlamak için aşağıdaki WSDL1.1 uzantıları kullanır.  
  
 wsdl:portType/wsdl:operation/@msc:isInitiating  
 xs:Boolean, bu işlem bir WCF oturumunu başlatan gösterir. Varsayılan değer `false`.  
  
 wsdl:portType/wsdl:operation/@msc:isTerminating  
 xs:Boolean, bu işlem bir WCF oturumu sona erer gösterir. Varsayılan değer `false`.  
  
 wsdl:portType/wsdl:operation/@msc:usingSession  
 xs:Boolean, gösteren bu anlaşma için session kurulması gerekiyor.  
  
### <a name="soap-1x-http-binding-transport-uris"></a>SOAP 1.x HTTP bağlama aktarım URI'ler  
 WCF şu Urı'lere WSDL 1.1, SOAP 1.1 ve SOAP 1.2 bağlama uzantısı öğeleri için kullanılacak taşımalar belirtmek için kullanır.  
  
|Taşıma|URI|  
|---------------|---------|  
|HTTP|http://schemas.xmlsoap.org/soap/http|  
|TCP|http://schemas.microsoft.com/soap/tcp|  
|MSMQ|http://schemas.microsoft.com/soap/msmq|  
|Adlandırılmış Kanallar|http://schemas.microsoft.com/soap/named-pipe|  
  
## <a name="policy-assertions-implemented-by-wcf"></a>WCF tarafından uygulanan ilke onaylamalarını  
 İlke onaylamalarını sunulan Web Hizmetleri özelliklere ek olarak (WS-*) ve bu belgenin diğer bölümlerinde belirtildiği gibi WCF aşağıdaki ilke eklemeleri uygular.  
  
|İlke onaylama|Konu İlkesi|Açıklama|  
|----------------------|--------------------|-----------------|  
|http:HttpBasicAuthentication|Uç Noktası|Uç nokta HTTP temel kimlik doğrulaması kullanır.|  
|http:HttpDigestAuthentication|Uç Noktası|Uç nokta HTTP Digest kimlik doğrulaması kullanır.|  
|http:HttpNegotiateAuthentication|Uç Noktası|Uç nokta HTTP anlaşması kimlik doğrulaması kullanır.|  
|http:HttpNtlmAuthentication|Uç Noktası|Uç nokta HTTP NTLM kimlik doğrulaması kullanır.|  
|msf:Streamed|Uç Noktası|Uç nokta akış ileti sınırlandırmasını kullanır. Bu onay, TCP ve adlandırılmış kanallar gibi taşımalar için sağlanan ileti çerçeveleme protokolü ile kullanılır.|  
|msf:SslTransportSecurity|Uç Noktası|Uç nokta, Aktarım Katmanı Güvenliği (TLS) ile ileti sınırlandırmasını kullanır.|  
|msf:WindowsTransportSecurity|Uç Noktası|Uç nokta ileti çerçeveleme ile güvenlik sağlayıcısı anlaşması (SPNEGO) kullanır.|  
|msmq:MsmqBestEffort|Uç Noktası|MSMQ en yüksek çaba garanti eder.|  
|MSMQ:MsmqSession|Uç Noktası|MSMQ Oturumu ile garanti eder.|  
|msmq:MsmqVolatile|Uç Noktası|MSMQ geçici.|  
|MSMQ: kimlik doğrulaması|Uç Noktası|MSMQ taşıma ile kimlik doğrulaması kullanılır.|  
|msmq:WindowsDomain|Uç Noktası|MSMQ Windows etki alanı kimlik doğrulaması kullanır.|  
|cdp:CompositeDuplex|Uç Noktası|Uç nokta, iki ayrı ters taşıma bağlantısı için giriş ve çıkış iletileri kullanır.|  
|mssp:RsaToken|İç içe geçmiş|RSA anahtar belirteci onaylar. Bu gereksinim, doğrudan onaylanan bir imza anahtar bilgileri bir parçası olarak seri hale getirilmiş bir RSA anahtarı tarafından genellikle uyulmuş olur.|  
|mssp:SslContextToken|İç içe geçmiş|WS-Trust kullanarak ikili TLS anlaşması kullanılarak elde edilen bir SecurityContextToken kullanılmasını gerektirir. İç içe geçmiş bir onayları Ekle: sp:RequireDerivedKeys, mssp:MustNotSendCancel mssp:RequireClientCertificate.|  
|mssp:MustNotSendCancel|İç içe geçmiş|İstek bir güvenlik belirteci (k) iptal bağlama [WS-Trust, WS-SC] kullanarak iletileri WS-Trust isteği bir gereksinim belirtir verilen SecurityContextToken yayınlayanla gönderme. Bu onay varsa, ardından gibi istek iletilerinin yayınlayanla gönderilmelidir değil. Bu onay mevcut değilse, bu istek iletilerinin yayınlayanla gönderilebilir.|  
|mssp:RequireClientCertificate|İç içe geçmiş|Bu isteğe bağlı öğe TLSNEGO protokolünün bir parçası sağlanması için bir istemci sertifikası için bir gereksinim belirtir. Bu onay varsa, bir istemci sertifikası sağlanmalıdır. Bu onay mevcut değilse, bir istemci sertifikası verilmemelidir. Bu onay mssp:SslContextToken dışında kullanılmamalıdır.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Özel WSDL Yayımı](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)
- [Nasıl yapılır: Özel WSDL dışarı aktarma](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)
- [Nasıl yapılır: Özel WSDL içeri aktarma](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
