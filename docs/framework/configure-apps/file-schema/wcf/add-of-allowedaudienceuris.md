---
title: <add> , <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: 5538db902525b03513a69fcc1a5c06d0877b8e0e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281157"
---
# <a name="add-of-allowedaudienceuris"></a>\<Ekle >, \<allowedAudienceUris >
Bir hedef URI ekler, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için tarafından geçerli kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
\<serviceCredentials>  
\<ServiceCredentials >  
\<allowedAudienceUris >  
\<Ekle > öğesi için \<allowedAudienceUris >  
  
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
|allowedAudienceUri|Bir hedef URI içeren bir dize olan <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için tarafından geçerli kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<allowedAudienceUris >](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)|Koleksiyonunu temsil eder hedef URI, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için tarafından geçerli kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu koleksiyon veren bir güvenlik belirteci hizmeti (STS) kullanan bir Federasyon uygulamasında kullanması gereken <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteçleri. Güvenlik belirteci STS verdiğinde, kendisi için güvenlik belirteci amaçlanmıştır ekleyerek Web Hizmetleri URI'sini belirtebilirsiniz bir <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> için güvenlik belirteci. Veren <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> alıcı Web hizmetinin aşağıdakileri yaparak bu denetimi olacağını belirleyerek verilen güvenlik belirteci için bu Web hizmetini kullandığınızdan emin olun:  
  
-   Ayarlama `audienceUriMode` özniteliği `<issuedTokenAuthentication>` için <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> veya <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.  
  
-   Bu koleksiyona bir URI'leri ekleyerek geçerli URI'lerin kümesini belirtin.  
  
 Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [\<allowedAudienceUris >](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)
- [\<ServiceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Nasıl yapılır: Federe bir hizmette kimlik bilgilerini yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
