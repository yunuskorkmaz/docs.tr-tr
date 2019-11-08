---
title: <security> / <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: aa01e906ddd2f15007c72bfc2a45122cfb15ba2c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736376"
---
# <a name="security-of-nettcpbinding"></a>\<netTcpBinding > Güvenlik > \<
Bağlama için güvenlik ayarlarını tanımlar.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netTcpBinding >** ](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<güvenlik >**  
  
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
|mod|İsteğe bağlı. Uygulanan güvenlik türünü belirtir. Geçerli değerler aşağıda gösterilmiştir. Varsayılan değer `Transport` şeklindedir.<br /><br /> Bu öznitelik <xref:System.ServiceModel.SecurityMode>türündedir.|  
  
## <a name="mode-attribute"></a>Mode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|Güvenlik devre dışı bırakıldı.|  
|Aktarım|Aktarım güvenliği TCP veya SPNego üzerinden TLS kullanılarak sağlanır. Hizmetin SSL sertifikalarıyla yapılandırılması gerekebilir. Koruma düzeyini Bu modla denetlemek mümkündür.|  
|İleti|Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır. Varsayılan olarak, SOAP gövdesi şifrelenir ve imzalanır. Bu mod, hizmet kimlik bilgilerinin, istemci bant dışı, kullanılacak algoritma paketini ve ileti gövdesine uygulanacak koruma düzeyini belirtir gibi çeşitli özellikler sunar. Oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.|  
|TransportWithMessageCredential|Aktarım güvenliği, ileti güvenliği ile birlikte gönderilir. Aktarım güvenliği TCP veya SPNego üzerinden TLS tarafından sağlanır ve bütünlük, gizlilik ve sunucu kimlik doğrulamasını sağlar. SOAP iletisi güvenliği istemci kimlik doğrulaması sağlar. Varsayılan olarak, oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<taşıma >](transport-of-nettcpbinding.md)|Taşımanın güvenlik ayarlarını tanımlar. Bu öğe <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>türündedir.|  
|[\<ileti >](message-element-of-nettcpbinding.md)|İleti için güvenlik ayarlarını tanımlar. Bu öğe <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>türündedir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|bağlama|[\<netTcpBinding >](nettcpbinding.md)bağlama öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Standart bağlamaların her biri, aktarım güvenliği gereksinimlerini denetlemek için parametreler sağlar. Bu parametreler genellikle ileti düzeyi veya aktarım düzeyi güvenliğin kullanılıp kullanılmadığını ve istemci kimlik bilgisi türünü seçmesini belirten güvenlik modunu içerir. Bu parametrelerin mevcut seçeneklerinin seçimine bağlı olarak, uygun güvenlik ile bir kanal yığını oluşturulur.  
  
 Windows Communication Foundation (WCF) tarafından sağlanan sistem tarafından sağlanan bağlamalar, en yaygın senaryo gereksinimlerinin bazılarını karşılayacak şekilde tasarlanan bir kümesidir. Bu bağlamalardan her biri, belirli bir hedeflenmiş senaryolar için güvenlik gereksinimlerinin belirtilede olanak sağlar.  
  
 Bu yapılandırma öğesi `netTcpBinding`için güvenlik belirtimleri sağlar. Bu, makineler arası iletişim için uygun, güvenli, güvenilir ve iyileştirilmiş bir bağlamadır. Varsayılan olarak, ileti teslimi için TCP ve ileti güvenliği ve kimlik doğrulaması için Windows güvenliği, güvenilirlik açısından WS-ReliableMessaging ve ikili ileti kodlaması için TCP destekleyen bir çalışma zamanı iletişim yığını oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\< bağlama >](bindings.md)
