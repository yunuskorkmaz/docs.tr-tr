---
title: Derleme config ayarları
description: JIT derleyicisinin .NET Core uygulamaları için nasıl çalıştığını yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: adf1f01dba7387b89ee56784e33653d6a132c0e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092895"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="91329-103">Derleme için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="91329-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="91329-104">Katmanlı derleme</span><span class="sxs-lookup"><span data-stu-id="91329-104">Tiered compilation</span></span>

- <span data-ttu-id="91329-105">Tam zamanında (JIT) derleyicinin [katmanlı derleme](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="91329-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="91329-106">Katmanlı derleme yöntemlerini iki katman dan geçirir:</span><span class="sxs-lookup"><span data-stu-id="91329-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="91329-107">Birinci katman kodu daha hızlı[(hızlı JIT)](#quick-jit)oluşturur veya önceden derlenmiş kodu[(ReadyToRun)](#readytorun)yükler.</span><span class="sxs-lookup"><span data-stu-id="91329-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="91329-108">İkinci katman arka planda en iyi duruma getirilmiş kod oluşturur ("JIT'yi optimize etme").</span><span class="sxs-lookup"><span data-stu-id="91329-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="91329-109">.NET Core 3.0 ve sonraki durumlarda, katmanlı derleme varsayılan olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="91329-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="91329-110">.NET Core 2.1 ve 2.2'de katmanlı derleme varsayılan olarak devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="91329-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="91329-111">Daha fazla bilgi için [Katmanlı derleme kılavuzuna](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="91329-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span></span>

| | <span data-ttu-id="91329-112">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="91329-112">Setting name</span></span> | <span data-ttu-id="91329-113">Değerler</span><span class="sxs-lookup"><span data-stu-id="91329-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="91329-114">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="91329-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="91329-115">`true`- etkin</span><span class="sxs-lookup"><span data-stu-id="91329-115">`true` - enabled</span></span><br/><span data-ttu-id="91329-116">`false`- engelli</span><span class="sxs-lookup"><span data-stu-id="91329-116">`false` - disabled</span></span> |
| <span data-ttu-id="91329-117">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="91329-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="91329-118">`true`- etkin</span><span class="sxs-lookup"><span data-stu-id="91329-118">`true` - enabled</span></span><br/><span data-ttu-id="91329-119">`false`- engelli</span><span class="sxs-lookup"><span data-stu-id="91329-119">`false` - disabled</span></span> |
| <span data-ttu-id="91329-120">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="91329-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="91329-121">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="91329-121">`1` - enabled</span></span><br/><span data-ttu-id="91329-122">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="91329-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="91329-123">Örnekler</span><span class="sxs-lookup"><span data-stu-id="91329-123">Examples</span></span>

<span data-ttu-id="91329-124">*runtimeconfig.json* dosyası:</span><span class="sxs-lookup"><span data-stu-id="91329-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="91329-125">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="91329-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="91329-126">Hızlı JIT</span><span class="sxs-lookup"><span data-stu-id="91329-126">Quick JIT</span></span>

- <span data-ttu-id="91329-127">JIT derleyicisinin hızlı *JIT*kullanıp kullanmayacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="91329-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="91329-128">Döngü içermeyen ve önceden derlenmiş kodun kullanılamadığı yöntemler için, hızlı JIT bunları daha hızlı ancak optimizasyonlar olmadan derler.</span><span class="sxs-lookup"><span data-stu-id="91329-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="91329-129">Hızlı JIT etkinleştirme başlangıç süresini azaltır, ancak bozulmuş performans özellikleri ile kod üretebilir.</span><span class="sxs-lookup"><span data-stu-id="91329-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="91329-130">Örneğin, kod daha fazla yığın alanı kullanabilir, daha fazla bellek tahsis edebilir ve daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="91329-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="91329-131">Hızlı JIT devre dışı bırakılır, ancak [katmanlı derleme](#tiered-compilation) etkinse, yalnızca önceden derlenmiş kod katmanlı derlemeye katılır.</span><span class="sxs-lookup"><span data-stu-id="91329-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="91329-132">Bir yöntem [ReadyToRun](#readytorun)ile önceden derlenmiyorsa, JIT davranışı [katmanlı derleme](#tiered-compilation) devre dışı bırakılmış gibi aynıdır.</span><span class="sxs-lookup"><span data-stu-id="91329-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="91329-133">.NET Core 3.0 ve sonraki durumlarda, hızlı JIT varsayılan olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="91329-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="91329-134">.NET Core 2.1 ve 2.2'de, hızlı JIT varsayılan olarak devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="91329-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="91329-135">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="91329-135">Setting name</span></span> | <span data-ttu-id="91329-136">Değerler</span><span class="sxs-lookup"><span data-stu-id="91329-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="91329-137">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="91329-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="91329-138">`true`- etkin</span><span class="sxs-lookup"><span data-stu-id="91329-138">`true` - enabled</span></span><br/><span data-ttu-id="91329-139">`false`- engelli</span><span class="sxs-lookup"><span data-stu-id="91329-139">`false` - disabled</span></span> |
| <span data-ttu-id="91329-140">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="91329-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="91329-141">`true`- etkin</span><span class="sxs-lookup"><span data-stu-id="91329-141">`true` - enabled</span></span><br/><span data-ttu-id="91329-142">`false`- engelli</span><span class="sxs-lookup"><span data-stu-id="91329-142">`false` - disabled</span></span> |
| <span data-ttu-id="91329-143">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="91329-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="91329-144">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="91329-144">`1` - enabled</span></span><br/><span data-ttu-id="91329-145">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="91329-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="91329-146">Örnekler</span><span class="sxs-lookup"><span data-stu-id="91329-146">Examples</span></span>

<span data-ttu-id="91329-147">*runtimeconfig.json* dosyası:</span><span class="sxs-lookup"><span data-stu-id="91329-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="91329-148">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="91329-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="91329-149">Döngüler için hızlı JIT</span><span class="sxs-lookup"><span data-stu-id="91329-149">Quick JIT for loops</span></span>

- <span data-ttu-id="91329-150">JIT derleyicisinin döngü içeren yöntemlerde hızlı JIT kullanıp kullanmayacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="91329-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="91329-151">Döngüler için hızlı JIT'yi etkinleştirmek başlangıç performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="91329-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="91329-152">Ancak, uzun süren döngüler uzun süreler için daha az optimize edilmiş kodda sıkışıp kalabilir.</span><span class="sxs-lookup"><span data-stu-id="91329-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="91329-153">[Hızlı JIT](#quick-jit) devre dışı bırakılırsa, bu ayarın hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="91329-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="91329-154">Varsayılan: Devre`false`Dışı ( ).</span><span class="sxs-lookup"><span data-stu-id="91329-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="91329-155">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="91329-155">Setting name</span></span> | <span data-ttu-id="91329-156">Değerler</span><span class="sxs-lookup"><span data-stu-id="91329-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="91329-157">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="91329-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="91329-158">`false`- engelli</span><span class="sxs-lookup"><span data-stu-id="91329-158">`false` - disabled</span></span><br/><span data-ttu-id="91329-159">`true`- etkin</span><span class="sxs-lookup"><span data-stu-id="91329-159">`true` - enabled</span></span> |
| <span data-ttu-id="91329-160">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="91329-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="91329-161">`false`- engelli</span><span class="sxs-lookup"><span data-stu-id="91329-161">`false` - disabled</span></span><br/><span data-ttu-id="91329-162">`true`- etkin</span><span class="sxs-lookup"><span data-stu-id="91329-162">`true` - enabled</span></span> |
| <span data-ttu-id="91329-163">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="91329-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="91329-164">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="91329-164">`0` - disabled</span></span><br/><span data-ttu-id="91329-165">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="91329-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="91329-166">Örnekler</span><span class="sxs-lookup"><span data-stu-id="91329-166">Examples</span></span>

<span data-ttu-id="91329-167">*runtimeconfig.json* dosyası:</span><span class="sxs-lookup"><span data-stu-id="91329-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="91329-168">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="91329-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="91329-169">Readytorun</span><span class="sxs-lookup"><span data-stu-id="91329-169">ReadyToRun</span></span>

- <span data-ttu-id="91329-170">.NET Core çalışma zamanının ready ReadyToRun verileriyle görüntüler için önceden derlenmiş kod kullanıp kullanmayacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="91329-170">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="91329-171">Bu seçeneğin devre dışı bırakılması çalışma zamanını JIT-derleme çerçeve koduna zorlar.</span><span class="sxs-lookup"><span data-stu-id="91329-171">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="91329-172">Daha fazla bilgi için [ReadyToRun'a](../whats-new/dotnet-core-3-0.md#readytorun-images)bakın.</span><span class="sxs-lookup"><span data-stu-id="91329-172">For more information, see [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span>
- <span data-ttu-id="91329-173">Varsayılan: Etkin`1`( ).</span><span class="sxs-lookup"><span data-stu-id="91329-173">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="91329-174">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="91329-174">Setting name</span></span> | <span data-ttu-id="91329-175">Değerler</span><span class="sxs-lookup"><span data-stu-id="91329-175">Values</span></span> |
| - | - | - |
| <span data-ttu-id="91329-176">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="91329-176">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="91329-177">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="91329-177">`1` - enabled</span></span><br/><span data-ttu-id="91329-178">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="91329-178">`0` - disabled</span></span> |
