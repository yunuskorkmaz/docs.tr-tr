---
title: <authentication><serviceCertificate> öğesinin
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 29170f032469b4d55b50f57ca06ce403a5aeaf2c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398220"
---
# <a name="authentication-of-servicecertificate-element"></a>\<\<ServiceCertificate > öğesinin kimlik doğrulama >
SSL/TLS anlaşması kullanılarak elde edilen hizmet sertifikalarının kimlik doğrulaması için istemci proxy tarafından kullanılan ayarları belirtir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<kimlik doğrulama >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|customCertificateValidatorType|Dizisinde. Özel bir türü doğrulamak için kullanılan tür ve derleme.|  
|certificateValidationMode|Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir. Olarak `Custom`ayarlanırsa, bir customcercertificate atevalidator da sağlanmalıdır. Varsayılan, `ChainTrust` değeridir.|  
|Revocationmodu|İptal edilen bir sertifika listesini (CRL) denetlemek için kullanılan modlardan biri. Varsayılan, `Online` değeridir.|  
|trustedStoreLocation|İki sistem depolama konumlarından biri: `LocalMachine` veya. `CurrentUser` Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır. Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir. Varsayılan, `CurrentUser` değeridir.|  
  
## <a name="customcertificatevalidator-attribute"></a>Customcercertificate Atevalidator özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Dize|Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Aşağıdaki değerlerden biri: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.<br /><br /> Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Aşağıdaki değerlerden biri: NoCheck, çevrimiçi, çevrimdışı.<br /><br /> Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Aşağıdaki değerlerden biri: LocalMachine veya CurrentUser. Varsayılan değer CurrentUser ' dır. İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle LocalMachine altında olur. İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle CurrentUser içinde olur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCertificate >](servicecertificate-of-clientcredentials-element.md)|İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesinin özniteliği, sertifikaların kimliğini doğrulamak için kullanılan güven düzeyini belirtir. `certificateValidationMode` Varsayılan olarak, düzeyi olarak `ChainTrust`ayarlanır; Bu, her bir sertifikanın, zincirin en üstündeki güvenilen bir sertifika yetkilisi ile biten sertifikalar hiyerarşisinde bulunması gerektiğini belirtir. En güvenli mod budur. Ayrıca, otomatik olarak verilen sertifikaların ( `PeerOrChainTrust`eş güven) kabul edildiğini ve güvenilen bir zincirdeki sertifikaların kabul edildiğini belirten değerini olarak da ayarlayabilirsiniz. Bu değer, istemci ve Hizmetleri geliştirirken ve hata ayıkladığında kullanılır çünkü kendinden verilen sertifikaların güvenilir bir yetkilinizden satın alınması gerekir. Bir istemciyi dağıttığınızda, bunun yerine `ChainTrust` değeri kullanın. Ayrıca, değerini veya `Custom` `None`olarak ayarlayabilirsiniz. `Custom` Değerini kullanmak için, bir derlemeyi ve sertifikayı doğrulamak için `customCertificateValidator` kullanılan türünü de özniteliğini ayarlamanız gerekir. Kendi özel Doğrulayıcısı oluşturmak için soyut X509CertificateValidator sınıfından devralması gerekir. Daha fazla bilgi için [nasıl yapılır: Özel bir sertifika Doğrulayıcı](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)kullanan bir hizmet oluşturun.  
  
 Özniteliği `revocationMode` , sertifikaların iptal için nasıl denetleneceğini belirtir. Varsayılan `online` değer, sertifikaların iptal için otomatik olarak denetleneceğini gösterir. Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki görevi yapar. İlk olarak, etki alanı adı `www.contoso.com` http protokolünün üzerinde olan uç noktalarla iletişim kurarken istemcinin kullanması için bir hizmet sertifikası belirtir. İkincisi, kimlik doğrulama sırasında kullanılan iptal modunu ve depolama konumunu belirtir.  
  
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

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Sertifikalarla Çalışma](../../../wcf/feature-details/working-with-certificates.md)
- [Nasıl yapılır: Özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<kimlik doğrulama >](authentication-of-clientcertificate-element.md)
- [İstemcileri Güvenli Hale Getirme](../../../wcf/securing-clients.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
