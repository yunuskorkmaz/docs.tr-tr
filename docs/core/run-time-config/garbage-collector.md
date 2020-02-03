---
title: Çöp toplayıcı yapılandırma ayarları
description: Çöp toplayıcının .NET Core uygulamaları için belleği nasıl yönettiğini yapılandırmak üzere çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 044083d69601f5092724a46d358b2ee5673d428d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733522"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="e3622-103">Çöp toplama için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e3622-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="e3622-104">Bu sayfa, çalışma zamanında değiştirilebilen çöp toplayıcı (GC) ayarları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e3622-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="e3622-105">Çalışan bir uygulamanın en yüksek performans düzeyine ulaşmak istiyorsanız bu ayarları kullanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="e3622-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="e3622-106">Bununla birlikte, varsayılan olarak, çoğu uygulama için tipik durumlarda en iyi performansı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3622-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="e3622-107">Ayarlar bu sayfadaki gruplar halinde düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="e3622-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="e3622-108">Her grup içindeki ayarlar, belirli bir sonuca ulaşmak için genellikle birbirleriyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e3622-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="e3622-109">Bu ayarlar ayrıca uygulama çalışırken dinamik olarak değiştirilebilir, bu nedenle ayarladığınız tüm çalışma zamanı ayarları geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="e3622-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="e3622-110">[Gecikme düzeyi](../../standard/garbage-collection/latency.md)gibi bazı ayarlar tipik olarak yalnızca TASARıM zamanında API aracılığıyla ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e3622-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="e3622-111">Bu tür ayarlar bu sayfadan çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="e3622-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="e3622-112">Sayı değerleri için, *runtimeconfig. JSON* dosyasındaki ayarlar için ondalık gösterimi ve ortam değişkeni ayarları için onaltılık gösterimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="e3622-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="e3622-113">Onaltılık değerler için, bunları "0x" öneki olmadan veya olmadan belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3622-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="e3622-114">Çöp toplamanın türleri</span><span class="sxs-lookup"><span data-stu-id="e3622-114">Flavors of garbage collection</span></span>

<span data-ttu-id="e3622-115">Çöp toplamanın iki ana özellikleri, iş istasyonu GC ve sunucu GC ' dir.</span><span class="sxs-lookup"><span data-stu-id="e3622-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="e3622-116">İkisi arasındaki farklılıklar hakkında daha fazla bilgi için bkz. [çöp toplamanın temelleri](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="e3622-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="e3622-117">Çöp toplamanın alt türleri arka plan ve eş zamanlı değil.</span><span class="sxs-lookup"><span data-stu-id="e3622-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="e3622-118">Çöp toplamanın türlerini seçmek için aşağıdaki ayarları kullanın:</span><span class="sxs-lookup"><span data-stu-id="e3622-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="e3622-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="e3622-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="e3622-120">Uygulamanın iş istasyonu çöp toplamayı veya sunucu çöp toplamayı kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e3622-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="e3622-121">Varsayılan: Iş Istasyonu atık toplama (`false`).</span><span class="sxs-lookup"><span data-stu-id="e3622-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="e3622-122">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="e3622-122">Setting name</span></span> | <span data-ttu-id="e3622-123">Değerler</span><span class="sxs-lookup"><span data-stu-id="e3622-123">Values</span></span> | <span data-ttu-id="e3622-124">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e3622-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e3622-125">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e3622-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="e3622-126">`false`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="e3622-126">`false` - workstation</span></span><br/><span data-ttu-id="e3622-127">`true`-sunucu</span><span class="sxs-lookup"><span data-stu-id="e3622-127">`true` - server</span></span> | <span data-ttu-id="e3622-128">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e3622-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="e3622-129">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="e3622-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="e3622-130">`false`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="e3622-130">`false` - workstation</span></span><br/><span data-ttu-id="e3622-131">`true`-sunucu</span><span class="sxs-lookup"><span data-stu-id="e3622-131">`true` - server</span></span> | <span data-ttu-id="e3622-132">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e3622-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="e3622-133">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="e3622-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="e3622-134">`0`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="e3622-134">`0` - workstation</span></span><br/><span data-ttu-id="e3622-135">`1`-sunucu</span><span class="sxs-lookup"><span data-stu-id="e3622-135">`1` - server</span></span> | <span data-ttu-id="e3622-136">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e3622-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="e3622-137">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="e3622-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e3622-138">GCServer</span><span class="sxs-lookup"><span data-stu-id="e3622-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="e3622-139">`false`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="e3622-139">`false` - workstation</span></span><br/><span data-ttu-id="e3622-140">`true`-sunucu</span><span class="sxs-lookup"><span data-stu-id="e3622-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="e3622-141">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e3622-141">Examples</span></span>

