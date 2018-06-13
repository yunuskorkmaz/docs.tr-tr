---
title: '&lt;roleClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 909df1bd6054d9737f91c30c3c6b2d68b932281c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755194"
---
# <a name="ltroleclaimtypegt"></a><span data-ttu-id="d3b5f-102">&lt;roleClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="d3b5f-102">&lt;roleClaimType&gt;</span></span>
<span data-ttu-id="d3b5f-103">Rol türü talepleri koleksiyonundaki tanımlar talep türünü belirten <xref:System.Security.Claims.ClaimsIdentity> tarafından döndürülen nesne <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> belirteci işleyicisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-103">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="d3b5f-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d3b5f-104">\<system.identityModel></span></span>  
<span data-ttu-id="d3b5f-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d3b5f-105">\<identityConfiguration></span></span>  
<span data-ttu-id="d3b5f-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="d3b5f-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d3b5f-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="d3b5f-107">\<add></span></span>  
<span data-ttu-id="d3b5f-108">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="d3b5f-108">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="d3b5f-109">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="d3b5f-109">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3b5f-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3b5f-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3b5f-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3b5f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d3b5f-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3b5f-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d3b5f-113">Attributes</span></span>  
  
|<span data-ttu-id="d3b5f-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d3b5f-114">Attribute</span></span>|<span data-ttu-id="d3b5f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3b5f-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3b5f-116">value</span><span class="sxs-lookup"><span data-stu-id="d3b5f-116">value</span></span>|<span data-ttu-id="d3b5f-117">Talep türü rol talep türü için kullanılacak bir talep gösteren URI belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-117">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3b5f-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3b5f-118">Child Elements</span></span>  
 <span data-ttu-id="d3b5f-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3b5f-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3b5f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d3b5f-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="d3b5f-121">Element</span></span>|<span data-ttu-id="d3b5f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3b5f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3b5f-123">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="d3b5f-123">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="d3b5f-124">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı ya da bu sınıfların ya da, türetilmiş bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-124">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3b5f-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3b5f-125">Remarks</span></span>  
 <span data-ttu-id="d3b5f-126">`<roleClaimType>` Öğesi kümeleri <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> özelliği, bir <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesne yapılandırmasından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-126">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3b5f-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3b5f-127">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3b5f-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3b5f-128">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
