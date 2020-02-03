---
title: Derleme yapılandırması ayarları
description: JıT derleyicisinin .NET Core uygulamaları için nasıl çalıştığını yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 0dab3b7b7726a232cf293e338308cf898b370759
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733529"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="c0cbc-103">Derleme için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="c0cbc-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="c0cbc-104">Katmanlı derleme</span><span class="sxs-lookup"><span data-stu-id="c0cbc-104">Tiered compilation</span></span>

- <span data-ttu-id="c0cbc-105">Just-In-Time (JıT) derleyicisinin [katmanlı derlemeyi](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c0cbc-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="c0cbc-106">İki katmanda katmanlı derleme geçişleri yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="c0cbc-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="c0cbc-107">İlk katman kodu daha hızlı üretir ([hızlı JIT](#quick-jit)) veya önceden derlenmiş kod ([readytorun](../whats-new/dotnet-core-3-0.md#readytorun-images)) yükler.</span><span class="sxs-lookup"><span data-stu-id="c0cbc-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images)).</span></span>
  - <span data-ttu-id="c0cbc-108">İkinci katman arka planda iyileştirilmiş kod üretir ("JıT 'i iyileştirme").</span><span class="sxs-lookup"><span data-stu-id="c0cbc-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="c0cbc-109">.NET Core 3,0 ve üzeri sürümlerde katmanlı derleme varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="c0cbc-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="c0cbc-110">.NET Core 2,1 ve 2,2 ' de katmanlı derleme varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="c0cbc-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="c0cbc-111">Daha fazla bilgi için [katmanlı derleme Kılavuzu](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md)' na bakın.</span><span class="sxs-lookup"><span data-stu-id="c0cbc-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span></span>

| | <span data-ttu-id="c0cbc-112">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="c0cbc-112">Setting name</span></span> | <span data-ttu-id="c0cbc-113">Değerler</span><span class="sxs-lookup"><span data-stu-id="c0cbc-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c0cbc-114">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c0cbc-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="c0cbc-115">`true` etkin</span><span class="sxs-lookup"><span data-stu-id="c0cbc-115">`true` - enabled</span></span><br/><span data-ttu-id="c0cbc-116">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="c0cbc-116">`false` - disabled</span></span> |
| <span data-ttu-id="c0cbc-117">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="c0cbc-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="c0cbc-118">`true` etkin</span><span class="sxs-lookup"><span data-stu-id="c0cbc-118">`true` - enabled</span></span><br/><span data-ttu-id="c0cbc-119">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="c0cbc-119">`false` - disabled</span></span> |
| <span data-ttu-id="c0cbc-120">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="c0cbc-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="c0cbc-121">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="c0cbc-121">`1` - enabled</span></span><br/><span data-ttu-id="c0cbc-122">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="c0cbc-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="c0cbc-123">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c0cbc-123">Examples</span></span>

<span data-ttu-id="c0cbc-124">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="c0cbc-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="c0cbc-125">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="c0cbc-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="c0cbc-126">Hızlı JıT</span><span class="sxs-lookup"><span data-stu-id="c0cbc-126">Quick JIT</span></span>

