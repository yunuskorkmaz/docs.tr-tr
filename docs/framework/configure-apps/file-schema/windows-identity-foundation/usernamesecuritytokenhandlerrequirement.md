---
description: 'Hakkında daha fazla bilgi edinin: <userNameSecurityTokenHandlerRequirement>'
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: c2bca086d06738699517fe140173f321a3233a4a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786505"
---
# \<userNameSecurityTokenHandlerRequirement>

<span data-ttu-id="b0ffb-102"><xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>Sınıf veya türetilmiş sınıflar için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0ffb-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameSecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="b0ffb-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="b0ffb-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0ffb-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0ffb-104">Attributes and Elements</span></span>  

 <span data-ttu-id="b0ffb-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0ffb-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0ffb-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b0ffb-106">Attributes</span></span>  
  
|<span data-ttu-id="b0ffb-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b0ffb-107">Attribute</span></span>|<span data-ttu-id="b0ffb-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0ffb-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b0ffb-109">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="b0ffb-109">membershipProviderName</span></span>|<span data-ttu-id="b0ffb-110"><xref:System.Web.Security.MembershipProvider>Güvenlik belirteci işleyicisi tarafından kullanılması gereken öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0ffb-110">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0ffb-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0ffb-111">Child Elements</span></span>  

 <span data-ttu-id="b0ffb-112">Yok</span><span class="sxs-lookup"><span data-stu-id="b0ffb-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0ffb-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0ffb-113">Parent Elements</span></span>  
  
|<span data-ttu-id="b0ffb-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0ffb-114">Element</span></span>|<span data-ttu-id="b0ffb-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0ffb-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="b0ffb-116">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="b0ffb-116">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0ffb-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0ffb-117">Remarks</span></span>  

 <span data-ttu-id="b0ffb-118">`<userNameSecurityTokenHandlerRequirement>` <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> Bir nesne yapılandırmadan başlatıldığında öğesi özelliği ayarlar <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="b0ffb-118">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0ffb-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0ffb-119">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
