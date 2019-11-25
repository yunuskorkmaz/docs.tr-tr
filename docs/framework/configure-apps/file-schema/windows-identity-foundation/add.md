---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 83ba51cbbd5100bf7412f9914a270cac88f7faa1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973810"
---
# <a name="add"></a><span data-ttu-id="2a3d6-101">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="2a3d6-101">\<add></span></span>
<span data-ttu-id="2a3d6-102">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
<span data-ttu-id="2a3d6-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2a3d6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2a3d6-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="2a3d6-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="2a3d6-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="2a3d6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="2a3d6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="2a3d6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="2a3d6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add >**</span><span class="sxs-lookup"><span data-stu-id="2a3d6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a3d6-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a3d6-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a3d6-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a3d6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2a3d6-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a3d6-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2a3d6-111">Attributes</span></span>  
  
|<span data-ttu-id="2a3d6-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2a3d6-112">Attribute</span></span>|<span data-ttu-id="2a3d6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a3d6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a3d6-114">türü</span><span class="sxs-lookup"><span data-stu-id="2a3d6-114">type</span></span>|<span data-ttu-id="2a3d6-115">Eklenecek belirteç işleyicisinin CLR tür adı.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-115">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="2a3d6-116">`type` özniteliğini belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="2a3d6-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a3d6-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a3d6-117">Child Elements</span></span>  
  
|<span data-ttu-id="2a3d6-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="2a3d6-118">Element</span></span>|<span data-ttu-id="2a3d6-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a3d6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a3d6-120">samlSecurityTokenRequirement > \<</span><span class="sxs-lookup"><span data-stu-id="2a3d6-120">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="2a3d6-121"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-121">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="2a3d6-122">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="2a3d6-122">\<sessionTokenRequirement></span></span>](sessiontokenrequirement.md)|<span data-ttu-id="2a3d6-123"><xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> sınıfı veya türetilmiş sınıflar için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="2a3d6-124">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="2a3d6-124">\<userNameSecurityTokenHandlerRequirement></span></span>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="2a3d6-125"><xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> sınıfı veya türetilmiş sınıflar için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-125">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="2a3d6-126">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="2a3d6-126">\<x509SecurityTokenHandlerRequirement></span></span>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="2a3d6-127"><xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> sınıfı veya türetilmiş sınıflar için isteğe bağlı yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-127">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2a3d6-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a3d6-128">Parent Elements</span></span>  
  
|<span data-ttu-id="2a3d6-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="2a3d6-129">Element</span></span>|<span data-ttu-id="2a3d6-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a3d6-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a3d6-131">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="2a3d6-131">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="2a3d6-132">Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-132">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a3d6-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a3d6-133">Remarks</span></span>  
 <span data-ttu-id="2a3d6-134">`<add>` öğesi, belirteç işleyicisinin yapılandırmasını belirten tek bir alt öğe alabilir.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-134">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="2a3d6-135">Bu, `<add>` öğesinin `type` özniteliği aracılığıyla başvurulan işleyici sınıfının bu özellik için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-135">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="2a3d6-136">Bu özelliği sağlayan belirteç işleyici sınıfları bir <xref:System.Xml.XmlElement> nesnesi alan bir oluşturucuyu kullanıma sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-136">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="2a3d6-137">Yerleşik güvenlik belirteci işleyici sınıflarından birkaçı bu işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-137">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="2a3d6-138">Bu sınıflar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>ve <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-138">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2a3d6-139">Belirteç işleyici koleksiyonu verilen herhangi bir tür için yalnızca tek bir işleyici içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-139">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="2a3d6-140">Bu, örneğin, koleksiyona <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfından türetilmiş bir işleyici eklemek istiyorsanız, öncelikle varsayılan olarak bulunan <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, koleksiyondan kaldırmanız gerekir; Yani</span><span class="sxs-lookup"><span data-stu-id="2a3d6-140">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="2a3d6-141">Koleksiyondan tek bir işleyiciyi kaldırmak için [\<remove >](remove.md) öğesini kullanabilir veya tüm işleyicileri koleksiyondan kaldırmak için [\<Clear >](clear.md) öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-141">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="2a3d6-142">Bir işleyicide belirtilen ayarlar, [\<securitytokenhandlerconfiguration >](securitytokenhandlerconfiguration.md) öğesi altındaki belirteç işleyici koleksiyonunda belirtilen eşdeğer ayarları geçersiz kılar ve [\<IdentityConfiguration >](identityconfiguration.md) öğesi altındaki hizmet düzeyinde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-142">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a3d6-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a3d6-143">Example</span></span>  
 <span data-ttu-id="2a3d6-144">Aşağıdaki XML, varsayılan oturum belirteci işleyicisini özel bir oturum belirteci işleyicisiyle değiştirmek için `<add>` ve `<remove>` öğelerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-144">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="2a3d6-145">XML `ClaimsAwareWebFarm` örneğinden alınır.</span><span class="sxs-lookup"><span data-stu-id="2a3d6-145">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
