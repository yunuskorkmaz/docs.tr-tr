---
title: '&lt;userNameSecurityTokenHandlerRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 4ffe9764eb730be4859fb66ae2f0cc845c9404e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltusernamesecuritytokenhandlerrequirementgt"></a><span data-ttu-id="75f34-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="75f34-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="75f34-103">İçin yapılandırma sağlar <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> sınıf veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="75f34-103">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="75f34-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="75f34-104">\<system.identityModel></span></span>  
<span data-ttu-id="75f34-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="75f34-105">\<identityConfiguration></span></span>  
<span data-ttu-id="75f34-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="75f34-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="75f34-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="75f34-107">\<add></span></span>  
<span data-ttu-id="75f34-108">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="75f34-108">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75f34-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75f34-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75f34-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="75f34-110">Attributes and Elements</span></span>  
 <span data-ttu-id="75f34-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="75f34-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75f34-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="75f34-112">Attributes</span></span>  
  
|<span data-ttu-id="75f34-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="75f34-113">Attribute</span></span>|<span data-ttu-id="75f34-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75f34-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75f34-115">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="75f34-115">membershipProviderName</span></span>|<span data-ttu-id="75f34-116">Belirtir <xref:System.Web.Security.MembershipProvider> güvenlik belirteci işleyici tarafından kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="75f34-116">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75f34-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="75f34-117">Child Elements</span></span>  
 <span data-ttu-id="75f34-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="75f34-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75f34-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="75f34-119">Parent Elements</span></span>  
  
|<span data-ttu-id="75f34-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="75f34-120">Element</span></span>|<span data-ttu-id="75f34-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75f34-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75f34-122">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="75f34-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="75f34-123">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="75f34-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75f34-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75f34-124">Remarks</span></span>  
 <span data-ttu-id="75f34-125">`<userNameSecurityTokenHandlerRequirement>` Öğesi kümeleri <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> özelliği, bir <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> nesne yapılandırmasından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="75f34-125">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75f34-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="75f34-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
