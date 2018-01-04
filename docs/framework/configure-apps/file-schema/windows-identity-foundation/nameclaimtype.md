---
title: '&lt;nameClaimType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2c53886458b4c6e2867e1f9fddd4ab50b199c660
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltnameclaimtypegt"></a>&lt;nameClaimType&gt;
Belirtir talep türünü ayarlar <xref:System.Security.Principal.IIdentity.Name%2A> özelliği. Talep türü aramak için kullanılan bir <xref:System.Security.Claims.Claim> koleksiyonunda <xref:System.Security.Claims.ClaimsIdentity> tarafından döndürülen nesne <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> Bu belirteci işleyicisi yöntemi. Eşleşen talep değerinin sonra adı olarak ayarlandığını <xref:System.Security.Principal.IIdentity> Bu belirteci işleyiciden oluşturulur.  
  
 \<System.IdentityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<ekleme >  
\<samlSecurityTokenRequirement >  
\<nameClaimType >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <nameClaimType value=xs:string>  
          </nameClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|value|Kullanılacak talep talep türünü temsil eden URI belirten bir dize <xref:System.Security.Principal.IIdentity.Name%2A> özelliği. Gerekli.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı ya da bu sınıfların ya da, türetilmiş bir sınıf.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<nameClaimType>` Öğesi kümeleri <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> özelliği, bir <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesne yapılandırmasından başlatıldı.  
  
## <a name="example"></a>Örnek  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
