---
title: <defaultCertificate> Öğesi
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: 93410e815a156f91db1962f05fb1aa6baca7f955
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919245"
---
# <a name="defaultcertificate-element"></a>\<defaultCertificate > öğesi
Bir hizmet veya STS bir anlaşma protokolü aracılığıyla bir tane sağlamıyorsa kullanılacak bir X. 509.952 sertifikası belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
Endpointdavranışlar bölümü  
\<davranış >  
\<clientCredentials >  
\<serviceCertificate >  
\<defaultCertificate >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|findValue|Dizisinde. Aranacak değer.|  
|x509FindType|Listelenen. Arama yapılacak sertifika alanlarından biri.|  
|storeLocation|Listelenen. Aranacak iki sistem depolama konumundan biri.|  
|storeName|Listelenen. Arama yapmak için sistem mağazalarından biri.|  
  
## <a name="findvalue-attribute"></a>findValue özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Dize|Değer, aranmakta olan alana bağlıdır (X509FindType özniteliğiyle belirtilir). Örneğin, bir parmak izi arıyorsanız, değerin onaltılık sayı dizesi olması gerekir.|  
  
## <a name="x509findtype-attribute"></a>x509FindType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Değerler şunlardır: Findbyparmak izi, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, Findbytımenotyetvalid, FindBySerialNumber, Findbytimedoldu, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>storeLocation özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|CurrentUser veya LocalMachine.|  
  
## <a name="storename-attribute"></a>storeName özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Değerler şunlardır: AddressBook, AuthRoot, CertificateAuthority, Izin verilmeyen, My, root, Trustedkişilerim ve TrustedPublisher.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCertificate >](servicecertificate-of-clientcredentials-element.md)|İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Sertifika tabanlı ileti güvenliği kullanan bağlamalar için, bu yapılandırma öğesi tarafından belirtilen sertifika, iletileri hizmete şifrelemek için kullanılır ve istemciye yanıtları imzalamak için hizmet tarafından kullanılması beklenir. Bir hizmet tarafından hiçbir sertifika belirtilmediğinde kullanılacak tek bir sertifika depolar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, URI 'si ile `http://www.contoso.com` başlayan uç noktalar için kullanılacak bir sertifikayı ve sertifika anlaşması gerçekleştirmeyin diğer tüm uç noktalar için kullanılacak bir sertifikayı belirtir.  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [Sertifikalarla Çalışma](../../../wcf/feature-details/working-with-certificates.md)
- [\<kimlik doğrulama >](authentication-of-clientcertificate-element.md)
- [İstemcileri Güvenli Hale Getirme](../../../wcf/securing-clients.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
