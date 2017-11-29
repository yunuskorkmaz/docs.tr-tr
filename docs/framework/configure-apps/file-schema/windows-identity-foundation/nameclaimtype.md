---
title: '&lt;nameClaimType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e910333084aae9e47153cfe3ee4b5cd943a37f71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltnameclaimtypegt"></a><span data-ttu-id="c6039-102">&lt;nameClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="c6039-102">&lt;nameClaimType&gt;</span></span>
<span data-ttu-id="c6039-103">Belirtir talep türünü ayarlar <xref:System.Security.Principal.IIdentity.Name%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c6039-103">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="c6039-104">Talep türü aramak için kullanılan bir <xref:System.Security.Claims.Claim> koleksiyonunda <xref:System.Security.Claims.ClaimsIdentity> tarafından döndürülen nesne <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> Bu belirteci işleyicisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c6039-104">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="c6039-105">Eşleşen talep değerinin sonra adı olarak ayarlandığını <xref:System.Security.Principal.IIdentity> Bu belirteci işleyiciden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c6039-105">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="c6039-106">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="c6039-106">\<system.identityModel></span></span>  
<span data-ttu-id="c6039-107">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="c6039-107">\<identityConfiguration></span></span>  
<span data-ttu-id="c6039-108">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="c6039-108">\<securityTokenHandlers></span></span>  
<span data-ttu-id="c6039-109">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="c6039-109">\<add></span></span>  
<span data-ttu-id="c6039-110">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="c6039-110">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="c6039-111">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="c6039-111">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6039-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6039-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6039-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6039-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c6039-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6039-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6039-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c6039-115">Attributes</span></span>  
  
|<span data-ttu-id="c6039-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c6039-116">Attribute</span></span>|<span data-ttu-id="c6039-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6039-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6039-118">value</span><span class="sxs-lookup"><span data-stu-id="c6039-118">value</span></span>|<span data-ttu-id="c6039-119">Kullanılacak talep talep türünü temsil eden URI belirten bir dize <xref:System.Security.Principal.IIdentity.Name%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c6039-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="c6039-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c6039-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6039-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6039-121">Child Elements</span></span>  
 <span data-ttu-id="c6039-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="c6039-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6039-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6039-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c6039-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6039-124">Element</span></span>|<span data-ttu-id="c6039-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6039-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6039-126">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="c6039-126">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="c6039-127">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı ya da bu sınıfların ya da, türetilmiş bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="c6039-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6039-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6039-128">Remarks</span></span>  
 <span data-ttu-id="c6039-129">`<nameClaimType>` Öğesi kümeleri <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> özelliği, bir <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesne yapılandırmasından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="c6039-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6039-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6039-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6039-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6039-131">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
