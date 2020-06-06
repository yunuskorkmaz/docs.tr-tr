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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74802117"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a><span data-ttu-id="e83b3-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Öğesi</span><span class="sxs-lookup"><span data-stu-id="e83b3-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>

<span data-ttu-id="e83b3-103">Çalışma zamanının, yöntemin karma kodlarını hesaplamak için sabit miktarda bellek kullanıp kullanmadığını belirtir <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e83b3-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>**  

## <a name="syntax"></a><span data-ttu-id="e83b3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e83b3-104">Syntax</span></span>

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e83b3-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e83b3-105">Attributes and Elements</span></span>

<span data-ttu-id="e83b3-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e83b3-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e83b3-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e83b3-107">Attributes</span></span>

|<span data-ttu-id="e83b3-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e83b3-108">Attribute</span></span>|<span data-ttu-id="e83b3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e83b3-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="e83b3-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e83b3-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="e83b3-111">Ortak dil çalışma zamanının karma kodları hesaplarken sabit miktarda bellek ayırıp ayırmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e83b3-111">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="e83b3-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e83b3-112">enabled Attribute</span></span>

|<span data-ttu-id="e83b3-113">Değer</span><span class="sxs-lookup"><span data-stu-id="e83b3-113">Value</span></span>|<span data-ttu-id="e83b3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e83b3-114">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="e83b3-115">0</span><span class="sxs-lookup"><span data-stu-id="e83b3-115">0</span></span>|<span data-ttu-id="e83b3-116">Ortak dil çalışma zamanı, <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> karma kodları hesaplamak için yöntemi için değişken miktarda bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="e83b3-116">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="e83b3-117">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="e83b3-117">This is the default.</span></span>|
|<span data-ttu-id="e83b3-118">1</span><span class="sxs-lookup"><span data-stu-id="e83b3-118">1</span></span>|<span data-ttu-id="e83b3-119">Ortak dil çalışma zamanı, <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> karma kodları hesaplamak için yöntemi için sabit miktarda bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="e83b3-119">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e83b3-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e83b3-120">Child Elements</span></span>

<span data-ttu-id="e83b3-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="e83b3-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e83b3-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e83b3-122">Parent Elements</span></span>

|<span data-ttu-id="e83b3-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="e83b3-123">Element</span></span>|<span data-ttu-id="e83b3-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e83b3-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="e83b3-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e83b3-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="e83b3-126">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e83b3-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e83b3-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e83b3-127">Remarks</span></span>

<span data-ttu-id="e83b3-128">Varsayılan olarak, ortak dil çalışma zamanı yöntemi için değişken miktarda bellek ayırır <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> ve <xref:System.ArgumentException> yöntemi çok büyük dizelerin karma kodunu (birkaç milyon karakter uzunluğunda) hesaplamaya çalıştığında oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="e83b3-128">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="e83b3-129">Bu öğeyi bir uygulama yapılandırma dosyasına ekleyerek ve `enabled` özniteliğini "1" olarak ayarlayarak, <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemin karma kodların hesaplaması için sabit miktarda bellek ayıran alternatif bir algoritma kullanmasını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e83b3-129">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e83b3-130">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>`Öğesi, Windows 8 ve sonraki sürümlerde kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="e83b3-130">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in Windows 8 and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="e83b3-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e83b3-131">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e83b3-132">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="e83b3-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e83b3-133">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="e83b3-133">Configuration File Schema</span></span>](../index.md)
