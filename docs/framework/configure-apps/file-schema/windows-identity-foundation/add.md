---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 34643d10ef1ed2e87152e5013634e62859e0594e
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759489"
---
# <a name="add"></a><span data-ttu-id="bea89-101">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="bea89-101">\<add></span></span>
<span data-ttu-id="bea89-102">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="bea89-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
 <span data-ttu-id="bea89-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="bea89-103">\<system.identityModel></span></span>  
<span data-ttu-id="bea89-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="bea89-104">\<identityConfiguration></span></span>  
<span data-ttu-id="bea89-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="bea89-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="bea89-106">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="bea89-106">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bea89-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bea89-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bea89-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bea89-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bea89-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bea89-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bea89-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bea89-110">Attributes</span></span>  
  
|<span data-ttu-id="bea89-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bea89-111">Attribute</span></span>|<span data-ttu-id="bea89-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bea89-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bea89-113">türü</span><span class="sxs-lookup"><span data-stu-id="bea89-113">type</span></span>|<span data-ttu-id="bea89-114">Belirteci işleyicisi eklenecek CLR türü adı.</span><span class="sxs-lookup"><span data-stu-id="bea89-114">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="bea89-115">Belirtme hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvurularını](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="bea89-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bea89-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bea89-116">Child Elements</span></span>  
  
|<span data-ttu-id="bea89-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="bea89-117">Element</span></span>|<span data-ttu-id="bea89-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bea89-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bea89-119">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="bea89-119">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="bea89-120">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> sınıfı <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı veya türetilmiş bir sınıf ya da bu sınıflarının biri.</span><span class="sxs-lookup"><span data-stu-id="bea89-120">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="bea89-121">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="bea89-121">\<sessionTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|<span data-ttu-id="bea89-122">İçin yapılandırma sağlar <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> sınıfı veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="bea89-122">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="bea89-123">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="bea89-123">\<userNameSecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="bea89-124">İçin yapılandırma sağlar <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> sınıfı veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="bea89-124">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="bea89-125">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="bea89-125">\<x509SecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|<span data-ttu-id="bea89-126">İsteğe bağlı yapılandırma için sağlar <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> sınıfı veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="bea89-126">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bea89-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bea89-127">Parent Elements</span></span>  
  
|<span data-ttu-id="bea89-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="bea89-128">Element</span></span>|<span data-ttu-id="bea89-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bea89-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bea89-130">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="bea89-130">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="bea89-131">Uç noktası ile kayıtlı bir güvenlik belirteci işleyicileri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="bea89-131">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bea89-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bea89-132">Remarks</span></span>  
 <span data-ttu-id="bea89-133">`<add>` Öğesi belirteç işleyici yapılandırması belirten tek bir alt öğe alabilir.</span><span class="sxs-lookup"><span data-stu-id="bea89-133">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="bea89-134">Bu bağımlı olup olmadığını işleyicisi sınıfı aracılığıyla başvurulan üzerinde `type` özniteliği `<add>` öğesi, bu özellik için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="bea89-134">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="bea89-135">Bu özelliği sağlayan belirteci işleyicisi sınıflar alan bir oluşturucu kullanıma gereken bir <xref:System.Xml.XmlElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="bea89-135">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="bea89-136">Birkaç yerleşik güvenlik belirteci işleyici sınıflarını, bu işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="bea89-136">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="bea89-137">Bu sınıflar <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, ve <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="bea89-137">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bea89-138">Belirteci işleyicisi koleksiyon, yalnızca belirli herhangi bir türde tek bir işleyici içerebilir.</span><span class="sxs-lookup"><span data-stu-id="bea89-138">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="bea89-139">Türetilen bir işleyici eklemek istiyorsanız, örneğin, yani <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> sınıfı koleksiyona önce kaldırmalısınız <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, koleksiyondan varsayılan olarak, mevcut olduğu.</span><span class="sxs-lookup"><span data-stu-id="bea89-139">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="bea89-140">Kullanabilirsiniz [ \<kaldırma >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) tek bir işleyici koleksiyonu veya kullanım kaldırmak için öğeyi [ \<Temizle >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) tüm işleyiciler Koleksiyondan kaldırılacak öğe.</span><span class="sxs-lookup"><span data-stu-id="bea89-140">You can use the [\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) element to remove a single handler from the collection or use the [\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="bea89-141">Belirtilen bir işleyici ayarları geçersiz kılma eşdeğer ayarlar altında belirteci işleyicisi koleksiyonu belirtilen [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) öğesi ve altında hizmet düzeyinde belirtilenlerden [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="bea89-141">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bea89-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="bea89-142">Example</span></span>  
 <span data-ttu-id="bea89-143">Aşağıdaki XML kullanımını gösterir `<add>` ve `<remove>` öğeleri varsayılan oturum belirteci işleyicisi bir özel oturum belirteci işleyicisi ile değiştirilecek.</span><span class="sxs-lookup"><span data-stu-id="bea89-143">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="bea89-144">XML alınır `ClaimsAwareWebFarm` örnek.</span><span class="sxs-lookup"><span data-stu-id="bea89-144">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
