---
title: İş parçacığı yapılandırma ayarları
description: .NET Core uygulamaları için iş parçacığı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789848"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="86fa4-103">İş parçacığı için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="86fa4-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="86fa4-104">CPU grupları</span><span class="sxs-lookup"><span data-stu-id="86fa4-104">CPU groups</span></span>

- <span data-ttu-id="86fa4-105">İş parçacıklarının CPU grupları arasında otomatik olarak dağıtılıp dağıtılmayacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="86fa4-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="86fa4-106">Varsayılan: devre dışı (`0`).</span><span class="sxs-lookup"><span data-stu-id="86fa4-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="86fa4-107">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="86fa4-107">Setting name</span></span> | <span data-ttu-id="86fa4-108">Değerler</span><span class="sxs-lookup"><span data-stu-id="86fa4-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="86fa4-109">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="86fa4-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="86fa4-110">YOK</span><span class="sxs-lookup"><span data-stu-id="86fa4-110">N/A</span></span> | <span data-ttu-id="86fa4-111">YOK</span><span class="sxs-lookup"><span data-stu-id="86fa4-111">N/A</span></span> |
| <span data-ttu-id="86fa4-112">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="86fa4-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="86fa4-113">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="86fa4-113">`0` - disabled</span></span><br/><span data-ttu-id="86fa4-114">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="86fa4-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="86fa4-115">En düşük iş parçacıkları</span><span class="sxs-lookup"><span data-stu-id="86fa4-115">Minimum threads</span></span>

- <span data-ttu-id="86fa4-116">Çalışan iş parçacığı havuzu için en az iş parçacığı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="86fa4-116">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="86fa4-117"><xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> yöntemine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="86fa4-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="86fa4-118">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="86fa4-118">Setting name</span></span> | <span data-ttu-id="86fa4-119">Değerler</span><span class="sxs-lookup"><span data-stu-id="86fa4-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="86fa4-120">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="86fa4-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="86fa4-121">En az iş parçacığı sayısını temsil eden bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="86fa4-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="86fa4-122">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="86fa4-122">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="86fa4-123">En az iş parçacığı sayısını temsil eden bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="86fa4-123">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="86fa4-124">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="86fa4-124">**Environment variable**</span></span> | <span data-ttu-id="86fa4-125">YOK</span><span class="sxs-lookup"><span data-stu-id="86fa4-125">N/A</span></span> | <span data-ttu-id="86fa4-126">YOK</span><span class="sxs-lookup"><span data-stu-id="86fa4-126">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="86fa4-127">Örnekler</span><span class="sxs-lookup"><span data-stu-id="86fa4-127">Examples</span></span>

<span data-ttu-id="86fa4-128">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="86fa4-128">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="86fa4-129">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="86fa4-129">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="86fa4-130">En fazla iş parçacığı</span><span class="sxs-lookup"><span data-stu-id="86fa4-130">Maximum threads</span></span>

- <span data-ttu-id="86fa4-131">Çalışan iş parçacığı havuzu için en fazla iş parçacığı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="86fa4-131">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="86fa4-132"><xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> yöntemine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="86fa4-132">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="86fa4-133">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="86fa4-133">Setting name</span></span> | <span data-ttu-id="86fa4-134">Değerler</span><span class="sxs-lookup"><span data-stu-id="86fa4-134">Values</span></span> |
| - | - | - |
| <span data-ttu-id="86fa4-135">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="86fa4-135">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="86fa4-136">En fazla iş parçacığı sayısını temsil eden bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="86fa4-136">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="86fa4-137">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="86fa4-137">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="86fa4-138">En fazla iş parçacığı sayısını temsil eden bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="86fa4-138">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="86fa4-139">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="86fa4-139">**Environment variable**</span></span> | <span data-ttu-id="86fa4-140">YOK</span><span class="sxs-lookup"><span data-stu-id="86fa4-140">N/A</span></span> | <span data-ttu-id="86fa4-141">YOK</span><span class="sxs-lookup"><span data-stu-id="86fa4-141">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="86fa4-142">Örnekler</span><span class="sxs-lookup"><span data-stu-id="86fa4-142">Examples</span></span>

<span data-ttu-id="86fa4-143">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="86fa4-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="86fa4-144">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="86fa4-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
