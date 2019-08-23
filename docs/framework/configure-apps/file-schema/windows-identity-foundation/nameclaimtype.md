---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 47366c5bb2bd9228268fce3ae6e1fb5ad457dab1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942616"
---
# <a name="nameclaimtype"></a><span data-ttu-id="6c564-101">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="6c564-101">\<nameClaimType></span></span>
<span data-ttu-id="6c564-102"><xref:System.Security.Principal.IIdentity.Name%2A> Özelliği belirten talep türünü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6c564-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="6c564-103">Talep türü, bu belirteç işleyicisinin <xref:System.Security.Claims.Claim> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodu tarafından döndürülen <xref:System.Security.Claims.ClaimsIdentity> nesneler koleksiyonunda bir aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c564-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="6c564-104">Daha sonra, eşleşen talebin değeri bu belirteç işleyiciden <xref:System.Security.Principal.IIdentity> oluşturulan adı olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="6c564-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="6c564-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="6c564-105">\<system.identityModel></span></span>  
<span data-ttu-id="6c564-106">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6c564-106">\<identityConfiguration></span></span>  
<span data-ttu-id="6c564-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="6c564-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="6c564-108">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="6c564-108">\<add></span></span>  
<span data-ttu-id="6c564-109">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="6c564-109">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="6c564-110">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="6c564-110">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c564-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c564-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c564-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c564-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6c564-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c564-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c564-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c564-114">Attributes</span></span>  
  
|<span data-ttu-id="6c564-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6c564-115">Attribute</span></span>|<span data-ttu-id="6c564-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c564-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c564-117">value</span><span class="sxs-lookup"><span data-stu-id="6c564-117">value</span></span>|<span data-ttu-id="6c564-118"><xref:System.Security.Principal.IIdentity.Name%2A> Özelliği için kullanılacak talebin talep türünü temsil eden URI 'yi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="6c564-118">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="6c564-119">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="6c564-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c564-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c564-120">Child Elements</span></span>  
 <span data-ttu-id="6c564-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="6c564-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c564-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c564-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6c564-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c564-123">Element</span></span>|<span data-ttu-id="6c564-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c564-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c564-125">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="6c564-125">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="6c564-126"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Sınıf<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , sınıf veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c564-126">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c564-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c564-127">Remarks</span></span>  
 <span data-ttu-id="6c564-128"><xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> Bir `<nameClaimType>` nesne<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> yapılandırmadan başlatıldığında öğesi özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6c564-128">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c564-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c564-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c564-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c564-130">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
