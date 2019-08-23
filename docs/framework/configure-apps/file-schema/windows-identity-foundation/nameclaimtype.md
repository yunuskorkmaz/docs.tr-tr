---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 47366c5bb2bd9228268fce3ae6e1fb5ad457dab1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942616"
---
# <a name="nameclaimtype"></a>\<nameClaimType >
<xref:System.Security.Principal.IIdentity.Name%2A> Özelliği belirten talep türünü ayarlar. Talep türü, bu belirteç işleyicisinin <xref:System.Security.Claims.Claim> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodu tarafından döndürülen <xref:System.Security.Claims.ClaimsIdentity> nesneler koleksiyonunda bir aramak için kullanılır. Daha sonra, eşleşen talebin değeri bu belirteç işleyiciden <xref:System.Security.Principal.IIdentity> oluşturulan adı olarak ayarlanır.  
  
 \<system.identityModel>  
\<IdentityConfiguration >  
\<securityTokenHandlers >  
\<> Ekle  
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
|value|<xref:System.Security.Principal.IIdentity.Name%2A> Özelliği için kullanılacak talebin talep türünü temsil eden URI 'yi belirten bir dize. Gerekli.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement >](samlsecuritytokenrequirement.md)|<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Sınıf<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , sınıf veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> Bir `<nameClaimType>` nesne<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> yapılandırmadan başlatıldığında öğesi özelliği ayarlar.  
  
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
