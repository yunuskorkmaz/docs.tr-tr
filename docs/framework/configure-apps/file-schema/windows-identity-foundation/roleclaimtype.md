---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 812d44ef947d27b0f73d9dc2172494e89ee56d72
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270881"
---
# <a name="roleclaimtype"></a><span data-ttu-id="15712-101">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="15712-101">\<roleClaimType></span></span>
<span data-ttu-id="15712-102">Rol türü talep koleksiyonunda tanımlayan talep türünü belirtir <xref:System.Security.Claims.ClaimsIdentity> tarafından döndürülen nesne <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> belirteci işleyicisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="15712-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="15712-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="15712-103">\<system.identityModel></span></span>  
<span data-ttu-id="15712-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="15712-104">\<identityConfiguration></span></span>  
<span data-ttu-id="15712-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="15712-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="15712-106">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="15712-106">\<add></span></span>  
<span data-ttu-id="15712-107">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="15712-107">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="15712-108">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="15712-108">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15712-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15712-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15712-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="15712-110">Attributes and Elements</span></span>  
 <span data-ttu-id="15712-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="15712-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15712-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="15712-112">Attributes</span></span>  
  
|<span data-ttu-id="15712-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="15712-113">Attribute</span></span>|<span data-ttu-id="15712-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15712-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="15712-115">value</span><span class="sxs-lookup"><span data-stu-id="15712-115">value</span></span>|<span data-ttu-id="15712-116">Talep türü rol talep türü için kullanılacak talep temsil eden URI belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="15712-116">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15712-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="15712-117">Child Elements</span></span>  
 <span data-ttu-id="15712-118">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="15712-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="15712-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="15712-119">Parent Elements</span></span>  
  
|<span data-ttu-id="15712-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="15712-120">Element</span></span>|<span data-ttu-id="15712-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15712-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15712-122">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="15712-122">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="15712-123">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı veya türetilmiş bir sınıf ya da bu sınıflarının biri.</span><span class="sxs-lookup"><span data-stu-id="15712-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15712-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15712-124">Remarks</span></span>  
 <span data-ttu-id="15712-125">`<roleClaimType>` Öğe kümeleri <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> özelliği, bir <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesne yapılandırmadan başlatılır.</span><span class="sxs-lookup"><span data-stu-id="15712-125">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15712-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="15712-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="15712-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15712-127">See also</span></span>
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
