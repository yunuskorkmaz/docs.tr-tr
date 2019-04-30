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
ms.openlocfilehash: a04cca3e57af5cc422776c5b2444a140e86f98b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674473"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="d8cdf-102">\<kaldırma > bypasslist (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="d8cdf-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="d8cdf-103">Bir IP adresi veya DNS adı proxy atlama listeden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

<span data-ttu-id="d8cdf-104">\<Yapılandırma > \\</span><span class="sxs-lookup"><span data-stu-id="d8cdf-104">\<configuration>\\</span></span>
<span data-ttu-id="d8cdf-105">\<System.NET > \\</span><span class="sxs-lookup"><span data-stu-id="d8cdf-105">\<system.net>\\</span></span>
<span data-ttu-id="d8cdf-106">\<defaultProxy > \\</span><span class="sxs-lookup"><span data-stu-id="d8cdf-106">\<defaultProxy>\\</span></span>
<span data-ttu-id="d8cdf-107">\<bypasslist>\\</span><span class="sxs-lookup"><span data-stu-id="d8cdf-107">\<bypasslist>\\</span></span>
<span data-ttu-id="d8cdf-108">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="d8cdf-108">\<remove></span></span>

## <a name="syntax"></a><span data-ttu-id="d8cdf-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8cdf-109">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d8cdf-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8cdf-110">Attributes and Elements</span></span>

<span data-ttu-id="d8cdf-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d8cdf-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d8cdf-112">Attributes</span></span>

|<span data-ttu-id="d8cdf-113">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="d8cdf-113">**Attribute**</span></span>|<span data-ttu-id="d8cdf-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d8cdf-114">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="d8cdf-115">Bir IP adresi veya DNS adını tanımlayan bir normal ifade.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-115">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="d8cdf-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8cdf-116">Child Elements</span></span>

<span data-ttu-id="d8cdf-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d8cdf-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8cdf-118">Parent Elements</span></span>

|<span data-ttu-id="d8cdf-119">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="d8cdf-119">**Element**</span></span>|<span data-ttu-id="d8cdf-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d8cdf-120">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="d8cdf-121">bypasslist</span><span class="sxs-lookup"><span data-stu-id="d8cdf-121">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="d8cdf-122">Bir proxy sunucu kullanmaması adresleri açıklayan normal bir ifade kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d8cdf-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8cdf-123">Remarks</span></span>

<span data-ttu-id="d8cdf-124">`remove` Öğeyi normal ifadeler IP adresi veya DNS sunucu adları bir ara sunucu atlama adresleri listesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="d8cdf-125">Adresler, yapılandırma dosyasında ya da daha yüksek bir düzeyde yapılandırma hiyerarşideki daha önce tanımlanmadı.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="d8cdf-126">Değeri `address` öznitelik, bir dizi IP adresi veya ana bilgisayar adları açıklayan bir normal ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="d8cdf-127">Normal ifadeler hakkında daha fazla bilgi için bkz. [.NET framework normal ifadelerinde](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d8cdf-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="d8cdf-128">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="d8cdf-128">Configuration Files</span></span>

<span data-ttu-id="d8cdf-129">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="d8cdf-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8cdf-130">Example</span></span>

<span data-ttu-id="d8cdf-131">Aşağıdaki örnek, adventure works.com'u etki alanı için herhangi bir önceki tanım kaldırır ve sonra contoso.com etki alanına atlama listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d8cdf-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-132">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="d8cdf-133">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d8cdf-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
