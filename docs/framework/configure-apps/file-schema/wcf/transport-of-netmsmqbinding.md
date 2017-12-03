---
title: "&lt;netMsmqBinding&gt; &lt;taşıma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 51dcdc268a012cb8298dbc380c9c5d33a9db8d02
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltnetmsmqbindinggt"></a>&lt;netMsmqBinding&gt; &lt;taşıma&gt;
Taşıma güvenlik ayarları tanımlar.  
  
 \<Sistem. ServiceModel >  
\<bağlamaları >  
\<netMsmqBinding >  
\<bağlama >  
\<Güvenlik >  
\<taşıma >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netMsmqBinding>  
    <binding>  
    <security>  
         <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
    </security>  
   </binding>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|msmqAuthenticationMode|İletinin MSMQ taşıma tarafından nasıl doğrulanmış gerekir belirtir. Geçerli değerler şunlardır:<br /><br /> -Hiçbiri: Kimlik doğrulaması yok.<br />-WindowsDomain: İleti ile ilişkili güvenlik tanımlayıcısı X.509 sertifikası almak için Active Directory kimlik doğrulama mekanizması kullanır. Bu, daha sonra kullanıcı emin olmak için ACL sıranın sıra için yazma iznine sahip denetlemek için kullanılır.<br />-Sertifika: Kanal sertifikayı sertifika deposundan alır.<br /><br /> Varsayılan, `WindowsDomain` değeridir.<br /><br /> Bu öznitelik ayarlanırsa `None`, `msmqProtectionLevel` özniteliği de ayarlanmalıdır `None`. Bu öznitelik türünde<xref:System.ServiceModel.MsmqAuthenticationMode>|  
|msmqEncryptionAlgorithm|İleti şifreleme hattaki iletileri ileti sırası yöneticileri arasında aktarırken kullanılacak algoritmayı belirtir. Geçerli değerler şunlardır:<br /><br /> -RC4Stream<br />-AES<br />-Varsayılan değer `RC4Stream`. Bu öznitelik türünde <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|msmqProtectionLevel|MSMQ taşıma düzeyinde şekilde iletileri güvenli hale getirilen belirtir. İleti bütünlüğü ve takası ileti bütünlüğü, oturum while ve şifreleme sağlar şifreleme sağlar. Diğer bir deyişle, gerçekten gönderenden gelen ileti ve gönderenin kim kendisinin gerçekleştirilmesine söyler. Geçerli değerler şunlardır:<br /><br /> -Hiçbiri: Koruma yok.<br />-Oturum: İletileri imzalanmıştır.<br />-Da EncryptAndSign: İletileri şifrelenmiş ve imzalanmış.<br />-Varsayılan `Sign`.|  
|msmqSecureHashAlgorithm|İleti özeti bilgi işlem için kullanılacak karma algoritmasını belirtir. Geçerli değerler şunlardır:<br /><br /> -MD5<br />-SHA1<br />-SHA256<br />-SHA512<br /><br /> Varsayılan, `SHA1` değeridir. Bu öznitelik türünde <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Sıraya alınan taşımaları taşıma güvenlik ayarlarını tanımlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [Wcf'de kuyruklar](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem tarafından sağlanan bağlamaları yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
