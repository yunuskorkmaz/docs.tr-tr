---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 68e3a0802a10b14148188a81ee24ed901caa147f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925376"
---
# <a name="issuedtoken"></a>\<IssuedToken >
Bir hizmette istemcinin kimliğini doğrulamak için kullanılan özel bir belirteci belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
Endpointdavranışlar bölümü  
\<davranış >  
\<clientCredentials >  
\<IssuedToken >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`cacheIssuedTokens`|Belirteçlerin önbelleğe alınıp alınmayacağını belirten isteğe bağlı Boolean özniteliği. Varsayılan, `true` değeridir.|  
|`defaultKeyEntropyMode`|El sıkışma işlemleri için hangi rastgele değerlerin (entropler) kullanıldığını belirten isteğe bağlı dize özniteliği. `ClientEntropy`Değerleri, `ServerEntropy`, ve`CombinedEntropy`değerleridir .varsayılandeğer.`CombinedEntropy` Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`issuedTokenRenewalThresholdPercentage`|Bir belirtecin yenilenmesinden önce geçebilen geçerli bir zaman çerçevesinin (belirteç veren tarafından sağlanan) yüzdesini belirten isteğe bağlı tamsayı özniteliği. Değerler 0 ile 100 arasında değerlerdir. Yenileme deneninceye kadar geçen sürenin% 60 ' i belirten varsayılan değer 60 ' dir.|  
|`issuerChannelBehaviors`|Verenle iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.|  
|`localIssuerChannelBehaviors`|Yerel veren ile iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.|  
|`maxIssuedTokenCachingTime`|Belirteç veren (STS) bir süre belirtmezse verilen belirteçlerin önbelleğe alındığı süreyi belirten isteğe bağlı TimeSpan özniteliği. Varsayılan değer "10675199.02:48:05.4775807" ' dir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<LocalIssuer >](localissuer.md)|Belirtecin yerel veren adresinin ve uç noktayla iletişim kurmak için kullanılan bağlamanın adresini belirtir.|  
|[\<ıssuerchanneldavranışlar >](issuerchannelbehaviors-element.md)|Yerel bir veren ile iletişim kurulurken kullanılacak uç nokta davranışlarını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCredentials >](clientcredentials.md)|Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Verilen belirteç, bir Federasyon senaryosunda güvenli bir belirteç hizmeti (STS) ile kimlik doğrulaması yapılırken kullanılan özel bir kimlik bilgisi türüdür. Varsayılan olarak, belirteç bir SAML belirtecidir. Daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md). ve [Federasyon ve verilen belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md).  
  
 Bu bölüm, bir güvenlik belirteci hizmeti ile kullanılan bir belirteçleri yerel olarak veren veya davranışları yapılandırmak için kullanılan öğeleri içerir. Bir istemciyi yerel bir veren kullanmak üzere yapılandırmaya ilişkin yönergeler için bkz [. nasıl yapılır: Yerel bir veren](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)yapılandırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Federasyon ve Verilen Belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [İstemcileri Güvenli Hale Getirme](../../../wcf/securing-clients.md)
- [Nasıl yapılır: Federe Istemci oluşturma](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Nasıl yapılır: Yerel veren yapılandırma](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Federasyon ve Verilen Belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md)
