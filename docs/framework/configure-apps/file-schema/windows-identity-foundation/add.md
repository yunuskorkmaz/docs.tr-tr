---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 932e8452542ace66824fba1262694c220ce88676
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252180"
---
# <a name="add"></a><span data-ttu-id="a8cd3-101">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="a8cd3-101">\<add></span></span>
<span data-ttu-id="a8cd3-102">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
<span data-ttu-id="a8cd3-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a8cd3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a8cd3-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="a8cd3-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="a8cd3-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="a8cd3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="a8cd3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="a8cd3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="a8cd3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="a8cd3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8cd3-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8cd3-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8cd3-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8cd3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a8cd3-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8cd3-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8cd3-111">Attributes</span></span>  
  
|<span data-ttu-id="a8cd3-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8cd3-112">Attribute</span></span>|<span data-ttu-id="a8cd3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8cd3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a8cd3-114">türü</span><span class="sxs-lookup"><span data-stu-id="a8cd3-114">type</span></span>|<span data-ttu-id="a8cd3-115">Eklenecek belirteç işleyicisinin CLR tür adı.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-115">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="a8cd3-116">`type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="a8cd3-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8cd3-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8cd3-117">Child Elements</span></span>  
  
|<span data-ttu-id="a8cd3-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="a8cd3-118">Element</span></span>|<span data-ttu-id="a8cd3-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8cd3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8cd3-120">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="a8cd3-120">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="a8cd3-121"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Sınıf<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , sınıf veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-121">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="a8cd3-122">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="a8cd3-122">\<sessionTokenRequirement></span></span>](sessiontokenrequirement.md)|<span data-ttu-id="a8cd3-123"><xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> Sınıf veya türetilmiş sınıflar için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="a8cd3-124">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="a8cd3-124">\<userNameSecurityTokenHandlerRequirement></span></span>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="a8cd3-125"><xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> Sınıf veya türetilmiş sınıflar için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-125">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="a8cd3-126">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="a8cd3-126">\<x509SecurityTokenHandlerRequirement></span></span>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="a8cd3-127"><xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> Sınıf veya türetilmiş sınıflar için isteğe bağlı yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-127">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8cd3-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8cd3-128">Parent Elements</span></span>  
  
|<span data-ttu-id="a8cd3-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="a8cd3-129">Element</span></span>|<span data-ttu-id="a8cd3-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8cd3-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8cd3-131">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="a8cd3-131">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="a8cd3-132">Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-132">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8cd3-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8cd3-133">Remarks</span></span>  
 <span data-ttu-id="a8cd3-134">`<add>` Öğesi, belirteç işleyicisinin yapılandırmasını belirten tek bir alt öğe alabilir.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-134">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="a8cd3-135">Bu, `type` `<add>` öğesinin özniteliği aracılığıyla başvurulan işleyici sınıfının bu özellik için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-135">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="a8cd3-136">Bu özelliği sağlayan belirteç işleyici sınıfları bir <xref:System.Xml.XmlElement> nesne alan oluşturucuyu kullanıma sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-136">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="a8cd3-137">Yerleşik güvenlik belirteci işleyici sınıflarından birkaçı bu işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-137">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="a8cd3-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>Bu sınıflar <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ,<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>,, ve<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>' dir. <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler></span><span class="sxs-lookup"><span data-stu-id="a8cd3-138">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a8cd3-139">Belirteç işleyici koleksiyonu verilen herhangi bir tür için yalnızca tek bir işleyici içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-139">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="a8cd3-140">Bu, örneğin, koleksiyona <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfından türetilmiş bir işleyici eklemek istiyorsanız, öncelikle varsayılan olarak bulunan öğesini koleksiyondan <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>kaldırmanız gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-140">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="a8cd3-141">Koleksiyondan tek bir işleyiciyi kaldırmak veya [ \<Clear >](clear.md) öğesini kullanarak koleksiyondan tüm işleyicileri kaldırmak için [ \<Remove >](remove.md) öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-141">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="a8cd3-142">Bir işleyicide belirtilen ayarlar, [ \<SecurityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) öğesi altındaki belirteç işleyici koleksiyonunda belirtilen eşdeğer ayarları geçersiz kılar ve [ \< IdentityConfiguration >](identityconfiguration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-142">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8cd3-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8cd3-143">Example</span></span>  
 <span data-ttu-id="a8cd3-144">Aşağıdaki XML, varsayılan oturum belirteci işleyicisini özel `<add>` bir `<remove>` oturum belirteci işleyicisiyle değiştirmek için ve öğelerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-144">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="a8cd3-145">XML `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="a8cd3-145">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
