---
title: '&lt;userNameSecurityTokenHandlerRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: dfcaad8b150321fda2a86e601bf57204cbdc1a0e
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123390"
---
# <a name="ltusernamesecuritytokenhandlerrequirementgt"></a><span data-ttu-id="2107d-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="2107d-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="2107d-103">İçin yapılandırma sağlar <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> sınıfı veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="2107d-103">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="2107d-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="2107d-104">\<system.identityModel></span></span>  
<span data-ttu-id="2107d-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="2107d-105">\<identityConfiguration></span></span>  
<span data-ttu-id="2107d-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="2107d-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="2107d-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="2107d-107">\<add></span></span>  
<span data-ttu-id="2107d-108">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="2107d-108">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2107d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2107d-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
        <userNameSecurityTokenHandlerRequirement membershipProviderName=xs:string >  
        </userNameSecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2107d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2107d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2107d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2107d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2107d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2107d-112">Attributes</span></span>  
  
|<span data-ttu-id="2107d-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2107d-113">Attribute</span></span>|<span data-ttu-id="2107d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2107d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2107d-115">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="2107d-115">membershipProviderName</span></span>|<span data-ttu-id="2107d-116">Belirtir <xref:System.Web.Security.MembershipProvider> güvenlik belirteci işleyici tarafından kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2107d-116">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2107d-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2107d-117">Child Elements</span></span>  
 <span data-ttu-id="2107d-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="2107d-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2107d-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2107d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2107d-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="2107d-120">Element</span></span>|<span data-ttu-id="2107d-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2107d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2107d-122">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="2107d-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="2107d-123">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="2107d-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2107d-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2107d-124">Remarks</span></span>  
 <span data-ttu-id="2107d-125">`<userNameSecurityTokenHandlerRequirement>` Öğe kümeleri <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> özelliği, bir <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> nesne yapılandırmadan başlatılır.</span><span class="sxs-lookup"><span data-stu-id="2107d-125">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2107d-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="2107d-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
