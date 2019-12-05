---
title: İş parçacığı yapılandırma ayarları
description: .NET Core uygulamaları için iş parçacığı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 6a920dbc301830e3f4c95bf637ff3de6d4f464ff
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802766"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="e443d-103">İş parçacığı için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e443d-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="e443d-104">CPU grupları</span><span class="sxs-lookup"><span data-stu-id="e443d-104">CPU groups</span></span>

- <span data-ttu-id="e443d-105">İş parçacıklarının CPU grupları arasında otomatik olarak dağıtılıp dağıtılmayacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e443d-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="e443d-106">Varsayılan: devre dışı (`0`).</span><span class="sxs-lookup"><span data-stu-id="e443d-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="e443d-107">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="e443d-107">Setting name</span></span> | <span data-ttu-id="e443d-108">Değerler</span><span class="sxs-lookup"><span data-stu-id="e443d-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="e443d-109">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e443d-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="e443d-110">YOK</span><span class="sxs-lookup"><span data-stu-id="e443d-110">N/A</span></span> | <span data-ttu-id="e443d-111">YOK</span><span class="sxs-lookup"><span data-stu-id="e443d-111">N/A</span></span> |
| <span data-ttu-id="e443d-112">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="e443d-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="e443d-113">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="e443d-113">`0` - disabled</span></span><br/><span data-ttu-id="e443d-114">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="e443d-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="e443d-115">En düşük iş parçacıkları</span><span class="sxs-lookup"><span data-stu-id="e443d-115">Minimum threads</span></span>

- <span data-ttu-id="e443d-116">Çalışan ThreadPool için en az iş parçacığı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e443d-116">Specifies the minimum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="e443d-117"><xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> yöntemine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="e443d-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="e443d-118">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="e443d-118">Setting name</span></span> | <span data-ttu-id="e443d-119">Değerler</span><span class="sxs-lookup"><span data-stu-id="e443d-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="e443d-120">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e443d-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="e443d-121">En az iş parçacığı sayısını temsil eden bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="e443d-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="e443d-122">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="e443d-122">**Environment variable**</span></span> | <span data-ttu-id="e443d-123">YOK</span><span class="sxs-lookup"><span data-stu-id="e443d-123">N/A</span></span> | <span data-ttu-id="e443d-124">YOK</span><span class="sxs-lookup"><span data-stu-id="e443d-124">N/A</span></span> |

## <a name="maximum-threads"></a><span data-ttu-id="e443d-125">En fazla iş parçacığı</span><span class="sxs-lookup"><span data-stu-id="e443d-125">Maximum threads</span></span>

- <span data-ttu-id="e443d-126">Çalışan ThreadPool için en fazla iş parçacığı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e443d-126">Specifies the maximum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="e443d-127"><xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> yöntemine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="e443d-127">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="e443d-128">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="e443d-128">Setting name</span></span> | <span data-ttu-id="e443d-129">Değerler</span><span class="sxs-lookup"><span data-stu-id="e443d-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="e443d-130">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e443d-130">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="e443d-131">En fazla iş parçacığı sayısını temsil eden bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="e443d-131">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="e443d-132">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="e443d-132">**Environment variable**</span></span> | <span data-ttu-id="e443d-133">YOK</span><span class="sxs-lookup"><span data-stu-id="e443d-133">N/A</span></span> | <span data-ttu-id="e443d-134">YOK</span><span class="sxs-lookup"><span data-stu-id="e443d-134">N/A</span></span> |
