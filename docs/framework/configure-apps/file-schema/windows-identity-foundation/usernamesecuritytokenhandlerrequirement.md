---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: 18769794da8528f085c567264827db5aa6b214f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790461"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="3fa09-101">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="3fa09-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="3fa09-102">İçin yapılandırma sağlar <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> sınıfı veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="3fa09-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="3fa09-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="3fa09-103">\<system.identityModel></span></span>  
<span data-ttu-id="3fa09-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3fa09-104">\<identityConfiguration></span></span>  
<span data-ttu-id="3fa09-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="3fa09-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="3fa09-106">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="3fa09-106">\<add></span></span>  
<span data-ttu-id="3fa09-107">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="3fa09-107">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fa09-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3fa09-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3fa09-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3fa09-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3fa09-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3fa09-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3fa09-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3fa09-111">Attributes</span></span>  
  
|<span data-ttu-id="3fa09-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3fa09-112">Attribute</span></span>|<span data-ttu-id="3fa09-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fa09-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3fa09-114">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="3fa09-114">membershipProviderName</span></span>|<span data-ttu-id="3fa09-115">Belirtir <xref:System.Web.Security.MembershipProvider> güvenlik belirteci işleyici tarafından kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3fa09-115">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3fa09-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3fa09-116">Child Elements</span></span>  
 <span data-ttu-id="3fa09-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="3fa09-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3fa09-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3fa09-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3fa09-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="3fa09-119">Element</span></span>|<span data-ttu-id="3fa09-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fa09-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3fa09-121">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="3fa09-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="3fa09-122">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="3fa09-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fa09-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3fa09-123">Remarks</span></span>  
 <span data-ttu-id="3fa09-124">`<userNameSecurityTokenHandlerRequirement>` Öğe kümeleri <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> özelliği, bir <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> nesne yapılandırmadan başlatılır.</span><span class="sxs-lookup"><span data-stu-id="3fa09-124">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fa09-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="3fa09-125">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
