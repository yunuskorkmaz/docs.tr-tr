---
title: '&lt;clientCertificate&gt; Öğesi &lt;kimlik doğrulama&gt;'
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: ccc184f63428fd4a12b9047c0bcf4416e87f24d2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750485"
---
# <a name="ltauthenticationgt-of-ltclientcertificategt-element"></a>&lt;clientCertificate&gt; Öğesi &lt;kimlik doğrulama&gt;
Bir hizmeti tarafından kullanılan istemci sertifikaları için kimlik doğrulama davranışları belirtir.  
  
 \<system.ServiceModel>  
\<davranışları >  
\<serviceBehaviors>  
\<davranışı >  
\<serviceCredentials>  
\<clientCertificate >  
\<kimlik doğrulama >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<authentication  
customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
includeWindowsGroups="Boolean"  
mapClientCertificateToWindowsAccount="Boolean"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|customCertificateValidatorType|İsteğe bağlı dize. Tür ve bir özel tür doğrulamak için kullanılan derleme. Bu öznitelik ne zaman ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.|  
|certificateValidationMode değerini|İsteğe bağlı numaralandırması. Kimlik bilgilerini doğrulamak için kullanılan modlarından birini belirtir. Bu özniteliktir <xref:System.ServiceModel.Security.X509CertificateValidationMode> türü. Varsa kümesine <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, sonra bir `customCertificateValidator` de sağlanmalıdır. Varsayılan, <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType> değeridir.|  
|includeWindowsGroups|İsteğe bağlı Boole değeri. Windows grupları güvenlik bağlamında dahil edilip edilmediğini belirtir. Bu öznitelik ayarını `true` bir tam Grup genişletme sonuçları gibi bir performans etkisi olur. Bu öznitelik ayarlanırsa `false` gruplarının listesini oluşturmak ihtiyacınız yoksa bir kullanıcının ait olduğu.|  
|mapClientCertificateToWindowsAcccount|Boole değeri. İstemci sertifikası kullanılarak bir Windows kimliğine eşlenen olup olmadığını belirtir. Bunu yapmak için Active Directory etkinleştirilmesi gerekir.|  
|revocationMode|İsteğe bağlı numaralandırması. İptal edilen sertifika (RCL) listeler denetlemek için kullanılan modlarından birini. Varsayılan, `Online` değeridir. Bu değer, HTTP taşıma güvenliği kullanırken dikkate alınmaz.|  
|trustedStoreLocation|İsteğe bağlı numaralandırması. İki sistem deposu konumlardan birini: `LocalMachine` veya `CurrentUser`. Bu değer, bir hizmet sertifikası istemciye anlaşıldığında kullanılır. Doğrulama işlemi gerçekleştirildiğinde karşı **güvenilir kişiler** belirtilen depo konumda saklayın. Varsayılan, `CurrentUser` değeridir.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType özniteliği  
  
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
|Sabit Listesi|Aşağıdaki değerlerden birini: NoCheck, çevrimiçi, çevrimdışı. Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Aşağıdaki değerlerden birini: `LocalMachine` veya `CurrentUser`. Varsayılan, `CurrentUser` değeridir. İstemci uygulaması bir sistem hesabı altında çalışan sonra sertifika genellikle altında olduğu `LocalMachine`. İstemci uygulama bir kullanıcı hesabı altında çalışan sonra sertifikayı genellikle kullanımda `CurrentUser`.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|Bir hizmet için bir istemci kimlik doğrulaması için kullanılan bir X.509 sertifikası tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<authentication>` Öğesi karşılık gelen <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> sınıfı. İstemcilerin nasıl doğrulanır özelleştirmenize olanak tanır. Ayarlayabileceğiniz `certificateValidationMode` özniteliğini `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, veya `Custom`. Varsayılan olarak, düzeyini ayarlamak `ChainTrust`, belirten her sertifika biten sertifika hiyerarşisini bulunması gereken bir *kök yetkilisi* zincirinin üstünde. Bu en güvenli bir moddur. De değer ayarlayabilirsiniz `PeerOrChainTrust`, kendi kendine verilen sertifikaların (eş güven) güvenilen zincirinde sertifikaları yanı sıra kabul edileceğini belirtir. Bu değer, geliştirme ve kendi kendine verilen sertifikaların güvenilir bir yetkiliden satın alınması değil çünkü hata ayıklama istemcileri ve Hizmetleri zaman kullanılır. Bir istemci dağıtımı sırasında kullanmak `ChainTrust` yerine değer.  
  
 De değer ayarlayabilirsiniz `Custom`. Ayarlandığında `Custom` değeri de ayarlamanız gerekir `customCertificateValidatorType` özniteliği bir derleme ve sertifikayı doğrulamak için kullanılan türü. Kendi özel Doğrulayıcısı oluşturmak için Özet devralmalıdır <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı. Daha fazla bilgi için bkz: [nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod bir X.509 sertifikası ve bir özel doğrulama türü belirtir `<authentication>` öğesi.  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
         storeLocation="CurrentUser"   
         storeName="TrustedPeople"  
         x509FindType="FindByIssuerName" />  
   <authentication customCertificateValidatorType="MyTypes.Coho"  
    certificateValidationMode="Custom"   
    revocationMode="Offline"  
    includeWindowsGroups="false"   
    mapClientCertificateToWindowsAccount="true" />  
  </clientCertificate>  
 </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>  
 <xref:System.ServiceModel.Security.X509CertificateValidationMode>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>  
 [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [Sertifikalarla Çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
