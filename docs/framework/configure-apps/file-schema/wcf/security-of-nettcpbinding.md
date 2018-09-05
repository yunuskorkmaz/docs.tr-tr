---
title: '&lt;netTcpBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 13aeb3261fdb9689caa1dea1ec7382fdb9d9b1ce
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516979"
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a>&lt;netTcpBinding&gt; &lt;güvenliği&gt;
Bir bağlama için güvenlik ayarlarını tanımlar.  
  
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
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|mod|İsteğe bağlı. Uygulanan güvenlik türünü belirtir. Geçerli değerler, aşağıda gösterilmiştir. Varsayılan değer `Transport` şeklindedir.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>mod özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|Güvenlik devre dışı bırakıldı.|  
|Taşıma|Aktarım güvenliği TLS TCP veya SPNego kullanılarak sağlanır. Hizmet, SSL sertifikalarıyla yapılandırılması gerekebilir. Bu mod koruma düzeyiyle denetlemek mümkündür.|  
|İleti|SOAP ileti güveliği kullanarak güvenliği sağlanır. Varsayılan olarak, SOAP gövdesi imzalı ve şifrelenir. Çeşitli hizmet kimlik bilgilerini kullanmak için algoritma paketini olan bant dışı istemci kullanılabilir olup gibi özellikler, bu mod sunar ve ileti gövdesi uygulamak için koruma düzeyini. İstemci kimlik doğrulaması, oturum başına bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturum süresi boyunca önbelleğe alınır.|  
|TransportWithMessageCredential|Aktarım güvenliği ile ileti güvenliği amacıyla birlikte çalışır. Aktarım güvenliği TCP veya SPNego üzerinden TLS tarafından sağlanır ve sunucu kimlik doğrulaması bütünlüğü ve gizliliği sağlar. SOAP ileti güvenliği, istemci kimlik doğrulaması sağlar. Varsayılan olarak, istemci kimlik doğrulaması, oturum başına bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturum süresi boyunca önbelleğe alınır.|  
  
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
 Her standart bağlamaları parametreleri aktarımı güvenlik gereksinimleri kontrol etmek için sağlar. Bu parametreler, genelde ileti düzeyi veya aktarım düzeyi güvenlik kullanılıp kullanılmadığını ve istemci kimlik bilgisi türü seçimi belirlenen güvenlik modu içerir. Bu parametreleri mevcut bir kanal yığını uygun güvenlik ile oluşturulmuş seçenekleri seçimi temel.  
  
 Windows Communication Foundation (WCF) tarafından sağlanan sistem tarafından sağlanan bağlamalar, bazı yaygın senaryo gereksinimleri karşılamak için tasarlanan bir kümesidir. Her biri bu bağlamaları belirli bazı hedeflenen senaryoları için güvenlik gereksinimlerini belirtilmesine izin verir.  
  
 Bu yapılandırma öğesi için güvenlik özelliklerini sağlayan `netTcpBinding`. Çapraz makine haberleşmesi için güvenli, güvenilir ve iyileştirilmiş bağlama budur. Varsayılan olarak TCP ileti güvenliği ve kimlik doğrulaması, güvenilirlik ve ikili ileti kodlama WS-ReliableMessaging ileti teslimi ve Windows güvenliği destekleyen bir çalışma zamanı iletişim yığını oluşturur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
