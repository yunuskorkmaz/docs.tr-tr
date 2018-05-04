---
title: '&lt;netTcpBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f58dd0ee1b00785e82628e5442c736866ffe7db5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a>&lt;netTcpBinding&gt; &lt;güvenliği&gt;
Bağlama için güvenlik ayarlarını tanımlar.  
  
 \<system.ServiceModel>  
\<bağlamaları >  
\<netTcpBinding>  
\<bağlama >  
\<Güvenlik >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
           protectionLevel="None/Sign/EncryptAndSign" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|mod|İsteğe bağlı. Uygulanan güvenlik türünü belirtir. Geçerli değerler aşağıda verilmiştir. Varsayılan değer `Transport` şeklindedir.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>mod özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|Güvenliği devre dışı bırakıldı.|  
|Taşıma|Taşıma güvenliği, TLS üzerinden TCP veya SPNego kullanılarak sağlanır. Hizmet SSL sertifikalarıyla yapılandırılması gerekebilir. Bu mod koruma düzeyiyle denetlemek mümkündür.|  
|İleti|Güvenlik SOAP ileti güvenliği sağlanır. Varsayılan olarak, SOAP gövdesi imzalı ve şifrelenir. Bu mod hizmet kimlik bilgilerini bant, kullanmak için algoritma paketini dışında istemcide kullanılabilir olup olmadığı gibi özellikleri, çeşitli sunar ve hangi ileti gövdesi uygulamak için koruma düzeyi. İstemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturumu boyunca önbelleğe alınır.|  
|TransportWithMessageCredential|Taşıma güvenliği ile ileti güvenliği birleştirilmiştir. Taşıma güvenliği tarafından TLS TCP veya SPNego sağlanır ve bütünlüğü, gizlilik ve sunucu kimlik doğrulaması sağlar. SOAP iletisi güvenlik istemci kimlik doğrulaması sağlar. Varsayılan olarak, kimlik doğrulama sonuçlarını oturumu boyunca önbelleğe alınır ve istemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<taşıma >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|Taşıma için güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.|  
|[\<İleti >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|İleti için güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|bağlama|Bağlama öğesi [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Her standart bağlamaları parametreleri aktarımı güvenlik gereksinimleri denetlemek için sağlar. Bu parametreler genellikle ileti düzeyi veya aktarım düzeyinde güvenlik kullanılıp kullanılmadığını ve istemci kimlik bilgisi türü seçimine belirtilen güvenlik modunu içerir. Bu parametreler varsa, bir kanal yığını uygun güvenlik ile oluşturulan seçenekleri seçimine dayalı olarak.  
  
 Windows Communication Foundation (WCF) tarafından sağlanan sistem tarafından sağlanan bağlamalar bazı yaygın senaryo gereksinimleri karşılamak için tasarlanmış bir kümesidir. Her bu bağlamaların bazı belirli hedeflenen senaryoları için güvenlik gereksinimlerini belirtimi sağlar.  
  
 Bu yapılandırma öğesi için güvenlik belirtimler sağlar `netTcpBinding`. Güvenli, güvenilir ve en iyi duruma getirilmiş bağlama makineler arası iletişim için uygun budur. Varsayılan olarak TCP ileti güvenliği ve kimlik doğrulaması, WS-ReliableMessaging güvenilirlik ve ikili ileti kodlama için ileti teslimi ve Windows Güvenlik destekleyen bir çalışma zamanı iletişim yığını oluşturur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
