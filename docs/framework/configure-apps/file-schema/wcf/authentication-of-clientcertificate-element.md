---
title: <authentication><clientCertificate>öğesinin
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: 13296dbc2b3bc8836770197a1549586c841b4635
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201609"
---
# <a name="authentication-of-clientcertificate-element"></a>\<authentication>\<clientCertificate>öğesinin

Bir hizmet tarafından kullanılan istemci sertifikaları için kimlik doğrulaması davranışlarını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a>Syntax  
  
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
|Customcercertificate Atevalidatortype|İsteğe bağlı dize. Özel bir türü doğrulamak için kullanılan tür ve derleme. Bu öznitelik `certificateValidationMode` , olarak ayarlandığında ayarlanmalıdır `Custom` .|  
|certificateValidationMode|İsteğe bağlı sabit listesi. Kimlik bilgilerini doğrulamak için kullanılan modlardan birini belirtir. Bu öznitelik <xref:System.ServiceModel.Security.X509CertificateValidationMode> türü. Olarak ayarlanırsa <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType> , bir `customCertificateValidator` de sağlanmalıdır. Varsayılan değer: <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.|  
|IncludeWindowsGroups|İsteğe bağlı Boolean. Windows gruplarının güvenlik bağlamına dahil edilip edilmediğini belirtir. Bu özniteliğin olarak ayarlanması `true` , tam grup genişlemesiyle sonuçlandığından performans etkisine sahiptir. `false`Bir kullanıcının ait olduğu grupların listesini oluşturmanız gerekmiyorsa, bu özniteliği olarak ayarlayın.|  
|mapClientCertificateToWindowsAccount|Boolean. İstemcinin sertifikayı kullanarak bir Windows kimliğiyle eşleştirilip eşlenmeyeceğini belirtir. Bunu yapmak için Active Directory etkinleştirilmelidir.|  
|Revocationmodu|İsteğe bağlı sabit listesi. İptal edilen sertifika listelerini (RCL) denetlemek için kullanılan modlardan biri. Varsayılan değer: `Online`. HTTP taşıma güvenliği kullanılırken bu değer yoksayılır.|  
|trustedStoreLocation|İsteğe bağlı sabit listesi. İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser` . Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır. Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir. Varsayılan değer: `CurrentUser`.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>Customcercertificate Atevalidatortype özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Dize|Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Şu değerlerden biri: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.<br /><br /> Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Şu değerlerden biri: NoCheck, çevrimiçi, çevrimdışı. Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Şu değerlerden biri: `LocalMachine` veya `CurrentUser` . Varsayılan değer: `CurrentUser`. İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle altında olur `LocalMachine` . İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle içinde olur `CurrentUser` .|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|Bir hizmette istemcinin kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikası tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  

 `<authentication>`Öğesi sınıfına karşılık gelir <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> . İstemcilerin nasıl doğrulandığını özelleştirmenizi sağlar. Özniteliğini,,, `certificateValidationMode` veya olarak `None` ayarlayabilirsiniz `ChainTrust` `PeerOrChainTrust` `PeerTrust` `Custom` . Varsayılan olarak, düzeyi olarak ayarlanır `ChainTrust` ; Bu, her bir sertifikanın, zincirinin en üstündeki bir *kök yetkilide* sonlanan sertifikaların hiyerarşisinde bulunması gerektiğini belirtir. En güvenli mod budur. Ayrıca, `PeerOrChainTrust` otomatik olarak verilen sertifikaların (eş güven) kabul edildiğini ve güvenilen bir zincirdeki sertifikaların kabul edildiğini belirten değerini olarak da ayarlayabilirsiniz. Bu değer, istemci ve Hizmetleri geliştirirken ve hata ayıkladığında kullanılır çünkü kendinden verilen sertifikaların güvenilir bir yetkilinizden satın alınması gerekir. Bir istemciyi dağıttığınızda, `ChainTrust` bunun yerine değeri kullanın.  
  
 Değerini olarak da ayarlayabilirsiniz `Custom` . `Custom`Değere ayarlandığında, `customCertificateValidatorType` bir derlemeyi ve sertifikayı doğrulamak için kullanılan türünü de ayarlamanız gerekir. Kendi özel Doğrulayıcısı oluşturmak için soyut sınıftan devralması gerekir <xref:System.IdentityModel.Selectors.X509CertificateValidator> . Daha fazla bilgi için bkz. [nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, öğesinde bir X. 509.952 sertifikası ve özel bir doğrulama türü belirtir `<authentication>` .  
  
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
- [Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [Sertifikalarla Çalışma](../../../wcf/feature-details/working-with-certificates.md)
