---
title: <authentication><clientCertificate> öğesinin
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: 99084f6b7afbdd8586ee706cd6ec44b349d81ff2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398263"
---
# <a name="authentication-of-clientcertificate-element"></a>\<\<ClientCertificate > öğesinin kimlik doğrulama >
Bir hizmet tarafından kullanılan istemci sertifikaları için kimlik doğrulaması davranışlarını belirtir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCertificate >** ](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<kimlik doğrulama >**  
  
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
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|customCertificateValidatorType|İsteğe bağlı dize. Özel bir türü doğrulamak için kullanılan tür ve derleme. Bu öznitelik `certificateValidationMode` , olarak `Custom`ayarlandığında ayarlanmalıdır.|  
|certificateValidationMode|İsteğe bağlı sabit listesi. Kimlik bilgilerini doğrulamak için kullanılan modlardan birini belirtir. Bu öznitelik <xref:System.ServiceModel.Security.X509CertificateValidationMode> türü. Olarak <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>ayarlanırsa, bir `customCertificateValidator` de sağlanmalıdır. Varsayılan, <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType> değeridir.|  
|IncludeWindowsGroups|İsteğe bağlı Boolean. Windows gruplarının güvenlik bağlamına dahil edilip edilmediğini belirtir. Bu özniteliğin olarak `true` ayarlanması, tam grup genişlemesiyle sonuçlandığından performans etkisine sahiptir. Bir kullanıcının ait olduğu `false` grupların listesini oluşturmanız gerekmiyorsa, bu özniteliği olarak ayarlayın.|  
|mapClientCertificateToWindowsAccount|Boolean. İstemcinin sertifikayı kullanarak bir Windows kimliğiyle eşleştirilip eşlenmeyeceğini belirtir. Bunu yapmak için Active Directory etkinleştirilmelidir.|  
|Revocationmodu|İsteğe bağlı sabit listesi. İptal edilen sertifika listelerini (RCL) denetlemek için kullanılan modlardan biri. Varsayılan, `Online` değeridir. HTTP taşıma güvenliği kullanılırken bu değer yoksayılır.|  
|trustedStoreLocation|İsteğe bağlı sabit listesi. İki sistem depolama konumlarından biri: `LocalMachine` veya. `CurrentUser` Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır. Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir. Varsayılan, `CurrentUser` değeridir.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>Customcercertificate Atevalidatortype özniteliği  
  
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
|Sabit Listesi|Aşağıdaki değerlerden biri: NoCheck, çevrimiçi, çevrimdışı. Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Şu değerlerden biri: `LocalMachine` veya. `CurrentUser` Varsayılan, `CurrentUser` değeridir. İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle altında `LocalMachine`olur. İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle içinde `CurrentUser`olur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCertificate >](clientcertificate-of-servicecredentials.md)|Bir hizmette istemcinin kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikası tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<authentication>` Öğesi <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> sınıfına karşılık gelir. İstemcilerin nasıl doğrulandığını özelleştirmenizi sağlar. `certificateValidationMode` Özniteliğini, ,,`ChainTrust` `None` veya`Custom`olarak ayarlayabilirsiniz. `PeerOrChainTrust` `PeerTrust` Varsayılan olarak, düzeyi olarak `ChainTrust`ayarlanır; Bu, her bir sertifikanın, zincirinin en üstündeki bir *kök yetkilide* sonlanan sertifikaların hiyerarşisinde bulunması gerektiğini belirtir. En güvenli mod budur. Ayrıca, otomatik olarak verilen sertifikaların ( `PeerOrChainTrust`eş güven) kabul edildiğini ve güvenilen bir zincirdeki sertifikaların kabul edildiğini belirten değerini olarak da ayarlayabilirsiniz. Bu değer, istemci ve Hizmetleri geliştirirken ve hata ayıkladığında kullanılır çünkü kendinden verilen sertifikaların güvenilir bir yetkilinizden satın alınması gerekir. Bir istemciyi dağıttığınızda, bunun yerine `ChainTrust` değeri kullanın.  
  
 Değerini olarak `Custom`da ayarlayabilirsiniz. `Custom` Değere ayarlandığında, bir derlemeyi ve sertifikayı doğrulamak için kullanılan türünü `customCertificateValidatorType` de ayarlamanız gerekir. Kendi özel Doğrulayıcısı oluşturmak için soyut <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıftan devralması gerekir. Daha fazla bilgi için [nasıl yapılır: Özel bir sertifika Doğrulayıcı](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)kullanan bir hizmet oluşturun.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, `<authentication>` öğesinde bir X. 509.952 sertifikası ve özel bir doğrulama türü belirtir.  
  
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
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Nasıl yapılır: Özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [Sertifikalarla Çalışma](../../../wcf/feature-details/working-with-certificates.md)
