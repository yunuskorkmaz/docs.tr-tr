---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 36d727f97597df816779da1c1f7ed5da1a1697f2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164941"
---
# \<roleClaimType>

<span data-ttu-id="46be0-101"><xref:System.Security.Claims.ClaimsIdentity>Belirteç işleyicisinin metodu tarafından döndürülen nesneler koleksiyonundaki rol türü taleplerini tanımlayan talep türünü belirtir <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> .</span><span class="sxs-lookup"><span data-stu-id="46be0-101">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<roleClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="46be0-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="46be0-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <roleClaimType value=xs:string>  
          </roleClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46be0-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="46be0-103">Attributes and Elements</span></span>  

 <span data-ttu-id="46be0-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="46be0-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46be0-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="46be0-105">Attributes</span></span>  
  
|<span data-ttu-id="46be0-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="46be0-106">Attribute</span></span>|<span data-ttu-id="46be0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46be0-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46be0-108">değer</span><span class="sxs-lookup"><span data-stu-id="46be0-108">value</span></span>|<span data-ttu-id="46be0-109">Rol talep türü için kullanılacak talebin talep türünü temsil eden URI 'yi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="46be0-109">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46be0-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="46be0-110">Child Elements</span></span>  

 <span data-ttu-id="46be0-111">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="46be0-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46be0-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="46be0-112">Parent Elements</span></span>  
  
|<span data-ttu-id="46be0-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="46be0-113">Element</span></span>|<span data-ttu-id="46be0-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46be0-114">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="46be0-115"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>Sınıf, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıf veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="46be0-115">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46be0-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46be0-116">Remarks</span></span>  

 <span data-ttu-id="46be0-117">`<roleClaimType>` <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> Bir nesne yapılandırmadan başlatıldığında öğesi özelliği ayarlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> .</span><span class="sxs-lookup"><span data-stu-id="46be0-117">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46be0-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="46be0-118">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="46be0-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46be0-119">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
