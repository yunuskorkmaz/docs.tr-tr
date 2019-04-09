---
title: <authentication> ' ın <serviceCertificate> öğesi
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: b96d53312d672eebd67de82f69cd9a0a2b5bd22e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117777"
---
# <a name="authentication-of-servicecertificate-element"></a>\<kimlik doğrulama >, \<serviceCertificate > öğesi
SSL/TLS anlaşması kullanılarak elde edilen hizmet sertifikalarının kimlik doğrulaması için istemci proxy tarafından kullanılan ayarları belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
endpointBehaviors bölümü  
\<davranışı >  
\<clientCredentials >  
\<serviceCertificate >  
\<kimlik doğrulama >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|customCertificateValidatorType|dize. Tür ve özel bir tür doğrulamak için kullanılan bir derleme.|  
|Certificatevalidationmode'u|Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir. Varsa kümesine `Custom`, sonra da bir customCertificateValidator de sağlanmalıdır. Varsayılan, `ChainTrust` değeridir.|  
|revocationMode|İptal edilen sertifikalar listelerini (CRL) denetlemek için kullanılan modlardan biri. Varsayılan, `Online` değeridir.|  
|trustedStoreLocation|İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser`. Bir hizmet sertifikası istemciye anlaşıldığında, bu değer kullanılır. Doğrulama işlemi gerçekleştirildiğinde karşı **güvenilir kişiler** depolamak belirtilen depolama konumu. Varsayılan, `CurrentUser` değeridir.|  
  
## <a name="customcertificatevalidator-attribute"></a>customCertificateValidator özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Dize|Tür adı ve derleme ve diğer veri türünü bulmak için kullanılan belirtir.|  
  
## <a name="certificatevalidationmode-attribute"></a>Certificatevalidationmode'u özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Aşağıdaki değerlerden biri: None, PeerTrust, ChainTrust, PeerOrChainTrust, özel.<br /><br /> Daha fazla bilgi için [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Aşağıdaki değerlerden biri: NoCheck, Online, Offline.<br /><br /> Daha fazla bilgi için [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Aşağıdaki değerlerden biri: LocalMachine ya da CurrentUser. CurrentUser varsayılandır. İstemci uygulama bir sistem hesabı altında çalışıyorsa, sertifika genellikle altında LocalMachine dizisidir. İstemci uygulama bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle içinde CurrentUser dizisidir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|İstemci bir hizmete kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `certificateValidationMode` Bu yapılandırma öğesinin özniteliği sertifikaların kimliğini doğrulamak için kullanılan güven düzeyini belirtir. Varsayılan olarak, düzeyi `ChainTrust`, her bir sertifikanın sertifika zinciri üst kısmındaki bir güvenilen sertifika yetkilisi ile biten bir hiyerarşideki bulunması gereken belirtir. En güvenli mod budur. De değer ayarlayabilirsiniz `PeerOrChainTrust`, kendi kendine verilen sertifikaların (eş güven) güvenilen bir zinciri olan sertifikaları yanı sıra kabul edildiğini belirtir. Bu değer, geliştirme ve istemciler ve hizmetler kendi kendine verilen sertifikaların güvenilir yetkilisinden satın alınması değil çünkü hata ayıklama kullanılır. Bir istemci dağıtırken kullanırsınız `ChainTrust` yerine değeri. De değer ayarlayabilirsiniz `Custom` veya `None`. Kullanılacak `Custom` değeri ayarlamanız gerekir `customCertificateValidator` öznitelik bir bütünleştirilmiş kod ve sertifikayı doğrulamak için kullanılan tür. Kendi özel Doğrulayıcı sağlayıcısı oluşturmak için soyut X509CertificateValidator sınıftan devralmalıdır. Daha fazla bilgi için [nasıl yapılır: Özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 `revocationMode` Özniteliği belirtir nasıl sertifika iptali için denetlenir. Varsayılan değer `online` gösteren sertifika iptali için otomatik olarak denetlenir. Daha fazla bilgi için [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki görevleri gerçekleştirir. Bir hizmet uç noktaları ile iletişim kurulurken etki alanı adını kullanmak istemci sertifikası ilk belirtir `www.contoso.com` HTTP protokolü üzerinden. İkinci olarak, kimlik doğrulaması sırasında kullanılan iptal modu ve depolama konumunu belirtir.  
  
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
- [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Sertifikalarla Çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<kimlik doğrulama >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)
- [İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/securing-clients.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
