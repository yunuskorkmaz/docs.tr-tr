---
title: Derleme yapılandırması ayarları
description: JıT derleyicisinin .NET Core uygulamaları için nasıl çalıştığını yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: e5f9e1245b749864787fb808527d022665197edf
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654848"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="fce8d-103">Derleme için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="fce8d-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="fce8d-104">Katmanlı derleme</span><span class="sxs-lookup"><span data-stu-id="fce8d-104">Tiered compilation</span></span>

- <span data-ttu-id="fce8d-105">Just-In-Time (JıT) derleyicisinin [katmanlı derlemeyi](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="fce8d-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="fce8d-106">İki katmanda katmanlı derleme geçişleri yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="fce8d-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="fce8d-107">İlk katman kodu daha hızlı üretir ([hızlı JIT](#quick-jit)) veya önceden derlenmiş kod ([readytorun](#readytorun)) yükler.</span><span class="sxs-lookup"><span data-stu-id="fce8d-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="fce8d-108">İkinci katman arka planda iyileştirilmiş kod üretir ("JıT 'i iyileştirme").</span><span class="sxs-lookup"><span data-stu-id="fce8d-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="fce8d-109">.NET Core 3,0 ve üzeri sürümlerde katmanlı derleme varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="fce8d-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="fce8d-110">.NET Core 2,1 ve 2,2 ' de katmanlı derleme varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="fce8d-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="fce8d-111">Daha fazla bilgi için [katmanlı derleme Kılavuzu](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md)' na bakın.</span><span class="sxs-lookup"><span data-stu-id="fce8d-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span></span>

| | <span data-ttu-id="fce8d-112">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="fce8d-112">Setting name</span></span> | <span data-ttu-id="fce8d-113">Değerler</span><span class="sxs-lookup"><span data-stu-id="fce8d-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fce8d-114">\*\* Üzerinderuntimeconfig.js\*\*</span><span class="sxs-lookup"><span data-stu-id="fce8d-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="fce8d-115">`true` -etkin</span><span class="sxs-lookup"><span data-stu-id="fce8d-115">`true` - enabled</span></span><br/><span data-ttu-id="fce8d-116">`false` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="fce8d-116">`false` - disabled</span></span> |
| <span data-ttu-id="fce8d-117">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="fce8d-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="fce8d-118">`true` -etkin</span><span class="sxs-lookup"><span data-stu-id="fce8d-118">`true` - enabled</span></span><br/><span data-ttu-id="fce8d-119">`false` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="fce8d-119">`false` - disabled</span></span> |
| <span data-ttu-id="fce8d-120">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="fce8d-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="fce8d-121">`1` -etkin</span><span class="sxs-lookup"><span data-stu-id="fce8d-121">`1` - enabled</span></span><br/><span data-ttu-id="fce8d-122">`0` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="fce8d-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="fce8d-123">Örnekler</span><span class="sxs-lookup"><span data-stu-id="fce8d-123">Examples</span></span>

<span data-ttu-id="fce8d-124">*runtimeconfig.js* dosya:</span><span class="sxs-lookup"><span data-stu-id="fce8d-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="fce8d-125">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="fce8d-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="fce8d-126">Hızlı JıT</span><span class="sxs-lookup"><span data-stu-id="fce8d-126">Quick JIT</span></span>

- <span data-ttu-id="fce8d-127">JıT derleyicisinin *hızlı JIT*kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="fce8d-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="fce8d-128">Döngüler içermeyen ve önceden derlenmiş kodun kullanılamadığı yöntemler için, hızlı JıT bunları daha hızlı bir şekilde derler ancak iyileştirmelere gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="fce8d-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="fce8d-129">Hızlı JıT başlatma süresini azaltır, ancak performansı düşürülmüş performans özellikleriyle kod üretebilir.</span><span class="sxs-lookup"><span data-stu-id="fce8d-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="fce8d-130">Örneğin, kod daha fazla yığın alanı kullanabilir, daha fazla bellek ayırabilir ve daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="fce8d-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="fce8d-131">Hızlı JıT devre dışıysa ancak [katmanlı derleme](#tiered-compilation) etkinleştirilirse, yalnızca önceden derlenmiş kod katmanlı derlemeye katılır.</span><span class="sxs-lookup"><span data-stu-id="fce8d-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="fce8d-132">Bir yöntem [Readytorun](#readytorun)ile önceden DERLENMIŞSE, JIT davranışı [katmanlı derleme](#tiered-compilation) devre dışı bırakılmışsa aynı olur.</span><span class="sxs-lookup"><span data-stu-id="fce8d-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="fce8d-133">.NET Core 3,0 ve üzeri sürümlerde, hızlı JıT varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="fce8d-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="fce8d-134">.NET Core 2,1 ve 2,2 ' de, hızlı JıT varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="fce8d-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="fce8d-135">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="fce8d-135">Setting name</span></span> | <span data-ttu-id="fce8d-136">Değerler</span><span class="sxs-lookup"><span data-stu-id="fce8d-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fce8d-137">\*\* Üzerinderuntimeconfig.js\*\*</span><span class="sxs-lookup"><span data-stu-id="fce8d-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="fce8d-138">`true` -etkin</span><span class="sxs-lookup"><span data-stu-id="fce8d-138">`true` - enabled</span></span><br/><span data-ttu-id="fce8d-139">`false` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="fce8d-139">`false` - disabled</span></span> |
| <span data-ttu-id="fce8d-140">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="fce8d-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="fce8d-141">`true` -etkin</span><span class="sxs-lookup"><span data-stu-id="fce8d-141">`true` - enabled</span></span><br/><span data-ttu-id="fce8d-142">`false` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="fce8d-142">`false` - disabled</span></span> |
| <span data-ttu-id="fce8d-143">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="fce8d-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="fce8d-144">`1` -etkin</span><span class="sxs-lookup"><span data-stu-id="fce8d-144">`1` - enabled</span></span><br/><span data-ttu-id="fce8d-145">`0` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="fce8d-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="fce8d-146">Örnekler</span><span class="sxs-lookup"><span data-stu-id="fce8d-146">Examples</span></span>

<span data-ttu-id="fce8d-147">*runtimeconfig.js* dosya:</span><span class="sxs-lookup"><span data-stu-id="fce8d-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="fce8d-148">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="fce8d-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="fce8d-149">Döngüler için hızlı JıT</span><span class="sxs-lookup"><span data-stu-id="fce8d-149">Quick JIT for loops</span></span>

- <span data-ttu-id="fce8d-150">JıT derleyicisinin döngüleri içeren yöntemlerde hızlı JıT kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="fce8d-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="fce8d-151">Döngüler için hızlı JıT 'nin etkinleştirilmesi, başlangıç performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="fce8d-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="fce8d-152">Ancak uzun süreli döngüler, uzun süreler için daha az iyileştirilmiş kod ile takılmasına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="fce8d-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="fce8d-153">[Hızlı JIT](#quick-jit) devre dışıysa, bu ayarın etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fce8d-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="fce8d-154">Bu ayarı atlarsanız, döngüleri içeren yöntemler için hızlı JıT kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="fce8d-154">If you omit this setting, quick JIT is not used for methods that contain loops.</span></span> <span data-ttu-id="fce8d-155">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="fce8d-155">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="fce8d-156">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="fce8d-156">Setting name</span></span> | <span data-ttu-id="fce8d-157">Değerler</span><span class="sxs-lookup"><span data-stu-id="fce8d-157">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fce8d-158">\*\* Üzerinderuntimeconfig.js\*\*</span><span class="sxs-lookup"><span data-stu-id="fce8d-158">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="fce8d-159">`false` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="fce8d-159">`false` - disabled</span></span><br/><span data-ttu-id="fce8d-160">`true` -etkin</span><span class="sxs-lookup"><span data-stu-id="fce8d-160">`true` - enabled</span></span> |
| <span data-ttu-id="fce8d-161">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="fce8d-161">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="fce8d-162">`false` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="fce8d-162">`false` - disabled</span></span><br/><span data-ttu-id="fce8d-163">`true` -etkin</span><span class="sxs-lookup"><span data-stu-id="fce8d-163">`true` - enabled</span></span> |
| <span data-ttu-id="fce8d-164">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="fce8d-164">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="fce8d-165">`0` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="fce8d-165">`0` - disabled</span></span><br/><span data-ttu-id="fce8d-166">`1` -etkin</span><span class="sxs-lookup"><span data-stu-id="fce8d-166">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="fce8d-167">Örnekler</span><span class="sxs-lookup"><span data-stu-id="fce8d-167">Examples</span></span>

<span data-ttu-id="fce8d-168">*runtimeconfig.js* dosya:</span><span class="sxs-lookup"><span data-stu-id="fce8d-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="fce8d-169">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="fce8d-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="fce8d-170">ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="fce8d-170">ReadyToRun</span></span>

- <span data-ttu-id="fce8d-171">.NET Core çalışma zamanının, kullanılabilir ReadyToRun verilerine sahip görüntüler için önceden derlenmiş kod kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="fce8d-171">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="fce8d-172">Bu seçeneği devre dışı bırakmak, çalışma zamanını JıT derleme çerçevesi koduna zorlar.</span><span class="sxs-lookup"><span data-stu-id="fce8d-172">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="fce8d-173">Daha fazla bilgi için bkz. [çalıştırılmaya hazırlanma](../deploying/ready-to-run.md).</span><span class="sxs-lookup"><span data-stu-id="fce8d-173">For more information, see [Ready to Run](../deploying/ready-to-run.md).</span></span>
- <span data-ttu-id="fce8d-174">Bu ayarı atlarsanız, .NET kullanılabilir olduğunda ReadyToRun verilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fce8d-174">If you omit this setting, .NET uses ReadyToRun data when it's available.</span></span> <span data-ttu-id="fce8d-175">Bu değeri değerine ayarlamaya eşdeğerdir `1` .</span><span class="sxs-lookup"><span data-stu-id="fce8d-175">This is equivalent to setting the value to `1`.</span></span>

| | <span data-ttu-id="fce8d-176">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="fce8d-176">Setting name</span></span> | <span data-ttu-id="fce8d-177">Değerler</span><span class="sxs-lookup"><span data-stu-id="fce8d-177">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fce8d-178">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="fce8d-178">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="fce8d-179">`1` -etkin</span><span class="sxs-lookup"><span data-stu-id="fce8d-179">`1` - enabled</span></span><br/><span data-ttu-id="fce8d-180">`0` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="fce8d-180">`0` - disabled</span></span> |
