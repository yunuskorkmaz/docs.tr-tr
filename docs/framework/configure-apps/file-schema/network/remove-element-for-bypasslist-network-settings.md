---
description: 'Hakkında daha fazla bilgi edinin: <remove> BypassList için öğesi (ağ ayarları)'
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
ms.openlocfilehash: 48441f1b402b339a1bd2ea069678afb4b1d5f2e1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740294"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="5c6e4-103">bypasslist için \<remove> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="5c6e4-103">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="5c6e4-104">Proxy atlama listesinden bir IP adresi veya DNS adı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5c6e4-104">Removes an IP address or DNS name from the proxy bypass list.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  

## <a name="syntax"></a><span data-ttu-id="5c6e4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5c6e4-105">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5c6e4-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c6e4-106">Attributes and Elements</span></span>

<span data-ttu-id="5c6e4-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5c6e4-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5c6e4-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5c6e4-108">Attributes</span></span>

|<span data-ttu-id="5c6e4-109">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="5c6e4-109">**Attribute**</span></span>|<span data-ttu-id="5c6e4-110">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5c6e4-110">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="5c6e4-111">IP adresini veya DNS adını tanımlayan bir normal ifade.</span><span class="sxs-lookup"><span data-stu-id="5c6e4-111">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5c6e4-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c6e4-112">Child Elements</span></span>

<span data-ttu-id="5c6e4-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="5c6e4-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5c6e4-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c6e4-114">Parent Elements</span></span>

|<span data-ttu-id="5c6e4-115">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="5c6e4-115">**Element**</span></span>|<span data-ttu-id="5c6e4-116">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5c6e4-116">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="5c6e4-117">BypassList</span><span class="sxs-lookup"><span data-stu-id="5c6e4-117">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="5c6e4-118">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c6e4-118">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5c6e4-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c6e4-119">Remarks</span></span>

<span data-ttu-id="5c6e4-120">`remove`Öğesi, IP adreslerini veya DNS sunucusu adlarını tanımlayan normal ifadeleri bir proxy sunucusunu atlayan adresler listesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5c6e4-120">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="5c6e4-121">Adresler yapılandırma hiyerarşisinde daha önce veya yapılandırma hiyerarşisinde daha yüksek bir düzeyde tanımlandı.</span><span class="sxs-lookup"><span data-stu-id="5c6e4-121">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="5c6e4-122">`address`Özniteliğin değeri BIR IP adresi veya ana bilgisayar adı kümesini açıklayan bir normal ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5c6e4-122">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="5c6e4-123">Normal ifadeler hakkında daha fazla bilgi için bkz.. [Normal ifadeleri .NET Framework](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="5c6e4-123">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="5c6e4-124">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="5c6e4-124">Configuration Files</span></span>

<span data-ttu-id="5c6e4-125">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5c6e4-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="5c6e4-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c6e4-126">Example</span></span>

<span data-ttu-id="5c6e4-127">Aşağıdaki örnek, adventure-works.com etki alanı için önceki tüm tanımları kaldırır ve ardından contoso.com etki alanını atlama listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="5c6e4-127">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5c6e4-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c6e4-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="5c6e4-129">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="5c6e4-129">Network Settings Schema</span></span>](index.md)
