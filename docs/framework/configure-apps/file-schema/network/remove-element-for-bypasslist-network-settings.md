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
ms.openlocfilehash: 99c18bd5b779845d52831b4a9591eaf4d5e5530b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920957"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="a2845-102">\<BypassList için > öğesini kaldır (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="a2845-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="a2845-103">Proxy atlama listesinden bir IP adresi veya DNS adı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a2845-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

<span data-ttu-id="a2845-104">\<Yapılandırma > </span><span class="sxs-lookup"><span data-stu-id="a2845-104">\<configuration></span></span>\
<span data-ttu-id="a2845-105">\<System. net > </span><span class="sxs-lookup"><span data-stu-id="a2845-105">\<system.net></span></span>\
<span data-ttu-id="a2845-106">\<defaultProxy > </span><span class="sxs-lookup"><span data-stu-id="a2845-106">\<defaultProxy></span></span>\
<span data-ttu-id="a2845-107">\<BypassList > </span><span class="sxs-lookup"><span data-stu-id="a2845-107">\<bypasslist></span></span>\
<span data-ttu-id="a2845-108">\<> Kaldır</span><span class="sxs-lookup"><span data-stu-id="a2845-108">\<remove></span></span>

## <a name="syntax"></a><span data-ttu-id="a2845-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2845-109">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a2845-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2845-110">Attributes and Elements</span></span>

<span data-ttu-id="a2845-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a2845-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a2845-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a2845-112">Attributes</span></span>

|<span data-ttu-id="a2845-113">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="a2845-113">**Attribute**</span></span>|<span data-ttu-id="a2845-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="a2845-114">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="a2845-115">IP adresini veya DNS adını tanımlayan bir normal ifade.</span><span class="sxs-lookup"><span data-stu-id="a2845-115">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a2845-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2845-116">Child Elements</span></span>

<span data-ttu-id="a2845-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="a2845-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a2845-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2845-118">Parent Elements</span></span>

|<span data-ttu-id="a2845-119">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="a2845-119">**Element**</span></span>|<span data-ttu-id="a2845-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="a2845-120">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="a2845-121">BypassList</span><span class="sxs-lookup"><span data-stu-id="a2845-121">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="a2845-122">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2845-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a2845-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2845-123">Remarks</span></span>

<span data-ttu-id="a2845-124">Öğesi `remove` , IP adreslerini veya DNS sunucusu adlarını tanımlayan normal ifadeleri bir proxy sunucusunu atlayan adresler listesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a2845-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="a2845-125">Adresler yapılandırma hiyerarşisinde daha önce veya yapılandırma hiyerarşisinde daha yüksek bir düzeyde tanımlandı.</span><span class="sxs-lookup"><span data-stu-id="a2845-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="a2845-126">`address` Özniteliğin değeri bir IP adresi veya ana bilgisayar adı kümesini açıklayan bir normal ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a2845-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="a2845-127">Normal ifadeler hakkında daha fazla bilgi için bkz. [Normal ifadeleri .NET Framework](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a2845-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="a2845-128">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="a2845-128">Configuration Files</span></span>

<span data-ttu-id="a2845-129">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a2845-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="a2845-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2845-130">Example</span></span>

<span data-ttu-id="a2845-131">Aşağıdaki örnek, adventure-works.com etki alanı için önceki tüm tanımları kaldırır ve ardından contoso.com etki alanını atlama listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="a2845-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a2845-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2845-132">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="a2845-133">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a2845-133">Network Settings Schema</span></span>](index.md)
