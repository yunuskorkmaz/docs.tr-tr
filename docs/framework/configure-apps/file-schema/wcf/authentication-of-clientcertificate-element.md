---
title: <authentication> ' ın <clientCertificate> öğesi
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: e232cde8f6838de734e37aeee3f52cd7f7e7502d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221208"
---
# <a name="authentication-of-clientcertificate-element"></a>\<kimlik doğrulama >, \<clientCertificate > öğesi
Bir hizmet tarafından kullanılan istemci sertifikaları için kimlik doğrulaması davranışlarını belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
\<serviceCredentials>  
\<clientCertificate >  
\<kimlik doğrulama >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|customCertificateValidatorType|İsteğe bağlı dize. Tür ve özel bir tür doğrulamak için kullanılan bir derleme. Bu öznitelik olduğunda ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.|  
|Certificatevalidationmode'u|İsteğe bağlı sabit listesi. Kimlik bilgilerini doğrulamak için kullanılan modlardan birini belirtir. Bu özniteliktir <xref:System.ServiceModel.Security.X509CertificateValidationMode> türü. Varsa kümesine <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, ardından bir `customCertificateValidator` de sağlanmalıdır. Varsayılan, <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType> değeridir.|  
|includeWindowsGroups|İsteğe bağlı Boolean. Windows gruplarını güvenlik bağlamına dahil edilip edilmediğini belirtir. Bu öznitelik ayarını `true` içinde bir tam Grup genişletme sonuçları gibi bir performans etkisi vardır. Bu öznitelik ayarlanan `false` gruplarının listesini oluşturmak ihtiyacınız yoksa bir kullanıcıya ait.|  
|mapClientCertificateToWindowsAcccount|Boole değeri. İstemci sertifikasını kullanarak bir Windows kimliği eşlenen olup olmadığını belirtir. Bunu yapmak için Active Directory etkinleştirilmesi gerekir.|  
|revocationMode|İsteğe bağlı sabit listesi. İptal edilen sertifikalar listelerini (RCL) denetlemek için kullanılan modlardan biri. Varsayılan, `Online` değeridir. HTTP aktarım güvenliği kullanırken, bu değer yoksayılır.|  
|trustedStoreLocation|İsteğe bağlı sabit listesi. İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser`. Bir hizmet sertifikası istemciye anlaşıldığında, bu değer kullanılır. Doğrulama işlemi gerçekleştirildiğinde karşı **güvenilir kişiler** depolamak belirtilen depolama konumu. Varsayılan, `CurrentUser` değeridir.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType özniteliği  
  
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
|Sabit Listesi|Aşağıdaki değerlerden biri: NoCheck, Online, Offline. Daha fazla bilgi için [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Aşağıdaki değerlerden biri: `LocalMachine` veya `CurrentUser`. Varsayılan, `CurrentUser` değeridir. İstemci uygulama bir sistem hesabı altında çalıştığından sonra sertifika genellikle altında olduğu `LocalMachine`. İstemci uygulama bir kullanıcı hesabı altında çalıştığından sonra sertifika genellikle kullanımda `CurrentUser`.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|Bir hizmete istemcinin kimliğini doğrulamak için kullanılan bir X.509 sertifikası tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<authentication>` Karşılık gelen öğe <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> sınıfı. İstemcilerin nasıl doğrulanır özelleştirmenize olanak sağlar. Ayarlayabileceğiniz `certificateValidationMode` özniteliğini `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, veya `Custom`. Varsayılan olarak, düzeyini ayarlamak `ChainTrust`, belirten her sertifika sonu sertifika hiyerarşisini bulunması gereken bir *kök yetkilisi* zinciri üstünde. En güvenli mod budur. De değer ayarlayabilirsiniz `PeerOrChainTrust`, kendi kendine verilen sertifikaların (eş güven) güvenilen bir zinciri olan sertifikaları yanı sıra kabul edildiğini belirtir. Bu değer, geliştirme ve istemciler ve hizmetler kendi kendine verilen sertifikaların güvenilir yetkilisinden satın alınması değil çünkü hata ayıklama kullanılır. Bir istemci dağıtırken kullanırsınız `ChainTrust` yerine değeri.  
  
 De değer ayarlayabilirsiniz `Custom`. Ayarlandığında `Custom` değeri ayarlamanız gerekir `customCertificateValidatorType` öznitelik bir bütünleştirilmiş kod ve sertifikayı doğrulamak için kullanılan tür. Kendi özel Doğrulayıcı sağlayıcısı oluşturmak için Özet devralmalıdır <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı. Daha fazla bilgi için [nasıl yapılır: Özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod bir X.509 sertifikası ve bir özel doğrulama türü belirtir `<authentication>` öğesi.  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>
- <xref:System.ServiceModel.Security.X509CertificateValidationMode>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>
- [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Nasıl yapılır: Özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [Sertifikalarla Çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
