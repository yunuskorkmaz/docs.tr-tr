---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 4ec5a99139112ae600c1c2bc44feb6d3f62da1e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931735"
---
# <a name="localissuer"></a>\<LocalIssuer >
Bir güvenlik belirteci elde etmek için kullanılacak yerel verenin adresini ve bağlamasını belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
Endpointdavranışlar bölümü  
\<davranış >  
\<clientCredentials >  
\<IssuedToken >  
\<LocalIssuer >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|adres|Gerekli dize. Yerel veren 'in URI 'sini belirtir.|  
|bağlama|İsteğe bağlı dize. Sistem tarafından belirtilen bağlamalardan biri. Bir liste için bkz. [sistem tarafından sunulan bağlamalar](../../../wcf/system-provided-bindings.md).|  
|bindingConfiguration|İsteğe bağlı dize. Yapılandırma dosyasında bulunan bir bağlama yapılandırmasını belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<kimlik >](identity.md)|Yerel veren için kimlik bilgilerini belirtir.|  
|[\<üst bilgiler >](headers-element.md)|Yerel sertifikayı vereni doğru bir şekilde ele almak için gerekli olan bir adres üst bilgileri koleksiyonu. Bu koleksiyona bir üst `add` bilgi eklemek için anahtar sözcüğünü kullanabilirsiniz.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<IssuedToken >](issuedtoken.md)|Bir hizmette istemcinin kimliğini doğrulamak için kullanılan özel bir belirteci belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir güvenlik belirteci hizmetinden (STS) verilen bir belirteç edinirken, istemci uygulamanın STS ile iletişim kurmak için kullanılacak adresle ve bağlamaya yapılandırılması gerekir. Güvenlik belirteci hizmeti için bir URL sağlamadığınızda veya bir Federasyon `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` bağlamasının veren adresi veya `null`olduğunda, istemcinin Windows Communication Foundation (WCF) kanalı tarafından belirtilen değerleri kullanır. <xref:System.ServiceModel.WSFederationHttpBinding> `address` ve`binding` verilen belirteci almak için STS ile iletişim kurun. Yerel veren yapılandırma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Yerel bir veren](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)yapılandırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir `address` `bindingConfiguration` `binding` öğesinin,veöznitelikleriniayarlar`localIssuer` .  
  
```xml  
<system.serviceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="MyEndpointBehavior">
        <clientCredentials>
          <issuedToken cacheIssuedTokens="false"
                       defaultKeyEntropyMode="ClientEntropy">
            <localIssuer address="net.tcp://cohowinery/tokens"
                         binding="netTcpBinding"
                         bindingConfiguration="myTcpBindingConfig" />
          </issuedToken>
        </clientCredentials>
      </behavior>
    </endpointBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Nasıl yapılır: Yerel veren yapılandırma](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Kimlik Doğrulama ile Hizmet Kimliği](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Federasyon ve Verilen Belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [İstemcileri Güvenli Hale Getirme](../../../wcf/securing-clients.md)
- [Nasıl yapılır: Federe Istemci oluşturma](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Federasyon ve Verilen Belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md)
