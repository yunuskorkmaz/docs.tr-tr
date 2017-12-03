---
title: '&lt;allowedAudienceUris&gt; &lt;eklemesi&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5fbf38e3b8430811b9e26b1580f781da9049d036
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltallowedaudienceurisgt"></a>&lt;allowedAudienceUris&gt; &lt;eklemesi&gt;
Hedef URI ekler, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için geçerli olarak kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<serviceBehaviors >  
\<davranışı >  
\<serviceCredentials >  
\<issuedTokenAuthentication >  
\<allowedAudienceUris >  
\<Ekle > öğesi için \<allowedAudienceUris >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<allowedAudienceUris>   
   <add allowedAudienceUri="String"/>  
</allowedAudienceUris>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|allowedAudienceUri|Hedef URI içeren bir dize olan <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için geçerli olarak kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<allowedAudienceUris >](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)|Koleksiyonunu temsil eder hedef URI, <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteci hedef olarak kullanılabilir için geçerli olarak kabul edilmesi için bir <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> örneği.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu koleksiyon veren bir güvenlik belirteci hizmeti (STS) kullanan bir federasyon uygulaması kullanması gereken <xref:System.IdentityModel.Tokens.SamlSecurityToken> güvenlik belirteçleri. Güvenlik belirteci STS gönderdiğinde, kendisi için güvenlik belirteci amaçlanmıştır ekleyerek Web Hizmetleri URI'sini belirtebilirsiniz bir <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> için güvenlik belirteci. İzin veren <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> verilen güvenlik belirteci bu Web hizmeti için bu onay aşağıdakileri yaparak olacağını belirterek hedeflenen doğrulamak alıcı Web hizmeti için:  
  
-   Ayarlama `audienceUriMode` özniteliği `<issuedTokenAuthentication>` için <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> veya <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.  
  
-   Bu koleksiyona URI'ler ekleyerek geçerli URI'ler kümesini belirtin.  
  
 Daha fazla bilgi için bkz. <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Federasyon Hizmeti kimlik bilgileri yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>  
 [\<allowedAudienceUris >](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)  
 [\<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [Güvenlik davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Nasıl yapılır: federe bir hizmette kimlik bilgilerini yapılandırın](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
