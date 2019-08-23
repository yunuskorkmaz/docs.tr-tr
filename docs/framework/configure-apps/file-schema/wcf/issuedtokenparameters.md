---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 07fc2c4c52c29de1cfc9f498a6dc6b6da887b502
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925340"
---
# <a name="issuedtokenparameters"></a>\<IssuedTokenParameters >
Federasyon güvenlik senaryosunda verilen bir güvenlik belirteci için parametreleri belirtir.  
  
 \<system.serviceModel>  
\<bağlama >  
\<customBinding >  
\<bağlama >  
\<Güvenlik >  
\<IssuedTokenParameters >  
  
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
|defaultMessageSecurityVersion|Bağlama tarafından desteklenmesi gereken güvenlik belirtimleri sürümlerini (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) belirtir. Bu değer türünde <xref:System.ServiceModel.MessageSecurityVersion>.|  
|Yani ıonmode|Belirteç ekleme gereksinimlerini belirtir. Bu öznitelik türü <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.|  
|keySize|Belirteç anahtar boyutunu belirten bir tamsayı. Varsayılan değer 256 ' dir.|  
|Anahtar|Anahtar türünü belirten geçerli <xref:System.IdentityModel.Tokens.SecurityKeyType> bir değeri. Varsayılan, `SymmetricKey` değeridir.|  
|Belirteç|Belirteç türünü belirten bir dize. Varsayılan değer "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<additionalRequestParameters >](additionalrequestparameters-element.md)|Ek istek parametrelerini belirten yapılandırma öğeleri koleksiyonu.|  
|[\<claimTypeRequirements >](claimtyperequirements-element.md)|Gerekli talep türlerinin koleksiyonunu belirtir.<br /><br /> Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır. Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır. Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.|  
|[\<veren >](issuer-of-issuedtokenparameters.md)|Geçerli belirteci veren bitiş noktasını belirten bir yapılandırma öğesi.|  
|[\<IssuerMetadata >](issuermetadata-of-issuedtokenparameters.md)|Belirteç verenin meta verilerinin uç nokta adresini belirten bir yapılandırma öğesi.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Securebir Bootstrap >](secureconversationbootstrap.md)|Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.|  
|[\<Güvenlik >](security-of-custombinding.md)|Özel bağlama için güvenlik seçeneklerini belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
- [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Özel Bağlama Güvenliği](../../../wcf/samples/custom-binding-security.md)
- [Kimlik Doğrulama ile Hizmet Kimliği](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Federasyon ve Verilen Belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Özel Bağlamalarla Güvenlik Özellikleri](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Federasyon ve Verilen Belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md)
