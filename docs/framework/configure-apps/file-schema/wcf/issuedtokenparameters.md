---
title: '&lt;İssuermetadata&gt;'
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 2060f98e94cec9e656420ac073204a82bc592b92
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149247"
---
# <a name="ltissuedtokenparametersgt"></a>&lt;İssuermetadata&gt;
Bir federe güvenlik senaryosundaki güvenlik belirteci için parametreleri belirtir.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<Güvenlik >  
\<İssuermetadata >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<issuedTokenParameters defaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"
                       inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"
                       keySize="Integer"
                       keyType="AsymmetricKey/BearerKey/SymmetricKey"
                       tokenType="String">
  <additionalRequestParameters />
  <claimTypeRequirements>
    <add claimType="URI"
         isOptional="Boolean" />
  </claimTypeRequirements>
  <issuer address="String"
          binding="" />
  <issuerMetadata address="String" />
</issuedTokenParameters>
```  
  
## <a name="type"></a>Tür  
 `Type`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|defaultMessageSecurityVersion|Güvenlik belirtimleri sürümlerini belirtir (WS-Security, WS-Trust, WS-Secure Conversation ve WS-Security Policy) bağlama tarafından desteklenmelidir. Bu değer türünde <xref:System.ServiceModel.MessageSecurityVersion>.|  
|inclusionMode|Belirteç ekleme gereksinimlerini belirtir. Bu öznitelik türünde <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.|  
|KeySize|Belirteç anahtar boyutunu belirten bir tamsayı. Varsayılan değer 256'dır.|  
|KeyType|Geçerli değerini <xref:System.IdentityModel.Tokens.SecurityKeyType> anahtar türünü belirtir. Varsayılan, `SymmetricKey` değeridir.|  
|TokenType|Belirteç türünü belirten bir dize. Varsayılan değer "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<additionalRequestParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|Ek istek parametrelerini belirten yapılandırma öğelerinin koleksiyonu.|  
|[\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|Gerekli talep türlerinin koleksiyonunu belirtir.<br /><br /> Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin. Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir. Bu koleksiyondaki her öğe bir birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.|  
|[\<veren >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|Geçerli belirtecini veren uç noktasını belirtir bir yapılandırma öğesi.|  
|[\<İssuedtokenparameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|Belirteç Verenin meta veri uç nokta adresini belirten bir yapılandırma öğesi.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<secureConversationBootstrap >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Özel bağlama için güvenlik seçeneklerini belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Özel Bağlama Güvenliği](../../../../../docs/framework/wcf/samples/custom-binding-security.md)  
 [Kimlik Doğrulama ile Hizmet Kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Federasyon ve Verilen Belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Özel Bağlamalarla Güvenlik Özellikleri](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Federasyon ve Verilen Belirteçler](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
