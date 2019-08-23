---
title: <serviceCertificate><clientCredentials> öğesinin
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: a3013d0f7efd3014892cf6400447d708809c5fcd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936335"
---
# <a name="servicecertificate-of-clientcredentials-element"></a>\<ServiceCertificate > \<ClientCredentials > öğesi
İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<Endpointdavranışlar >  
\<davranış >  
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
|[\<defaultCertificate >](defaultcertificate-element.md)|Bir hizmet veya STS bir anlaşma protokolü aracılığıyla bir tane sağlamıyorsa kullanılacak bir X. 509.952 sertifikası belirtir.|  
|[\<scopedCertificates >](scopedcertificates-element.md)|Kimlik doğrulama için belirli hizmetler (kapsamlı) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder. Bu koleksiyon genellikle, bir Federasyon senaryosunda güvenlik belirteci Hizmetleri için hizmet sertifikalarını belirtmek için kullanılır.|  
|[\<kimlik doğrulama >](authentication-of-servicecertificate-element.md)|İstemci tarafından kullanılan hizmet sertifikaları için kimlik doğrulaması davranışlarını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCredentials >](clientcredentials.md)|İstemci tarafından bir hizmette kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesi, SSL kimlik doğrulaması kullanılarak hizmet tarafından sunulan sertifikayı doğrulamak için istemci tarafından kullanılan ayarları belirtir. Ayrıca, istemcide ileti güvenliği kullanılarak iletileri şifrelemek için kullanılmak üzere açıkça yapılandırılmış hizmet için bir sertifika içerir.  
  
 `serviceCertificate` Öğesinin öznitelikleri, [ \<ClientCertificate >](clientcertificate-of-clientcredentials-element.md)öznitelikleriyle aynıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [İstemcileri Güvenli Hale Getirme](../../../wcf/securing-clients.md)
- [Sertifikalarla Çalışma](../../../wcf/feature-details/working-with-certificates.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
