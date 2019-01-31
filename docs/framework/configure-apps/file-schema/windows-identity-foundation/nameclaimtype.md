---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: aab76949d9c31ac003b8afd519c2ad66529cbf26
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254873"
---
# <a name="nameclaimtype"></a><span data-ttu-id="ca676-101">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="ca676-101">\<nameClaimType></span></span>
<span data-ttu-id="ca676-102">Talep türünü belirleyen ayarlar <xref:System.Security.Principal.IIdentity.Name%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ca676-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="ca676-103">Aramak için kullanılan talep türünü bir <xref:System.Security.Claims.Claim> koleksiyonunun <xref:System.Security.Claims.ClaimsIdentity> tarafından döndürülen nesne <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> Bu belirteci işleyicisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ca676-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="ca676-104">Eşleşen talep değerinin sonra adı olarak ayarlanması <xref:System.Security.Principal.IIdentity> Bu belirteci işleyicisi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ca676-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="ca676-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="ca676-105">\<system.identityModel></span></span>  
<span data-ttu-id="ca676-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ca676-106">\<identityConfiguration></span></span>  
<span data-ttu-id="ca676-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="ca676-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="ca676-108">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="ca676-108">\<add></span></span>  
<span data-ttu-id="ca676-109">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="ca676-109">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="ca676-110">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="ca676-110">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca676-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca676-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca676-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca676-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ca676-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ca676-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca676-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ca676-114">Attributes</span></span>  
  
|<span data-ttu-id="ca676-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ca676-115">Attribute</span></span>|<span data-ttu-id="ca676-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca676-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ca676-117">value</span><span class="sxs-lookup"><span data-stu-id="ca676-117">value</span></span>|<span data-ttu-id="ca676-118">Talep için talep türünü temsil eden URI belirten bir dize <xref:System.Security.Principal.IIdentity.Name%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ca676-118">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="ca676-119">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ca676-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca676-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca676-120">Child Elements</span></span>  
 <span data-ttu-id="ca676-121">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="ca676-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ca676-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca676-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ca676-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="ca676-123">Element</span></span>|<span data-ttu-id="ca676-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca676-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca676-125">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="ca676-125">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="ca676-126">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı veya türetilmiş bir sınıf ya da bu sınıflarının biri.</span><span class="sxs-lookup"><span data-stu-id="ca676-126">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca676-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca676-127">Remarks</span></span>  
 <span data-ttu-id="ca676-128">`<nameClaimType>` Öğe kümeleri <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> özelliği, bir <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> nesne yapılandırmadan başlatılır.</span><span class="sxs-lookup"><span data-stu-id="ca676-128">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca676-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca676-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca676-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca676-130">See also</span></span>
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
