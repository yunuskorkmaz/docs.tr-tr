---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 5202e162a7eb5fc4e36d6a6c0a2c18af48872a69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791605"
---
# <a name="nameclaimtype"></a>\<nameClaimType >
Talep türünü belirleyen ayarlar <xref:System.Security.Principal.IIdentity.Name%2A> özelliği. Aramak için kullanılan talep türünü bir <xref:System.Security.Claims.Claim> koleksiyonunun <xref:System.Security.Claims.ClaimsIdentity> tarafından döndürülen nesne <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> Bu belirteci işleyicisi yöntemi. Eşleşen talep değerinin sonra adı olarak ayarlanması <xref:System.Security.Principal.IIdentity> Bu belirteci işleyicisi oluşturulur.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<Ekle >  
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
|value|Talep için talep türünü temsil eden URI belirten bir dize <xref:System.Security.Principal.IIdentity.Name%2A> özelliği. Gerekli.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı veya türetilmiş bir sınıf ya da bu sınıflarının biri.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<nameClaimType>` Öğe kümeleri <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> özelliği, bir <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesne yapılandırmadan başlatılır.  
  
## <a name="example"></a>Örnek  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
