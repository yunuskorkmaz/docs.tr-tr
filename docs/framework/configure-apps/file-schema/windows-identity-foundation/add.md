---
title: '&lt;add&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c0709159207cfd9f32aa9b6243bb53b7c1ed0e3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt"></a><span data-ttu-id="77699-102">&lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="77699-102">&lt;add&gt;</span></span>
<span data-ttu-id="77699-103">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="77699-103">Adds the specified security token handler to the token handler collection.</span></span>  
  
 <span data-ttu-id="77699-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="77699-104">\<system.identityModel></span></span>  
<span data-ttu-id="77699-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="77699-105">\<identityConfiguration></span></span>  
<span data-ttu-id="77699-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="77699-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="77699-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="77699-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77699-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77699-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77699-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="77699-109">Attributes and Elements</span></span>  
 <span data-ttu-id="77699-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="77699-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77699-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="77699-111">Attributes</span></span>  
  
|<span data-ttu-id="77699-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="77699-112">Attribute</span></span>|<span data-ttu-id="77699-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77699-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="77699-114">türü</span><span class="sxs-lookup"><span data-stu-id="77699-114">type</span></span>|<span data-ttu-id="77699-115">Eklenecek belirteci işleyicisi CLR türü adı.</span><span class="sxs-lookup"><span data-stu-id="77699-115">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="77699-116">Nasıl belirleneceği hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvuruları](http://msdn.microsoft.com/en-us/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="77699-116">For more information about how to specify the `type` attribute, see [Custom Type References](http://msdn.microsoft.com/en-us/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77699-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="77699-117">Child Elements</span></span>  
  
|<span data-ttu-id="77699-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="77699-118">Element</span></span>|<span data-ttu-id="77699-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77699-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77699-120">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="77699-120">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="77699-121">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı ya da bu sınıfların ya da, türetilmiş bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="77699-121">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="77699-122">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="77699-122">\<sessionTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|<span data-ttu-id="77699-123">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> sınıf veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="77699-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="77699-124">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="77699-124">\<userNameSecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="77699-125">İçin yapılandırma sağlar <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> sınıf veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="77699-125">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="77699-126">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="77699-126">\<x509SecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|<span data-ttu-id="77699-127">İçin isteğe bağlı yapılandırma sağlar <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> sınıf veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="77699-127">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="77699-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="77699-128">Parent Elements</span></span>  
  
|<span data-ttu-id="77699-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="77699-129">Element</span></span>|<span data-ttu-id="77699-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77699-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77699-131">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="77699-131">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="77699-132">Uç noktası ile kayıtlı güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="77699-132">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77699-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77699-133">Remarks</span></span>  
 <span data-ttu-id="77699-134">`<add>` Öğesi belirteç işleyici yapılandırması belirten tek bir alt öğe alabilir.</span><span class="sxs-lookup"><span data-stu-id="77699-134">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="77699-135">Bu olup olmadığını işleyici sınıfı aracılığıyla başvurulan üzerinde bağımlı `type` özniteliği `<add>` öğesi, bu özellik için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="77699-135">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="77699-136">Bu özellik sağlayan belirteci işleyicisi sınıflar alan oluşturucu kullanıma gerekir bir <xref:System.Xml.XmlElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="77699-136">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="77699-137">Birkaç yerleşik güvenlik belirteci işleyicisi sınıfların bu işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="77699-137">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="77699-138">Bu sınıflar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, ve <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="77699-138">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="77699-139">Belirteç işleyici koleksiyonu yalnızca herhangi bir türde tek bir işleyici içerebilir.</span><span class="sxs-lookup"><span data-stu-id="77699-139">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="77699-140">Türetilmiş bir işleyici eklemek istiyorsanız, örneğin, yani <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı önce kaldırmalısınız koleksiyona <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, koleksiyondan varsayılan olarak, mevcut olduğu.</span><span class="sxs-lookup"><span data-stu-id="77699-140">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="77699-141">Kullanabileceğiniz [ \<Kaldır >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) tek bir işleyici koleksiyonu veya kullanım kaldırmak için öğesi [ \<temizleyin >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) tüm işleyiciler Koleksiyondan kaldırılacak öğe.</span><span class="sxs-lookup"><span data-stu-id="77699-141">You can use the [\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) element to remove a single handler from the collection or use the [\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="77699-142">Üzerinde bir işleyici için belirtilen ayarları altında belirteci işleyicisi koleksiyonu belirtilen eşdeğer ayarları geçersiz kılar [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) öğesi ve altında hizmet düzeyindeki belirtilenlerle [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="77699-142">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77699-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="77699-143">Example</span></span>  
 <span data-ttu-id="77699-144">Aşağıdaki XML kullanımı gösterilmiştir `<add>` ve `<remove>` öğeleri varsayılan oturum belirteci işleyicisi özel oturum belirteci işleyicisi ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="77699-144">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="77699-145">XML alınırlar `ClaimsAwareWebFarm` örnek.</span><span class="sxs-lookup"><span data-stu-id="77699-145">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
