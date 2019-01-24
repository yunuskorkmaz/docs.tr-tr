---
title: '&lt;scopedCertificates&gt; Öğesi &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 2406c93307ed9beb5738567a473406026b09b0a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508749"
---
# <a name="ltaddgt-of-ltscopedcertificatesgt-element"></a>&lt;scopedCertificates&gt; Öğesi &lt;ekleme&gt;
Kapsamlı sertifikalar koleksiyonuna bir X.509 sertifikası ekler.  
  
 \<system.ServiceModel>  
\<davranışlar >  
endpointBehaviors bölümü  
\<davranışı >  
\<clientCredentials >  
\<serviceCertificate >  
\<scopedCertificates >  
\<Ekle > öğesi için \<scopedCertificates >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Hedefuri|dize. Sertifikayla ilişkili hizmetin URI belirtir.|  
|findValue|dize. Aranacak değer.|  
|X509FindType|Sabit listesi. Aranacak sertifika alanlardan biri.|  
|storeLocation|Sabit listesi. İki birini aranacak konumların depolayın.|  
|storeName|Sabit listesi. Aranacak bir sistemin depolar.|  
  
## <a name="findvalue-attribute"></a>findValue özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Dize|Değer (X509FindType özniteliği tarafından belirtilen) alan bağlıdır Aranan. Örneğin, bir parmak izi için arama değeri bir dize onaltılık bir sayı olmalıdır.|  
  
## <a name="x509findtype-attribute"></a>x509FindType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Değerler şunlardır: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy FindByCertificatePolicy, FindByExtension FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|LocalMachine ya da CurrentUser.|  
  
## <a name="storename-attribute"></a>storeName özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Değerler şunlardır: Adres Defteri, AuthRoot, CertificateAuthority, My izni, kök, TrustedPeople ve TrustedPublisher.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<scopedCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|Belirli hizmetler (kapsamlı kimlik doğrulaması için) tarafından sağlanan X.509 Sertifika koleksiyonunu temsil eder.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe kullanmak için hizmet sertifikası yapılandırmak istemci kurduğu hizmet URL'sini temel sağlar. Bu, özellikle bir istemci birden çok hizmeti (uç hizmetinin yanı sıra Ara güvenlik belirteci hizmetlerine) burada iletişim verilen belirteç senaryolarda yararlıdır. Bu sertifika, sertifika tabanlı ileti güvenliği kullanan bağlamaları için hizmet iletileri şifrelemek için kullanılır ve istemciye yanıt imzalama için hizmet tarafından kullanılmak üzere beklenir.  
  
 Bağlama, hizmet ve URL ScopedCertificates içinde bulunan hizmet için belirli bir sertifika için bir sertifika gerektiriyorsa, varsayılan sertifika kullanılır.  
  
 Daha fazla bilgi için "Sertifikalar kapsamlı" bölümüne bakın. [nasıl yapılır: Federe istemci oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek koleksiyonuna bir X.509 sertifikası ekler.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <serviceCertificate>
          <scopedCertificates>
            <add targetUri="http://www.contoso.com"
                 findValue="www.Contoso.com"
                 storeLocation="LocalMachine"
                 storeName="Root"
                 x509FindType="FindByIssuerName" />
          </scopedCertificates>
        </serviceCertificate>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [Nasıl yapılır: Federe istemci oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Sertifikalarla Çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/securing-clients.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
