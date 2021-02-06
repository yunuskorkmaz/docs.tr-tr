---
description: 'Daha fazla bilgi edinin: GCLOHThreshold öğesi'
title: GCLOHThreshold öğesi
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: 5d4ef4e6aaf44642c2307dc27ac2e99e966d3ad0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652815"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="4948e-103">GCLOHThreshold öğesi</span><span class="sxs-lookup"><span data-stu-id="4948e-103">GCLOHThreshold element</span></span>

<span data-ttu-id="4948e-104">Çöp toplayıcısının nesneleri büyük nesne yığınına (LOH) yerleştirmesine neden olan eşik boyutunu bayt cinsinden belirtir.</span><span class="sxs-lookup"><span data-stu-id="4948e-104">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold>

## <a name="syntax"></a><span data-ttu-id="4948e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4948e-105">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="4948e-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4948e-106">Attributes</span></span>

|<span data-ttu-id="4948e-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4948e-107">Attribute</span></span>|<span data-ttu-id="4948e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4948e-108">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="4948e-109">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4948e-109">Required attribute.</span></span><br /><br /><span data-ttu-id="4948e-110">Nesnelerin büyük nesne yığınında geçmesine neden olan eşik boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4948e-110">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="4948e-111">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="4948e-111">enabled attribute</span></span>

|<span data-ttu-id="4948e-112">Değer</span><span class="sxs-lookup"><span data-stu-id="4948e-112">Value</span></span>|<span data-ttu-id="4948e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4948e-113">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="4948e-114">Büyük nesne yığınında nesnelerin gitmesini sağlayan bayt cinsinden eşik boyutu.</span><span class="sxs-lookup"><span data-stu-id="4948e-114">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="4948e-115">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="4948e-115">Child elements</span></span>

<span data-ttu-id="4948e-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="4948e-116">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="4948e-117">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="4948e-117">Parent elements</span></span>

|<span data-ttu-id="4948e-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="4948e-118">Element</span></span>|<span data-ttu-id="4948e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4948e-119">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="4948e-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4948e-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="4948e-121">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4948e-121">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4948e-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4948e-122">Remarks</span></span>

<span data-ttu-id="4948e-123">Bu ayar .NET Framework 4,8 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="4948e-123">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="4948e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4948e-124">See also</span></span>

- [<span data-ttu-id="4948e-125">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="4948e-125">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="4948e-126">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="4948e-126">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="4948e-127">Çöp toplamanın temelleri</span><span class="sxs-lookup"><span data-stu-id="4948e-127">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="4948e-128">GC için NET Core çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="4948e-128">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)
