---
title: "&lt;serviceCredentials&gt; için &lt;clientCertificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fc2dfd94ffbf8ce08dee9c14421f389861e99e77
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientcertificategt-of-ltservicecredentialsgt"></a>&lt;serviceCredentials&gt; için &lt;clientCertificate&gt;
Oturum açın ve bir istemci forma çift yönlü iletişim düzeni hizmetinde iletileri şifrelemek için kullanılan bir X.509 sertifikası tanımlar.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<serviceBehaviors >  
\<serviceBehaviors >  
\<davranışı >  
\<serviceCredentials >  
\<clientCertificate >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<clientCertificate>  
 <certificate/>  
 <authentication/>  
</clientCertificate>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<kimlik doğrulama >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|İstemci sertifikası kimlik doğrulama seçeneklerini belirtir.|  
|[\<Sertifika >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|Kullanılacak sertifikayı belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Hizmet kimlik doğrulaması kullanmak için kimlik bilgilerini belirtir ve istemci kimlik doğrulaması ilgili ayarları.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, hizmeti istemcisi ile önceden güvenli bir şekilde iletişim kurmak için istemci sertifikasını olmalıdır kullanılır. Bu, çift yönlü iletişim düzeni kullanırken oluşur. Daha tipik istek/yanıt desende istemci sertifikasını istemciye yanıt imzalamak ve şifrelemek için hizmet kullanır istekte içerir. Çift yönlü iletişimi düzeninde ancak, hizmeti istemciden gelen istekte yok ve bu nedenle önceden istemciye ileti güvenliğini sağlamak için istemci sertifikasını gerekiyor. Bu nedenle bir bant dışı anlaşma istemci sertifikasını elde etmek ve bu öğe kullanarak sertifikayı belirtmeniz gerekir. Çift yönlü hizmetler hakkında daha fazla bilgi için bkz: [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
 Bu öğe kümesindeki sertifika ile yapılandırılmış bağlamaları için istemciye iletileri şifrelemek için kullanılan `MutualCertificateDuplex` ileti güvenlik kimlik doğrulama modu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>  
 [Nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [Güvenlik davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Sertifikalar ile çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
