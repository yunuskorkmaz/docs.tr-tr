---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: fed8964e03b80e365fdc5eafd45b4fc372a6e352
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944260"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="0ed1d-101">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="0ed1d-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="0ed1d-102"><xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> Sınıf veya türetilmiş sınıflar için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ed1d-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="0ed1d-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="0ed1d-103">\<system.identityModel></span></span>  
<span data-ttu-id="0ed1d-104">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="0ed1d-104">\<identityConfiguration></span></span>  
<span data-ttu-id="0ed1d-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="0ed1d-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="0ed1d-106">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="0ed1d-106">\<add></span></span>  
<span data-ttu-id="0ed1d-107">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="0ed1d-107">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ed1d-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ed1d-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ed1d-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ed1d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0ed1d-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0ed1d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ed1d-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0ed1d-111">Attributes</span></span>  
  
|<span data-ttu-id="0ed1d-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0ed1d-112">Attribute</span></span>|<span data-ttu-id="0ed1d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ed1d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0ed1d-114">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="0ed1d-114">membershipProviderName</span></span>|<span data-ttu-id="0ed1d-115"><xref:System.Web.Security.MembershipProvider> Güvenlik belirteci işleyicisi tarafından kullanılması gereken öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ed1d-115">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ed1d-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ed1d-116">Child Elements</span></span>  
 <span data-ttu-id="0ed1d-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="0ed1d-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ed1d-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ed1d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0ed1d-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="0ed1d-119">Element</span></span>|<span data-ttu-id="0ed1d-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ed1d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ed1d-121">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="0ed1d-121">\<add></span></span>](add.md)|<span data-ttu-id="0ed1d-122">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="0ed1d-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ed1d-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ed1d-123">Remarks</span></span>  
 <span data-ttu-id="0ed1d-124"><xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> Bir `<userNameSecurityTokenHandlerRequirement>` nesne<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> yapılandırmadan başlatıldığında öğesi özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0ed1d-124">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ed1d-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ed1d-125">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
