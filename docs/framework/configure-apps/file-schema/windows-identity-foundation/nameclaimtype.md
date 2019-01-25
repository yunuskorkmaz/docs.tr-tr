---
title: '&lt;nameClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 502fc5dd14d7bc3d979153607e1eeeb9354031bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737435"
---
# <a name="ltnameclaimtypegt"></a><span data-ttu-id="76b8f-102">&lt;nameClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="76b8f-102">&lt;nameClaimType&gt;</span></span>
<span data-ttu-id="76b8f-103">Talep türünü belirleyen ayarlar <xref:System.Security.Principal.IIdentity.Name%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="76b8f-103">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="76b8f-104">Aramak için kullanılan talep türünü bir <xref:System.Security.Claims.Claim> koleksiyonunun <xref:System.Security.Claims.ClaimsIdentity> tarafından döndürülen nesne <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> Bu belirteci işleyicisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="76b8f-104">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="76b8f-105">Eşleşen talep değerinin sonra adı olarak ayarlanması <xref:System.Security.Principal.IIdentity> Bu belirteci işleyicisi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="76b8f-105">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="76b8f-106">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="76b8f-106">\<system.identityModel></span></span>  
<span data-ttu-id="76b8f-107">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="76b8f-107">\<identityConfiguration></span></span>  
<span data-ttu-id="76b8f-108">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="76b8f-108">\<securityTokenHandlers></span></span>  
<span data-ttu-id="76b8f-109">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="76b8f-109">\<add></span></span>  
<span data-ttu-id="76b8f-110">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="76b8f-110">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="76b8f-111">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="76b8f-111">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76b8f-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76b8f-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76b8f-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="76b8f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="76b8f-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="76b8f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76b8f-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="76b8f-115">Attributes</span></span>  
  
|<span data-ttu-id="76b8f-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="76b8f-116">Attribute</span></span>|<span data-ttu-id="76b8f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76b8f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76b8f-118">value</span><span class="sxs-lookup"><span data-stu-id="76b8f-118">value</span></span>|<span data-ttu-id="76b8f-119">Talep için talep türünü temsil eden URI belirten bir dize <xref:System.Security.Principal.IIdentity.Name%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="76b8f-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="76b8f-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="76b8f-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76b8f-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="76b8f-121">Child Elements</span></span>  
 <span data-ttu-id="76b8f-122">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="76b8f-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76b8f-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="76b8f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="76b8f-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="76b8f-124">Element</span></span>|<span data-ttu-id="76b8f-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76b8f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76b8f-126">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="76b8f-126">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="76b8f-127">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı veya türetilmiş bir sınıf ya da bu sınıflarının biri.</span><span class="sxs-lookup"><span data-stu-id="76b8f-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76b8f-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76b8f-128">Remarks</span></span>  
 <span data-ttu-id="76b8f-129">`<nameClaimType>` Öğe kümeleri <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> özelliği, bir <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesne yapılandırmadan başlatılır.</span><span class="sxs-lookup"><span data-stu-id="76b8f-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76b8f-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="76b8f-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="76b8f-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76b8f-131">See also</span></span>
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
