---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: 18769794da8528f085c567264827db5aa6b214f1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271895"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a>\<userNameSecurityTokenHandlerRequirement >
İçin yapılandırma sağlar <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> sınıfı veya türetilmiş sınıflar.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<Ekle >  
\<userNameSecurityTokenHandlerRequirement >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
        <userNameSecurityTokenHandlerRequirement membershipProviderName=xs:string >  
        </userNameSecurityTokenHandlerRequirement>  
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
|membershipProviderName|Belirtir <xref:System.Web.Security.MembershipProvider> güvenlik belirteci işleyici tarafından kullanılmalıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyona ekler.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<userNameSecurityTokenHandlerRequirement>` Öğe kümeleri <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> özelliği, bir <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> nesne yapılandırmadan başlatılır.  
  
## <a name="example"></a>Örnek  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