<span data-ttu-id="e3622-142">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="e3622-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="e3622-143">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="e3622-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="e3622-144">System. GC. eşzamanlı/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="e3622-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="e3622-145">Arka plan (eşzamanlı) Çöp toplamanın etkinleştirilip etkinleştirilmeyeceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e3622-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="e3622-146">Varsayılan: etkin (`true`).</span><span class="sxs-lookup"><span data-stu-id="e3622-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="e3622-147">Daha fazla bilgi için bkz. [arka plan atık toplama](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) ve [arka plan sunucusu çöp toplama](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="e3622-147">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="e3622-148">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="e3622-148">Setting name</span></span> | <span data-ttu-id="e3622-149">Değerler</span><span class="sxs-lookup"><span data-stu-id="e3622-149">Values</span></span> | <span data-ttu-id="e3622-150">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e3622-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e3622-151">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e3622-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="e3622-152">`true` arka plan GC</span><span class="sxs-lookup"><span data-stu-id="e3622-152">`true` - background GC</span></span><br/><span data-ttu-id="e3622-153">`false`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="e3622-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="e3622-154">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e3622-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="e3622-155">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="e3622-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="e3622-156">`true` arka plan GC</span><span class="sxs-lookup"><span data-stu-id="e3622-156">`true` - background GC</span></span><br/><span data-ttu-id="e3622-157">`false`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="e3622-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="e3622-158">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e3622-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="e3622-159">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="e3622-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="e3622-160">`true` arka plan GC</span><span class="sxs-lookup"><span data-stu-id="e3622-160">`true` - background GC</span></span><br/><span data-ttu-id="e3622-161">`false`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="e3622-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="e3622-162">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e3622-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="e3622-163">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="e3622-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e3622-164">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="e3622-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="e3622-165">`true` arka plan GC</span><span class="sxs-lookup"><span data-stu-id="e3622-165">`true` - background GC</span></span><br/><span data-ttu-id="e3622-166">`false`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="e3622-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="e3622-167">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e3622-167">Examples</span></span>

<span data-ttu-id="e3622-168">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="e3622-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="e3622-169">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="e3622-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="e3622-170">Kaynak kullanımını yönetme</span><span class="sxs-lookup"><span data-stu-id="e3622-170">Manage resource usage</span></span>

<span data-ttu-id="e3622-171">Çöp toplayıcının bellek ve işlemci kullanımını yönetmek için bu bölümde açıklanan ayarları kullanın.</span><span class="sxs-lookup"><span data-stu-id="e3622-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="e3622-172">Bu ayarlardan bazıları hakkında daha fazla bilgi için, bkz. [iş istasyonu ve sunucu GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blogu girişi.</span><span class="sxs-lookup"><span data-stu-id="e3622-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="e3622-173">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="e3622-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="e3622-174">Çöp toplayıcı tarafından oluşturulan Heap sayısını sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="e3622-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="e3622-175">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e3622-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="e3622-176">GC işlemci benzeşimi etkinse, varsayılan olarak, yığın sayısı ayarı GC sayfa@@/iş parçacıklarını ilk `n` işlemcilere `n`.</span><span class="sxs-lookup"><span data-stu-id="e3622-176">If GC processor affinity is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="e3622-177">(Tam olarak hangi işlemcilerin olduğunu belirtmek için, bu maskeyi seçin veya aralıklar ayarlarını kesin olarak belirleyin.)</span><span class="sxs-lookup"><span data-stu-id="e3622-177">(Use the affinitize mask or affinitize ranges settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="e3622-178">GC işlemci benzeşimi devre dışıysa, bu ayar GC yığınlarının sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="e3622-178">If GC processor affinity is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="e3622-179">Daha fazla bilgi için [Gcheapcount açıklamalarını](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)inceleyin.</span><span class="sxs-lookup"><span data-stu-id="e3622-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="e3622-180">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="e3622-180">Setting name</span></span> | <span data-ttu-id="e3622-181">Değerler</span><span class="sxs-lookup"><span data-stu-id="e3622-181">Values</span></span> | <span data-ttu-id="e3622-182">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e3622-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e3622-183">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e3622-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="e3622-184">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="e3622-184">*decimal value*</span></span> | <span data-ttu-id="e3622-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e3622-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="e3622-186">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="e3622-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="e3622-187">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="e3622-187">*hexadecimal value*</span></span> | <span data-ttu-id="e3622-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e3622-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="e3622-189">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="e3622-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e3622-190">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="e3622-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="e3622-191">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="e3622-191">*decimal value*</span></span> | <span data-ttu-id="e3622-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="e3622-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="e3622-193">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e3622-193">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapCount": 16
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="e3622-194">*Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="e3622-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="e3622-195">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="e3622-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="e3622-196">Örneğin, Heap sayısını 16 ile sınırlamak için değerler JSON dosyası için 16, ortam değişkeni için 0x10 veya 10 olur.</span><span class="sxs-lookup"><span data-stu-id="e3622-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="e3622-197">System. GC. ısıpaffinitizemask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="e3622-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="e3622-198">Çöp toplayıcı iş parçacıklarının kullanması gereken tam işlemcileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3622-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="e3622-199">`System.GC.NoAffinitize` `true`olarak ayarlanarak, işlemci benzeşimi devre dışı bırakıldıysa, bu ayar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="e3622-199">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="e3622-200">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e3622-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="e3622-201">Değer, işlem için kullanılabilir olan işlemcileri tanımlayan bir bit maskesidir.</span><span class="sxs-lookup"><span data-stu-id="e3622-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="e3622-202">Örneğin, bir 1023 ondalık değeri (veya ortam değişkenini kullanıyorsanız, 0x3FF veya 3FF onaltılı değeri), ikili gösterimde 0011 1111 1111 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e3622-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="e3622-203">Bu, ilk 10 işlemcinin kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3622-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="e3622-204">Sıradaki 10 işlemciyi belirtmek için, işlemci 10-19 ' 1047552 nin ondalık değerini (veya 0xFFC00 ya da FFC00) bir 1111 1111 1100 0000 0000 ikili değere eşdeğer bir değere belirleyin.</span><span class="sxs-lookup"><span data-stu-id="e3622-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="e3622-205">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="e3622-205">Setting name</span></span> | <span data-ttu-id="e3622-206">Değerler</span><span class="sxs-lookup"><span data-stu-id="e3622-206">Values</span></span> | <span data-ttu-id="e3622-207">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e3622-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e3622-208">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e3622-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="e3622-209">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="e3622-209">*decimal value*</span></span> | <span data-ttu-id="e3622-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e3622-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="e3622-211">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="e3622-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="e3622-212">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="e3622-212">*hexadecimal value*</span></span> | <span data-ttu-id="e3622-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e3622-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="e3622-214">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="e3622-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e3622-215">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="e3622-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="e3622-216">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="e3622-216">*decimal value*</span></span> | <span data-ttu-id="e3622-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="e3622-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="e3622-218">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e3622-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="e3622-219">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="e3622-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="e3622-220">Çöp toplayıcı iş parçacıkları için kullanılacak işlemcilerin listesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3622-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="e3622-221">Bu ayar `System.GC.HeapAffinitizeMask`benzerdir, ancak 64 'den fazla işlemciyi belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3622-221">This setting is similar to `System.GC.HeapAffinitizeMask`, except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="e3622-222">Windows işletim sistemleri için, işlemci numarasını veya aralığını karşılık gelen [CPU grubuyla](/windows/win32/procthread/processor-groups)önek olarak ekleyin, örneğin, "0:1-10, 0:12, 1:50-52, 1:70".</span><span class="sxs-lookup"><span data-stu-id="e3622-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="e3622-223">`System.GC.NoAffinitize` `true`olarak ayarlanarak, işlemci benzeşimi devre dışı bırakıldıysa, bu ayar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="e3622-223">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="e3622-224">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e3622-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="e3622-225">Daha fazla bilgi için bkz. Maoni Stephens ' blogu üzerinde [> 64 CPU 'su olan MAKINELERDE GC için daha Iyi hale getirme](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) .</span><span class="sxs-lookup"><span data-stu-id="e3622-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="e3622-226">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="e3622-226">Setting name</span></span> | <span data-ttu-id="e3622-227">Değerler</span><span class="sxs-lookup"><span data-stu-id="e3622-227">Values</span></span> | <span data-ttu-id="e3622-228">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e3622-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e3622-229">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e3622-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="e3622-230">İşlemci numaralarının veya işlemci numarası aralıklarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="e3622-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="e3622-231">UNIX örneği: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="e3622-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="e3622-232">Windows örnek: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="e3622-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="e3622-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e3622-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="e3622-234">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="e3622-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="e3622-235">İşlemci numaralarının veya işlemci numarası aralıklarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="e3622-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="e3622-236">UNIX örneği: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="e3622-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="e3622-237">Windows örnek: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="e3622-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="e3622-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e3622-238">.NET Core 3.0</span></span> |

<span data-ttu-id="e3622-239">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e3622-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="e3622-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="e3622-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="e3622-241">Çöp toplayıcının [CPU grupları](/windows/win32/procthread/processor-groups) kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e3622-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="e3622-242">64 bitlik bir Windows bilgisayarında birden çok CPU grubu olduğunda, diğer bir deyişle, 64 ' den fazla işlemci varsa, bu öğenin tüm CPU gruplarında çöp toplamayı genişletmelerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="e3622-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="e3622-243">Çöp toplayıcı, Heap 'ler oluşturmak ve dengelemek için tüm çekirdekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="e3622-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="e3622-244">Yalnızca 64-bit Windows işletim sistemlerinde sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e3622-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="e3622-245">Varsayılan: devre dışı (`0`).</span><span class="sxs-lookup"><span data-stu-id="e3622-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="e3622-246">Daha fazla bilgi için bkz. Maoni Stephens ' blogu üzerinde [> 64 CPU 'su olan MAKINELERDE GC için daha Iyi hale getirme](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) .</span><span class="sxs-lookup"><span data-stu-id="e3622-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="e3622-247">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="e3622-247">Setting name</span></span> | <span data-ttu-id="e3622-248">Değerler</span><span class="sxs-lookup"><span data-stu-id="e3622-248">Values</span></span> | <span data-ttu-id="e3622-249">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e3622-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e3622-250">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e3622-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="e3622-251">Yok</span><span class="sxs-lookup"><span data-stu-id="e3622-251">N/A</span></span> | <span data-ttu-id="e3622-252">Yok</span><span class="sxs-lookup"><span data-stu-id="e3622-252">N/A</span></span> | <span data-ttu-id="e3622-253">Yok</span><span class="sxs-lookup"><span data-stu-id="e3622-253">N/A</span></span> |
| <span data-ttu-id="e3622-254">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="e3622-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="e3622-255">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="e3622-255">`0` - disabled</span></span><br/><span data-ttu-id="e3622-256">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="e3622-256">`1` - enabled</span></span> | <span data-ttu-id="e3622-257">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e3622-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="e3622-258">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="e3622-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e3622-259">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="e3622-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="e3622-260">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="e3622-260">`false` - disabled</span></span><br/><span data-ttu-id="e3622-261">`true` etkin</span><span class="sxs-lookup"><span data-stu-id="e3622-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="e3622-262">Ortak dil çalışma zamanını (CLR) tüm CPU grupları arasında iş parçacığı havuzundan da dağıtmak üzere yapılandırmak için, [Thread_UseAllCpuGroups öğesi](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) seçeneğini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="e3622-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="e3622-263">.NET Core uygulamaları için `COMPlus_Thread_UseAllCpuGroups` ortam değişkeninin değerini `1`olarak ayarlayarak bu seçeneği etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3622-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="e3622-264">System. GC. Noafınitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="e3622-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="e3622-265">*Çöp toplama* iş parçacıklarının işlemcilerle kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3622-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="e3622-266">Bir GC iş parçacığını eklemek için yalnızca belirli bir CPU üzerinde çalışabilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e3622-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="e3622-267">Her GC iş parçacığı için bir yığın oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e3622-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="e3622-268">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e3622-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="e3622-269">Varsayılan: işlemciler (`false`) ile atık toplama iş parçacıklarını ön olarak başlatma.</span><span class="sxs-lookup"><span data-stu-id="e3622-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="e3622-270">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="e3622-270">Setting name</span></span> | <span data-ttu-id="e3622-271">Değerler</span><span class="sxs-lookup"><span data-stu-id="e3622-271">Values</span></span> | <span data-ttu-id="e3622-272">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e3622-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e3622-273">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e3622-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="e3622-274">`false`-afze</span><span class="sxs-lookup"><span data-stu-id="e3622-274">`false` - affinitize</span></span><br/><span data-ttu-id="e3622-275">`true`-yok etme</span><span class="sxs-lookup"><span data-stu-id="e3622-275">`true` - don't affinitize</span></span> | <span data-ttu-id="e3622-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e3622-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="e3622-277">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="e3622-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="e3622-278">`0`-afze</span><span class="sxs-lookup"><span data-stu-id="e3622-278">`0` - affinitize</span></span><br/><span data-ttu-id="e3622-279">`1`-yok etme</span><span class="sxs-lookup"><span data-stu-id="e3622-279">`1` - don't affinitize</span></span> | <span data-ttu-id="e3622-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e3622-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="e3622-281">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="e3622-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e3622-282">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="e3622-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="e3622-283">`false`-afze</span><span class="sxs-lookup"><span data-stu-id="e3622-283">`false` - affinitize</span></span><br/><span data-ttu-id="e3622-284">`true`-yok etme</span><span class="sxs-lookup"><span data-stu-id="e3622-284">`true` - don't affinitize</span></span> | <span data-ttu-id="e3622-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="e3622-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="e3622-286">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e3622-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="e3622-287">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="e3622-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="e3622-288">GC yığını ve GC booksaklanması için bayt cinsinden en fazla tamamlama boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3622-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>

| | <span data-ttu-id="e3622-289">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="e3622-289">Setting name</span></span> | <span data-ttu-id="e3622-290">Değerler</span><span class="sxs-lookup"><span data-stu-id="e3622-290">Values</span></span> | <span data-ttu-id="e3622-291">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e3622-291">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e3622-292">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e3622-292">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="e3622-293">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="e3622-293">*decimal value*</span></span> | <span data-ttu-id="e3622-294">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e3622-294">.NET Core 3.0</span></span> |
| <span data-ttu-id="e3622-295">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="e3622-295">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="e3622-296">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="e3622-296">*hexadecimal value*</span></span> | <span data-ttu-id="e3622-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e3622-297">.NET Core 3.0</span></span> |

<span data-ttu-id="e3622-298">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e3622-298">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimit": 209715200
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="e3622-299">*Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="e3622-299">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="e3622-300">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="e3622-300">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="e3622-301">Örneğin, 200 mebibytes (MIB) yığın sabit sınırı belirtmek için, değerler JSON dosyası için 209715200 ve ortam değişkeni için 0xC800000 veya C800000 olur.</span><span class="sxs-lookup"><span data-stu-id="e3622-301">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="e3622-302">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="e3622-302">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="e3622-303">Toplam belleğin yüzdesi olarak GC yığın kullanımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3622-303">Specifies the GC heap usage as a percentage of the total memory.</span></span>

| | <span data-ttu-id="e3622-304">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="e3622-304">Setting name</span></span> | <span data-ttu-id="e3622-305">Değerler</span><span class="sxs-lookup"><span data-stu-id="e3622-305">Values</span></span> | <span data-ttu-id="e3622-306">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e3622-306">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e3622-307">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e3622-307">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="e3622-308">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="e3622-308">*decimal value*</span></span> | <span data-ttu-id="e3622-309">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e3622-309">.NET Core 3.0</span></span> |
| <span data-ttu-id="e3622-310">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="e3622-310">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="e3622-311">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="e3622-311">*hexadecimal value*</span></span> | <span data-ttu-id="e3622-312">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e3622-312">.NET Core 3.0</span></span> |

<span data-ttu-id="e3622-313">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e3622-313">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimitPercent": 30
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="e3622-314">*Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="e3622-314">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="e3622-315">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="e3622-315">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="e3622-316">Örneğin, yığın kullanımını %30 olarak sınırlandırmak için değerler JSON dosyası için 30, ortam değişkeni için 0x1E veya 1E olur.</span><span class="sxs-lookup"><span data-stu-id="e3622-316">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="e3622-317">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="e3622-317">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="e3622-318">Silinmesi gereken segmentlerin ileride kullanılmak üzere bir bekleme listesine mi yerleştirileceğini, yoksa işletim sistemine (OS) geri mi bırakılacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e3622-318">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="e3622-319">Varsayılan: kesimleri işletim sistemine (`false`) yeniden bırakın.</span><span class="sxs-lookup"><span data-stu-id="e3622-319">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="e3622-320">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="e3622-320">Setting name</span></span> | <span data-ttu-id="e3622-321">Değerler</span><span class="sxs-lookup"><span data-stu-id="e3622-321">Values</span></span> | <span data-ttu-id="e3622-322">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e3622-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e3622-323">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e3622-323">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="e3622-324">`false`-işletim sistemine yayın</span><span class="sxs-lookup"><span data-stu-id="e3622-324">`false` - release to OS</span></span><br/><span data-ttu-id="e3622-325">`true`-bekleme üzerine koy</span><span class="sxs-lookup"><span data-stu-id="e3622-325">`true` - put on standby</span></span> | <span data-ttu-id="e3622-326">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e3622-326">.NET Core 1.0</span></span> |
| <span data-ttu-id="e3622-327">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="e3622-327">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="e3622-328">`false`-işletim sistemine yayın</span><span class="sxs-lookup"><span data-stu-id="e3622-328">`false` - release to OS</span></span><br/><span data-ttu-id="e3622-329">`true`-bekleme üzerine koy</span><span class="sxs-lookup"><span data-stu-id="e3622-329">`true` - put on standby</span></span> | <span data-ttu-id="e3622-330">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e3622-330">.NET Core 1.0</span></span> |
| <span data-ttu-id="e3622-331">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="e3622-331">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="e3622-332">`0`-işletim sistemine yayın</span><span class="sxs-lookup"><span data-stu-id="e3622-332">`0` - release to OS</span></span><br/><span data-ttu-id="e3622-333">`1`-bekleme üzerine koy</span><span class="sxs-lookup"><span data-stu-id="e3622-333">`1` - put on standby</span></span> | <span data-ttu-id="e3622-334">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e3622-334">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="e3622-335">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e3622-335">Examples</span></span>

<span data-ttu-id="e3622-336">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="e3622-336">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="e3622-337">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="e3622-337">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="e3622-338">Büyük sayfalar</span><span class="sxs-lookup"><span data-stu-id="e3622-338">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="e3622-339">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="e3622-339">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="e3622-340">Bir yığın sabit sınırı ayarlandığında büyük sayfaların kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3622-340">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="e3622-341">Varsayılan: devre dışı (`0`).</span><span class="sxs-lookup"><span data-stu-id="e3622-341">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="e3622-342">Bu bir deneysel ayardır.</span><span class="sxs-lookup"><span data-stu-id="e3622-342">This is an experimental setting.</span></span>

| | <span data-ttu-id="e3622-343">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="e3622-343">Setting name</span></span> | <span data-ttu-id="e3622-344">Değerler</span><span class="sxs-lookup"><span data-stu-id="e3622-344">Values</span></span> | <span data-ttu-id="e3622-345">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e3622-345">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e3622-346">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e3622-346">**runtimeconfig.json**</span></span> | <span data-ttu-id="e3622-347">Yok</span><span class="sxs-lookup"><span data-stu-id="e3622-347">N/A</span></span> | <span data-ttu-id="e3622-348">Yok</span><span class="sxs-lookup"><span data-stu-id="e3622-348">N/A</span></span> | <span data-ttu-id="e3622-349">Yok</span><span class="sxs-lookup"><span data-stu-id="e3622-349">N/A</span></span> |
| <span data-ttu-id="e3622-350">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="e3622-350">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="e3622-351">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="e3622-351">`0` - disabled</span></span><br/><span data-ttu-id="e3622-352">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="e3622-352">`1` - enabled</span></span> | <span data-ttu-id="e3622-353">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e3622-353">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="e3622-354">Büyük nesneler</span><span class="sxs-lookup"><span data-stu-id="e3622-354">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="e3622-355">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="e3622-355">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="e3622-356">Toplam boyuttaki 2 gigabayttan (GB) büyük olan diziler için 64 bitlik platformlarda çöp toplayıcı desteğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e3622-356">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="e3622-357">Varsayılan: etkin (`1`).</span><span class="sxs-lookup"><span data-stu-id="e3622-357">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="e3622-358">Bu seçenek, .NET 'in gelecek bir sürümünde kullanımdan kalkabilir.</span><span class="sxs-lookup"><span data-stu-id="e3622-358">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="e3622-359">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="e3622-359">Setting name</span></span> | <span data-ttu-id="e3622-360">Değerler</span><span class="sxs-lookup"><span data-stu-id="e3622-360">Values</span></span> | <span data-ttu-id="e3622-361">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e3622-361">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e3622-362">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e3622-362">**runtimeconfig.json**</span></span> | <span data-ttu-id="e3622-363">Yok</span><span class="sxs-lookup"><span data-stu-id="e3622-363">N/A</span></span> | <span data-ttu-id="e3622-364">Yok</span><span class="sxs-lookup"><span data-stu-id="e3622-364">N/A</span></span> | <span data-ttu-id="e3622-365">Yok</span><span class="sxs-lookup"><span data-stu-id="e3622-365">N/A</span></span> |
| <span data-ttu-id="e3622-366">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="e3622-366">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="e3622-367">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="e3622-367">`1` - enabled</span></span><br/> <span data-ttu-id="e3622-368">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="e3622-368">`0` - disabled</span></span> | <span data-ttu-id="e3622-369">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e3622-369">.NET Core 1.0</span></span> |
| <span data-ttu-id="e3622-370">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="e3622-370">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e3622-371">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="e3622-371">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="e3622-372">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="e3622-372">`1` - enabled</span></span><br/> <span data-ttu-id="e3622-373">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="e3622-373">`0` - disabled</span></span> | <span data-ttu-id="e3622-374">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="e3622-374">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="e3622-375">Büyük nesne yığın eşiği</span><span class="sxs-lookup"><span data-stu-id="e3622-375">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="e3622-376">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="e3622-376">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="e3622-377">Nesnelerin büyük nesne yığınında (LOH) geçmesine neden olan eşik boyutunu bayt cinsinden belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3622-377">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="e3622-378">Varsayılan eşik 85.000 bayttır.</span><span class="sxs-lookup"><span data-stu-id="e3622-378">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="e3622-379">Belirttiğiniz değer varsayılan eşikten büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e3622-379">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="e3622-380">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="e3622-380">Setting name</span></span> | <span data-ttu-id="e3622-381">Değerler</span><span class="sxs-lookup"><span data-stu-id="e3622-381">Values</span></span> | <span data-ttu-id="e3622-382">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e3622-382">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e3622-383">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e3622-383">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="e3622-384">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="e3622-384">*decimal value*</span></span> | <span data-ttu-id="e3622-385">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e3622-385">.NET Core 1.0</span></span> |
| <span data-ttu-id="e3622-386">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="e3622-386">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="e3622-387">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="e3622-387">*hexadecimal value*</span></span> | <span data-ttu-id="e3622-388">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e3622-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="e3622-389">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="e3622-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e3622-390">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="e3622-390">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="e3622-391">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="e3622-391">*decimal value*</span></span> | <span data-ttu-id="e3622-392">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="e3622-392">.NET Framework 4.8</span></span> |

<span data-ttu-id="e3622-393">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e3622-393">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.LOHThreshold": 120000
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="e3622-394">*Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="e3622-394">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="e3622-395">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="e3622-395">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="e3622-396">Örneğin, 120.000 baytlık bir eşik boyutu ayarlamak için, değerler JSON dosyası için 120000, ve ortam değişkeni için 0x1D4C0 ya da 1D4C0 olur.</span><span class="sxs-lookup"><span data-stu-id="e3622-396">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="e3622-397">Tek başına GC</span><span class="sxs-lookup"><span data-stu-id="e3622-397">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="e3622-398">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="e3622-398">COMPlus_GCName</span></span>

- <span data-ttu-id="e3622-399">Çalışma zamanının yüklemeyi amaçladığı çöp toplayıcısını içeren kitaplığın yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3622-399">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="e3622-400">Daha fazla bilgi için bkz. [tek BAŞıNA GC yükleyici tasarımı](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="e3622-400">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="e3622-401">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="e3622-401">Setting name</span></span> | <span data-ttu-id="e3622-402">Değerler</span><span class="sxs-lookup"><span data-stu-id="e3622-402">Values</span></span> | <span data-ttu-id="e3622-403">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e3622-403">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e3622-404">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="e3622-404">**runtimeconfig.json**</span></span> | <span data-ttu-id="e3622-405">Yok</span><span class="sxs-lookup"><span data-stu-id="e3622-405">N/A</span></span> | <span data-ttu-id="e3622-406">Yok</span><span class="sxs-lookup"><span data-stu-id="e3622-406">N/A</span></span> | <span data-ttu-id="e3622-407">Yok</span><span class="sxs-lookup"><span data-stu-id="e3622-407">N/A</span></span> |
| <span data-ttu-id="e3622-408">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="e3622-408">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="e3622-409">*string_path*</span><span class="sxs-lookup"><span data-stu-id="e3622-409">*string_path*</span></span> | <span data-ttu-id="e3622-410">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="e3622-410">.NET Core 2.0</span></span> |
