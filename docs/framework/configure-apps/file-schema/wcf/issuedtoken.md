---
title: '&lt;IssuedToken&gt;'
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: a06d59c5dfb14e5f3346ff2424339659568a369a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150194"
---
# <a name="ltissuedtokengt"></a>&lt;IssuedToken&gt;
Bir hizmete istemcinin kimliğini doğrulamak için kullanılan özel simgeyi belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
endpointBehaviors bölümü  
\<davranışı >  
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
|`cacheIssuedTokens`|Belirteçleri önbelleğe yazılıp yazılmayacağını belirten isteğe bağlı Boolean özniteliği. Varsayılan, `true` değeridir.|  
|`defaultKeyEntropyMode`|Hangi rastgele değerlerin (entropilerin) el sıkışma işlemlerinde kullanılacağını belirten isteğe bağlı dize özniteliği. Değerler `ClientEntropy`, `ServerEntropy`, ve `CombinedEntropy`, varsayılan `CombinedEntropy`. Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`issuedTokenRenewalThresholdPercentage`|Geçerli saat (belirteç vericisi tarafından sağlanan) bir belirtecin yenilenmesinden önce geçebilecek çerçeve yüzdesini belirten isteğe bağlı tamsayı özniteliği. Değerler 0 ile 100 arasındadır. 60 yenileme denenmeden önce %60 zaman geçiş belirten varsayılandır.|  
|`issuerChannelBehaviors`|Verici ile iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.|  
|`localIssuerChannelBehaviors`|Yerel verici ile iletişim kurarken kullanılacak kanal davranışlarını belirten isteğe bağlı öznitelik.|  
|`maxIssuedTokenCachingTime`|Verilen belirteçler süreyi belirten isteğe bağlı Timespan özniteliği önbelleğe belirteç vericisinin (STS) bir süre belirtmediği. Varsayılan değer "10675199.02:48:05.4775807."|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<localIssuer >](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|Belirteç uç noktası ile iletişim kurmak için kullanılan bağlama ve yerel dağıtımcının adresini belirtir.|  
|[\<issuerChannelBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|Yerel verici ile iletişim kurarken kullanılacak uç nokta davranışlarını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Verilen bir belirteç, örneğin, ile bir güvenli belirteç hizmeti (STS) bir Federasyon senaryosunda kimlik doğrulaması için kullanılan bir özel kimlik bilgisi türüdür. Varsayılan olarak, SAML belirteci bir belirteçtir. Daha fazla bilgi için [Federasyon ve verilen belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). ve [Federasyon ve verilen belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Bu bölümde, belirteçleri veya güvenlik belirteci hizmeti ile kullanılan davranışlar yerel yayımlayan yapılandırma için kullanılan öğeleri içerir. Yerel yayımlayan kullanmak bir istemci yapılandırma yönergeleri için bkz: [nasıl yapılır: Yerel yayımlayan yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Federasyon ve Verilen Belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/securing-clients.md)  
 [Nasıl yapılır: Federe istemci oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Nasıl yapılır: Yerel yayımlayan yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [Federasyon ve Verilen Belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
