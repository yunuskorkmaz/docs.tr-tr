---
title: '&lt;IssuedToken&gt;'
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 9a8d701e0806aae0a17a1c5ff7284606dd080f85
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltissuedtokengt"></a>&lt;IssuedToken&gt;
Bir hizmet için bir istemci kimlik doğrulaması için kullanılan özel bir belirteç belirtir.  
  
 \<system.ServiceModel>  
\<davranışları >  
endpointBehaviors bölümü  
\<davranışı >  
\<clientCredentials >  
\<IssuedToken >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<issuedToken   
   cacheIssuedTokens="Boolean"  
   defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"  
   issuedTokenRenewalThresholdPercentage = "0 to 100"  
   issuerChannelBehaviors="String"  
      localIssuerChannelBehaviors="String"  
   maxIssuedTokenCachingTime="TimeSpan"  
</issuedToken>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`cacheIssuedTokens`|Belirteçleri önbelleğe alınıp alınmayacağını belirtir isteğe bağlı Boole öznitelik. Varsayılan, `true` değeridir.|  
|`defaultKeyEntropyMode`|Hangi rastgele değerler (entropies) el sıkışması işlemleri için kullanılan belirten isteğe bağlı dize özniteliği. Değerler `ClientEntropy`, `ServerEntropy`, ve `CombinedEntropy`, varsayılan `CombinedEntropy`. Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|`issuedTokenRenewalThresholdPercentage`|Geçerli saat (belirteci veren tarafından sağlanan) bir belirteç yenilenmeden önce bir geçirebilirsiniz çerçevesi yüzdesini belirtir isteğe bağlı tamsayı özniteliği. Değerler 0 ile 100 arasındadır. 60, yenileme denenmeden önce zaman geçişleri % 60 belirten varsayılandır.|  
|`issuerChannelBehaviors`|Veren ile iletişim kurarken kullanması için kanal davranışları belirten isteğe bağlı öznitelik.|  
|`localIssuerChannelBehaviors`|Yerel veren ile iletişim kurarken kullanması için kanal davranışları belirten isteğe bağlı öznitelik.|  
|`maxIssuedTokenCachingTime`|Verilen belirteçler süreyi belirten isteğe bağlı Timespan özniteliği önbelleğe alınır Belirteç Verenin (STS) birer belirtmediğinde. Varsayılan değer "10675199.02:48:05.4775807."|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<localIssuer >](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|Belirteç ve bağlama bitiş noktası ile iletişim kurmak için kullanılan yerel verenin adresini belirtir.|  
|[\<issuerChannelBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|Yerel yayımlayan kurulurken kullanmak için uç nokta davranışları belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Bir hizmet için bir istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Verilen bir belirteç, örneğin, ile bir güvenli belirteç hizmeti (STS) Federasyon senaryosunda doğrulanırken kullanılan bir özel kimlik bilgileri türüdür. Varsayılan olarak, bir SAML belirtecine bir belirteçtir. Daha fazla bilgi için bkz: [Federasyon ve verilen belirteçleri](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md). ve [Federasyon ve verilen belirteçleri](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Bu bölümde yerel yayımlayan belirteçleri veya güvenlik belirteci hizmeti ile kullanılan davranışlar yapılandırmak için kullanılan öğeleri içerir. Yerel yayımlayan kullanmak bir istemci yapılandırma yönergeleri için bkz: [nasıl yapılır: yerel yayımlayan yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
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
 [Nasıl yapılır: Federe İstemci Oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Nasıl yapılır: Yerel Yayımlayan Yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [Federasyon ve Verilen Belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
