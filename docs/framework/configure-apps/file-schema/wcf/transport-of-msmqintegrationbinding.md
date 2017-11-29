---
title: "&lt;msmqIntegrationBinding&gt; &lt;taşıma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d9def7fbd0082cc7fa9d9f18388604383cb71f9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltmsmqintegrationbindinggt"></a>&lt;msmqIntegrationBinding&gt; &lt;taşıma&gt;
Message Queuing tümleştirme taşıma için güvenlik ayarlarını tanımlar.  
  
 \<Sistem. ServiceModel >  
\<bağlamaları >  
msmqIntegrationBinding  
\<bağlama >  
\<Güvenlik >  
\<taşıma >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<security>  
    <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
        msmqEncryptionAlgorithm="RC4Stream/AES"  
        msmqProtectionLevel="None/Sign/EncryptAndSign"  
        msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|İletinin MSMQ taşıma tarafından nasıl doğrulanmış gerekir belirtir. Bu ayarlanırsa `None`, değeri `msmqProtectionLevel` özniteliği de ayarlanmalıdır `None`.<br /><br /> Geçerli değerler şunlardır:<br /><br /> -Hiçbiri: Kimlik doğrulaması yok.<br />-WindowsDomain: SID iletiyle ilişkili X.509 sertifikası almak için Active Directory kimlik doğrulama mekanizması kullanır. Bu, daha sonra kullanıcı emin olmak için ACL sırasının sıraya yazmak için yeterli izne sahip denetlemek için kullanılır.<br />-Sertifika: Kanal sertifikayı sertifika deposundan alır.<br /><br /> WindowsDomain varsayılan değerdir. Bu öznitelik türünde <xref:System.ServiceModel.MsmqAuthenticationMode>.|  
|`msmqEncryptionAlgorithm`|İleti şifreleme hattaki iletileri ileti sırası yöneticileri arasında aktarırken kullanılacak algoritmayı belirtir. Geçerli değerler şunlardır:<br /><br /> -RC4Stream<br />-AES<br /><br /> RC4Stream varsayılan değerdir. Bu öznitelik türünde <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|`msmqProtectionLevel`|İletinin MSMQ taşıma düzeyinde güvenliği nasıl belirtir. İleti bütünlüğü ve takası da EncryptAndSign sağlar ancak şifreleme ileti bütünlüğü sağlar; diğer bir deyişle, iletinin gerçekten gönderenden gelir ve gönderenin kim kendisinin gerçekleştirilmesine söyler.<br /><br /> -Geçerli değerler şunlardır:<br />-Hiçbiri: Koruma yok.<br />-Oturum: İletileri imzalanmıştır.<br />-Da EncryptAndSign: İletileri şifrelenmiş ve imzalanmış.<br /><br /> Varsayılan değer işaretidir. Bu öznitelik ProtectionLevel türüdür.|  
|`msmqSecureHashAlgorithm`|-Özet imzaları bir parçası olarak bilgisayar kullanılacak algoritmayı belirtir. Geçerli değerler şunlardır:<br />-MD5<br />-SHA1<br />-SHA256<br />-SHA512<br /><br /> SHA1 varsayılan değerdir. Bu öznitelik türünde <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|MSMQ bağlama için güvenlik ayarlarını tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe Message Queuing tümleştirme taşıma için güvenlik ayarlarını saklar. Ayarları Message Queuing tümleştirme ve sıraya alınan taşımaları için aynıdır. Kimlik doğrulama modu, şifreleme algoritması, güvenli karma algoritması ve koruma düzeyini ayarlamanıza imkan sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem tarafından sağlanan bağlamaları yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
