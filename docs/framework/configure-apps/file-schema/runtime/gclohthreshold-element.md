---
title: GCLOHThreshold element
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451222"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="acb20-102">GCLOHThreshold element</span><span class="sxs-lookup"><span data-stu-id="acb20-102">GCLOHThreshold element</span></span>

<span data-ttu-id="acb20-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span><span class="sxs-lookup"><span data-stu-id="acb20-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

<span data-ttu-id="acb20-104">[\<configuration>](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="acb20-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="acb20-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="acb20-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="acb20-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold></span><span class="sxs-lookup"><span data-stu-id="acb20-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold></span></span>

## <a name="syntax"></a><span data-ttu-id="acb20-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="acb20-107">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="acb20-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="acb20-108">Attributes</span></span>

|<span data-ttu-id="acb20-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="acb20-109">Attribute</span></span>|<span data-ttu-id="acb20-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="acb20-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="acb20-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="acb20-111">Required attribute.</span></span><br /><br /><span data-ttu-id="acb20-112">Specifies the threshold size that causes objects to go on the large object heap.</span><span class="sxs-lookup"><span data-stu-id="acb20-112">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="acb20-113">enabled attribute</span><span class="sxs-lookup"><span data-stu-id="acb20-113">enabled attribute</span></span>

|<span data-ttu-id="acb20-114">Değer</span><span class="sxs-lookup"><span data-stu-id="acb20-114">Value</span></span>|<span data-ttu-id="acb20-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="acb20-115">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="acb20-116">The threshold size, in bytes, that causes objects to go on the large object heap.</span><span class="sxs-lookup"><span data-stu-id="acb20-116">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="acb20-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="acb20-117">Child elements</span></span>

<span data-ttu-id="acb20-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="acb20-118">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="acb20-119">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="acb20-119">Parent elements</span></span>

|<span data-ttu-id="acb20-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="acb20-120">Element</span></span>|<span data-ttu-id="acb20-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="acb20-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="acb20-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="acb20-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="acb20-123">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="acb20-123">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="acb20-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="acb20-124">Remarks</span></span>

<span data-ttu-id="acb20-125">This setting was introduced in .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="acb20-125">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="acb20-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acb20-126">See also</span></span>

- [<span data-ttu-id="acb20-127">Run-time settings schema</span><span class="sxs-lookup"><span data-stu-id="acb20-127">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="acb20-128">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="acb20-128">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="acb20-129">Fundamentals of garbage collection</span><span class="sxs-lookup"><span data-stu-id="acb20-129">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="acb20-130">NET Core run-time config options for GC</span><span class="sxs-lookup"><span data-stu-id="acb20-130">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)
