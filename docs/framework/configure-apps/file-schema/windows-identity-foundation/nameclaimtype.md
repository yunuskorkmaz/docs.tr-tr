---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 5202e162a7eb5fc4e36d6a6c0a2c18af48872a69
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130331"
---
# <a name="nameclaimtype"></a><span data-ttu-id="2ec99-101">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="2ec99-101">\<nameClaimType></span></span>
<span data-ttu-id="2ec99-102">Talep türünü belirleyen ayarlar <xref:System.Security.Principal.IIdentity.Name%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2ec99-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="2ec99-103">Aramak için kullanılan talep türünü bir <xref:System.Security.Claims.Claim> koleksiyonunun <xref:System.Security.Claims.ClaimsIdentity> tarafından döndürülen nesne <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> Bu belirteci işleyicisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2ec99-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="2ec99-104">Eşleşen talep değerinin sonra adı olarak ayarlanması <xref:System.Security.Principal.IIdentity> Bu belirteci işleyicisi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2ec99-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="2ec99-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="2ec99-105">\<system.identityModel></span></span>  
<span data-ttu-id="2ec99-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="2ec99-106">\<identityConfiguration></span></span>  
<span data-ttu-id="2ec99-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="2ec99-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="2ec99-108">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="2ec99-108">\<add></span></span>  
<span data-ttu-id="2ec99-109">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="2ec99-109">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="2ec99-110">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="2ec99-110">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ec99-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ec99-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ec99-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2ec99-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2ec99-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2ec99-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ec99-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2ec99-114">Attributes</span></span>  
  
|<span data-ttu-id="2ec99-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2ec99-115">Attribute</span></span>|<span data-ttu-id="2ec99-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ec99-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ec99-117">value</span><span class="sxs-lookup"><span data-stu-id="2ec99-117">value</span></span>|<span data-ttu-id="2ec99-118">Talep için talep türünü temsil eden URI belirten bir dize <xref:System.Security.Principal.IIdentity.Name%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2ec99-118">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="2ec99-119">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2ec99-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ec99-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2ec99-120">Child Elements</span></span>  
 <span data-ttu-id="2ec99-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="2ec99-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ec99-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2ec99-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2ec99-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="2ec99-123">Element</span></span>|<span data-ttu-id="2ec99-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ec99-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ec99-125">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="2ec99-125">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="2ec99-126">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı veya türetilmiş bir sınıf ya da bu sınıflarının biri.</span><span class="sxs-lookup"><span data-stu-id="2ec99-126">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ec99-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ec99-127">Remarks</span></span>  
 <span data-ttu-id="2ec99-128">`<nameClaimType>` Öğe kümeleri <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> özelliği, bir <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesne yapılandırmadan başlatılır.</span><span class="sxs-lookup"><span data-stu-id="2ec99-128">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ec99-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ec99-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ec99-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ec99-130">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
