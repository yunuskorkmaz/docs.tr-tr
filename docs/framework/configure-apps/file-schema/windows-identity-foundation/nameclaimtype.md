---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 4bf8ad2f70499edfc72dd9fcd9a5d8a0aafbbc66
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251935"
---
# <a name="nameclaimtype"></a><span data-ttu-id="eda12-101">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="eda12-101">\<nameClaimType></span></span>
<span data-ttu-id="eda12-102"><xref:System.Security.Principal.IIdentity.Name%2A> Özelliği belirten talep türünü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="eda12-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="eda12-103">Talep türü, bu belirteç işleyicisinin <xref:System.Security.Claims.Claim> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodu tarafından döndürülen <xref:System.Security.Claims.ClaimsIdentity> nesneler koleksiyonunda bir aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eda12-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="eda12-104">Daha sonra, eşleşen talebin değeri bu belirteç işleyiciden <xref:System.Security.Principal.IIdentity> oluşturulan adı olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="eda12-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
<span data-ttu-id="eda12-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="eda12-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="eda12-106">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="eda12-106">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="eda12-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="eda12-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="eda12-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="eda12-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="eda12-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> Ekle**](add.md)</span><span class="sxs-lookup"><span data-stu-id="eda12-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="eda12-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<samlSecurityTokenRequirement >** ](samlsecuritytokenrequirement.md)</span><span class="sxs-lookup"><span data-stu-id="eda12-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)</span></span>\
<span data-ttu-id="eda12-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<nameClaimType >**</span><span class="sxs-lookup"><span data-stu-id="eda12-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameClaimType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eda12-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eda12-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eda12-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="eda12-113">Attributes and Elements</span></span>  
 <span data-ttu-id="eda12-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eda12-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eda12-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="eda12-115">Attributes</span></span>  
  
|<span data-ttu-id="eda12-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="eda12-116">Attribute</span></span>|<span data-ttu-id="eda12-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eda12-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eda12-118">value</span><span class="sxs-lookup"><span data-stu-id="eda12-118">value</span></span>|<span data-ttu-id="eda12-119"><xref:System.Security.Principal.IIdentity.Name%2A> Özelliği için kullanılacak talebin talep türünü temsil eden URI 'yi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="eda12-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="eda12-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="eda12-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eda12-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="eda12-121">Child Elements</span></span>  
 <span data-ttu-id="eda12-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="eda12-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eda12-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="eda12-123">Parent Elements</span></span>  
  
|<span data-ttu-id="eda12-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="eda12-124">Element</span></span>|<span data-ttu-id="eda12-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eda12-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eda12-126">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="eda12-126">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="eda12-127"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Sınıf<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , sınıf veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="eda12-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eda12-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eda12-128">Remarks</span></span>  
 <span data-ttu-id="eda12-129"><xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> Bir `<nameClaimType>` nesne<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> yapılandırmadan başlatıldığında öğesi özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="eda12-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eda12-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="eda12-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eda12-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eda12-131">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
