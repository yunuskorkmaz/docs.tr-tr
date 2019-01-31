---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: 18769794da8528f085c567264827db5aa6b214f1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271895"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="5bde6-101">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="5bde6-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="5bde6-102">İçin yapılandırma sağlar <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> sınıfı veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="5bde6-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="5bde6-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="5bde6-103">\<system.identityModel></span></span>  
<span data-ttu-id="5bde6-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5bde6-104">\<identityConfiguration></span></span>  
<span data-ttu-id="5bde6-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="5bde6-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="5bde6-106">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="5bde6-106">\<add></span></span>  
<span data-ttu-id="5bde6-107">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="5bde6-107">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bde6-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5bde6-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bde6-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bde6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5bde6-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5bde6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bde6-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5bde6-111">Attributes</span></span>  
  
|<span data-ttu-id="5bde6-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5bde6-112">Attribute</span></span>|<span data-ttu-id="5bde6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5bde6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5bde6-114">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="5bde6-114">membershipProviderName</span></span>|<span data-ttu-id="5bde6-115">Belirtir <xref:System.Web.Security.MembershipProvider> güvenlik belirteci işleyici tarafından kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5bde6-115">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5bde6-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bde6-116">Child Elements</span></span>  
 <span data-ttu-id="5bde6-117">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="5bde6-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5bde6-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bde6-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5bde6-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="5bde6-119">Element</span></span>|<span data-ttu-id="5bde6-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5bde6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bde6-121">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="5bde6-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="5bde6-122">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="5bde6-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bde6-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5bde6-123">Remarks</span></span>  
 <span data-ttu-id="5bde6-124">`<userNameSecurityTokenHandlerRequirement>` Öğe kümeleri <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> özelliği, bir <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> nesne yapılandırmadan başlatılır.</span><span class="sxs-lookup"><span data-stu-id="5bde6-124">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bde6-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="5bde6-125">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
