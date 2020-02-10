---
title: Derleme yapılandırması ayarları
description: JıT derleyicisinin .NET Core uygulamaları için nasıl çalıştığını yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: adf1f01dba7387b89ee56784e33653d6a132c0e3
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092895"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="90e23-103">Derleme için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="90e23-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="90e23-104">Katmanlı derleme</span><span class="sxs-lookup"><span data-stu-id="90e23-104">Tiered compilation</span></span>

- <span data-ttu-id="90e23-105">Just-In-Time (JıT) derleyicisinin [katmanlı derlemeyi](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="90e23-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="90e23-106">İki katmanda katmanlı derleme geçişleri yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="90e23-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="90e23-107">İlk katman kodu daha hızlı üretir ([hızlı JIT](#quick-jit)) veya önceden derlenmiş kod ([readytorun](#readytorun)) yükler.</span><span class="sxs-lookup"><span data-stu-id="90e23-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="90e23-108">İkinci katman arka planda iyileştirilmiş kod üretir ("JıT 'i iyileştirme").</span><span class="sxs-lookup"><span data-stu-id="90e23-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="90e23-109">.NET Core 3,0 ve üzeri sürümlerde katmanlı derleme varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="90e23-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="90e23-110">.NET Core 2,1 ve 2,2 ' de katmanlı derleme varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="90e23-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="90e23-111">Daha fazla bilgi için [katmanlı derleme Kılavuzu](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md)' na bakın.</span><span class="sxs-lookup"><span data-stu-id="90e23-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span></span>

| | <span data-ttu-id="90e23-112">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="90e23-112">Setting name</span></span> | <span data-ttu-id="90e23-113">Değerler</span><span class="sxs-lookup"><span data-stu-id="90e23-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="90e23-114">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="90e23-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="90e23-115">`true` etkin</span><span class="sxs-lookup"><span data-stu-id="90e23-115">`true` - enabled</span></span><br/><span data-ttu-id="90e23-116">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="90e23-116">`false` - disabled</span></span> |
| <span data-ttu-id="90e23-117">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="90e23-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="90e23-118">`true` etkin</span><span class="sxs-lookup"><span data-stu-id="90e23-118">`true` - enabled</span></span><br/><span data-ttu-id="90e23-119">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="90e23-119">`false` - disabled</span></span> |
| <span data-ttu-id="90e23-120">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="90e23-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="90e23-121">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="90e23-121">`1` - enabled</span></span><br/><span data-ttu-id="90e23-122">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="90e23-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="90e23-123">Örnekler</span><span class="sxs-lookup"><span data-stu-id="90e23-123">Examples</span></span>

<span data-ttu-id="90e23-124">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="90e23-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="90e23-125">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="90e23-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="90e23-126">Hızlı JıT</span><span class="sxs-lookup"><span data-stu-id="90e23-126">Quick JIT</span></span>

- <span data-ttu-id="90e23-127">JıT derleyicisinin *hızlı JIT*kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="90e23-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="90e23-128">Döngüler içermeyen ve önceden derlenmiş kodun kullanılamadığı yöntemler için, hızlı JıT bunları daha hızlı bir şekilde derler ancak iyileştirmelere gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="90e23-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="90e23-129">Hızlı JıT başlatma süresini azaltır, ancak performansı düşürülmüş performans özellikleriyle kod üretebilir.</span><span class="sxs-lookup"><span data-stu-id="90e23-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="90e23-130">Örneğin, kod daha fazla yığın alanı kullanabilir, daha fazla bellek ayırabilir ve daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="90e23-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="90e23-131">Hızlı JıT devre dışıysa ancak [katmanlı derleme](#tiered-compilation) etkinleştirilirse, yalnızca önceden derlenmiş kod katmanlı derlemeye katılır.</span><span class="sxs-lookup"><span data-stu-id="90e23-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="90e23-132">Bir yöntem [Readytorun](#readytorun)ile önceden DERLENMIŞSE, JIT davranışı [katmanlı derleme](#tiered-compilation) devre dışı bırakılmışsa aynı olur.</span><span class="sxs-lookup"><span data-stu-id="90e23-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="90e23-133">.NET Core 3,0 ve üzeri sürümlerde, hızlı JıT varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="90e23-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="90e23-134">.NET Core 2,1 ve 2,2 ' de, hızlı JıT varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="90e23-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="90e23-135">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="90e23-135">Setting name</span></span> | <span data-ttu-id="90e23-136">Değerler</span><span class="sxs-lookup"><span data-stu-id="90e23-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="90e23-137">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="90e23-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="90e23-138">`true` etkin</span><span class="sxs-lookup"><span data-stu-id="90e23-138">`true` - enabled</span></span><br/><span data-ttu-id="90e23-139">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="90e23-139">`false` - disabled</span></span> |
| <span data-ttu-id="90e23-140">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="90e23-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="90e23-141">`true` etkin</span><span class="sxs-lookup"><span data-stu-id="90e23-141">`true` - enabled</span></span><br/><span data-ttu-id="90e23-142">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="90e23-142">`false` - disabled</span></span> |
| <span data-ttu-id="90e23-143">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="90e23-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="90e23-144">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="90e23-144">`1` - enabled</span></span><br/><span data-ttu-id="90e23-145">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="90e23-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="90e23-146">Örnekler</span><span class="sxs-lookup"><span data-stu-id="90e23-146">Examples</span></span>

<span data-ttu-id="90e23-147">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="90e23-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="90e23-148">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="90e23-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="90e23-149">Döngüler için hızlı JıT</span><span class="sxs-lookup"><span data-stu-id="90e23-149">Quick JIT for loops</span></span>

- <span data-ttu-id="90e23-150">JıT derleyicisinin döngüleri içeren yöntemlerde hızlı JıT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="90e23-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="90e23-151">Döngüler için hızlı JıT 'nin etkinleştirilmesi, başlangıç performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="90e23-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="90e23-152">Ancak uzun süreli döngüler, uzun süreler için daha az iyileştirilmiş kod ile takılmasına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="90e23-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="90e23-153">[Hızlı JIT](#quick-jit) devre dışıysa, bu ayarın etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="90e23-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="90e23-154">Varsayılan: devre dışı (`false`).</span><span class="sxs-lookup"><span data-stu-id="90e23-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="90e23-155">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="90e23-155">Setting name</span></span> | <span data-ttu-id="90e23-156">Değerler</span><span class="sxs-lookup"><span data-stu-id="90e23-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="90e23-157">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="90e23-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="90e23-158">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="90e23-158">`false` - disabled</span></span><br/><span data-ttu-id="90e23-159">`true` etkin</span><span class="sxs-lookup"><span data-stu-id="90e23-159">`true` - enabled</span></span> |
| <span data-ttu-id="90e23-160">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="90e23-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="90e23-161">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="90e23-161">`false` - disabled</span></span><br/><span data-ttu-id="90e23-162">`true` etkin</span><span class="sxs-lookup"><span data-stu-id="90e23-162">`true` - enabled</span></span> |
| <span data-ttu-id="90e23-163">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="90e23-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="90e23-164">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="90e23-164">`0` - disabled</span></span><br/><span data-ttu-id="90e23-165">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="90e23-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="90e23-166">Örnekler</span><span class="sxs-lookup"><span data-stu-id="90e23-166">Examples</span></span>

<span data-ttu-id="90e23-167">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="90e23-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="90e23-168">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="90e23-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="90e23-169">ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="90e23-169">ReadyToRun</span></span>

- <span data-ttu-id="90e23-170">.NET Core çalışma zamanının, kullanılabilir ReadyToRun verilerine sahip görüntüler için önceden derlenmiş kod kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="90e23-170">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="90e23-171">Bu seçeneği devre dışı bırakmak, çalışma zamanını JıT derleme çerçevesi koduna zorlar.</span><span class="sxs-lookup"><span data-stu-id="90e23-171">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="90e23-172">Daha fazla bilgi için bkz. [Readytorun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="90e23-172">For more information, see [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span>
- <span data-ttu-id="90e23-173">Varsayılan: etkin (`1`).</span><span class="sxs-lookup"><span data-stu-id="90e23-173">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="90e23-174">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="90e23-174">Setting name</span></span> | <span data-ttu-id="90e23-175">Değerler</span><span class="sxs-lookup"><span data-stu-id="90e23-175">Values</span></span> |
| - | - | - |
| <span data-ttu-id="90e23-176">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="90e23-176">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="90e23-177">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="90e23-177">`1` - enabled</span></span><br/><span data-ttu-id="90e23-178">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="90e23-178">`0` - disabled</span></span> |
