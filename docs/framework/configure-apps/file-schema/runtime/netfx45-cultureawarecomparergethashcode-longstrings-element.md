---
title: <NetFx45_CultureAwareComparerGetHashCode_LongStrings> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: 413eb6c6e61b509135601c65cf045eabd849e8b3
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802117"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a><span data-ttu-id="cd1e2-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings > öğesi</span><span class="sxs-lookup"><span data-stu-id="cd1e2-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>

<span data-ttu-id="cd1e2-103">Çalışma zamanının <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi için karma kodları hesaplamak üzere sabit miktarda bellek kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd1e2-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="cd1e2-104">[ **\<yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cd1e2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cd1e2-105">&nbsp;&nbsp;[ **\<çalışma zamanı >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="cd1e2-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="cd1e2-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<NetFx45_CultureAwareComparerGetHashCode_LongStrings >**</span><span class="sxs-lookup"><span data-stu-id="cd1e2-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="cd1e2-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd1e2-107">Syntax</span></span>

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cd1e2-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd1e2-108">Attributes and Elements</span></span>

<span data-ttu-id="cd1e2-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cd1e2-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cd1e2-110">{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="cd1e2-110">Attributes</span></span>

|<span data-ttu-id="cd1e2-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cd1e2-111">Attribute</span></span>|<span data-ttu-id="cd1e2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd1e2-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="cd1e2-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="cd1e2-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="cd1e2-114">Ortak dil çalışma zamanının karma kodları hesaplarken sabit miktarda bellek ayırıp ayırmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd1e2-114">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="cd1e2-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cd1e2-115">enabled Attribute</span></span>

|<span data-ttu-id="cd1e2-116">Değer</span><span class="sxs-lookup"><span data-stu-id="cd1e2-116">Value</span></span>|<span data-ttu-id="cd1e2-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd1e2-117">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="cd1e2-118">0</span><span class="sxs-lookup"><span data-stu-id="cd1e2-118">0</span></span>|<span data-ttu-id="cd1e2-119">Ortak dil çalışma zamanı, karma kodları hesaplamak için <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi için değişken miktarda bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="cd1e2-119">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="cd1e2-120">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="cd1e2-120">This is the default.</span></span>|
|<span data-ttu-id="cd1e2-121">1\.</span><span class="sxs-lookup"><span data-stu-id="cd1e2-121">1</span></span>|<span data-ttu-id="cd1e2-122">Ortak dil çalışma zamanı, karma kodları hesaplamak için <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi için sabit miktarda bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="cd1e2-122">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="cd1e2-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd1e2-123">Child Elements</span></span>

<span data-ttu-id="cd1e2-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="cd1e2-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cd1e2-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd1e2-125">Parent Elements</span></span>

|<span data-ttu-id="cd1e2-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="cd1e2-126">Element</span></span>|<span data-ttu-id="cd1e2-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd1e2-127">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="cd1e2-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="cd1e2-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="cd1e2-129">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="cd1e2-129">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cd1e2-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd1e2-130">Remarks</span></span>

<span data-ttu-id="cd1e2-131">Varsayılan olarak, ortak dil çalışma zamanı <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi için değişken miktarda bellek ayırır ve yöntem çok büyük dizelerin karma kodunu (birkaç milyon karakter uzunluğunda) hesaplamaya çalıştığında bir <xref:System.ArgumentException> oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="cd1e2-131">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="cd1e2-132">Bu öğeyi bir uygulama yapılandırma dosyasına ekleyip `enabled` özniteliğini "1" olarak ayarlayarak, <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yönteminin karma kodların hesaplaması için sabit miktarda bellek ayıran alternatif bir algoritma kullanmasını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd1e2-132">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cd1e2-133">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` öğesi Windows 8 ve sonraki sürümlerde kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="cd1e2-133">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in Windows 8 and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd1e2-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd1e2-134">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="cd1e2-135">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="cd1e2-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cd1e2-136">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="cd1e2-136">Configuration File Schema</span></span>](../index.md)
