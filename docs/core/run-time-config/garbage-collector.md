---
title: Çöp toplayıcı yapılandırma ayarları
description: Çöp toplayıcının .NET Core uygulamaları için belleği nasıl yönettiğini yapılandırmak üzere çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 07/10/2020
ms.topic: reference
ms.openlocfilehash: 1bae00d2fc6e80811986bbb111f38582720f8487
ms.sourcegitcommit: 872ca41d1c26f39d0aef57cc365d09503bac780d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2021
ms.locfileid: "106288088"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="989d8-103">Çöp toplama için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="989d8-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="989d8-104">Bu sayfa, çalışma zamanında değiştirilebilen çöp toplayıcı (GC) ayarları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="989d8-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="989d8-105">Çalışan bir uygulamanın en yüksek performans düzeyine ulaşmak istiyorsanız bu ayarları kullanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="989d8-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="989d8-106">Bununla birlikte, varsayılan olarak, çoğu uygulama için tipik durumlarda en iyi performansı sağlar.</span><span class="sxs-lookup"><span data-stu-id="989d8-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="989d8-107">Ayarlar bu sayfadaki gruplar halinde düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="989d8-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="989d8-108">Her grup içindeki ayarlar, belirli bir sonuca ulaşmak için genellikle birbirleriyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="989d8-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="989d8-109">Bu ayarlar ayrıca uygulama çalışırken dinamik olarak değiştirilebilir, bu nedenle ayarladığınız tüm çalışma zamanı ayarları geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="989d8-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="989d8-110">[Gecikme düzeyi](../../standard/garbage-collection/latency.md)gibi bazı ayarlar tipik olarak yalnızca TASARıM zamanında API aracılığıyla ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="989d8-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="989d8-111">Bu tür ayarlar bu sayfadan çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="989d8-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="989d8-112">Sayı değerleri için, dosyadaki *runtimeconfig.js* , ortam değişkeni ayarları için onaltılı gösterimdeki ayarlar için ondalık gösterimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="989d8-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="989d8-113">Onaltılık değerler için, bunları "0x" öneki olmadan veya olmadan belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="989d8-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="989d8-114">Çöp toplamanın türleri</span><span class="sxs-lookup"><span data-stu-id="989d8-114">Flavors of garbage collection</span></span>

<span data-ttu-id="989d8-115">Çöp toplamanın iki ana özellikleri, iş istasyonu GC ve sunucu GC ' dir.</span><span class="sxs-lookup"><span data-stu-id="989d8-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="989d8-116">İkisi arasındaki farklılıklar hakkında daha fazla bilgi için bkz. [Workstation and Server çöp toplama](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="989d8-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="989d8-117">Çöp toplamanın alt türleri arka plan ve eş zamanlı değil.</span><span class="sxs-lookup"><span data-stu-id="989d8-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="989d8-118">Çöp toplamanın türlerini seçmek için aşağıdaki ayarları kullanın:</span><span class="sxs-lookup"><span data-stu-id="989d8-118">Use the following settings to select flavors of garbage collection:</span></span>

