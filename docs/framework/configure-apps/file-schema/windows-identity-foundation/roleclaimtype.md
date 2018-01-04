---
title: '&lt;roleClaimType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: eb46585561ca8a2ab7c69f09d073d38bc1b60646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltroleclaimtypegt"></a><span data-ttu-id="4c046-102">&lt;roleClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="4c046-102">&lt;roleClaimType&gt;</span></span>
<span data-ttu-id="4c046-103">Rol türü talepleri koleksiyonundaki tanımlar talep türünü belirten <xref:System.Security.Claims.ClaimsIdentity> tarafından döndürülen nesne <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> belirteci işleyicisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4c046-103">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="4c046-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="4c046-104">\<system.identityModel></span></span>  
<span data-ttu-id="4c046-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4c046-105">\<identityConfiguration></span></span>  
<span data-ttu-id="4c046-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="4c046-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="4c046-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="4c046-107">\<add></span></span>  
<span data-ttu-id="4c046-108">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="4c046-108">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="4c046-109">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="4c046-109">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c046-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c046-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c046-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c046-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4c046-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c046-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c046-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4c046-113">Attributes</span></span>  
  
|<span data-ttu-id="4c046-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4c046-114">Attribute</span></span>|<span data-ttu-id="4c046-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c046-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4c046-116">value</span><span class="sxs-lookup"><span data-stu-id="4c046-116">value</span></span>|<span data-ttu-id="4c046-117">Talep türü rol talep türü için kullanılacak bir talep gösteren URI belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4c046-117">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c046-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c046-118">Child Elements</span></span>  
 <span data-ttu-id="4c046-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="4c046-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c046-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c046-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4c046-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="4c046-121">Element</span></span>|<span data-ttu-id="4c046-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c046-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4c046-123">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="4c046-123">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="4c046-124">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı ya da bu sınıfların ya da, türetilmiş bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="4c046-124">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c046-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c046-125">Remarks</span></span>  
 <span data-ttu-id="4c046-126">`<roleClaimType>` Öğesi kümeleri <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> özelliği, bir <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesne yapılandırmasından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="4c046-126">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c046-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="4c046-127">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c046-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4c046-128">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
