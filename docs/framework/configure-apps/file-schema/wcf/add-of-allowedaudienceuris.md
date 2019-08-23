---
title: <add> / <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: 64f0dd5c97ddfcd2fffd8ff4820d02af8c1ced54
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926888"
---
# <a name="add-of-allowedaudienceuris"></a>\<\<AllowedAudienceUris > ekleyin >
<xref:System.IdentityModel.Tokens.SamlSecurityToken> Bir<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği bir hedef URI ekler.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranış >  
\<serviceCredentials>  
\<IssuedTokenAuthentication >  
\<allowedAudienceUris >  
\<AllowedAudienceUris için \<> öğesi ekleyin >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|allowedAudienceUri|<xref:System.IdentityModel.Tokens.SamlSecurityToken> Bir<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği bir hedef URI içeren dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<allowedAudienceUris >](allowedaudienceuris.md)|<xref:System.IdentityModel.Tokens.SamlSecurityToken> Bir<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örnek tarafından geçerli kabul edilebilmesi için güvenlik belirtecinin hedeflenebileceği hedef URI 'lerin bir koleksiyonunu temsil eder.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu koleksiyonu, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteçleri veren bir güvenlik belirteci hizmeti (STS) kullanan bir Federasyon uygulamasında kullanmanız gerekir. STS güvenlik belirtecini aldığında güvenlik belirtecinin bir <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> güvenlik belirtecine ekleyerek amaçlanan Web hizmetlerinin URI 'sini belirtebilir. Bu, alıcı <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> Web hizmeti için, aşağıdaki işlemleri yaparak bu denetimi gerçekleşmelidir belirterek, verilen güvenlik belirtecinin bu Web hizmetine yönelik olduğunu doğrulamasına izin verir:  
  
- `audienceUriMode` Özniteliğini veya olarak<xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>ayarlayın. <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> `<issuedTokenAuthentication>`  
  
- URI 'Leri bu koleksiyona ekleyerek geçerli URI 'Ler kümesini belirtin.  
  
 Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Federasyon Hizmeti](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)kimlik bilgilerini yapılandırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [\<allowedAudienceUris >](allowedaudienceuris.md)
- [\<IssuedTokenAuthentication >](issuedtokenauthentication-of-servicecredentials.md)
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Nasıl yapılır: Federasyon Hizmeti kimlik bilgilerini yapılandırma](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
