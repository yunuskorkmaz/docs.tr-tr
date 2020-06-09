---
title: WSDL ve İlke
ms.date: 03/30/2017
ms.assetid: cea87440-3519-4640-8494-b8a2b0e88c84
ms.openlocfilehash: 201920a8ebf639c74acfb20b2e990c8bbc0c5b55
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600107"
---
# <a name="wsdl-and-policy"></a>WSDL ve İlke
Bu konuda Windows Communication Foundation (WCF) WSDL 1,1, WS-Policy ve WS-PolicyAttachment uygulama ayrıntılarının yanı sıra WCF tarafından sunulan ek WS-Policy onayları ve WSDL 1,1 uzantıları ele alınmaktadır.  
  
 WCF, bu belgede açıklanan kısıtlamalar ve açıklamalar ile W3C 'a gönderilen WS-Policy ve WS-PolicyAttachment belirtimlerini uygular.  
  
 Bu belge, aşağıdaki tabloda gösterilen ön ekleri ve ad alanlarını kullanır.  
  
|Ön ek|Ad Alanı|  
|------------|---------------|  
|WSP (WS-Policy 1,2)|`http://schemas.xmlsoap.org/ws/2004/09/policy`|  
|WSP (WS-Policy 1,5)|`http://www.w3.org/ns/ws-policy`|  
|http|`http://schemas.microsoft.com/ws/06/2004/policy/http`|  
|'yu|`http://schemas.microsoft.com/ws/06/2004/mspolicy/msmq`|  
|'si|`http://schemas.microsoft.com/ws/2006/05/framing/policy`|  
|MSSP|`http://schemas.microsoft.com/ws/2005/07/securitypolicy`|  
|msc|`http://schemas.microsoft.com/ws/2005/12/wsdl/contract`|  
|'si|`http://schemas.microsoft.com/net/2006/06/duplex`|  
  
## <a name="wcf-wsdl11-extensions"></a>WCF WSDL 1.1 uzantıları  
 WCF, sözleşme oturumu gereksinimlerini anlatmak için aşağıdaki WSDL 1.1 uzantılarını kullanır.  
  
 wsdl:portType/wsdl:operation/@msc:isInitiating  
 xs: Boolean, bu işlemin bir WCF oturumu başlattığını belirtir; Varsayılan değer `false` .  
  
 wsdl:portType/wsdl:operation/@msc:isTerminating  
 xs: Boolean, bu işlemin bir WCF oturumunu sonlandırdığını belirtir; Varsayılan değer `false` .  
  
 wsdl:portType/wsdl:operation/@msc:usingSession  
 xs: Boolean, bu sözleşmenin oturumun kurulmasını gerektirip gerektirmediğini belirtir.  
  
### <a name="soap-1x-http-binding-transport-uris"></a>SOAP 1. x HTTP bağlama taşıma URI 'Leri  
 WCF, WSDL 1,1, SOAP 1,1 ve SOAP 1,2 bağlama uzantı öğeleri için kullanılacak aktarımları göstermek üzere aşağıdaki URI 'Leri kullanır.  
  
|Aktarım|URI|  
|---------------|---------|  
|HTTP|`http://schemas.xmlsoap.org/soap/http`|  
|TCP|`http://schemas.microsoft.com/soap/tcp`|  
|MSMQ|`http://schemas.microsoft.com/soap/msmq`|  
|Adlandırılmış Kanallar|`http://schemas.microsoft.com/soap/named-pipe`|  
  
## <a name="policy-assertions-implemented-by-wcf"></a>WCF tarafından uygulanan ilke onayları  
 Web Hizmetleri belirtimlerinde (WS-*) tanıtılan ve bu belgenin diğer bölümlerinde bahsedilen ilke onaylamalarına ek olarak, WCF aşağıdaki ilke onaylamalarını uygular.  
  
