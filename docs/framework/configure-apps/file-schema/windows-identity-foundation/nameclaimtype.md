---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 4bf8ad2f70499edfc72dd9fcd9a5d8a0aafbbc66
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251935"
---
# \<nameClaimType>
<span data-ttu-id="d37a3-101">Özelliği belirten talep türünü ayarlar <xref:System.Security.Principal.IIdentity.Name%2A> .</span><span class="sxs-lookup"><span data-stu-id="d37a3-101">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="d37a3-102">Talep türü, <xref:System.Security.Claims.Claim> <xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> Bu belirteç işleyicisinin metodu tarafından döndürülen nesneler koleksiyonunda bir aramak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d37a3-102">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="d37a3-103">Daha sonra, eşleşen talebin değeri <xref:System.Security.Principal.IIdentity> Bu belirteç işleyiciden oluşturulan adı olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d37a3-103">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="d37a3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d37a3-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d37a3-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d37a3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d37a3-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d37a3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d37a3-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d37a3-107">Attributes</span></span>  
  
|<span data-ttu-id="d37a3-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d37a3-108">Attribute</span></span>|<span data-ttu-id="d37a3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d37a3-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d37a3-110">value</span><span class="sxs-lookup"><span data-stu-id="d37a3-110">value</span></span>|<span data-ttu-id="d37a3-111">Özelliği için kullanılacak talebin talep türünü temsil eden URI 'yi belirten bir dize <xref:System.Security.Principal.IIdentity.Name%2A> .</span><span class="sxs-lookup"><span data-stu-id="d37a3-111">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="d37a3-112">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d37a3-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d37a3-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d37a3-113">Child Elements</span></span>  
 <span data-ttu-id="d37a3-114">Yok</span><span class="sxs-lookup"><span data-stu-id="d37a3-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d37a3-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d37a3-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d37a3-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="d37a3-116">Element</span></span>|<span data-ttu-id="d37a3-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d37a3-117">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="d37a3-118"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>Sınıf, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıf veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="d37a3-118">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d37a3-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d37a3-119">Remarks</span></span>  
 <span data-ttu-id="d37a3-120">`<nameClaimType>` <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> Bir nesne yapılandırmadan başlatıldığında öğesi özelliği ayarlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> .</span><span class="sxs-lookup"><span data-stu-id="d37a3-120">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d37a3-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="d37a3-121">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d37a3-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d37a3-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
