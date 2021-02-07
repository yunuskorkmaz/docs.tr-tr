---
description: 'Hakkında daha fazla bilgi edinin: <nameClaimType>'
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: d5bc2f96c2753febdb61c3495b7067c0e31e52d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664060"
---
# \<nameClaimType>

<span data-ttu-id="11da9-102">Özelliği belirten talep türünü ayarlar <xref:System.Security.Principal.IIdentity.Name%2A> .</span><span class="sxs-lookup"><span data-stu-id="11da9-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="11da9-103">Talep türü, <xref:System.Security.Claims.Claim> <xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> Bu belirteç işleyicisinin metodu tarafından döndürülen nesneler koleksiyonunda bir aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="11da9-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="11da9-104">Daha sonra, eşleşen talebin değeri <xref:System.Security.Principal.IIdentity> Bu belirteç işleyiciden oluşturulan adı olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="11da9-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="11da9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="11da9-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11da9-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="11da9-106">Attributes and Elements</span></span>  

 <span data-ttu-id="11da9-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="11da9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11da9-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="11da9-108">Attributes</span></span>  
  
|<span data-ttu-id="11da9-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="11da9-109">Attribute</span></span>|<span data-ttu-id="11da9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11da9-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11da9-111">değer</span><span class="sxs-lookup"><span data-stu-id="11da9-111">value</span></span>|<span data-ttu-id="11da9-112">Özelliği için kullanılacak talebin talep türünü temsil eden URI 'yi belirten bir dize <xref:System.Security.Principal.IIdentity.Name%2A> .</span><span class="sxs-lookup"><span data-stu-id="11da9-112">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="11da9-113">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="11da9-113">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11da9-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="11da9-114">Child Elements</span></span>  

 <span data-ttu-id="11da9-115">Yok</span><span class="sxs-lookup"><span data-stu-id="11da9-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11da9-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="11da9-116">Parent Elements</span></span>  
  
|<span data-ttu-id="11da9-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="11da9-117">Element</span></span>|<span data-ttu-id="11da9-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11da9-118">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="11da9-119"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>Sınıf, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıf veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="11da9-119">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11da9-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11da9-120">Remarks</span></span>  

 <span data-ttu-id="11da9-121">`<nameClaimType>` <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> Bir nesne yapılandırmadan başlatıldığında öğesi özelliği ayarlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> .</span><span class="sxs-lookup"><span data-stu-id="11da9-121">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11da9-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="11da9-122">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="11da9-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11da9-123">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
