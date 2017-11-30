---
title: '&lt;msmqTransportSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: eee2cb916d79bf3b79e882cd757b10344121f6b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmsmqtransportsecuritygt"></a>&lt;msmqTransportSecurity&gt;
Özel bağlama için MSMQ taşıma güvenlik ayarlarını belirtir.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<msmqIntegration >  
\<msmqTransportSecurity >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<msmqTransportSecurity>  
   msmqAuthenticationMode="None/Windows/Certificate"  
   msmqEncryptionAlgorithm="RC4Stream/AES"  
   msmqProtectionLevel="None/Sign/EncryptAndSign"  
   msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</msmqTransportSecurity>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|İletinin MSMQ taşıma tarafından nasıl doğrulanmış gerekir belirtir. Bu ayarlanırsa `None`, değeri `msmqProtectionLevel` özniteliği de ayarlanmalıdır `None`.<br /><br /> Geçerli değerler şunlardır:<br /><br /> -Hiçbiri: Kimlik doğrulaması yok.<br />-Windows: SID iletiyle ilişkili X.509 sertifikası almak için Active Directory kimlik doğrulama mekanizması kullanır. Bu, daha sonra kullanıcı emin olmak için ACL sırasının sıraya yazmak için yeterli izne sahip denetlemek için kullanılır.<br />-Sertifika: Kanal sertifikayı sertifika deposundan alır.<br /><br /> Windows varsayılan değerdir. Bu öznitelik türünde <xref:System.ServiceModel.MsmqAuthenticationMode>.|  
|`msmqEncryptionAlgorithm`|İleti şifreleme hattaki iletileri ileti sırası yöneticileri arasında aktarırken kullanılacak algoritmayı belirtir. Geçerli değerler şunlardır:<br /><br /> -RC4Stream<br />-AES<br /><br /> RC4Stream varsayılan değerdir. Bu öznitelik türünde <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|`msmqProtectionLevel`|İletinin MSMQ taşıma düzeyinde güvenliği nasıl belirtir. İleti bütünlüğü ve takası da EncryptAndSign sağlar ancak şifreleme ileti bütünlüğü sağlar; diğer bir deyişle, iletinin gerçekten gönderenden gelir ve gönderenin kim kendisinin gerçekleştirilmesine söyler. Geçerli değerler şunlardır:<br /><br /> -Hiçbiri: Koruma yok.<br />-Oturum: İletileri imzalanmıştır.<br />-Da EncryptAndSign: İletileri şifrelenmiş ve imzalanmış.<br /><br /> Varsayılan değer işaretidir. Bu öznitelik türünde <xref:System.Net.Security.ProtectionLevel>.|  
|`msmqSecureHashAlgorithm`|Özet imzaları bir parçası olarak bilgisayar kullanılacak algoritmayı belirtir. Geçerli değerler şunlardır:<br /><br /> -MD5<br />-SHA1<br />-SHA256<br />-SHA512<br /><br /> SHA1 varsayılan değerdir. Bu öznitelik türünde <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<msmqIntegration >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegration.md)|Message Queuing (MSMQ) gönderen veya alıcı ile etkileşim için gerekli ayarları belirtir.|  
|[\<msmqTransport >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransport.md)|Yerel MSMQ protokolünü kullanan bir Windows Communication Foundation (WCF) hizmetini queuing iletişimi özelliklerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Taşıma güvenliği hakkında daha fazla bilgi için bkz: [taşıma güvenliği](../../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Wcf'de kuyruklar](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Taşımalar](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Taşıma seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Taşıma güvenliği](../../../../../docs/framework/wcf/feature-details/transport-security.md)