- <span data-ttu-id="c0cbc-127">JıT derleyicisinin *hızlı JIT*kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c0cbc-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="c0cbc-128">Döngüler içermeyen ve önceden derlenmiş kodun kullanılamadığı yöntemler için, hızlı JıT bunları daha hızlı bir şekilde derler ancak iyileştirmelere gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="c0cbc-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="c0cbc-129">Hızlı JıT başlatma süresini azaltır, ancak performansı düşürülmüş performans özellikleriyle kod üretebilir.</span><span class="sxs-lookup"><span data-stu-id="c0cbc-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="c0cbc-130">Örneğin, kod daha fazla yığın alanı kullanabilir, daha fazla bellek ayırabilir ve daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="c0cbc-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="c0cbc-131">Hızlı JıT devre dışıysa ancak [katmanlı derleme](#tiered-compilation) etkinleştirilirse, yalnızca önceden derlenmiş kod katmanlı derlemeye katılır.</span><span class="sxs-lookup"><span data-stu-id="c0cbc-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="c0cbc-132">Bir yöntem [Readytorun](../whats-new/dotnet-core-3-0.md#readytorun-images)ile önceden DERLENMIŞSE, JIT davranışı [katmanlı derleme](#tiered-compilation) devre dışı bırakılmışsa aynı olur.</span><span class="sxs-lookup"><span data-stu-id="c0cbc-132">If a method is not pre-compiled with [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="c0cbc-133">.NET Core 3,0 ve üzeri sürümlerde, hızlı JıT varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="c0cbc-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="c0cbc-134">.NET Core 2,1 ve 2,2 ' de, hızlı JıT varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="c0cbc-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="c0cbc-135">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="c0cbc-135">Setting name</span></span> | <span data-ttu-id="c0cbc-136">Değerler</span><span class="sxs-lookup"><span data-stu-id="c0cbc-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c0cbc-137">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c0cbc-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="c0cbc-138">`true` etkin</span><span class="sxs-lookup"><span data-stu-id="c0cbc-138">`true` - enabled</span></span><br/><span data-ttu-id="c0cbc-139">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="c0cbc-139">`false` - disabled</span></span> |
| <span data-ttu-id="c0cbc-140">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="c0cbc-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="c0cbc-141">`true` etkin</span><span class="sxs-lookup"><span data-stu-id="c0cbc-141">`true` - enabled</span></span><br/><span data-ttu-id="c0cbc-142">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="c0cbc-142">`false` - disabled</span></span> |
| <span data-ttu-id="c0cbc-143">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="c0cbc-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="c0cbc-144">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="c0cbc-144">`1` - enabled</span></span><br/><span data-ttu-id="c0cbc-145">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="c0cbc-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="c0cbc-146">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c0cbc-146">Examples</span></span>

<span data-ttu-id="c0cbc-147">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="c0cbc-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="c0cbc-148">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="c0cbc-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="c0cbc-149">Döngüler için hızlı JıT</span><span class="sxs-lookup"><span data-stu-id="c0cbc-149">Quick JIT for loops</span></span>

- <span data-ttu-id="c0cbc-150">JıT derleyicisinin döngüleri içeren yöntemlerde hızlı JıT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c0cbc-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="c0cbc-151">Döngüler için hızlı JıT 'nin etkinleştirilmesi, başlangıç performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="c0cbc-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="c0cbc-152">Ancak uzun süreli döngüler, uzun süreler için daha az iyileştirilmiş kod ile takılmasına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="c0cbc-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="c0cbc-153">[Hızlı JIT](#quick-jit) devre dışıysa, bu ayarın etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c0cbc-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="c0cbc-154">Varsayılan: devre dışı (`false`).</span><span class="sxs-lookup"><span data-stu-id="c0cbc-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="c0cbc-155">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="c0cbc-155">Setting name</span></span> | <span data-ttu-id="c0cbc-156">Değerler</span><span class="sxs-lookup"><span data-stu-id="c0cbc-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c0cbc-157">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c0cbc-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="c0cbc-158">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="c0cbc-158">`false` - disabled</span></span><br/><span data-ttu-id="c0cbc-159">`true` etkin</span><span class="sxs-lookup"><span data-stu-id="c0cbc-159">`true` - enabled</span></span> |
| <span data-ttu-id="c0cbc-160">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="c0cbc-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="c0cbc-161">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="c0cbc-161">`false` - disabled</span></span><br/><span data-ttu-id="c0cbc-162">`true` etkin</span><span class="sxs-lookup"><span data-stu-id="c0cbc-162">`true` - enabled</span></span> |
| <span data-ttu-id="c0cbc-163">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="c0cbc-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="c0cbc-164">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="c0cbc-164">`0` - disabled</span></span><br/><span data-ttu-id="c0cbc-165">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="c0cbc-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="c0cbc-166">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c0cbc-166">Examples</span></span>

<span data-ttu-id="c0cbc-167">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="c0cbc-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="c0cbc-168">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="c0cbc-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```
