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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697902"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="d1fad-102">bypasslist için \<remove> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="d1fad-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="d1fad-103">Proxy atlama listesinden bir IP adresi veya DNS adı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d1fad-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  

## <a name="syntax"></a><span data-ttu-id="d1fad-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1fad-104">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d1fad-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1fad-105">Attributes and Elements</span></span>

<span data-ttu-id="d1fad-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d1fad-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d1fad-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d1fad-107">Attributes</span></span>

|<span data-ttu-id="d1fad-108">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="d1fad-108">**Attribute**</span></span>|<span data-ttu-id="d1fad-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d1fad-109">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="d1fad-110">IP adresini veya DNS adını tanımlayan bir normal ifade.</span><span class="sxs-lookup"><span data-stu-id="d1fad-110">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="d1fad-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1fad-111">Child Elements</span></span>

<span data-ttu-id="d1fad-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="d1fad-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d1fad-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1fad-113">Parent Elements</span></span>

|<span data-ttu-id="d1fad-114">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="d1fad-114">**Element**</span></span>|<span data-ttu-id="d1fad-115">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d1fad-115">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="d1fad-116">BypassList</span><span class="sxs-lookup"><span data-stu-id="d1fad-116">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="d1fad-117">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1fad-117">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d1fad-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1fad-118">Remarks</span></span>

<span data-ttu-id="d1fad-119">`remove`Öğesi, IP adreslerini veya DNS sunucusu adlarını tanımlayan normal ifadeleri bir proxy sunucusunu atlayan adresler listesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d1fad-119">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="d1fad-120">Adresler yapılandırma hiyerarşisinde daha önce veya yapılandırma hiyerarşisinde daha yüksek bir düzeyde tanımlandı.</span><span class="sxs-lookup"><span data-stu-id="d1fad-120">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="d1fad-121">`address`Özniteliğin değeri BIR IP adresi veya ana bilgisayar adı kümesini açıklayan bir normal ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d1fad-121">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="d1fad-122">Normal ifadeler hakkında daha fazla bilgi için bkz.. [Normal ifadeleri .NET Framework](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d1fad-122">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="d1fad-123">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="d1fad-123">Configuration Files</span></span>

<span data-ttu-id="d1fad-124">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1fad-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="d1fad-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1fad-125">Example</span></span>

<span data-ttu-id="d1fad-126">Aşağıdaki örnek, adventure-works.com etki alanı için önceki tüm tanımları kaldırır ve ardından contoso.com etki alanını atlama listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="d1fad-126">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d1fad-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1fad-127">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="d1fad-128">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d1fad-128">Network Settings Schema</span></span>](index.md)
