---
title: GCLOHThreshold öğesi
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74451222"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="eac67-102">GCLOHThreshold öğesi</span><span class="sxs-lookup"><span data-stu-id="eac67-102">GCLOHThreshold element</span></span>

<span data-ttu-id="eac67-103">Çöp toplayıcısının nesneleri büyük nesne yığınına (LOH) yerleştirmesine neden olan eşik boyutunu bayt cinsinden belirtir.</span><span class="sxs-lookup"><span data-stu-id="eac67-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold>

## <a name="syntax"></a><span data-ttu-id="eac67-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eac67-104">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="eac67-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="eac67-105">Attributes</span></span>

|<span data-ttu-id="eac67-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="eac67-106">Attribute</span></span>|<span data-ttu-id="eac67-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eac67-107">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="eac67-108">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="eac67-108">Required attribute.</span></span><br /><br /><span data-ttu-id="eac67-109">Nesnelerin büyük nesne yığınında geçmesine neden olan eşik boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="eac67-109">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="eac67-110">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="eac67-110">enabled attribute</span></span>

|<span data-ttu-id="eac67-111">Değer</span><span class="sxs-lookup"><span data-stu-id="eac67-111">Value</span></span>|<span data-ttu-id="eac67-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eac67-112">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="eac67-113">Büyük nesne yığınında nesnelerin gitmesini sağlayan bayt cinsinden eşik boyutu.</span><span class="sxs-lookup"><span data-stu-id="eac67-113">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="eac67-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="eac67-114">Child elements</span></span>

<span data-ttu-id="eac67-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="eac67-115">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="eac67-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="eac67-116">Parent elements</span></span>

|<span data-ttu-id="eac67-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="eac67-117">Element</span></span>|<span data-ttu-id="eac67-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eac67-118">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="eac67-119">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="eac67-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="eac67-120">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="eac67-120">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="eac67-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eac67-121">Remarks</span></span>

<span data-ttu-id="eac67-122">Bu ayar .NET Framework 4,8 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="eac67-122">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="eac67-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eac67-123">See also</span></span>

- [<span data-ttu-id="eac67-124">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="eac67-124">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="eac67-125">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="eac67-125">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="eac67-126">Çöp toplamanın temelleri</span><span class="sxs-lookup"><span data-stu-id="eac67-126">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="eac67-127">GC için NET Core çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="eac67-127">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)
