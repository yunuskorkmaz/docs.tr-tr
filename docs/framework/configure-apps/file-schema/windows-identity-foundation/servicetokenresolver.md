---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152586"
---
# \<serviceTokenResolver>
<span data-ttu-id="3b5f3-101">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan hizmet belirteci çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3b5f3-101">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="3b5f3-102">Hizmet belirteci çözümleyici, gelen belirteçlerde ve iletilerde şifreleme belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3b5f3-102">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="3b5f3-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b5f3-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b5f3-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b5f3-104">Attributes and Elements</span></span>  
 <span data-ttu-id="3b5f3-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3b5f3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b5f3-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3b5f3-106">Attributes</span></span>  
  
|<span data-ttu-id="3b5f3-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3b5f3-107">Attribute</span></span>|<span data-ttu-id="3b5f3-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b5f3-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3b5f3-109">tür</span><span class="sxs-lookup"><span data-stu-id="3b5f3-109">type</span></span>|<span data-ttu-id="3b5f3-110">Hizmet belirteci Çözümleyicisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b5f3-110">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="3b5f3-111">Ya <xref:System.IdentityModel.Selectors.SecurityTokenResolver> tür ya da sınıftan türeyen bir tür <xref:System.IdentityModel.Selectors.SecurityTokenResolver> .</span><span class="sxs-lookup"><span data-stu-id="3b5f3-111">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="3b5f3-112">Özniteliği belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="3b5f3-112">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="3b5f3-113">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3b5f3-113">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b5f3-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b5f3-114">Child Elements</span></span>  
 <span data-ttu-id="3b5f3-115">Yok</span><span class="sxs-lookup"><span data-stu-id="3b5f3-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b5f3-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b5f3-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3b5f3-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="3b5f3-117">Element</span></span>|<span data-ttu-id="3b5f3-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b5f3-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="3b5f3-119">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b5f3-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b5f3-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b5f3-120">Remarks</span></span>  
 <span data-ttu-id="3b5f3-121">Hizmet belirteci çözümleyici, gelen belirteçlerde ve iletilerde şifreleme belirtecini çözümlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b5f3-121">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="3b5f3-122">Gelen belirteçlerin şifresini çözmek için kullanılması gereken anahtarı almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3b5f3-122">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="3b5f3-123">Özniteliğini belirtmeniz gerekir `type` .</span><span class="sxs-lookup"><span data-stu-id="3b5f3-123">You must specify the `type` attribute.</span></span> <span data-ttu-id="3b5f3-124">Belirtilen tür ya da <xref:System.IdentityModel.Selectors.SecurityTokenResolver> sınıfından türetilen özel bir tür olabilir <xref:System.IdentityModel.Selectors.SecurityTokenResolver> .</span><span class="sxs-lookup"><span data-stu-id="3b5f3-124">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="3b5f3-125">Bazı belirteç işleyicileri, yapılandırmada hizmet belirteci çözümleyici ayarlarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3b5f3-125">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="3b5f3-126">Bağımsız belirteç işleyicilerindeki ayarlar, güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="3b5f3-126">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b5f3-127">Öğenin `<serviceTokenResolver>` bir alt öğesi olarak belirtilmesi [\<identityConfiguration>](identityconfiguration.md) kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3b5f3-127">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="3b5f3-128">`<securityTokenHandlerConfiguration>`Öğesindeki ayarlar, öğesinde olanları geçersiz kılar `<identityConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="3b5f3-128">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b5f3-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b5f3-129">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
