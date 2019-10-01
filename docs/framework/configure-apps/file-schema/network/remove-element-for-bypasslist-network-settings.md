---
title: bypasslist için <remove> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: 97b49a8a520d6a4f72945366874991d2deb18710
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697902"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="a71b7-102">BypassList için \<remove > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="a71b7-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="a71b7-103">Proxy atlama listesinden bir IP adresi veya DNS adı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a71b7-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

[<span data-ttu-id="a71b7-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="a71b7-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a71b7-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a71b7-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="a71b7-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a71b7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="a71b7-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<bypasslist >** ](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a71b7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>  
<span data-ttu-id="a71b7-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="a71b7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="a71b7-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a71b7-109">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a71b7-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a71b7-110">Attributes and Elements</span></span>

<span data-ttu-id="a71b7-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a71b7-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a71b7-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a71b7-112">Attributes</span></span>

|<span data-ttu-id="a71b7-113">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="a71b7-113">**Attribute**</span></span>|<span data-ttu-id="a71b7-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="a71b7-114">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="a71b7-115">IP adresini veya DNS adını tanımlayan bir normal ifade.</span><span class="sxs-lookup"><span data-stu-id="a71b7-115">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a71b7-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a71b7-116">Child Elements</span></span>

<span data-ttu-id="a71b7-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="a71b7-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a71b7-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a71b7-118">Parent Elements</span></span>

|<span data-ttu-id="a71b7-119">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="a71b7-119">**Element**</span></span>|<span data-ttu-id="a71b7-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="a71b7-120">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="a71b7-121">BypassList</span><span class="sxs-lookup"><span data-stu-id="a71b7-121">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="a71b7-122">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a71b7-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a71b7-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a71b7-123">Remarks</span></span>

<span data-ttu-id="a71b7-124">@No__t-0 öğesi, IP adreslerini veya DNS sunucu adlarını tanımlayan normal ifadeleri, bir proxy sunucusunu atlayan adresler listesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a71b7-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="a71b7-125">Adresler yapılandırma hiyerarşisinde daha önce veya yapılandırma hiyerarşisinde daha yüksek bir düzeyde tanımlandı.</span><span class="sxs-lookup"><span data-stu-id="a71b7-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="a71b7-126">@No__t-0 özniteliğinin değeri bir IP adresi veya ana bilgisayar adı kümesini açıklayan bir normal ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a71b7-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="a71b7-127">Normal ifadeler hakkında daha fazla bilgi için bkz. [Normal ifadeleri .NET Framework](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a71b7-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="a71b7-128">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="a71b7-128">Configuration Files</span></span>

<span data-ttu-id="a71b7-129">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a71b7-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="a71b7-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="a71b7-130">Example</span></span>

<span data-ttu-id="a71b7-131">Aşağıdaki örnek, adventure-works.com etki alanı için önceki tüm tanımları kaldırır ve ardından contoso.com etki alanını atlama listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="a71b7-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <bypasslist>
        <remove address="[a-z]+\.adventure-works\.com$" />
        <add address="[a-z]+\.contoso\.com$" />
      </bypasslist>
    </defaultProxy>
  </system.net>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a71b7-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a71b7-132">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="a71b7-133">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a71b7-133">Network Settings Schema</span></span>](index.md)
