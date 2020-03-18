---
title: Config ayarlarını iş parçacığı
description: .NET Core uygulamaları için iş parçacığı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789848"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="39faf-103">İş parçacığı için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="39faf-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="39faf-104">CPU grupları</span><span class="sxs-lookup"><span data-stu-id="39faf-104">CPU groups</span></span>

- <span data-ttu-id="39faf-105">İş parçacıklarının CPU gruplarına otomatik olarak dağıtılıp dağıtılmayacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="39faf-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="39faf-106">Varsayılan: Devre`0`Dışı ( ).</span><span class="sxs-lookup"><span data-stu-id="39faf-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="39faf-107">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="39faf-107">Setting name</span></span> | <span data-ttu-id="39faf-108">Değerler</span><span class="sxs-lookup"><span data-stu-id="39faf-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="39faf-109">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="39faf-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="39faf-110">Yok</span><span class="sxs-lookup"><span data-stu-id="39faf-110">N/A</span></span> | <span data-ttu-id="39faf-111">Yok</span><span class="sxs-lookup"><span data-stu-id="39faf-111">N/A</span></span> |
| <span data-ttu-id="39faf-112">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="39faf-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="39faf-113">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="39faf-113">`0` - disabled</span></span><br/><span data-ttu-id="39faf-114">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="39faf-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="39faf-115">Minimum iş parçacıkları</span><span class="sxs-lookup"><span data-stu-id="39faf-115">Minimum threads</span></span>

- <span data-ttu-id="39faf-116">Alt iş parçacığı havuzu için en az iş parçacığı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39faf-116">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="39faf-117">Yönteme <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="39faf-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="39faf-118">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="39faf-118">Setting name</span></span> | <span data-ttu-id="39faf-119">Değerler</span><span class="sxs-lookup"><span data-stu-id="39faf-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="39faf-120">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="39faf-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="39faf-121">En az iş parçacığı sayısını temsil eden bir karşıcı</span><span class="sxs-lookup"><span data-stu-id="39faf-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="39faf-122">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="39faf-122">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="39faf-123">En az iş parçacığı sayısını temsil eden bir karşıcı</span><span class="sxs-lookup"><span data-stu-id="39faf-123">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="39faf-124">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="39faf-124">**Environment variable**</span></span> | <span data-ttu-id="39faf-125">Yok</span><span class="sxs-lookup"><span data-stu-id="39faf-125">N/A</span></span> | <span data-ttu-id="39faf-126">Yok</span><span class="sxs-lookup"><span data-stu-id="39faf-126">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="39faf-127">Örnekler</span><span class="sxs-lookup"><span data-stu-id="39faf-127">Examples</span></span>

<span data-ttu-id="39faf-128">*runtimeconfig.json* dosyası:</span><span class="sxs-lookup"><span data-stu-id="39faf-128">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="39faf-129">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="39faf-129">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="39faf-130">Maksimum iş parçacıkları</span><span class="sxs-lookup"><span data-stu-id="39faf-130">Maximum threads</span></span>

- <span data-ttu-id="39faf-131">Alt iş parçacığı havuzu için en fazla iş parçacığı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39faf-131">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="39faf-132">Yönteme <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="39faf-132">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="39faf-133">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="39faf-133">Setting name</span></span> | <span data-ttu-id="39faf-134">Değerler</span><span class="sxs-lookup"><span data-stu-id="39faf-134">Values</span></span> |
| - | - | - |
| <span data-ttu-id="39faf-135">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="39faf-135">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="39faf-136">En fazla iş parçacığı sayısını temsil eden bir sonsayı</span><span class="sxs-lookup"><span data-stu-id="39faf-136">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="39faf-137">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="39faf-137">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="39faf-138">En fazla iş parçacığı sayısını temsil eden bir sonsayı</span><span class="sxs-lookup"><span data-stu-id="39faf-138">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="39faf-139">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="39faf-139">**Environment variable**</span></span> | <span data-ttu-id="39faf-140">Yok</span><span class="sxs-lookup"><span data-stu-id="39faf-140">N/A</span></span> | <span data-ttu-id="39faf-141">Yok</span><span class="sxs-lookup"><span data-stu-id="39faf-141">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="39faf-142">Örnekler</span><span class="sxs-lookup"><span data-stu-id="39faf-142">Examples</span></span>

<span data-ttu-id="39faf-143">*runtimeconfig.json* dosyası:</span><span class="sxs-lookup"><span data-stu-id="39faf-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="39faf-144">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="39faf-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
