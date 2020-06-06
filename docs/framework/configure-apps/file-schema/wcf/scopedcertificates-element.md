---
title: <scopedCertificates> Öğesi
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 3c06159709df0afe2a475de1e186b0114af32bc2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399950"
---
# <a name="scopedcertificates-element"></a>\<scopedCertificates> Öğesi
Kimlik doğrulama için belirli hizmetler (kapsamlı) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder. Bu koleksiyon genellikle, bir Federasyon senaryosunda güvenlik belirteci Hizmetleri için hizmet sertifikalarını belirtmek için kullanılır.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopedCertificates>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<add>](add-of-scopedcertificates-element.md)|Kapsamlı sertifikalar koleksiyonuna bir X. 509.440 sertifikası ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu koleksiyon, istemcinin iletişim kurduğu hizmetin URL 'sini temel alarak kullanılacak hizmet sertifikalarını yapılandırmasına olanak sağlar. Bu özellikle, bir istemcinin birden çok hizmetle (bitiş hizmeti ve aracı güvenlik belirteci Hizmetleri) iletişim kuramadığı verilen belirteç senaryolarında kullanışlıdır. Sertifika tabanlı ileti güvenliği kullanan bağlamalar için, bu sertifika hizmete iletileri şifrelemek için kullanılır ve istemciye yanıtları imzalamak için hizmet tarafından kullanılması beklenir.  
  
 Bir bağlama hizmet için bir sertifika gerektiriyorsa ve hizmet URL 'SI için belirli bir sertifika ScopedCertificates içinde bulunmazsa, varsayılan sertifika kullanılır.  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: federe Istemci oluşturma](../../../wcf/feature-details/how-to-create-a-federated-client.md)konusunun "kapsamlı sertifikalar" bölümü.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, etki alanı adı HTTP protokolünün üzerinde olan uç noktalarla iletişim kurarken İstemcinin kullanacağı bir hizmet sertifikasını belirtir `http://www.contoso.com` .  
  
```xml  
<serviceCertificate>
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
</serviceCertificate>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [Sertifikalarla Çalışma](../../../wcf/feature-details/working-with-certificates.md)
- [Nasıl yapılır: Federe İstemci Oluşturma](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [\<add>](add-of-scopedcertificates-element.md)
- [İstemcileri Güvenli Hale Getirme](../../../wcf/securing-clients.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