- [<span data-ttu-id="989d8-119">İş istasyonu ile sunucu GC</span><span class="sxs-lookup"><span data-stu-id="989d8-119">Workstation vs. server GC</span></span>](#workstation-vs-server)
- [<span data-ttu-id="989d8-120">Arka Plan GC</span><span class="sxs-lookup"><span data-stu-id="989d8-120">Background GC</span></span>](#background-gc)

### <a name="workstation-vs-server"></a><span data-ttu-id="989d8-121">İş istasyonu ile sunucu</span><span class="sxs-lookup"><span data-stu-id="989d8-121">Workstation vs. server</span></span>

- <span data-ttu-id="989d8-122">Uygulamanın iş istasyonu çöp toplamayı veya sunucu çöp toplamayı kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="989d8-122">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="989d8-123">Varsayılan: Iş Istasyonu atık toplama.</span><span class="sxs-lookup"><span data-stu-id="989d8-123">Default: Workstation garbage collection.</span></span> <span data-ttu-id="989d8-124">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="989d8-124">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="989d8-125">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-125">Setting name</span></span> | <span data-ttu-id="989d8-126">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-126">Values</span></span> | <span data-ttu-id="989d8-127">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-127">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-128">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-128">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="989d8-129">`false` -iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="989d8-129">`false` - workstation</span></span><br/><span data-ttu-id="989d8-130">`true` -sunucu</span><span class="sxs-lookup"><span data-stu-id="989d8-130">`true` - server</span></span> | <span data-ttu-id="989d8-131">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="989d8-131">.NET Core 1.0</span></span> |
| <span data-ttu-id="989d8-132">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="989d8-132">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="989d8-133">`false` -iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="989d8-133">`false` - workstation</span></span><br/><span data-ttu-id="989d8-134">`true` -sunucu</span><span class="sxs-lookup"><span data-stu-id="989d8-134">`true` - server</span></span> | <span data-ttu-id="989d8-135">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="989d8-135">.NET Core 1.0</span></span> |
| <span data-ttu-id="989d8-136">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-136">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="989d8-137">`0` -iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="989d8-137">`0` - workstation</span></span><br/><span data-ttu-id="989d8-138">`1` -sunucu</span><span class="sxs-lookup"><span data-stu-id="989d8-138">`1` - server</span></span> | <span data-ttu-id="989d8-139">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="989d8-139">.NET Core 1.0</span></span> |
| <span data-ttu-id="989d8-140">**.NET Framework içinapp.config**</span><span class="sxs-lookup"><span data-stu-id="989d8-140">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="989d8-141">GCServer</span><span class="sxs-lookup"><span data-stu-id="989d8-141">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="989d8-142">`false` -iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="989d8-142">`false` - workstation</span></span><br/><span data-ttu-id="989d8-143">`true` -sunucu</span><span class="sxs-lookup"><span data-stu-id="989d8-143">`true` - server</span></span> |  |

#### <a name="examples"></a><span data-ttu-id="989d8-144">Örnekler</span><span class="sxs-lookup"><span data-stu-id="989d8-144">Examples</span></span>

<span data-ttu-id="989d8-145">*runtimeconfig.js* dosya:</span><span class="sxs-lookup"><span data-stu-id="989d8-145">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="989d8-146">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="989d8-146">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="background-gc"></a><span data-ttu-id="989d8-147">Arka Plan GC</span><span class="sxs-lookup"><span data-stu-id="989d8-147">Background GC</span></span>

- <span data-ttu-id="989d8-148">Arka plan (eşzamanlı) Çöp toplamanın etkinleştirilip etkinleştirilmeyeceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="989d8-148">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="989d8-149">Varsayılan: arka plan GC kullanın.</span><span class="sxs-lookup"><span data-stu-id="989d8-149">Default: Use background GC.</span></span> <span data-ttu-id="989d8-150">Bu değeri değerine ayarlamaya eşdeğerdir `true` .</span><span class="sxs-lookup"><span data-stu-id="989d8-150">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="989d8-151">Daha fazla bilgi için bkz. [arka plan atık toplama](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="989d8-151">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="989d8-152">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-152">Setting name</span></span> | <span data-ttu-id="989d8-153">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-153">Values</span></span> | <span data-ttu-id="989d8-154">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-154">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-155">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-155">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="989d8-156">`true` -arka plan GC</span><span class="sxs-lookup"><span data-stu-id="989d8-156">`true` - background GC</span></span><br/><span data-ttu-id="989d8-157">`false` -eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="989d8-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="989d8-158">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="989d8-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="989d8-159">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="989d8-159">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="989d8-160">`true` -arka plan GC</span><span class="sxs-lookup"><span data-stu-id="989d8-160">`true` - background GC</span></span><br/><span data-ttu-id="989d8-161">`false` -eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="989d8-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="989d8-162">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="989d8-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="989d8-163">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-163">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="989d8-164">`1` -arka plan GC</span><span class="sxs-lookup"><span data-stu-id="989d8-164">`1` - background GC</span></span><br/><span data-ttu-id="989d8-165">`0` -eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="989d8-165">`0` - non-concurrent GC</span></span> | <span data-ttu-id="989d8-166">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="989d8-166">.NET Core 1.0</span></span> |
| <span data-ttu-id="989d8-167">**.NET Framework içinapp.config**</span><span class="sxs-lookup"><span data-stu-id="989d8-167">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="989d8-168">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="989d8-168">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="989d8-169">`true` -arka plan GC</span><span class="sxs-lookup"><span data-stu-id="989d8-169">`true` - background GC</span></span><br/><span data-ttu-id="989d8-170">`false` -eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="989d8-170">`false` - non-concurrent GC</span></span> |  |

#### <a name="examples"></a><span data-ttu-id="989d8-171">Örnekler</span><span class="sxs-lookup"><span data-stu-id="989d8-171">Examples</span></span>

<span data-ttu-id="989d8-172">*runtimeconfig.js* dosya:</span><span class="sxs-lookup"><span data-stu-id="989d8-172">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="989d8-173">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="989d8-173">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="989d8-174">Kaynak kullanımını yönetme</span><span class="sxs-lookup"><span data-stu-id="989d8-174">Manage resource usage</span></span>

<span data-ttu-id="989d8-175">Çöp toplayıcının bellek ve işlemci kullanımını yönetmek için aşağıdaki ayarları kullanın:</span><span class="sxs-lookup"><span data-stu-id="989d8-175">Use the following settings to manage the garbage collector's memory and processor usage:</span></span>

- [<span data-ttu-id="989d8-176">Toplamak</span><span class="sxs-lookup"><span data-stu-id="989d8-176">Affinitize</span></span>](#affinitize)
- [<span data-ttu-id="989d8-177">Maskeyi afleştir</span><span class="sxs-lookup"><span data-stu-id="989d8-177">Affinitize mask</span></span>](#affinitize-mask)
- [<span data-ttu-id="989d8-178">Aralıkları afleştir</span><span class="sxs-lookup"><span data-stu-id="989d8-178">Affinitize ranges</span></span>](#affinitize-ranges)
- [<span data-ttu-id="989d8-179">CPU grupları</span><span class="sxs-lookup"><span data-stu-id="989d8-179">CPU groups</span></span>](#cpu-groups)
- [<span data-ttu-id="989d8-180">Yığın sayısı</span><span class="sxs-lookup"><span data-stu-id="989d8-180">Heap count</span></span>](#heap-count)
- [<span data-ttu-id="989d8-181">Yığın sınırı</span><span class="sxs-lookup"><span data-stu-id="989d8-181">Heap limit</span></span>](#heap-limit)
- [<span data-ttu-id="989d8-182">Yığın sınırı yüzdesi</span><span class="sxs-lookup"><span data-stu-id="989d8-182">Heap limit percent</span></span>](#heap-limit-percent)
- [<span data-ttu-id="989d8-183">Yüksek bellek yüzdesi</span><span class="sxs-lookup"><span data-stu-id="989d8-183">High memory percent</span></span>](#high-memory-percent)
- [<span data-ttu-id="989d8-184">Nesne başına yığın sınırları</span><span class="sxs-lookup"><span data-stu-id="989d8-184">Per-object-heap limits</span></span>](#per-object-heap-limits)
- [<span data-ttu-id="989d8-185">Nesne başına yığın sınırı yüzdesi</span><span class="sxs-lookup"><span data-stu-id="989d8-185">Per-object-heap limit percents</span></span>](#per-object-heap-limit-percents)
- [<span data-ttu-id="989d8-186">VM 'yi koruma</span><span class="sxs-lookup"><span data-stu-id="989d8-186">Retain VM</span></span>](#retain-vm)

<span data-ttu-id="989d8-187">Bu ayarlardan bazıları hakkında daha fazla bilgi için, bkz. [iş istasyonu ve sunucu GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blogu girişi.</span><span class="sxs-lookup"><span data-stu-id="989d8-187">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="heap-count"></a><span data-ttu-id="989d8-188">Yığın sayısı</span><span class="sxs-lookup"><span data-stu-id="989d8-188">Heap count</span></span>

- <span data-ttu-id="989d8-189">Çöp toplayıcı tarafından oluşturulan Heap sayısını sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="989d8-189">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="989d8-190">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="989d8-190">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="989d8-191">[GC işlemci benzeşimi](#affinitize) etkinse, varsayılan olarak, yığın sayısı ayarı `n` GC sayfa@@/iş parçacıklarını ilk işlemcilere göre sayar `n` .</span><span class="sxs-lookup"><span data-stu-id="989d8-191">If [GC processor affinity](#affinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="989d8-192">(Tam olarak hangi işlemcilerin olduğunu belirtmek için, bu [maskeyi](#affinitize-mask) seçin veya [aralıklar](#affinitize-ranges) ayarlarını kesin olarak belirleyin.)</span><span class="sxs-lookup"><span data-stu-id="989d8-192">(Use the [affinitize mask](#affinitize-mask) or [affinitize ranges](#affinitize-ranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="989d8-193">[GC işlemci benzeşimi](#affinitize) devre dışıysa, bu ayar GC yığınlarının sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="989d8-193">If [GC processor affinity](#affinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="989d8-194">Daha fazla bilgi için [Gcheapcount açıklamalarını](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)inceleyin.</span><span class="sxs-lookup"><span data-stu-id="989d8-194">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="989d8-195">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-195">Setting name</span></span> | <span data-ttu-id="989d8-196">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-196">Values</span></span> | <span data-ttu-id="989d8-197">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-197">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-198">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-198">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="989d8-199">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-199">*decimal value*</span></span> | <span data-ttu-id="989d8-200">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="989d8-200">.NET Core 3.0</span></span> |
| <span data-ttu-id="989d8-201">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-201">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="989d8-202">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-202">*hexadecimal value*</span></span> | <span data-ttu-id="989d8-203">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="989d8-203">.NET Core 3.0</span></span> |
| <span data-ttu-id="989d8-204">**.NET Framework içinapp.config**</span><span class="sxs-lookup"><span data-stu-id="989d8-204">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="989d8-205">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="989d8-205">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="989d8-206">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-206">*decimal value*</span></span> | <span data-ttu-id="989d8-207">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="989d8-207">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="989d8-208">Örnek:</span><span class="sxs-lookup"><span data-stu-id="989d8-208">Example:</span></span>

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
> <span data-ttu-id="989d8-209">*Üzerinderuntimeconfig.js* seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="989d8-209">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="989d8-210">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="989d8-210">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="989d8-211">Örneğin, Heap sayısını 16 ile sınırlamak için değerler JSON dosyası için 16, ortam değişkeni için 0x10 veya 10 olur.</span><span class="sxs-lookup"><span data-stu-id="989d8-211">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="affinitize-mask"></a><span data-ttu-id="989d8-212">Maskeyi afleştir</span><span class="sxs-lookup"><span data-stu-id="989d8-212">Affinitize mask</span></span>

- <span data-ttu-id="989d8-213">Çöp toplayıcı iş parçacıklarının kullanması gereken tam işlemcileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="989d8-213">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="989d8-214">[GC işlemci benzeşimi](#affinitize) devre dışıysa, bu ayar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="989d8-214">If [GC processor affinity](#affinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="989d8-215">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="989d8-215">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="989d8-216">Değer, işlem için kullanılabilir olan işlemcileri tanımlayan bir bit maskesidir.</span><span class="sxs-lookup"><span data-stu-id="989d8-216">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="989d8-217">Örneğin, bir 1023 ondalık değeri (veya ortam değişkenini kullanıyorsanız, 0x3FF veya 3FF onaltılı değeri), ikili gösterimde 0011 1111 1111 ' dir.</span><span class="sxs-lookup"><span data-stu-id="989d8-217">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="989d8-218">Bu, ilk 10 işlemcinin kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="989d8-218">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="989d8-219">Sıradaki 10 işlemciyi belirtmek için, işlemci 10-19 ' 1047552 nin ondalık değerini (veya 0xFFC00 ya da FFC00) bir 1111 1111 1100 0000 0000 ikili değere eşdeğer bir değere belirleyin.</span><span class="sxs-lookup"><span data-stu-id="989d8-219">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="989d8-220">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-220">Setting name</span></span> | <span data-ttu-id="989d8-221">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-221">Values</span></span> | <span data-ttu-id="989d8-222">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-222">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-223">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-223">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="989d8-224">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-224">*decimal value*</span></span> | <span data-ttu-id="989d8-225">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="989d8-225">.NET Core 3.0</span></span> |
| <span data-ttu-id="989d8-226">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-226">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="989d8-227">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-227">*hexadecimal value*</span></span> | <span data-ttu-id="989d8-228">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="989d8-228">.NET Core 3.0</span></span> |
| <span data-ttu-id="989d8-229">**.NET Framework içinapp.config**</span><span class="sxs-lookup"><span data-stu-id="989d8-229">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="989d8-230">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="989d8-230">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="989d8-231">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-231">*decimal value*</span></span> | <span data-ttu-id="989d8-232">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="989d8-232">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="989d8-233">Örnek:</span><span class="sxs-lookup"><span data-stu-id="989d8-233">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="affinitize-ranges"></a><span data-ttu-id="989d8-234">Aralıkları afleştir</span><span class="sxs-lookup"><span data-stu-id="989d8-234">Affinitize ranges</span></span>

- <span data-ttu-id="989d8-235">Çöp toplayıcı iş parçacıkları için kullanılacak işlemcilerin listesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="989d8-235">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="989d8-236">Bu ayar [System. GC. Cenpaffinitizemask](#affinitize-mask)ile benzerdir, ancak 64 'den fazla işlemci belirtmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="989d8-236">This setting is similar to [System.GC.HeapAffinitizeMask](#affinitize-mask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="989d8-237">Windows işletim sistemleri için, işlemci numarasını veya aralığını karşılık gelen [CPU grubuyla](/windows/win32/procthread/processor-groups)önek olarak ekleyin, örneğin, "0:1-10, 0:12, 1:50-52, 1:70".</span><span class="sxs-lookup"><span data-stu-id="989d8-237">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="989d8-238">[GC işlemci benzeşimi](#affinitize) devre dışıysa, bu ayar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="989d8-238">If [GC processor affinity](#affinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="989d8-239">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="989d8-239">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="989d8-240">Daha fazla bilgi için bkz. Maoni Stephens ' blogu üzerinde [> 64 CPU 'su olan MAKINELERDE GC için daha Iyi hale getirme](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) .</span><span class="sxs-lookup"><span data-stu-id="989d8-240">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="989d8-241">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-241">Setting name</span></span> | <span data-ttu-id="989d8-242">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-242">Values</span></span> | <span data-ttu-id="989d8-243">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-243">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-244">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-244">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="989d8-245">İşlemci numaralarının veya işlemci numarası aralıklarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="989d8-245">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="989d8-246">UNIX örneği: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="989d8-246">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="989d8-247">Windows örnek: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="989d8-247">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="989d8-248">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="989d8-248">.NET Core 3.0</span></span> |
| <span data-ttu-id="989d8-249">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-249">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="989d8-250">İşlemci numaralarının veya işlemci numarası aralıklarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="989d8-250">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="989d8-251">UNIX örneği: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="989d8-251">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="989d8-252">Windows örnek: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="989d8-252">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="989d8-253">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="989d8-253">.NET Core 3.0</span></span> |

<span data-ttu-id="989d8-254">Örnek:</span><span class="sxs-lookup"><span data-stu-id="989d8-254">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="cpu-groups"></a><span data-ttu-id="989d8-255">CPU grupları</span><span class="sxs-lookup"><span data-stu-id="989d8-255">CPU groups</span></span>

- <span data-ttu-id="989d8-256">Çöp toplayıcının [CPU grupları](/windows/win32/procthread/processor-groups) kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="989d8-256">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="989d8-257">64 bitlik bir Windows bilgisayarında birden çok CPU grubu olduğunda, diğer bir deyişle, 64 ' den fazla işlemci varsa, bu öğenin tüm CPU gruplarında çöp toplamayı genişletmelerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="989d8-257">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="989d8-258">Çöp toplayıcı, Heap 'ler oluşturmak ve dengelemek için tüm çekirdekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="989d8-258">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="989d8-259">Yalnızca 64-bit Windows işletim sistemlerinde sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="989d8-259">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="989d8-260">Varsayılan: GC, CPU grupları arasında genişletilmez.</span><span class="sxs-lookup"><span data-stu-id="989d8-260">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="989d8-261">Bu değeri değerine ayarlamaya eşdeğerdir `0` .</span><span class="sxs-lookup"><span data-stu-id="989d8-261">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="989d8-262">Daha fazla bilgi için bkz. Maoni Stephens ' blogu üzerinde [> 64 CPU 'su olan MAKINELERDE GC için daha Iyi hale getirme](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) .</span><span class="sxs-lookup"><span data-stu-id="989d8-262">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="989d8-263">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-263">Setting name</span></span> | <span data-ttu-id="989d8-264">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-264">Values</span></span> | <span data-ttu-id="989d8-265">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-265">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-266">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-266">**runtimeconfig.json**</span></span> | `System.GC.CpuGroup` | <span data-ttu-id="989d8-267">`0` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="989d8-267">`0` - disabled</span></span><br/><span data-ttu-id="989d8-268">`1` -etkin</span><span class="sxs-lookup"><span data-stu-id="989d8-268">`1` - enabled</span></span> | <span data-ttu-id="989d8-269">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="989d8-269">.NET 5.0</span></span> |
| <span data-ttu-id="989d8-270">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-270">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="989d8-271">`0` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="989d8-271">`0` - disabled</span></span><br/><span data-ttu-id="989d8-272">`1` -etkin</span><span class="sxs-lookup"><span data-stu-id="989d8-272">`1` - enabled</span></span> | <span data-ttu-id="989d8-273">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="989d8-273">.NET Core 1.0</span></span> |
| <span data-ttu-id="989d8-274">**.NET Framework içinapp.config**</span><span class="sxs-lookup"><span data-stu-id="989d8-274">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="989d8-275">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="989d8-275">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="989d8-276">`false` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="989d8-276">`false` - disabled</span></span><br/><span data-ttu-id="989d8-277">`true` -etkin</span><span class="sxs-lookup"><span data-stu-id="989d8-277">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="989d8-278">Ortak dil çalışma zamanını (CLR) tüm CPU grupları arasında iş parçacığı havuzundan da dağıtmak üzere yapılandırmak için, [Thread_UseAllCpuGroups öğesi](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) seçeneğini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="989d8-278">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="989d8-279">.NET Core uygulamaları için, ortam değişkeninin değerini olarak ayarlayarak bu seçeneği etkinleştirebilirsiniz `COMPlus_Thread_UseAllCpuGroups` `1` .</span><span class="sxs-lookup"><span data-stu-id="989d8-279">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="affinitize"></a><span data-ttu-id="989d8-280">Toplamak</span><span class="sxs-lookup"><span data-stu-id="989d8-280">Affinitize</span></span>

- <span data-ttu-id="989d8-281">*Çöp toplama* iş parçacıklarının işlemcilerle kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="989d8-281">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="989d8-282">Bir GC iş parçacığını eklemek için yalnızca belirli bir CPU üzerinde çalışabilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="989d8-282">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="989d8-283">Her GC iş parçacığı için bir yığın oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="989d8-283">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="989d8-284">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="989d8-284">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="989d8-285">Varsayılan: işlemcilere sahip çöp toplama iş parçacıklarını ön olarak başlatma.</span><span class="sxs-lookup"><span data-stu-id="989d8-285">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="989d8-286">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="989d8-286">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="989d8-287">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-287">Setting name</span></span> | <span data-ttu-id="989d8-288">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-288">Values</span></span> | <span data-ttu-id="989d8-289">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-289">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-290">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-290">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="989d8-291">`false` -afze</span><span class="sxs-lookup"><span data-stu-id="989d8-291">`false` - affinitize</span></span><br/><span data-ttu-id="989d8-292">`true` -yok etme</span><span class="sxs-lookup"><span data-stu-id="989d8-292">`true` - don't affinitize</span></span> | <span data-ttu-id="989d8-293">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="989d8-293">.NET Core 3.0</span></span> |
| <span data-ttu-id="989d8-294">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-294">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="989d8-295">`0` -afze</span><span class="sxs-lookup"><span data-stu-id="989d8-295">`0` - affinitize</span></span><br/><span data-ttu-id="989d8-296">`1` -yok etme</span><span class="sxs-lookup"><span data-stu-id="989d8-296">`1` - don't affinitize</span></span> | <span data-ttu-id="989d8-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="989d8-297">.NET Core 3.0</span></span> |
| <span data-ttu-id="989d8-298">**.NET Framework içinapp.config**</span><span class="sxs-lookup"><span data-stu-id="989d8-298">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="989d8-299">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="989d8-299">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="989d8-300">`false` -afze</span><span class="sxs-lookup"><span data-stu-id="989d8-300">`false` - affinitize</span></span><br/><span data-ttu-id="989d8-301">`true` -yok etme</span><span class="sxs-lookup"><span data-stu-id="989d8-301">`true` - don't affinitize</span></span> | <span data-ttu-id="989d8-302">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="989d8-302">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="989d8-303">Örnek:</span><span class="sxs-lookup"><span data-stu-id="989d8-303">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="heap-limit"></a><span data-ttu-id="989d8-304">Yığın sınırı</span><span class="sxs-lookup"><span data-stu-id="989d8-304">Heap limit</span></span>

- <span data-ttu-id="989d8-305">GC yığını ve GC booksaklanması için bayt cinsinden en fazla tamamlama boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="989d8-305">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="989d8-306">Bu ayar yalnızca 64 bitlik bilgisayarlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="989d8-306">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="989d8-307">[Nesne başına yığın sınırları](#per-object-heap-limits) yapılandırılırsa Bu ayar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="989d8-307">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="989d8-308">Yalnızca belirli durumlarda geçerli olan varsayılan değer, kapsayıcıdaki bellek sınırının 20 MB veya %75 ' sinden daha fazladır.</span><span class="sxs-lookup"><span data-stu-id="989d8-308">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="989d8-309">Varsayılan değer şu durumlarda geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="989d8-309">The default value applies if:</span></span>

  - <span data-ttu-id="989d8-310">İşlem belirtilen bellek sınırına sahip bir kapsayıcı içinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="989d8-310">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="989d8-311">[System. GC. HeapHardLimitPercent](#heap-limit-percent) ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="989d8-311">[System.GC.HeapHardLimitPercent](#heap-limit-percent) is not set.</span></span>

| | <span data-ttu-id="989d8-312">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-312">Setting name</span></span> | <span data-ttu-id="989d8-313">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-313">Values</span></span> | <span data-ttu-id="989d8-314">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-314">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-315">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-315">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="989d8-316">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-316">*decimal value*</span></span> | <span data-ttu-id="989d8-317">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="989d8-317">.NET Core 3.0</span></span> |
| <span data-ttu-id="989d8-318">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-318">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="989d8-319">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-319">*hexadecimal value*</span></span> | <span data-ttu-id="989d8-320">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="989d8-320">.NET Core 3.0</span></span> |

<span data-ttu-id="989d8-321">Örnek:</span><span class="sxs-lookup"><span data-stu-id="989d8-321">Example:</span></span>

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
> <span data-ttu-id="989d8-322">*Üzerinderuntimeconfig.js* seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="989d8-322">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="989d8-323">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="989d8-323">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="989d8-324">Örneğin, 200 mebibytes (MIB) yığın sabit sınırı belirtmek için, değerler JSON dosyası için 209715200 ve ortam değişkeni için 0xC800000 veya C800000 olur.</span><span class="sxs-lookup"><span data-stu-id="989d8-324">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="heap-limit-percent"></a><span data-ttu-id="989d8-325">Yığın sınırı yüzdesi</span><span class="sxs-lookup"><span data-stu-id="989d8-325">Heap limit percent</span></span>

- <span data-ttu-id="989d8-326">Toplam fiziksel belleğin yüzdesi olarak izin verilen GC yığın kullanımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="989d8-326">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="989d8-327">[System. GC. HeapHardLimit](#heap-limit) da ayarlandıysa, bu ayar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="989d8-327">If [System.GC.HeapHardLimit](#heap-limit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="989d8-328">Bu ayar yalnızca 64 bitlik bilgisayarlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="989d8-328">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="989d8-329">İşlem belirtilen bellek sınırına sahip bir kapsayıcı içinde çalışıyorsa, yüzde bu bellek sınırının yüzdesi olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="989d8-329">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="989d8-330">[Nesne başına yığın sınırları](#per-object-heap-limits) yapılandırılırsa Bu ayar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="989d8-330">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="989d8-331">Yalnızca belirli durumlarda geçerli olan varsayılan değer, kapsayıcıdaki bellek sınırının 20 MB veya %75 ' sinden daha fazladır.</span><span class="sxs-lookup"><span data-stu-id="989d8-331">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="989d8-332">Varsayılan değer şu durumlarda geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="989d8-332">The default value applies if:</span></span>

  - <span data-ttu-id="989d8-333">İşlem belirtilen bellek sınırına sahip bir kapsayıcı içinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="989d8-333">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="989d8-334">[System. GC. HeapHardLimit](#heap-limit) ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="989d8-334">[System.GC.HeapHardLimit](#heap-limit) is not set.</span></span>

| | <span data-ttu-id="989d8-335">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-335">Setting name</span></span> | <span data-ttu-id="989d8-336">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-336">Values</span></span> | <span data-ttu-id="989d8-337">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-337">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-338">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-338">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="989d8-339">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-339">*decimal value*</span></span> | <span data-ttu-id="989d8-340">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="989d8-340">.NET Core 3.0</span></span> |
| <span data-ttu-id="989d8-341">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-341">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="989d8-342">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-342">*hexadecimal value*</span></span> | <span data-ttu-id="989d8-343">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="989d8-343">.NET Core 3.0</span></span> |

<span data-ttu-id="989d8-344">Örnek:</span><span class="sxs-lookup"><span data-stu-id="989d8-344">Example:</span></span>

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
> <span data-ttu-id="989d8-345">*Üzerinderuntimeconfig.js* seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="989d8-345">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="989d8-346">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="989d8-346">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="989d8-347">Örneğin, yığın kullanımını %30 olarak sınırlandırmak için değerler JSON dosyası için 30, ortam değişkeni için 0x1E veya 1E olur.</span><span class="sxs-lookup"><span data-stu-id="989d8-347">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="per-object-heap-limits"></a><span data-ttu-id="989d8-348">Nesne başına yığın sınırları</span><span class="sxs-lookup"><span data-stu-id="989d8-348">Per-object-heap limits</span></span>

<span data-ttu-id="989d8-349">GC 'nin izin verilen yığın kullanımını nesne başına yığın temelinde belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="989d8-349">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="989d8-350">Farklı sayfa@@ 'ler büyük nesne yığını (LOH), küçük nesne yığını (SoH) ve sabitlenmiş nesne yığını (POH).</span><span class="sxs-lookup"><span data-stu-id="989d8-350">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

- <span data-ttu-id="989d8-351">, Veya ayarlarından herhangi biri için bir değer belirtirseniz `COMPLUS_GCHeapHardLimitSOH` `COMPLUS_GCHeapHardLimitLOH` `COMPLUS_GCHeapHardLimitPOH` , ve için bir değer de belirtmeniz gerekir `COMPLUS_GCHeapHardLimitSOH` `COMPLUS_GCHeapHardLimitLOH` .</span><span class="sxs-lookup"><span data-stu-id="989d8-351">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, or `COMPLUS_GCHeapHardLimitPOH` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH`.</span></span> <span data-ttu-id="989d8-352">Aksi takdirde, çalışma zamanı başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="989d8-352">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="989d8-353">İçin varsayılan değer `COMPLUS_GCHeapHardLimitPOH` 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="989d8-353">The default value for `COMPLUS_GCHeapHardLimitPOH` is 0.</span></span> <span data-ttu-id="989d8-354">`COMPLUS_GCHeapHardLimitSOH` ve `COMPLUS_GCHeapHardLimitLOH` varsayılan değerlere sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="989d8-354">`COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH` don't have default values.</span></span>

| | <span data-ttu-id="989d8-355">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-355">Setting name</span></span> | <span data-ttu-id="989d8-356">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-356">Values</span></span> | <span data-ttu-id="989d8-357">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-357">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-358">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-358">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitSOH` | <span data-ttu-id="989d8-359">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-359">*decimal value*</span></span> | <span data-ttu-id="989d8-360">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="989d8-360">.NET 5.0</span></span> |
| <span data-ttu-id="989d8-361">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-361">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOH` | <span data-ttu-id="989d8-362">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-362">*hexadecimal value*</span></span> | <span data-ttu-id="989d8-363">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="989d8-363">.NET 5.0</span></span> |

| | <span data-ttu-id="989d8-364">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-364">Setting name</span></span> | <span data-ttu-id="989d8-365">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-365">Values</span></span> | <span data-ttu-id="989d8-366">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-366">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-367">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-367">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitLOH` | <span data-ttu-id="989d8-368">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-368">*decimal value*</span></span> | <span data-ttu-id="989d8-369">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="989d8-369">.NET 5.0</span></span> |
| <span data-ttu-id="989d8-370">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-370">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOH` | <span data-ttu-id="989d8-371">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-371">*hexadecimal value*</span></span> | <span data-ttu-id="989d8-372">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="989d8-372">.NET 5.0</span></span> |

| | <span data-ttu-id="989d8-373">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-373">Setting name</span></span> | <span data-ttu-id="989d8-374">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-374">Values</span></span> | <span data-ttu-id="989d8-375">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-375">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-376">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-376">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPOH` | <span data-ttu-id="989d8-377">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-377">*decimal value*</span></span> | <span data-ttu-id="989d8-378">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="989d8-378">.NET 5.0</span></span> |
| <span data-ttu-id="989d8-379">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-379">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOH` | <span data-ttu-id="989d8-380">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-380">*hexadecimal value*</span></span> | <span data-ttu-id="989d8-381">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="989d8-381">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="989d8-382">*Üzerinderuntimeconfig.js* seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="989d8-382">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="989d8-383">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="989d8-383">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="989d8-384">Örneğin, 200 mebibytes (MIB) yığın sabit sınırı belirtmek için, değerler JSON dosyası için 209715200 ve ortam değişkeni için 0xC800000 veya C800000 olur.</span><span class="sxs-lookup"><span data-stu-id="989d8-384">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="per-object-heap-limit-percents"></a><span data-ttu-id="989d8-385">Nesne başına yığın sınırı yüzdesi</span><span class="sxs-lookup"><span data-stu-id="989d8-385">Per-object-heap limit percents</span></span>

<span data-ttu-id="989d8-386">GC 'nin izin verilen yığın kullanımını nesne başına yığın temelinde belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="989d8-386">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="989d8-387">Farklı sayfa@@ 'ler büyük nesne yığını (LOH), küçük nesne yığını (SoH) ve sabitlenmiş nesne yığını (POH).</span><span class="sxs-lookup"><span data-stu-id="989d8-387">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

- <span data-ttu-id="989d8-388">, Veya ayarlarından herhangi biri için bir değer belirtirseniz `COMPLUS_GCHeapHardLimitSOHPercent` `COMPLUS_GCHeapHardLimitLOHPercent` `COMPLUS_GCHeapHardLimitPOHPercent` , ve için bir değer de belirtmeniz gerekir `COMPLUS_GCHeapHardLimitSOHPercent` `COMPLUS_GCHeapHardLimitLOHPercent` .</span><span class="sxs-lookup"><span data-stu-id="989d8-388">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOHPercent`, `COMPLUS_GCHeapHardLimitLOHPercent`, or `COMPLUS_GCHeapHardLimitPOHPercent` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOHPercent` and `COMPLUS_GCHeapHardLimitLOHPercent`.</span></span> <span data-ttu-id="989d8-389">Aksi takdirde, çalışma zamanı başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="989d8-389">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="989d8-390">`COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH` , Ve belirtildiğinde bu ayarlar yoksayılır `COMPLUS_GCHeapHardLimitPOH` .</span><span class="sxs-lookup"><span data-stu-id="989d8-390">These settings are ignored if `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, and `COMPLUS_GCHeapHardLimitPOH` are specified.</span></span>
- <span data-ttu-id="989d8-391">1 değeri, GC 'nin bu nesne yığını için toplam fiziksel belleğin %1 ' i kullanması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="989d8-391">A value of 1 means that GC uses 1% of total physical memory for that object heap.</span></span>
- <span data-ttu-id="989d8-392">Her değerin sıfırdan büyük ve 100 ' den küçük olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="989d8-392">Each value must be greater than zero and less than 100.</span></span> <span data-ttu-id="989d8-393">Ayrıca, üç yüzde değerinin toplamı 100 ' den az olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="989d8-393">Additionally, the sum of the three percentage values must be less than 100.</span></span> <span data-ttu-id="989d8-394">Aksi takdirde, çalışma zamanı başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="989d8-394">Otherwise, the runtime will fail to initialize.</span></span>

| | <span data-ttu-id="989d8-395">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-395">Setting name</span></span> | <span data-ttu-id="989d8-396">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-396">Values</span></span> | <span data-ttu-id="989d8-397">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-397">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-398">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-398">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitSOHPercent` | <span data-ttu-id="989d8-399">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-399">*decimal value*</span></span> | <span data-ttu-id="989d8-400">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="989d8-400">.NET 5.0</span></span> |
| <span data-ttu-id="989d8-401">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-401">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOHPercent` | <span data-ttu-id="989d8-402">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-402">*hexadecimal value*</span></span> | <span data-ttu-id="989d8-403">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="989d8-403">.NET 5.0</span></span> |

| | <span data-ttu-id="989d8-404">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-404">Setting name</span></span> | <span data-ttu-id="989d8-405">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-405">Values</span></span> | <span data-ttu-id="989d8-406">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-406">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-407">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-407">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitLOHPercent` | <span data-ttu-id="989d8-408">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-408">*decimal value*</span></span> | <span data-ttu-id="989d8-409">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="989d8-409">.NET 5.0</span></span> |
| <span data-ttu-id="989d8-410">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-410">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOHPercent` | <span data-ttu-id="989d8-411">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-411">*hexadecimal value*</span></span> | <span data-ttu-id="989d8-412">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="989d8-412">.NET 5.0</span></span> |

| | <span data-ttu-id="989d8-413">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-413">Setting name</span></span> | <span data-ttu-id="989d8-414">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-414">Values</span></span> | <span data-ttu-id="989d8-415">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-415">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-416">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-416">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPOHPercent` | <span data-ttu-id="989d8-417">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-417">*decimal value*</span></span> | <span data-ttu-id="989d8-418">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="989d8-418">.NET 5.0</span></span> |
| <span data-ttu-id="989d8-419">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-419">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOHPercent` | <span data-ttu-id="989d8-420">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-420">*hexadecimal value*</span></span> | <span data-ttu-id="989d8-421">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="989d8-421">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="989d8-422">*Üzerinderuntimeconfig.js* seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="989d8-422">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="989d8-423">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="989d8-423">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="989d8-424">Örneğin, yığın kullanımını %30 olarak sınırlandırmak için değerler JSON dosyası için 30, ortam değişkeni için 0x1E veya 1E olur.</span><span class="sxs-lookup"><span data-stu-id="989d8-424">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="high-memory-percent"></a><span data-ttu-id="989d8-425">Yüksek bellek yüzdesi</span><span class="sxs-lookup"><span data-stu-id="989d8-425">High memory percent</span></span>

<span data-ttu-id="989d8-426">Bellek yükü, kullanımdaki fiziksel bellek yüzdesi ile belirtilir.</span><span class="sxs-lookup"><span data-stu-id="989d8-426">Memory load is indicated by the percentage of physical memory in use.</span></span> <span data-ttu-id="989d8-427">Varsayılan olarak, fiziksel bellek yükü **%90**' a ulaştığında çöp toplama işlemi, sayfalama önlemek için atık koleksiyonları düzenleme konusunda daha agresif hale gelir.</span><span class="sxs-lookup"><span data-stu-id="989d8-427">By default, when the physical memory load reaches **90%**, garbage collection becomes more aggressive about doing full, compacting garbage collections to avoid paging.</span></span> <span data-ttu-id="989d8-428">Bellek yükü %90 altındaysa, GC, daha kısa duraklamalar olan ancak toplam yığın boyutunu çok azalyan tüm çöp koleksiyonları için arka plan koleksiyonlarını tercih eder.</span><span class="sxs-lookup"><span data-stu-id="989d8-428">When memory load is below 90%, GC favors background collections for full garbage collections, which have shorter pauses but don't reduce the total heap size by much.</span></span> <span data-ttu-id="989d8-429">Önemli miktarda belleğe (80GB veya daha fazla) sahip makinelerde, varsayılan yükleme eşiği %90 ile %97 arasındadır.</span><span class="sxs-lookup"><span data-stu-id="989d8-429">On machines with a significant amount of memory (80GB or more), the default load threshold is between 90% and 97%.</span></span>

<span data-ttu-id="989d8-430">Yüksek bellek yükü eşiği, `COMPlus_GCHighMemPercent` ortam değişkeni veya `System.GC.HighMemoryPercent` JSON yapılandırma ayarı tarafından ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="989d8-430">The high memory load threshold can be adjusted by the `COMPlus_GCHighMemPercent` environment variable or `System.GC.HighMemoryPercent` JSON configuration setting.</span></span> <span data-ttu-id="989d8-431">Yığın boyutunu denetlemek istiyorsanız eşiği ayarlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="989d8-431">Consider adjusting the threshold if you want to control heap size.</span></span> <span data-ttu-id="989d8-432">Örneğin, 64 GB bellek içeren bir makinedeki baskın işlem için, kullanılabilir belleğin %10 ' u olduğunda GC 'nin yeniden davranmasını sağlamak mantıklıdır.</span><span class="sxs-lookup"><span data-stu-id="989d8-432">For example, for the dominant process on a machine with 64GB of memory, it's reasonable for GC to start reacting when there's 10% of memory available.</span></span> <span data-ttu-id="989d8-433">Ancak, daha küçük işlemler için, örneğin yalnızca 1 GB bellek tüketen bir işlem, kullanılabilir belleğin %10 ' dan az olan GC çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="989d8-433">But for smaller processes, for example, a process that only consumes 1GB of memory, GC can comfortably run with less than 10% of memory available.</span></span> <span data-ttu-id="989d8-434">Bu daha küçük süreçler için eşiği daha yüksek olarak ayarlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="989d8-434">For these smaller processes, consider setting the threshold higher.</span></span> <span data-ttu-id="989d8-435">Öte yandan, büyük işlemlerin daha küçük yığın boyutlarına sahip olmasını istiyorsanız (kullanılabilir fiziksel bellek miktarı olsa bile), bu eşiği düşürmek GC 'nin yığını daha erken sıkıştırmak için etkili bir şekilde tepki vermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="989d8-435">On the other hand, if you want larger processes to have smaller heap sizes (even when there's plenty of physical memory available), lowering this threshold is an effective way for GC to react sooner to compact the heap down.</span></span>

> [!NOTE]
> <span data-ttu-id="989d8-436">Bir kapsayıcıda çalışan süreçler için, GC fiziksel belleği kapsayıcı sınırına göre değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="989d8-436">For processes running in a container, GC considers the physical memory based on the container limit.</span></span>

| | <span data-ttu-id="989d8-437">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-437">Setting name</span></span> | <span data-ttu-id="989d8-438">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-438">Values</span></span> | <span data-ttu-id="989d8-439">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-439">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-440">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-440">**runtimeconfig.json**</span></span> | `System.GC.HighMemoryPercent` | <span data-ttu-id="989d8-441">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-441">*decimal value*</span></span> | <span data-ttu-id="989d8-442">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="989d8-442">.NET 5.0</span></span> |
| <span data-ttu-id="989d8-443">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-443">**Environment variable**</span></span> | `COMPlus_GCHighMemPercent` | <span data-ttu-id="989d8-444">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-444">*hexadecimal value*</span></span> | |

> [!TIP]
> <span data-ttu-id="989d8-445">*Üzerinderuntimeconfig.js* seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="989d8-445">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="989d8-446">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="989d8-446">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="989d8-447">Örneğin, yüksek bellek eşiğini %75 olarak ayarlamak için, değerler JSON dosyası için 75 ve ortam değişkeni için 0x4B veya 4B olacaktır.</span><span class="sxs-lookup"><span data-stu-id="989d8-447">For example, to set the high memory threshold to 75%, the values would be 75 for the JSON file and 0x4B or 4B for the environment variable.</span></span>

### <a name="retain-vm"></a><span data-ttu-id="989d8-448">VM 'yi koruma</span><span class="sxs-lookup"><span data-stu-id="989d8-448">Retain VM</span></span>

- <span data-ttu-id="989d8-449">Silinmesi gereken segmentlerin ileride kullanılmak üzere bir bekleme listesine mi yerleştirileceğini, yoksa işletim sistemine (OS) geri mi bırakılacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="989d8-449">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="989d8-450">Varsayılan: kesimleri işletim sistemine geri bırakın.</span><span class="sxs-lookup"><span data-stu-id="989d8-450">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="989d8-451">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="989d8-451">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="989d8-452">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-452">Setting name</span></span> | <span data-ttu-id="989d8-453">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-453">Values</span></span> | <span data-ttu-id="989d8-454">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-454">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-455">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-455">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="989d8-456">`false` -işletim sistemine yayın</span><span class="sxs-lookup"><span data-stu-id="989d8-456">`false` - release to OS</span></span><br/><span data-ttu-id="989d8-457">`true` -bekleme durumuna koy</span><span class="sxs-lookup"><span data-stu-id="989d8-457">`true` - put on standby</span></span> | <span data-ttu-id="989d8-458">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="989d8-458">.NET Core 1.0</span></span> |
| <span data-ttu-id="989d8-459">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="989d8-459">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="989d8-460">`false` -işletim sistemine yayın</span><span class="sxs-lookup"><span data-stu-id="989d8-460">`false` - release to OS</span></span><br/><span data-ttu-id="989d8-461">`true` -bekleme durumuna koy</span><span class="sxs-lookup"><span data-stu-id="989d8-461">`true` - put on standby</span></span> | <span data-ttu-id="989d8-462">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="989d8-462">.NET Core 1.0</span></span> |
| <span data-ttu-id="989d8-463">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-463">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="989d8-464">`0` -işletim sistemine yayın</span><span class="sxs-lookup"><span data-stu-id="989d8-464">`0` - release to OS</span></span><br/><span data-ttu-id="989d8-465">`1` -bekleme durumuna koy</span><span class="sxs-lookup"><span data-stu-id="989d8-465">`1` - put on standby</span></span> | <span data-ttu-id="989d8-466">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="989d8-466">.NET Core 1.0</span></span> |

#### <a name="examples"></a><span data-ttu-id="989d8-467">Örnekler</span><span class="sxs-lookup"><span data-stu-id="989d8-467">Examples</span></span>

<span data-ttu-id="989d8-468">*runtimeconfig.js* dosya:</span><span class="sxs-lookup"><span data-stu-id="989d8-468">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="989d8-469">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="989d8-469">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="989d8-470">Büyük sayfalar</span><span class="sxs-lookup"><span data-stu-id="989d8-470">Large pages</span></span>

- <span data-ttu-id="989d8-471">Bir yığın sabit sınırı ayarlandığında büyük sayfaların kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="989d8-471">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="989d8-472">Varsayılan: bir yığın sabit sınırı ayarlandığında büyük sayfalar kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="989d8-472">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="989d8-473">Bu değeri değerine ayarlamaya eşdeğerdir `0` .</span><span class="sxs-lookup"><span data-stu-id="989d8-473">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="989d8-474">Bu bir deneysel ayardır.</span><span class="sxs-lookup"><span data-stu-id="989d8-474">This is an experimental setting.</span></span>

| | <span data-ttu-id="989d8-475">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-475">Setting name</span></span> | <span data-ttu-id="989d8-476">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-476">Values</span></span> | <span data-ttu-id="989d8-477">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-477">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-478">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-478">**runtimeconfig.json**</span></span> | <span data-ttu-id="989d8-479">Yok</span><span class="sxs-lookup"><span data-stu-id="989d8-479">N/A</span></span> | <span data-ttu-id="989d8-480">Yok</span><span class="sxs-lookup"><span data-stu-id="989d8-480">N/A</span></span> | <span data-ttu-id="989d8-481">Yok</span><span class="sxs-lookup"><span data-stu-id="989d8-481">N/A</span></span> |
| <span data-ttu-id="989d8-482">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-482">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="989d8-483">`0` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="989d8-483">`0` - disabled</span></span><br/><span data-ttu-id="989d8-484">`1` -etkin</span><span class="sxs-lookup"><span data-stu-id="989d8-484">`1` - enabled</span></span> | <span data-ttu-id="989d8-485">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="989d8-485">.NET Core 3.0</span></span> |

## <a name="allow-large-objects"></a><span data-ttu-id="989d8-486">Büyük nesnelere izin ver</span><span class="sxs-lookup"><span data-stu-id="989d8-486">Allow large objects</span></span>

- <span data-ttu-id="989d8-487">Toplam boyuttaki 2 gigabayttan (GB) büyük olan diziler için 64 bitlik platformlarda çöp toplayıcı desteğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="989d8-487">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="989d8-488">Varsayılan: GC 2 GB 'tan büyük dizileri destekler.</span><span class="sxs-lookup"><span data-stu-id="989d8-488">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="989d8-489">Bu değeri değerine ayarlamaya eşdeğerdir `1` .</span><span class="sxs-lookup"><span data-stu-id="989d8-489">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="989d8-490">Bu seçenek, .NET 'in gelecek bir sürümünde kullanımdan kalkabilir.</span><span class="sxs-lookup"><span data-stu-id="989d8-490">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="989d8-491">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-491">Setting name</span></span> | <span data-ttu-id="989d8-492">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-492">Values</span></span> | <span data-ttu-id="989d8-493">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-493">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-494">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-494">**runtimeconfig.json**</span></span> | <span data-ttu-id="989d8-495">Yok</span><span class="sxs-lookup"><span data-stu-id="989d8-495">N/A</span></span> | <span data-ttu-id="989d8-496">Yok</span><span class="sxs-lookup"><span data-stu-id="989d8-496">N/A</span></span> | <span data-ttu-id="989d8-497">Yok</span><span class="sxs-lookup"><span data-stu-id="989d8-497">N/A</span></span> |
| <span data-ttu-id="989d8-498">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-498">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="989d8-499">`1` -etkin</span><span class="sxs-lookup"><span data-stu-id="989d8-499">`1` - enabled</span></span><br/> <span data-ttu-id="989d8-500">`0` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="989d8-500">`0` - disabled</span></span> | <span data-ttu-id="989d8-501">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="989d8-501">.NET Core 1.0</span></span> |
| <span data-ttu-id="989d8-502">**.NET Framework içinapp.config**</span><span class="sxs-lookup"><span data-stu-id="989d8-502">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="989d8-503">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="989d8-503">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="989d8-504">`1` -etkin</span><span class="sxs-lookup"><span data-stu-id="989d8-504">`1` - enabled</span></span><br/> <span data-ttu-id="989d8-505">`0` -devre dışı</span><span class="sxs-lookup"><span data-stu-id="989d8-505">`0` - disabled</span></span> | <span data-ttu-id="989d8-506">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="989d8-506">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="989d8-507">Büyük nesne yığın eşiği</span><span class="sxs-lookup"><span data-stu-id="989d8-507">Large object heap threshold</span></span>

- <span data-ttu-id="989d8-508">Nesnelerin büyük nesne yığınında (LOH) geçmesine neden olan eşik boyutunu bayt cinsinden belirtir.</span><span class="sxs-lookup"><span data-stu-id="989d8-508">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="989d8-509">Varsayılan eşik 85.000 bayttır.</span><span class="sxs-lookup"><span data-stu-id="989d8-509">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="989d8-510">Belirttiğiniz değer varsayılan eşikten büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="989d8-510">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="989d8-511">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-511">Setting name</span></span> | <span data-ttu-id="989d8-512">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-512">Values</span></span> | <span data-ttu-id="989d8-513">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-513">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-514">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-514">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="989d8-515">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-515">*decimal value*</span></span> | <span data-ttu-id="989d8-516">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="989d8-516">.NET Core 1.0</span></span> |
| <span data-ttu-id="989d8-517">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-517">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="989d8-518">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-518">*hexadecimal value*</span></span> | <span data-ttu-id="989d8-519">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="989d8-519">.NET Core 1.0</span></span> |
| <span data-ttu-id="989d8-520">**.NET Framework içinapp.config**</span><span class="sxs-lookup"><span data-stu-id="989d8-520">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="989d8-521">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="989d8-521">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="989d8-522">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="989d8-522">*decimal value*</span></span> | <span data-ttu-id="989d8-523"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="989d8-523">.NET Framework 4.8</span></span> |

<span data-ttu-id="989d8-524">Örnek:</span><span class="sxs-lookup"><span data-stu-id="989d8-524">Example:</span></span>

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
> <span data-ttu-id="989d8-525">*Üzerinderuntimeconfig.js* seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="989d8-525">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="989d8-526">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="989d8-526">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="989d8-527">Örneğin, 120.000 baytlık bir eşik boyutu ayarlamak için, değerler JSON dosyası için 120000, ve ortam değişkeni için 0x1D4C0 ya da 1D4C0 olur.</span><span class="sxs-lookup"><span data-stu-id="989d8-527">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="989d8-528">Tek başına GC</span><span class="sxs-lookup"><span data-stu-id="989d8-528">Standalone GC</span></span>

- <span data-ttu-id="989d8-529">Çalışma zamanının yüklemeyi amaçladığı çöp toplayıcısını içeren kitaplığın yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="989d8-529">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="989d8-530">Daha fazla bilgi için bkz. [tek BAŞıNA GC yükleyici tasarımı](https://github.com/dotnet/runtime/blob/main/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="989d8-530">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/main/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="989d8-531">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="989d8-531">Setting name</span></span> | <span data-ttu-id="989d8-532">Değerler</span><span class="sxs-lookup"><span data-stu-id="989d8-532">Values</span></span> | <span data-ttu-id="989d8-533">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="989d8-533">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="989d8-534">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="989d8-534">**runtimeconfig.json**</span></span> | <span data-ttu-id="989d8-535">Yok</span><span class="sxs-lookup"><span data-stu-id="989d8-535">N/A</span></span> | <span data-ttu-id="989d8-536">Yok</span><span class="sxs-lookup"><span data-stu-id="989d8-536">N/A</span></span> | <span data-ttu-id="989d8-537">Yok</span><span class="sxs-lookup"><span data-stu-id="989d8-537">N/A</span></span> |
| <span data-ttu-id="989d8-538">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="989d8-538">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="989d8-539">*string_path*</span><span class="sxs-lookup"><span data-stu-id="989d8-539">*string_path*</span></span> | <span data-ttu-id="989d8-540">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="989d8-540">.NET Core 2.0</span></span> |
