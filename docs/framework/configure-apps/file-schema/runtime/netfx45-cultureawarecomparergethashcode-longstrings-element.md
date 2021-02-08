---
description: 'Hakkında daha fazla bilgi edinin: <NetFx45_CultureAwareComparerGetHashCode_LongStrings> öğesi'
title: <NetFx45_CultureAwareComparerGetHashCode_LongStrings> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: ca4099d3bf812cb25e6a611b9b51b3752b1ad361
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782292"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a><span data-ttu-id="11d56-103">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Öğesi</span><span class="sxs-lookup"><span data-stu-id="11d56-103">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>

<span data-ttu-id="11d56-104">Çalışma zamanının, yöntemin karma kodlarını hesaplamak için sabit miktarda bellek kullanıp kullanmadığını belirtir <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="11d56-104">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>**  

## <a name="syntax"></a><span data-ttu-id="11d56-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="11d56-105">Syntax</span></span>

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11d56-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="11d56-106">Attributes and Elements</span></span>

<span data-ttu-id="11d56-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="11d56-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="11d56-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="11d56-108">Attributes</span></span>

|<span data-ttu-id="11d56-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="11d56-109">Attribute</span></span>|<span data-ttu-id="11d56-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11d56-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="11d56-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="11d56-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="11d56-112">Ortak dil çalışma zamanının karma kodları hesaplarken sabit miktarda bellek ayırıp ayırmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="11d56-112">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="11d56-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="11d56-113">enabled Attribute</span></span>

|<span data-ttu-id="11d56-114">Değer</span><span class="sxs-lookup"><span data-stu-id="11d56-114">Value</span></span>|<span data-ttu-id="11d56-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11d56-115">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="11d56-116">0</span><span class="sxs-lookup"><span data-stu-id="11d56-116">0</span></span>|<span data-ttu-id="11d56-117">Ortak dil çalışma zamanı, <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> karma kodları hesaplamak için yöntemi için değişken miktarda bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="11d56-117">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="11d56-118">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="11d56-118">This is the default.</span></span>|
|<span data-ttu-id="11d56-119">1</span><span class="sxs-lookup"><span data-stu-id="11d56-119">1</span></span>|<span data-ttu-id="11d56-120">Ortak dil çalışma zamanı, <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> karma kodları hesaplamak için yöntemi için sabit miktarda bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="11d56-120">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="11d56-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="11d56-121">Child Elements</span></span>

<span data-ttu-id="11d56-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="11d56-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="11d56-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="11d56-123">Parent Elements</span></span>

|<span data-ttu-id="11d56-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="11d56-124">Element</span></span>|<span data-ttu-id="11d56-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11d56-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="11d56-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="11d56-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="11d56-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="11d56-127">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="11d56-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11d56-128">Remarks</span></span>

<span data-ttu-id="11d56-129">Varsayılan olarak, ortak dil çalışma zamanı yöntemi için değişken miktarda bellek ayırır <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> ve <xref:System.ArgumentException> yöntemi çok büyük dizelerin karma kodunu (birkaç milyon karakter uzunluğunda) hesaplamaya çalıştığında oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="11d56-129">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="11d56-130">Bu öğeyi bir uygulama yapılandırma dosyasına ekleyerek ve `enabled` özniteliğini "1" olarak ayarlayarak, <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemin karma kodların hesaplaması için sabit miktarda bellek ayıran alternatif bir algoritma kullanmasını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11d56-130">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="11d56-131">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>`Öğesi, Windows 8 ve sonraki sürümlerde kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="11d56-131">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in Windows 8 and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="11d56-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11d56-132">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="11d56-133">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="11d56-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="11d56-134">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="11d56-134">Configuration File Schema</span></span>](../index.md)
