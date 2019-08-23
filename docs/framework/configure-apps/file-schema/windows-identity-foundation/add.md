---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 9505970c1fd7fcdfe62d3c6ef58f5d653fab4106
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941989"
---
# <a name="add"></a><span data-ttu-id="db393-101">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="db393-101">\<add></span></span>
<span data-ttu-id="db393-102">Belirtilen güvenlik belirteci işleyicisini belirteç işleyici koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="db393-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
 <span data-ttu-id="db393-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="db393-103">\<system.identityModel></span></span>  
<span data-ttu-id="db393-104">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="db393-104">\<identityConfiguration></span></span>  
<span data-ttu-id="db393-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="db393-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="db393-106">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="db393-106">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db393-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db393-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db393-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="db393-108">Attributes and Elements</span></span>  
 <span data-ttu-id="db393-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="db393-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db393-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="db393-110">Attributes</span></span>  
  
|<span data-ttu-id="db393-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="db393-111">Attribute</span></span>|<span data-ttu-id="db393-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db393-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db393-113">türü</span><span class="sxs-lookup"><span data-stu-id="db393-113">type</span></span>|<span data-ttu-id="db393-114">Eklenecek belirteç işleyicisinin CLR tür adı.</span><span class="sxs-lookup"><span data-stu-id="db393-114">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="db393-115">`type` Özniteliği belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="db393-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db393-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="db393-116">Child Elements</span></span>  
  
|<span data-ttu-id="db393-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="db393-117">Element</span></span>|<span data-ttu-id="db393-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db393-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db393-119">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="db393-119">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="db393-120"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Sınıf<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , sınıf veya bu sınıfların herhangi birinin türetilmiş bir sınıfı için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="db393-120">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="db393-121">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="db393-121">\<sessionTokenRequirement></span></span>](sessiontokenrequirement.md)|<span data-ttu-id="db393-122"><xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> Sınıf veya türetilmiş sınıflar için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="db393-122">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="db393-123">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="db393-123">\<userNameSecurityTokenHandlerRequirement></span></span>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="db393-124"><xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> Sınıf veya türetilmiş sınıflar için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="db393-124">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="db393-125">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="db393-125">\<x509SecurityTokenHandlerRequirement></span></span>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="db393-126"><xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> Sınıf veya türetilmiş sınıflar için isteğe bağlı yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="db393-126">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="db393-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="db393-127">Parent Elements</span></span>  
  
|<span data-ttu-id="db393-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="db393-128">Element</span></span>|<span data-ttu-id="db393-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db393-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db393-130">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="db393-130">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="db393-131">Uç nokta ile kaydedilmiş bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="db393-131">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db393-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db393-132">Remarks</span></span>  
 <span data-ttu-id="db393-133">`<add>` Öğesi, belirteç işleyicisinin yapılandırmasını belirten tek bir alt öğe alabilir.</span><span class="sxs-lookup"><span data-stu-id="db393-133">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="db393-134">Bu, `type` `<add>` öğesinin özniteliği aracılığıyla başvurulan işleyici sınıfının bu özellik için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="db393-134">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="db393-135">Bu özelliği sağlayan belirteç işleyici sınıfları bir <xref:System.Xml.XmlElement> nesne alan oluşturucuyu kullanıma sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db393-135">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="db393-136">Yerleşik güvenlik belirteci işleyici sınıflarından birkaçı bu işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="db393-136">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="db393-137"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>Bu sınıflar <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ,<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>,, ve<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>' dir. <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler></span><span class="sxs-lookup"><span data-stu-id="db393-137">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="db393-138">Belirteç işleyici koleksiyonu verilen herhangi bir tür için yalnızca tek bir işleyici içerebilir.</span><span class="sxs-lookup"><span data-stu-id="db393-138">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="db393-139">Bu, örneğin, koleksiyona <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfından türetilmiş bir işleyici eklemek istiyorsanız, öncelikle varsayılan olarak bulunan öğesini koleksiyondan <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>kaldırmanız gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="db393-139">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="db393-140">Koleksiyondan tek bir işleyiciyi kaldırmak veya [ \<Clear >](clear.md) öğesini kullanarak koleksiyondan tüm işleyicileri kaldırmak için [ \<Remove >](remove.md) öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db393-140">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="db393-141">Bir işleyicide belirtilen ayarlar, [ \<SecurityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) öğesi altındaki belirteç işleyici koleksiyonunda belirtilen eşdeğer ayarları geçersiz kılar ve [ \< IdentityConfiguration >](identityconfiguration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="db393-141">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db393-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="db393-142">Example</span></span>  
 <span data-ttu-id="db393-143">Aşağıdaki XML, varsayılan oturum belirteci işleyicisini özel `<add>` bir `<remove>` oturum belirteci işleyicisiyle değiştirmek için ve öğelerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="db393-143">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="db393-144">XML `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="db393-144">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
