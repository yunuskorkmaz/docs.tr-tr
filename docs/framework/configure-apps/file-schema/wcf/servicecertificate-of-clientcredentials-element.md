---
title: '&lt;clientCredentials&gt; Öğesi &lt;serviceCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 2f1d95238a16bfd286a64973c6e5cfb95fe02dc4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744888"
---
# <a name="ltservicecertificategt-of-ltclientcredentialsgt-element"></a>&lt;clientCredentials&gt; Öğesi &lt;serviceCertificate&gt;
İstemci bir hizmete kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<endpointBehaviors>  
\<davranışı >  
\<clientCredentials >  
\<serviceCertificate >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<defaultCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|Kullanılacak olan X.509 sertifikasını belirtir, STS veya hizmetin sağlamadığı anlaşma protokolü aracılığıyla.|  
|[\<scopedCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|Belirli hizmetler (kapsamlı kimlik doğrulaması için) tarafından sağlanan X.509 Sertifika koleksiyonunu temsil eder. Bu koleksiyon, genellikle hizmet sertifikaları için güvenlik belirteci hizmetlerine federe bir senaryoda belirtmek için kullanılır.|  
|[\<kimlik doğrulama >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|Bir istemci tarafından kullanılan hizmet sertifikaları için kimlik doğrulaması davranışlarını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Bir hizmete kendi kimliğini doğrulamak için istemci tarafından kullanılan kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesi, SSL kimlik doğrulaması kullanarak hizmeti tarafından sunulan sertifika doğrulamak için istemci tarafından kullanılan ayarları belirtir. Ayrıca, hizmet ileti güveliği kullanarak iletileri şifrelemek için kullanılacak istemci üzerinde açıkça yapılandırılmış hizmeti için herhangi bir sertifika içerir.  
  
 Özniteliklerini `serviceCertificate` öğesi için öznitelikleri aynı [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/securing-clients.md)
- [Sertifikalarla Çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
