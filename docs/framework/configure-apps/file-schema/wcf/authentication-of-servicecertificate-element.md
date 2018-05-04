---
title: '&lt;serviceCertificate&gt; Öğesi &lt;kimlik doğrulama&gt;'
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 9ef17c8bedf6bcef21a7c59d98a86bb20ad2da80
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltauthenticationgt-of-ltservicecertificategt-element"></a>&lt;serviceCertificate&gt; Öğesi &lt;kimlik doğrulama&gt;
SSL/TLS anlaşması kullanılarak elde edilen hizmet sertifikaların kimliğini doğrulamak için istemci Ara sunucusu tarafından kullanılan ayarları belirtir.  
  
 \<system.ServiceModel>  
\<davranışları >  
endpointBehaviors bölümü  
\<davranışı >  
\<clientCredentials >  
\<serviceCertificate >  
\<kimlik doğrulama >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<authentication customCertificateValidatorType="String" certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"   
trustedStoreLocation="LocalMachine/CurrentUser" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|customCertificateValidatorType|Dize. Tür ve bir özel tür doğrulamak için kullanılan derleme.|  
|certificateValidationMode değerini|Kimlik bilgilerini doğrulamak için kullanılan üç modlarından birini belirtir. Varsa kümesine `Custom`, sonra da bir customCertificateValidator de sağlanmalıdır. Varsayılan, `ChainTrust` değeridir.|  
|revocationMode|İptal edilen sertifika (CRL) listeler denetlemek için kullanılan modlarından birini. Varsayılan, `Online` değeridir.|  
|trustedStoreLocation|İki sistem deposu konumlardan birini: `LocalMachine` veya `CurrentUser`. Bu değer, bir hizmet sertifikası istemciye anlaşıldığında kullanılır. Doğrulama işlemi gerçekleştirildiğinde karşı **güvenilir kişiler** belirtilen depo konumda saklayın. Varsayılan, `CurrentUser` değeridir.|  
  
## <a name="customcertificatevalidator-attribute"></a>customCertificateValidator özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Dize|Tür adı ve derleme ve diğer veri türü bulmak için kullanılan belirtir.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode değerini özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Aşağıdaki değerlerden biri: None, PeerTrust, ChainTrust, PeerOrChainTrust, özel.<br /><br /> Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Aşağıdaki değerlerden birini: NoCheck, çevrimiçi, çevrimdışı.<br /><br /> Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Aşağıdaki değerlerden birini: LocalMachine veya Currentuser'a. Currentuser'a varsayılandır. Sonra sertifika, genellikle istemci uygulamasının sistem hesabı altında çalışıyorsa, LocalMachine altında içindir. İstemci uygulama bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle Currentuser'a içinde yok.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|İstemci bir hizmete kimlik doğrulanırken kullanılacak bir sertifika belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `certificateValidationMode` Bu yapılandırma öğesinin özniteliği sertifikaların kimliğini doğrulamak için kullanılan güven düzeyini belirtir. Varsayılan olarak, düzeyini ayarlamak `ChainTrust`, belirten her sertifika zinciri üstündeki bir güvenilen sertifika yetkilisi biten sertifikaların bir hiyerarşideki bulunması gerekir. Bu en güvenli bir moddur. De değer ayarlayabilirsiniz `PeerOrChainTrust`, kendi kendine verilen sertifikaların (eş güven) güvenilen zincirinde sertifikaları yanı sıra kabul edileceğini belirtir. Bu değer, geliştirme ve kendi kendine verilen sertifikaların güvenilir bir yetkiliden satın alınması değil çünkü hata ayıklama istemcileri ve Hizmetleri zaman kullanılır. Bir istemci dağıtımı sırasında kullanmak `ChainTrust` yerine değer. De değer ayarlayabilirsiniz `Custom` veya `None`. Kullanılacak `Custom` değeri de ayarlamanız gerekir `customCertificateValidator` özniteliği bir derleme ve sertifikayı doğrulamak için kullanılan türü. Kendi özel Doğrulayıcısı oluşturmak için Özet X509CertificateValidator sınıfından devralınan gerekir. Daha fazla bilgi için bkz: [nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 `revocationMode` Özniteliği belirtir sertifika iptali için nasıl denetlenir. Varsayılan değer `online` belirten sertifikaları iptal edilmek üzere otomatik olarak denetlenir. Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki görevi yapar. Öncelikle, istemcinin etki alanı adı uç ile iletişim kurmasını www.contoso.com HTTP protokolü üzerinden olduğunda kullanması bir hizmet sertifikası belirtir. İkinci olarak, kimlik doğrulaması sırasında kullanılan iptal modu ve depolama konumunu belirtir.  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>  
 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>  
 [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Sertifikalarla Çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [\<kimlik doğrulama >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/securing-clients.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
