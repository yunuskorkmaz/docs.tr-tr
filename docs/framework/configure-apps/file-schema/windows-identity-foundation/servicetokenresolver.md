---
description: 'Hakkında daha fazla bilgi edinin: <serviceTokenResolver>'
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: ab24c92eee43324365adb3bb3a64c8a765017a53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698303"
---
# \<serviceTokenResolver>

<span data-ttu-id="e03ce-102">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e03ce-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="e03ce-103">Hizmet belirteci çözümleyici, gelen belirteçlerde ve iletilerde şifreleme belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e03ce-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="e03ce-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e03ce-104">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e03ce-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e03ce-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e03ce-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e03ce-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e03ce-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e03ce-107">Attributes</span></span>  
  
|<span data-ttu-id="e03ce-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e03ce-108">Attribute</span></span>|<span data-ttu-id="e03ce-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e03ce-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e03ce-110">tür</span><span class="sxs-lookup"><span data-stu-id="e03ce-110">type</span></span>|<span data-ttu-id="e03ce-111">Hizmet belirteci Çözümleyicisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e03ce-111">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="e03ce-112">Ya <xref:System.IdentityModel.Selectors.SecurityTokenResolver> tür ya da sınıftan türeyen bir tür <xref:System.IdentityModel.Selectors.SecurityTokenResolver> .</span><span class="sxs-lookup"><span data-stu-id="e03ce-112">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="e03ce-113">Özniteliği belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="e03ce-113">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="e03ce-114">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e03ce-114">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e03ce-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e03ce-115">Child Elements</span></span>  

 <span data-ttu-id="e03ce-116">Yok</span><span class="sxs-lookup"><span data-stu-id="e03ce-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e03ce-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e03ce-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e03ce-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="e03ce-118">Element</span></span>|<span data-ttu-id="e03ce-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e03ce-119">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="e03ce-120">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="e03ce-120">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e03ce-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e03ce-121">Remarks</span></span>  

 <span data-ttu-id="e03ce-122">Hizmet belirteci çözümleyici, gelen belirteçlerde ve iletilerde şifreleme belirtecini çözümlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e03ce-122">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="e03ce-123">Gelen belirteçlerin şifresini çözmek için kullanılması gereken anahtarı almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e03ce-123">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="e03ce-124">Özniteliğini belirtmeniz gerekir `type` .</span><span class="sxs-lookup"><span data-stu-id="e03ce-124">You must specify the `type` attribute.</span></span> <span data-ttu-id="e03ce-125">Belirtilen tür ya da <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıfından türetilen özel bir tür olabilir <xref:System.IdentityModel.Selectors.SecurityTokenResolver> .</span><span class="sxs-lookup"><span data-stu-id="e03ce-125">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="e03ce-126">Bazı belirteç işleyicileri, yapılandırmada hizmet belirteci çözümleyici ayarlarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e03ce-126">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="e03ce-127">Bağımsız belirteç işleyicilerindeki ayarlar, güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e03ce-127">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e03ce-128">Öğenin `<serviceTokenResolver>` bir alt öğesi olarak belirtilmesi [\<identityConfiguration>](identityconfiguration.md) kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e03ce-128">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="e03ce-129">`<securityTokenHandlerConfiguration>`Öğesindeki ayarlar, öğesinde olanları geçersiz kılar `<identityConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="e03ce-129">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e03ce-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="e03ce-130">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
