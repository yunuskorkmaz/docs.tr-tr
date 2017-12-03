---
title: "WSDL ve İlke"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cea87440-3519-4640-8494-b8a2b0e88c84
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f502d24f98c9229d064be3de0e0edc081664dd03
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="wsdl-and-policy"></a>WSDL ve İlke
Bu konuda ele alınmaktadır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] WSDL 1.1, uygulama ayrıntılarını, WS-Policy ve WS-PolicyAttachment yanı sıra ek WS-Policy onaylar ve WSDL 1.1 uzantıları tarafından sunulan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]WS-Policy ve WS-PolicyAttachment belirtimleri kısıtlamaları ve bu belgede açıklanan açıklamalar için W3C gönderilen uygular.  
  
 Bu belgede, aşağıdaki tabloda gösterilen ad alanlarını ve önekleri kullanır.  
  
|önek|Ad Alanı|  
|------------|---------------|  
|WSP (WS-Policy 1.2)|http://schemas.xmlsoap.org/ws/2004/09/Policy|  
|WSP (WS-Policy 1.5)|http://www.w3.org/ns/WS-Policy|  
|http|http://schemas.microsoft.com/ws/06/2004/Policy/http|  
|MSMQ|http://schemas.microsoft.com/ws/06/2004/mspolicy/MSMQ|  
|MSF|http://schemas.microsoft.com/ws/2006/05/Framing/Policy|  
|mssp|http://schemas.microsoft.com/ws/2005/07/securityPolicy|  
|msc|http://schemas.microsoft.com/ws/2005/12/WSDL/Contract|  
|CDP|http://schemas.microsoft.com/NET/2006/06/Duplex|  
  
## <a name="wcf-wsdl11-extensions"></a>WCF WSDL1.1 uzantıları  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Sözleşme oturum gereksinimleri açıklamak için aşağıdaki WSDL1.1 uzantıları kullanır.  
  
 wsdl:portType/wsdl:operation/@msc:isInitiating  
 xs:Boolean, gösterir bu işlemi başlatan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oturumu; varsayılan değer `false`.  
  
 wsdl:portType/wsdl:operation/@msc:isTerminating  
 xs:Boolean, gösterir bu işlemi sonlandırır bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oturumu; varsayılan değer `false`.  
  
 wsdl:portType/wsdl:operation/@msc:usingSession  
 xs:Boolean, gösterir bu sözleşmenin oturum kurulmasını gerektirir.  
  
### <a name="soap-1x-http-binding-transport-uris"></a>SOAP 1.x HTTP bağlama taşıma URI'ler  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]WSDL 1.1, SOAP 1.1 ve SOAP 1.2 bağlama uzantısı öğeleri için kullanılacak taşımaları belirtmek için aşağıdaki URI'ler kullanır.  
  
|Taşıma|URI|  
|---------------|---------|  
|HTTP|http://schemas.xmlsoap.org/SOAP/http|  
|TCP|http://schemas.microsoft.com/SOAP/TCP|  
|MSMQ|http://schemas.microsoft.com/SOAP/MSMQ|  
|Adlandırılmış Kanallar|http://schemas.microsoft.com/SOAP/Named-Pipe|  
  
## <a name="policy-assertions-implemented-by-wcf"></a>WCF tarafından uygulanan ilke onaylamalarını  
 Web hizmetleri belirtimleri sunulan ilke onaylamalarını yanı sıra (WS-*) ve bu belgenin diğer bölümlerinde açıklanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aşağıdaki ilke onaylamalarını uygular.  
  
|İlke onaylama|İlke konu|Açıklama|  
|----------------------|--------------------|-----------------|  
|http:HttpBasicAuthentication|Uç Noktası|Uç nokta HTTP temel kimlik doğrulaması kullanır.|  
|http:HttpDigestAuthentication|Uç Noktası|Uç nokta HTTP Digest kimlik doğrulaması kullanır.|  
|http:HttpNegotiateAuthentication|Uç Noktası|Uç nokta HTTP anlaşması kimlik doğrulaması kullanır.|  
|http:HttpNtlmAuthentication|Uç Noktası|Uç nokta HTTP NTLM kimlik doğrulaması kullanır.|  
|MSF: akışı|Uç Noktası|Uç nokta akış ileti sınırlandırmasını kullanır. Bu onay TCP ve adlandırılmış kanallar gibi taşıma için sağlanan ileti çerçeveleme protokolü ile kullanılır.|  
|MSF:SslTransportSecurity|Uç Noktası|Uç nokta Aktarım Katmanı Güvenliği (TLS) ile ileti sınırlandırmasını kullanır.|  
|MSF:WindowsTransportSecurity|Uç Noktası|Uç nokta ileti sınırlandırmasını ile güvenlik sağlayıcısı anlaşma (SPNEGO) kullanır.|  
|MSMQ:MsmqBestEffort|Uç Noktası|MSMQ en yüksek çaba garanti ile.|  
|MSMQ:MsmqSession|Uç Noktası|MSMQ Oturumu ile güvence altına alır.|  
|MSMQ:MsmqVolatile|Uç Noktası|MSMQ geçici.|  
|MSMQ: kimlik doğrulaması|Uç Noktası|Kimlik doğrulaması ile MSMQ taşıma kullanılır.|  
|MSMQ:WindowsDomain|Uç Noktası|MSMQ Windows etki alanı kimlik doğrulaması kullanır.|  
|CDP:CompositeDuplex|Uç Noktası|Uç nokta iki ayrı ters aktarım bağlantıları için giriş ve çıkış iletileri kullanır.|  
|mssp:RsaToken|İç içe geçmiş|RSA anahtar belirteci onayı. Bu gereksinim, doğrudan bir onaylama imzada anahtar bilgilerinin bir parçası olarak serileştirilmiş bir RSA anahtarı tarafından genellikle uyulmuş olur.|  
|mssp:SslContextToken|İç içe geçmiş|WS-Trust kullanarak ikili TLS anlaşması kullanılarak edinilen SecurityContextToken kullanılmasını gerektirir. İç içe geçmiş onayları içerir: sp:RequireDerivedKeys, mssp:MustNotSendCancel, mssp:RequireClientCertificate.|  
|mssp:MustNotSendCancel|İç içe geçmiş|İstek bir güvenlik belirteci (RST) iletileri iptal bağlama [WS-Trust, WS-SC] kullanarak [WS-Trust] isteyin gereksinimi belirttiğinden verilen SecurityContextToken vereni gönderilmez. Bu onaylama işlemi varsa, ardından bu tür istek iletilerini vereni gönderilmemesi gerekir. Bu onay mevcut değilse, bu tür istek iletilerini vereni gönderilebilir.|  
|mssp:RequireClientCertificate|İç içe geçmiş|Bu isteğe bağlı öğe TLSNEGO protokolünün bir parçası sağlanacak bir istemci sertifikası gereksinimi belirtir. Bu onaylama işlemi varsa, bir istemci sertifikası sağlanmalıdır. Bu onay mevcut değilse, sonra bir istemci sertifikası sağlanmalıdır değil. Bu onay mssp:SslContextToken dışında kullanılmamalıdır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel WSDL yayımı](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
 [Nasıl yapılır: özel WSDL dışarı aktarma](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)  
 [Nasıl yapılır: özel WSDL içe aktarma](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
