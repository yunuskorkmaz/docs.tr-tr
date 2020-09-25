---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: a49b41c04c8f184188b62e04c3b232bd33752fca
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185528"
---
# \<userNameSecurityTokenHandlerRequirement>

<span data-ttu-id="f46c1-101"><xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>Sınıf veya türetilmiş sınıflar için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="f46c1-101">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameSecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="f46c1-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="f46c1-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f46c1-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f46c1-103">Attributes and Elements</span></span>  

 <span data-ttu-id="f46c1-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f46c1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f46c1-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f46c1-105">Attributes</span></span>  
  
|<span data-ttu-id="f46c1-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f46c1-106">Attribute</span></span>|<span data-ttu-id="f46c1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f46c1-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f46c1-108">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="f46c1-108">membershipProviderName</span></span>|<span data-ttu-id="f46c1-109"><xref:System.Web.Security.MembershipProvider>Güvenlik belirteci işleyicisi tarafından kullanılması gereken öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f46c1-109">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f46c1-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f46c1-110">Child Elements</span></span>  

 <span data-ttu-id="f46c1-111">Yok</span><span class="sxs-lookup"><span data-stu-id="f46c1-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f46c1-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f46c1-112">Parent Elements</span></span>  
  
|<span data-ttu-id="f46c1-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="f46c1-113">Element</span></span>|<span data-ttu-id="f46c1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f46c1-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="f46c1-115">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="f46c1-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f46c1-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f46c1-116">Remarks</span></span>  

 <span data-ttu-id="f46c1-117">`<userNameSecurityTokenHandlerRequirement>` <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> Bir nesne yapılandırmadan başlatıldığında öğesi özelliği ayarlar <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="f46c1-117">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f46c1-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="f46c1-118">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