|İlke onaylama|İlke konusu|Açıklama|  
|----------------------|--------------------|-----------------|  
|http: HttpBasicAuthentication|Uç Nokta|Uç nokta HTTP temel kimlik doğrulaması kullanıyor.|  
|http: HttpDigestAuthentication|Uç Nokta|Uç nokta HTTP Özet kimlik doğrulamasını kullanır.|  
|http: HttpNegotiateAuthentication|Uç Nokta|Uç nokta HTTP anlaşma kimlik doğrulamasını kullanır.|  
|http: HttpNtlmAuthentication|Uç Nokta|Uç nokta HTTP NTLM kimlik doğrulamasını kullanır.|  
|MSF: akışla|Uç Nokta|Uç nokta akış ileti çerçeveleme kullanır. Bu onaylama, TCP ve adlandırılmış kanallar gibi aktarımlar için sunulan Ileti çerçeveleme protokolüyle birlikte kullanılır.|  
|MSF: SslTransportSecurity|Uç Nokta|Uç nokta, ileti çerçevelemesi ile Aktarım Katmanı Güvenliği 'ni (TLS) kullanır.|  
|MSF: WindowsTransportSecurity|Uç Nokta|Uç noktası, ileti çerçevelemesi ile güvenlik sağlayıcısı anlaşmasını (SPNEGO) kullanır.|  
|MSMQ: MsmqBestEffort|Uç Nokta|En iyi çaba garantisi olan MSMQ.|  
|MSMQ: MsmqSession|Uç Nokta|Oturum garantisi olan MSMQ.|  
|MSMQ: MsmqVolatile|Uç Nokta|MSMQ geçici.|  
|MSMQ: kimliği doğrulanmış|Uç Nokta|Kimlik doğrulaması MSMQ taşıması ile kullanılır.|  
|MSMQ: WindowsDomain|Uç Nokta|MSMQ Windows etki alanı kimlik doğrulamasını kullanır.|  
|CDP: CompositeDuplex|Uç Nokta|Uç nokta, gelen ve giden iletilerde iki ayrı convera aktarım bağlantısı kullanır.|  
|mssp: RsaToken|Ble|RSA anahtar belirteci onaylama. Bu gereksinim, genellikle bir onaylama imzasında anahtar bilgisinin bir parçası olarak doğrudan seri hale getirilen bir RSA anahtarı tarafından karşılanır.|  
|mssp: SslContextToken|Ble|WS-Trust kullanılarak ikili TLS el sıkışması kullanılarak elde edilen bir SecurityContextToken gerektirir. İç içe onaylama işlemleri şunlardır: SP: RequireDerivedKeys, mssp: MustNotSendCancel, mssp: RequireClientCertificate.|  
|mssp: MustNotSendCancel|Ble|Belirli bir SecurityContextToken veren için Iptal bağlamayı [WS-Trust, WS-SC] kullanan bir istek güvenlik belirteci (RST) istek iletisi (WS-Trust]) için bir gereksinim belirtir. Bu onay varsa, bu tür istek iletileri veren 'e gönderilmemelidir. Bu onaylama yoksa, bu tür istek iletileri verene gönderilebilir.|  
|mssp: RequireClientCertificate|Ble|Bu isteğe bağlı öğe, TLSNEGO protokolünün bir parçası olarak bir istemci sertifikasının sağlanması gereksinimini belirtir. Bu onay varsa, bir istemci sertifikasının sağlanması gerekir. Bu onaylama yoksa, bir istemci sertifikasının sağlanması gerekir. Bu onaylama, mssp: SslContextToken dışında kullanılmamalıdır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel WSDL Yayımı](../samples/custom-wsdl-publication.md)
- [Nasıl yapılır: Özel WSDL Dışa Aktarma](../extending/how-to-export-custom-wsdl.md)
- [Nasıl yapılır: Özel WSDL İçe Aktarma](../extending/how-to-import-custom-wsdl.md)
