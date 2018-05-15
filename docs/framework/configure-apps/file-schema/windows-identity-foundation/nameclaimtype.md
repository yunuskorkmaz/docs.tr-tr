---
title: '&lt;nameClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e403667f16e316004f766b8476e20eca9bd1c988
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltnameclaimtypegt"></a><span data-ttu-id="6d8cf-102">&lt;nameClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="6d8cf-102">&lt;nameClaimType&gt;</span></span>
<span data-ttu-id="6d8cf-103">Belirtir talep türünü ayarlar <xref:System.Security.Principal.IIdentity.Name%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="6d8cf-103">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="6d8cf-104">Talep türü aramak için kullanılan bir <xref:System.Security.Claims.Claim> koleksiyonunda <xref:System.Security.Claims.ClaimsIdentity> tarafından döndürülen nesne <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> Bu belirteci işleyicisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6d8cf-104">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="6d8cf-105">Eşleşen talep değerinin sonra adı olarak ayarlandığını <xref:System.Security.Principal.IIdentity> Bu belirteci işleyiciden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6d8cf-105">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="6d8cf-106">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="6d8cf-106">\<system.identityModel></span></span>  
<span data-ttu-id="6d8cf-107">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6d8cf-107">\<identityConfiguration></span></span>  
<span data-ttu-id="6d8cf-108">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="6d8cf-108">\<securityTokenHandlers></span></span>  
<span data-ttu-id="6d8cf-109">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="6d8cf-109">\<add></span></span>  
<span data-ttu-id="6d8cf-110">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="6d8cf-110">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="6d8cf-111">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="6d8cf-111">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d8cf-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d8cf-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d8cf-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6d8cf-113">Attributes and Elements</span></span>  
 <span data-ttu-id="6d8cf-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6d8cf-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d8cf-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6d8cf-115">Attributes</span></span>  
  
|<span data-ttu-id="6d8cf-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6d8cf-116">Attribute</span></span>|<span data-ttu-id="6d8cf-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d8cf-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6d8cf-118">value</span><span class="sxs-lookup"><span data-stu-id="6d8cf-118">value</span></span>|<span data-ttu-id="6d8cf-119">Kullanılacak talep talep türünü temsil eden URI belirten bir dize <xref:System.Security.Principal.IIdentity.Name%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="6d8cf-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="6d8cf-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="6d8cf-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d8cf-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6d8cf-121">Child Elements</span></span>  
 <span data-ttu-id="6d8cf-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="6d8cf-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d8cf-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6d8cf-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6d8cf-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="6d8cf-124">Element</span></span>|<span data-ttu-id="6d8cf-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d8cf-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d8cf-126">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="6d8cf-126">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="6d8cf-127">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı ya da bu sınıfların ya da, türetilmiş bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="6d8cf-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d8cf-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d8cf-128">Remarks</span></span>  
 <span data-ttu-id="6d8cf-129">`<nameClaimType>` Öğesi kümeleri <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> özelliği, bir <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesne yapılandırmasından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="6d8cf-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d8cf-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d8cf-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d8cf-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6d8cf-131">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
