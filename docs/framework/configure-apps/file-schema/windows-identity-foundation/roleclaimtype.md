---
description: 'Hakkında daha fazla bilgi edinin: <roleClaimType>'
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 69b86489b0a970addb7fc7c11dd88be52ac68e95
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652685"
---
# \<roleClaimType>

<span data-ttu-id="6bc08-102"><xref:System.Security.Claims.ClaimsIdentity>Belirteç işleyicisinin metodu tarafından döndürülen nesneler koleksiyonundaki rol türü taleplerini tanımlayan talep türünü belirtir <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> .</span><span class="sxs-lookup"><span data-stu-id="6bc08-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<roleClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="6bc08-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="6bc08-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <roleClaimType value=xs:string>  
          </roleClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6bc08-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6bc08-104">Attributes and Elements</span></span>  

 <span data-ttu-id="6bc08-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6bc08-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6bc08-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6bc08-106">Attributes</span></span>  
  
|<span data-ttu-id="6bc08-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6bc08-107">Attribute</span></span>|<span data-ttu-id="6bc08-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bc08-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6bc08-109">değer</span><span class="sxs-lookup"><span data-stu-id="6bc08-109">value</span></span>|<span data-ttu-id="6bc08-110">Rol talep türü için kullanılacak talebin talep türünü temsil eden URI 'yi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="6bc08-110">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6bc08-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6bc08-111">Child Elements</span></span>  

 <span data-ttu-id="6bc08-112">Yok</span><span class="sxs-lookup"><span data-stu-id="6bc08-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6bc08-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6bc08-113">Parent Elements</span></span>  
  
|<span data-ttu-id="6bc08-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="6bc08-114">Element</span></span>|<span data-ttu-id="6bc08-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bc08-115">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="6bc08-116"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>Sınıf, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıf veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bc08-116">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bc08-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6bc08-117">Remarks</span></span>  

 <span data-ttu-id="6bc08-118">`<roleClaimType>` <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> Bir nesne yapılandırmadan başlatıldığında öğesi özelliği ayarlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> .</span><span class="sxs-lookup"><span data-stu-id="6bc08-118">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bc08-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="6bc08-119">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6bc08-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bc08-120">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
