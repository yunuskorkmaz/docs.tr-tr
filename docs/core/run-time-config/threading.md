---
title: İş parçacığı yapılandırma ayarları
description: .NET Core uygulamaları için iş parçacığı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 1c7c16993a07ef95223481791153b75ab2f61533
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761934"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="6a580-103">İş parçacığı için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6a580-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="6a580-104">CPU grupları</span><span class="sxs-lookup"><span data-stu-id="6a580-104">CPU groups</span></span>

- <span data-ttu-id="6a580-105">İş parçacıklarının CPU grupları arasında otomatik olarak dağıtılıp dağıtılmayacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="6a580-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="6a580-106">Bu ayarı atlarsanız, iş parçacıkları CPU grupları arasında dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="6a580-106">If you omit this setting, threads are not distributed across CPU groups.</span></span> <span data-ttu-id="6a580-107">Bu değeri değerine ayarlamaya eşdeğerdir `0` .</span><span class="sxs-lookup"><span data-stu-id="6a580-107">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="6a580-108">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="6a580-108">Setting name</span></span> | <span data-ttu-id="6a580-109">Değerler</span><span class="sxs-lookup"><span data-stu-id="6a580-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="6a580-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6a580-110">**runtimeconfig.json**</span></span> | <span data-ttu-id="6a580-111">Yok</span><span class="sxs-lookup"><span data-stu-id="6a580-111">N/A</span></span> | <span data-ttu-id="6a580-112">Yok</span><span class="sxs-lookup"><span data-stu-id="6a580-112">N/A</span></span> |
| <span data-ttu-id="6a580-113">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="6a580-113">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="6a580-114">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="6a580-114">`0` - disabled</span></span><br/><span data-ttu-id="6a580-115">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="6a580-115">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="6a580-116">En düşük iş parçacıkları</span><span class="sxs-lookup"><span data-stu-id="6a580-116">Minimum threads</span></span>

- <span data-ttu-id="6a580-117">Çalışan iş parçacığı havuzu için en az iş parçacığı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a580-117">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="6a580-118">Yöntemine karşılık gelir <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6a580-118">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="6a580-119">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="6a580-119">Setting name</span></span> | <span data-ttu-id="6a580-120">Değerler</span><span class="sxs-lookup"><span data-stu-id="6a580-120">Values</span></span> |
| - | - | - |
| <span data-ttu-id="6a580-121">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6a580-121">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="6a580-122">En az iş parçacığı sayısını temsil eden bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="6a580-122">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="6a580-123">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="6a580-123">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="6a580-124">En az iş parçacığı sayısını temsil eden bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="6a580-124">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="6a580-125">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="6a580-125">**Environment variable**</span></span> | <span data-ttu-id="6a580-126">Yok</span><span class="sxs-lookup"><span data-stu-id="6a580-126">N/A</span></span> | <span data-ttu-id="6a580-127">Yok</span><span class="sxs-lookup"><span data-stu-id="6a580-127">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="6a580-128">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6a580-128">Examples</span></span>

<span data-ttu-id="6a580-129">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="6a580-129">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="6a580-130">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="6a580-130">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="6a580-131">En fazla iş parçacığı</span><span class="sxs-lookup"><span data-stu-id="6a580-131">Maximum threads</span></span>

- <span data-ttu-id="6a580-132">Çalışan iş parçacığı havuzu için en fazla iş parçacığı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a580-132">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="6a580-133">Yöntemine karşılık gelir <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6a580-133">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="6a580-134">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="6a580-134">Setting name</span></span> | <span data-ttu-id="6a580-135">Değerler</span><span class="sxs-lookup"><span data-stu-id="6a580-135">Values</span></span> |
| - | - | - |
| <span data-ttu-id="6a580-136">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6a580-136">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="6a580-137">En fazla iş parçacığı sayısını temsil eden bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="6a580-137">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="6a580-138">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="6a580-138">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="6a580-139">En fazla iş parçacığı sayısını temsil eden bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="6a580-139">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="6a580-140">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="6a580-140">**Environment variable**</span></span> | <span data-ttu-id="6a580-141">Yok</span><span class="sxs-lookup"><span data-stu-id="6a580-141">N/A</span></span> | <span data-ttu-id="6a580-142">Yok</span><span class="sxs-lookup"><span data-stu-id="6a580-142">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="6a580-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6a580-143">Examples</span></span>

<span data-ttu-id="6a580-144">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="6a580-144">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="6a580-145">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="6a580-145">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
