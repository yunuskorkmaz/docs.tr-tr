---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 0f651377346b1f14a4226128cd5cf7059543adca
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251907"
---
# <a name="roleclaimtype"></a><span data-ttu-id="2812f-101">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="2812f-101">\<roleClaimType></span></span>
<span data-ttu-id="2812f-102">Belirteç işleyicisinin <xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodu tarafından döndürülen nesneler koleksiyonundaki rol türü taleplerini tanımlayan talep türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="2812f-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
<span data-ttu-id="2812f-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2812f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2812f-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="2812f-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="2812f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="2812f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="2812f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="2812f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="2812f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> Ekle**](add.md)</span><span class="sxs-lookup"><span data-stu-id="2812f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="2812f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<samlSecurityTokenRequirement >** ](samlsecuritytokenrequirement.md)</span><span class="sxs-lookup"><span data-stu-id="2812f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)</span></span>\
<span data-ttu-id="2812f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<roleClaimType >**</span><span class="sxs-lookup"><span data-stu-id="2812f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<roleClaimType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2812f-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2812f-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2812f-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2812f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2812f-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2812f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2812f-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2812f-113">Attributes</span></span>  
  
|<span data-ttu-id="2812f-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2812f-114">Attribute</span></span>|<span data-ttu-id="2812f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2812f-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2812f-116">value</span><span class="sxs-lookup"><span data-stu-id="2812f-116">value</span></span>|<span data-ttu-id="2812f-117">Rol talep türü için kullanılacak talebin talep türünü temsil eden URI 'yi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2812f-117">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2812f-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2812f-118">Child Elements</span></span>  
 <span data-ttu-id="2812f-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="2812f-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2812f-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2812f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2812f-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="2812f-121">Element</span></span>|<span data-ttu-id="2812f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2812f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2812f-123">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="2812f-123">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="2812f-124"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Sınıf<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , sınıf veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="2812f-124">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2812f-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2812f-125">Remarks</span></span>  
 <span data-ttu-id="2812f-126"><xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> Bir `<roleClaimType>` nesne<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> yapılandırmadan başlatıldığında öğesi özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2812f-126">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2812f-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="2812f-127">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2812f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2812f-128">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
