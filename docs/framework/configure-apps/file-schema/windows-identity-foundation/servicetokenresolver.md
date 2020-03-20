---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152586"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="a61d1-101">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="a61d1-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="a61d1-102">Belirteç işleyicisi koleksiyonunda işleyiciler tarafından kullanılan hizmet belirteci çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a61d1-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="a61d1-103">Hizmet belirteci çözümleyicisi, gelen belirteçler ve iletiler üzerindeki şifreleme belirteci çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a61d1-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="a61d1-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a61d1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a61d1-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="a61d1-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="a61d1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="a61d1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="a61d1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlikTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="a61d1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="a61d1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlikTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="a61d1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="a61d1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**</span><span class="sxs-lookup"><span data-stu-id="a61d1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a61d1-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a61d1-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a61d1-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a61d1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a61d1-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a61d1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a61d1-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a61d1-113">Attributes</span></span>  
  
|<span data-ttu-id="a61d1-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a61d1-114">Attribute</span></span>|<span data-ttu-id="a61d1-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a61d1-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a61d1-116">type</span><span class="sxs-lookup"><span data-stu-id="a61d1-116">type</span></span>|<span data-ttu-id="a61d1-117">Hizmet belirteci çözümleyicisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a61d1-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="a61d1-118"><xref:System.IdentityModel.Selectors.SecurityTokenResolver> Sınıftan <xref:System.IdentityModel.Selectors.SecurityTokenResolver> tür veya tür.</span><span class="sxs-lookup"><span data-stu-id="a61d1-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="a61d1-119">Öznitelik nasıl belirtilir `type` hakkında daha fazla bilgi için bkz: [Özel Tür Başvuruları].</span><span class="sxs-lookup"><span data-stu-id="a61d1-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="a61d1-120">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a61d1-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a61d1-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a61d1-121">Child Elements</span></span>  
 <span data-ttu-id="a61d1-122">None</span><span class="sxs-lookup"><span data-stu-id="a61d1-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a61d1-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a61d1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a61d1-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="a61d1-124">Element</span></span>|<span data-ttu-id="a61d1-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a61d1-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a61d1-126">\<güvenlikTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="a61d1-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="a61d1-127">Güvenlik belirteç işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="a61d1-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a61d1-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a61d1-128">Remarks</span></span>  
 <span data-ttu-id="a61d1-129">Hizmet belirteci çözümleyicisi, gelen belirteçler ve iletiler üzerindeki şifreleme belirteci çözümlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a61d1-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="a61d1-130">Gelen belirteçlerin şifresini çözmek için kullanılması gereken anahtarı almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a61d1-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="a61d1-131">Özniteliği belirtmeniz `type` gerekir.</span><span class="sxs-lookup"><span data-stu-id="a61d1-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="a61d1-132">Belirtilen tür, <xref:System.IdentityModel.Selectors.SecurityTokenResolver> <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıftan türeyen özel bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="a61d1-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="a61d1-133">Bazı belirteç işleyicileri yapılandırmada hizmet belirteç çözümleyicisi ayarlarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a61d1-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="a61d1-134">Tek tek belirteç işleyicileri ayarları, güvenlik belirteci işleyicisi koleksiyonunda belirtilenleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a61d1-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a61d1-135">Kimlik Yapılandırma `<serviceTokenResolver>` [ \<>](identityconfiguration.md) öğesinin alt öğesi olarak öğebelirtilmesi küçümsenmiştir, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a61d1-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="a61d1-136">Öğedeki `<securityTokenHandlerConfiguration>` `<identityConfiguration>` ayarlar, öğedekiayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a61d1-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a61d1-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="a61d1-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
