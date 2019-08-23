---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 0ce2e06ee895d09de193bac1fe7038e71794dda4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942534"
---
# <a name="roleclaimtype"></a><span data-ttu-id="333dc-101">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="333dc-101">\<roleClaimType></span></span>
<span data-ttu-id="333dc-102">Belirteç işleyicisinin <xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodu tarafından döndürülen nesneler koleksiyonundaki rol türü taleplerini tanımlayan talep türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="333dc-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="333dc-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="333dc-103">\<system.identityModel></span></span>  
<span data-ttu-id="333dc-104">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="333dc-104">\<identityConfiguration></span></span>  
<span data-ttu-id="333dc-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="333dc-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="333dc-106">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="333dc-106">\<add></span></span>  
<span data-ttu-id="333dc-107">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="333dc-107">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="333dc-108">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="333dc-108">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="333dc-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="333dc-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="333dc-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="333dc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="333dc-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="333dc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="333dc-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="333dc-112">Attributes</span></span>  
  
|<span data-ttu-id="333dc-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="333dc-113">Attribute</span></span>|<span data-ttu-id="333dc-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="333dc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="333dc-115">value</span><span class="sxs-lookup"><span data-stu-id="333dc-115">value</span></span>|<span data-ttu-id="333dc-116">Rol talep türü için kullanılacak talebin talep türünü temsil eden URI 'yi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="333dc-116">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="333dc-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="333dc-117">Child Elements</span></span>  
 <span data-ttu-id="333dc-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="333dc-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="333dc-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="333dc-119">Parent Elements</span></span>  
  
|<span data-ttu-id="333dc-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="333dc-120">Element</span></span>|<span data-ttu-id="333dc-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="333dc-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="333dc-122">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="333dc-122">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="333dc-123"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Sınıf<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , sınıf veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="333dc-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="333dc-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="333dc-124">Remarks</span></span>  
 <span data-ttu-id="333dc-125"><xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> Bir `<roleClaimType>` nesne<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> yapılandırmadan başlatıldığında öğesi özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="333dc-125">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="333dc-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="333dc-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="333dc-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="333dc-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
