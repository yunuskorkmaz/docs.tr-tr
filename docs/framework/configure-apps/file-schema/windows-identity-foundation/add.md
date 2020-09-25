---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 2f37019fa0787f5c5553dbd3debc173ec0a047ee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189968"
---
# \<add>

<span data-ttu-id="4d871-101">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="4d871-101">Adds the specified security token handler to the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="4d871-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="4d871-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d871-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d871-103">Attributes and Elements</span></span>  

 <span data-ttu-id="4d871-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4d871-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d871-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4d871-105">Attributes</span></span>  
  
|<span data-ttu-id="4d871-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4d871-106">Attribute</span></span>|<span data-ttu-id="4d871-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d871-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d871-108">tür</span><span class="sxs-lookup"><span data-stu-id="4d871-108">type</span></span>|<span data-ttu-id="4d871-109">Eklenecek belirteç işleyicisinin CLR tür adı.</span><span class="sxs-lookup"><span data-stu-id="4d871-109">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="4d871-110">Özniteliği belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="4d871-110">For more information about how to specify the `type` attribute, see [Custom Type References](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d871-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d871-111">Child Elements</span></span>  
  
|<span data-ttu-id="4d871-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="4d871-112">Element</span></span>|<span data-ttu-id="4d871-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d871-113">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="4d871-114"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>Sınıf, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıf veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d871-114">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[\<sessionTokenRequirement>](sessiontokenrequirement.md)|<span data-ttu-id="4d871-115"><xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>Sınıf veya türetilmiş sınıflar için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d871-115">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<userNameSecurityTokenHandlerRequirement>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="4d871-116"><xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>Sınıf veya türetilmiş sınıflar için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d871-116">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<x509SecurityTokenHandlerRequirement>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="4d871-117">Sınıf veya türetilmiş sınıflar için isteğe bağlı yapılandırma sağlar <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="4d871-117">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4d871-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d871-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4d871-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="4d871-119">Element</span></span>|<span data-ttu-id="4d871-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d871-120">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="4d871-121">Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d871-121">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d871-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d871-122">Remarks</span></span>  

 <span data-ttu-id="4d871-123">`<add>`Öğesi, belirteç işleyicisinin yapılandırmasını belirten tek bir alt öğe alabilir.</span><span class="sxs-lookup"><span data-stu-id="4d871-123">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="4d871-124">Bu, öğesinin özniteliği aracılığıyla başvurulan işleyici sınıfının `type` `<add>` Bu özellik için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d871-124">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="4d871-125">Bu özelliği sağlayan belirteç işleyici sınıfları bir nesne alan oluşturucuyu kullanıma sunmalıdır <xref:System.Xml.XmlElement> .</span><span class="sxs-lookup"><span data-stu-id="4d871-125">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="4d871-126">Yerleşik güvenlik belirteci işleyici sınıflarından birkaçı bu işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d871-126">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="4d871-127">Bu sınıflar,,, ve ' dir <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="4d871-127">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4d871-128">Belirteç işleyici koleksiyonu verilen herhangi bir tür için yalnızca tek bir işleyici içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4d871-128">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="4d871-129">Bu, örneğin, koleksiyona sınıfından türetilmiş bir işleyici eklemek istiyorsanız, öncelikle varsayılan olarak bulunan öğesini koleksiyondan kaldırmanız gerektiği anlamına gelir <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="4d871-129">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="4d871-130">[\<remove>](remove.md)Koleksiyondan tek bir işleyiciyi kaldırmak için öğesini kullanabilir veya [\<clear>](clear.md) tüm işleyicileri koleksiyondan kaldırmak için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d871-130">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="4d871-131">Bir işleyicide belirtilen ayarlar, öğesinin altındaki belirteç işleyici koleksiyonunda belirtilen eşdeğer ayarları geçersiz kılar [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) ve öğesi altındaki hizmet düzeyinde belirtilmiştir [\<identityConfiguration>](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="4d871-131">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d871-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d871-132">Example</span></span>  

 <span data-ttu-id="4d871-133">Aşağıdaki XML, `<add>` `<remove>` varsayılan oturum belirteci işleyicisini özel bir oturum belirteci işleyicisiyle değiştirmek için ve öğelerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4d871-133">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="4d871-134">XML `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="4d871-134">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
