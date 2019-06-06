---
title: <NetFx45_CultureAwareComparerGetHashCode_LongStrings> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23917977add2343732957eaa8dad5d2176315acf
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689868"
---
# <a name="netfx45cultureawarecomparergethashcodelongstrings-element"></a><span data-ttu-id="3550d-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings > öğesi</span><span class="sxs-lookup"><span data-stu-id="3550d-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>

<span data-ttu-id="3550d-103">Çalışma zamanı için karma kodları hesaplamak üzere sabit miktarda bellek kullanıp kullanmayacağını belirtir <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3550d-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="3550d-104">\<Yapılandırma > </span><span class="sxs-lookup"><span data-stu-id="3550d-104">\<configuration></span></span>\
<span data-ttu-id="3550d-105">\<çalışma zamanı > </span><span class="sxs-lookup"><span data-stu-id="3550d-105">\<runtime></span></span>\
<span data-ttu-id="3550d-106">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings ></span><span class="sxs-lookup"><span data-stu-id="3550d-106">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings></span></span>

## <a name="syntax"></a><span data-ttu-id="3550d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3550d-107">Syntax</span></span>

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3550d-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3550d-108">Attributes and Elements</span></span>

<span data-ttu-id="3550d-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3550d-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3550d-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3550d-110">Attributes</span></span>

|<span data-ttu-id="3550d-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3550d-111">Attribute</span></span>|<span data-ttu-id="3550d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3550d-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="3550d-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3550d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3550d-114">Ortak dil çalışma zamanının karma kodları hesaplarken sabit miktarda bellek ayırıp ayırmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3550d-114">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="3550d-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3550d-115">enabled Attribute</span></span>

|<span data-ttu-id="3550d-116">Değer</span><span class="sxs-lookup"><span data-stu-id="3550d-116">Value</span></span>|<span data-ttu-id="3550d-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3550d-117">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="3550d-118">0</span><span class="sxs-lookup"><span data-stu-id="3550d-118">0</span></span>|<span data-ttu-id="3550d-119">Ortak dil çalışma zamanı değişken miktarda bellek ayırır <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> karma kodları hesaplamak üzere yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3550d-119">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="3550d-120">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="3550d-120">This is the default.</span></span>|
|<span data-ttu-id="3550d-121">1.</span><span class="sxs-lookup"><span data-stu-id="3550d-121">1</span></span>|<span data-ttu-id="3550d-122">Ortak dil çalışma zamanı sabit miktarda bellek ayırır <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> karma kodları hesaplamak üzere yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3550d-122">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3550d-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3550d-123">Child Elements</span></span>

<span data-ttu-id="3550d-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="3550d-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3550d-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3550d-125">Parent Elements</span></span>

|<span data-ttu-id="3550d-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="3550d-126">Element</span></span>|<span data-ttu-id="3550d-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3550d-127">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="3550d-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3550d-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="3550d-129">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="3550d-129">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3550d-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3550d-130">Remarks</span></span>

<span data-ttu-id="3550d-131">Varsayılan olarak, ortak dil çalışma zamanı değişken miktarda bellek ayırır. <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi ve bir <xref:System.ArgumentException> yöntem çok büyük dizelerin karma kodunu (birkaç milyon karakterden uzun) hesaplamayı denediğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3550d-131">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="3550d-132">Bu öğe bir uygulama yapılandırma dosyası ve ayarı ekleyerek, `enabled` özniteliğini "1", şu belirtebilirsiniz <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi, karma kodları hesaplama için sabit miktarda bellek ayıran başka bir algoritma kullanın.</span><span class="sxs-lookup"><span data-stu-id="3550d-132">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3550d-133">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` Öğesi kullanılmaz [!INCLUDE[win8](../../../../../includes/win8-md.md)] ve sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="3550d-133">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in [!INCLUDE[win8](../../../../../includes/win8-md.md)] and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="3550d-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3550d-134">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3550d-135">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="3550d-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="3550d-136">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="3550d-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
