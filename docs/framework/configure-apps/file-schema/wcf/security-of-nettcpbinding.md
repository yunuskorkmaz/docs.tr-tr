---
title: <security> / <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: 971b1ea979877f631766e438cc41bc0bdabfd346
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399797"
---
# <a name="security-of-nettcpbinding"></a>\<\<NetTcpBinding > Güvenlik >
Bağlama için güvenlik ayarlarını tanımlar.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netTcpBinding >** ](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Güvenlik >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|mod|İsteğe bağlı. Uygulanan güvenlik türünü belirtir. Geçerli değerler aşağıda gösterilmiştir. Varsayılan değer `Transport` şeklindedir.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>mode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|Güvenlik devre dışı bırakıldı.|  
|Aktarım|Aktarım güvenliği TCP veya SPNego üzerinden TLS kullanılarak sağlanır. Hizmetin SSL sertifikalarıyla yapılandırılması gerekebilir. Koruma düzeyini Bu modla denetlemek mümkündür.|  
|`Message`|Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır. Varsayılan olarak, SOAP gövdesi şifrelenir ve imzalanır. Bu mod, hizmet kimlik bilgilerinin, istemci bant dışı, kullanılacak algoritma paketini ve ileti gövdesine uygulanacak koruma düzeyini belirtir gibi çeşitli özellikler sunar. Oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.|  
|TransportWithMessageCredential|Aktarım güvenliği, ileti güvenliği ile birlikte gönderilir. Aktarım güvenliği TCP veya SPNego üzerinden TLS tarafından sağlanır ve bütünlük, gizlilik ve sunucu kimlik doğrulamasını sağlar. SOAP iletisi güvenliği istemci kimlik doğrulaması sağlar. Varsayılan olarak, oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Taşıma >](transport-of-nettcpbinding.md)|Taşımanın güvenlik ayarlarını tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.|  
|[\<ileti >](message-element-of-nettcpbinding.md)|İleti için güvenlik ayarlarını tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|bağlama|NetTcpBinding > bağlama öğesi. [ \<](nettcpbinding.md)|  
  
## <a name="remarks"></a>Açıklamalar  
 Standart bağlamaların her biri, aktarım güvenliği gereksinimlerini denetlemek için parametreler sağlar. Bu parametreler genellikle ileti düzeyi veya aktarım düzeyi güvenliğin kullanılıp kullanılmadığını ve istemci kimlik bilgisi türünü seçmesini belirten güvenlik modunu içerir. Bu parametrelerin mevcut seçeneklerinin seçimine bağlı olarak, uygun güvenlik ile bir kanal yığını oluşturulur.  
  
 Windows Communication Foundation (WCF) tarafından sağlanan sistem tarafından sağlanan bağlamalar, en yaygın senaryo gereksinimlerinin bazılarını karşılayacak şekilde tasarlanan bir kümesidir. Bu bağlamalardan her biri, belirli bir hedeflenmiş senaryolar için güvenlik gereksinimlerinin belirtilede olanak sağlar.  
  
 Bu yapılandırma öğesi için `netTcpBinding`güvenlik belirtimleri sağlar. Bu, makineler arası iletişim için uygun, güvenli, güvenilir ve iyileştirilmiş bir bağlamadır. Varsayılan olarak, ileti teslimi için TCP ve ileti güvenliği ve kimlik doğrulaması için Windows güvenliği, güvenilirlik açısından WS-ReliableMessaging ve ikili ileti kodlaması için TCP destekleyen bir çalışma zamanı iletişim yığını oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../misc/binding.md)
