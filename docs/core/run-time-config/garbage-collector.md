---
title: Çöp toplayıcı yapılandırma ayarları
description: Çöp toplayıcının .NET Core uygulamaları için belleği nasıl yönettiğini yapılandırmak üzere çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 0ce2f70204463c1525ef7d29de21ddf5384d0238
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202093"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="f1e30-103">Çöp toplama için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="f1e30-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="f1e30-104">Bu sayfa, çalışma zamanında değiştirilebilen çöp toplayıcı (GC) ayarları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="f1e30-105">Çalışan bir uygulamanın en yüksek performans düzeyine ulaşmak istiyorsanız bu ayarları kullanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="f1e30-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="f1e30-106">Bununla birlikte, varsayılan olarak, çoğu uygulama için tipik durumlarda en iyi performansı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1e30-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="f1e30-107">Ayarlar bu sayfadaki gruplar halinde düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="f1e30-108">Her grup içindeki ayarlar, belirli bir sonuca ulaşmak için genellikle birbirleriyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="f1e30-109">Bu ayarlar ayrıca uygulama çalışırken dinamik olarak değiştirilebilir, bu nedenle ayarladığınız tüm çalışma zamanı ayarları geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="f1e30-110">[Gecikme düzeyi](../../standard/garbage-collection/latency.md)gibi bazı ayarlar tipik olarak yalnızca TASARıM zamanında API aracılığıyla ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="f1e30-111">Bu tür ayarlar bu sayfadan çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="f1e30-112">Sayı değerleri için, *runtimeconfig. JSON* dosyasındaki ayarlar için ondalık gösterimi ve ortam değişkeni ayarları için onaltılık gösterimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f1e30-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="f1e30-113">Onaltılık değerler için, bunları "0x" öneki olmadan veya olmadan belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1e30-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="f1e30-114">Çöp toplamanın türleri</span><span class="sxs-lookup"><span data-stu-id="f1e30-114">Flavors of garbage collection</span></span>

<span data-ttu-id="f1e30-115">Çöp toplamanın iki ana özellikleri, iş istasyonu GC ve sunucu GC ' dir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="f1e30-116">İkisi arasındaki farklılıklar hakkında daha fazla bilgi için bkz. [Workstation and Server çöp toplama](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="f1e30-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="f1e30-117">Çöp toplamanın alt türleri arka plan ve eş zamanlı değil.</span><span class="sxs-lookup"><span data-stu-id="f1e30-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="f1e30-118">Çöp toplamanın türlerini seçmek için aşağıdaki ayarları kullanın:</span><span class="sxs-lookup"><span data-stu-id="f1e30-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="f1e30-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="f1e30-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="f1e30-120">Uygulamanın iş istasyonu çöp toplamayı veya sunucu çöp toplamayı kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="f1e30-121">Varsayılan: Iş Istasyonu atık toplama.</span><span class="sxs-lookup"><span data-stu-id="f1e30-121">Default: Workstation garbage collection.</span></span> <span data-ttu-id="f1e30-122">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="f1e30-122">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="f1e30-123">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="f1e30-123">Setting name</span></span> | <span data-ttu-id="f1e30-124">Değerler</span><span class="sxs-lookup"><span data-stu-id="f1e30-124">Values</span></span> | <span data-ttu-id="f1e30-125">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f1e30-125">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f1e30-126">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f1e30-126">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="f1e30-127">`false`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="f1e30-127">`false` - workstation</span></span><br/><span data-ttu-id="f1e30-128">`true`-sunucu</span><span class="sxs-lookup"><span data-stu-id="f1e30-128">`true` - server</span></span> | <span data-ttu-id="f1e30-129">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="f1e30-129">.NET Core 1.0</span></span> |
| <span data-ttu-id="f1e30-130">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="f1e30-130">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="f1e30-131">`false`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="f1e30-131">`false` - workstation</span></span><br/><span data-ttu-id="f1e30-132">`true`-sunucu</span><span class="sxs-lookup"><span data-stu-id="f1e30-132">`true` - server</span></span> | <span data-ttu-id="f1e30-133">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="f1e30-133">.NET Core 1.0</span></span> |
| <span data-ttu-id="f1e30-134">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="f1e30-134">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="f1e30-135">`0`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="f1e30-135">`0` - workstation</span></span><br/><span data-ttu-id="f1e30-136">`1`-sunucu</span><span class="sxs-lookup"><span data-stu-id="f1e30-136">`1` - server</span></span> | <span data-ttu-id="f1e30-137">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="f1e30-137">.NET Core 1.0</span></span> |
| <span data-ttu-id="f1e30-138">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="f1e30-138">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f1e30-139">GCServer</span><span class="sxs-lookup"><span data-stu-id="f1e30-139">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="f1e30-140">`false`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="f1e30-140">`false` - workstation</span></span><br/><span data-ttu-id="f1e30-141">`true`-sunucu</span><span class="sxs-lookup"><span data-stu-id="f1e30-141">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="f1e30-142">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f1e30-142">Examples</span></span>

<span data-ttu-id="f1e30-143">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="f1e30-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="f1e30-144">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="f1e30-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="f1e30-145">System. GC. eşzamanlı/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="f1e30-145">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="f1e30-146">Arka plan (eşzamanlı) Çöp toplamanın etkinleştirilip etkinleştirilmeyeceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-146">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="f1e30-147">Varsayılan: arka plan GC kullanın.</span><span class="sxs-lookup"><span data-stu-id="f1e30-147">Default: Use background GC.</span></span> <span data-ttu-id="f1e30-148">Bu değeri değerine ayarlamaya eşdeğerdir `true` .</span><span class="sxs-lookup"><span data-stu-id="f1e30-148">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="f1e30-149">Daha fazla bilgi için bkz. [arka plan atık toplama](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="f1e30-149">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="f1e30-150">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="f1e30-150">Setting name</span></span> | <span data-ttu-id="f1e30-151">Değerler</span><span class="sxs-lookup"><span data-stu-id="f1e30-151">Values</span></span> | <span data-ttu-id="f1e30-152">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f1e30-152">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f1e30-153">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f1e30-153">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="f1e30-154">`true`-arka plan GC</span><span class="sxs-lookup"><span data-stu-id="f1e30-154">`true` - background GC</span></span><br/><span data-ttu-id="f1e30-155">`false`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="f1e30-155">`false` - non-concurrent GC</span></span> | <span data-ttu-id="f1e30-156">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="f1e30-156">.NET Core 1.0</span></span> |
| <span data-ttu-id="f1e30-157">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="f1e30-157">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="f1e30-158">`true`-arka plan GC</span><span class="sxs-lookup"><span data-stu-id="f1e30-158">`true` - background GC</span></span><br/><span data-ttu-id="f1e30-159">`false`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="f1e30-159">`false` - non-concurrent GC</span></span> | <span data-ttu-id="f1e30-160">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="f1e30-160">.NET Core 1.0</span></span> |
| <span data-ttu-id="f1e30-161">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="f1e30-161">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="f1e30-162">`1`-arka plan GC</span><span class="sxs-lookup"><span data-stu-id="f1e30-162">`1` - background GC</span></span><br/><span data-ttu-id="f1e30-163">`0`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="f1e30-163">`0` - non-concurrent GC</span></span> | <span data-ttu-id="f1e30-164">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="f1e30-164">.NET Core 1.0</span></span> |
| <span data-ttu-id="f1e30-165">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="f1e30-165">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f1e30-166">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="f1e30-166">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="f1e30-167">`true`-arka plan GC</span><span class="sxs-lookup"><span data-stu-id="f1e30-167">`true` - background GC</span></span><br/><span data-ttu-id="f1e30-168">`false`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="f1e30-168">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="f1e30-169">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f1e30-169">Examples</span></span>

<span data-ttu-id="f1e30-170">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="f1e30-170">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="f1e30-171">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="f1e30-171">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="f1e30-172">Kaynak kullanımını yönetme</span><span class="sxs-lookup"><span data-stu-id="f1e30-172">Manage resource usage</span></span>

<span data-ttu-id="f1e30-173">Çöp toplayıcının bellek ve işlemci kullanımını yönetmek için bu bölümde açıklanan ayarları kullanın.</span><span class="sxs-lookup"><span data-stu-id="f1e30-173">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="f1e30-174">Bu ayarlardan bazıları hakkında daha fazla bilgi için, bkz. [iş istasyonu ve sunucu GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blogu girişi.</span><span class="sxs-lookup"><span data-stu-id="f1e30-174">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="f1e30-175">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="f1e30-175">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="f1e30-176">Çöp toplayıcı tarafından oluşturulan Heap sayısını sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-176">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="f1e30-177">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-177">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="f1e30-178">[GC işlemci benzeşimi](#systemgcnoaffinitizecomplus_gcnoaffinitize) etkinse, varsayılan olarak, yığın sayısı ayarı `n` GC sayfa@@/iş parçacıklarını ilk işlemcilere göre sayar `n` .</span><span class="sxs-lookup"><span data-stu-id="f1e30-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="f1e30-179">(Tam olarak hangi işlemcilerin olduğunu belirtmek için, bu [maskeyi](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) seçin veya [aralıklar](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) ayarlarını kesin olarak belirleyin.)</span><span class="sxs-lookup"><span data-stu-id="f1e30-179">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="f1e30-180">[GC işlemci benzeşimi](#systemgcnoaffinitizecomplus_gcnoaffinitize) devre dışıysa, bu ayar GC yığınlarının sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="f1e30-180">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="f1e30-181">Daha fazla bilgi için [Gcheapcount açıklamalarını](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)inceleyin.</span><span class="sxs-lookup"><span data-stu-id="f1e30-181">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="f1e30-182">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="f1e30-182">Setting name</span></span> | <span data-ttu-id="f1e30-183">Değerler</span><span class="sxs-lookup"><span data-stu-id="f1e30-183">Values</span></span> | <span data-ttu-id="f1e30-184">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f1e30-184">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f1e30-185">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f1e30-185">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="f1e30-186">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="f1e30-186">*decimal value*</span></span> | <span data-ttu-id="f1e30-187">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f1e30-187">.NET Core 3.0</span></span> |
| <span data-ttu-id="f1e30-188">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="f1e30-188">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="f1e30-189">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="f1e30-189">*hexadecimal value*</span></span> | <span data-ttu-id="f1e30-190">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f1e30-190">.NET Core 3.0</span></span> |
| <span data-ttu-id="f1e30-191">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="f1e30-191">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f1e30-192">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="f1e30-192">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="f1e30-193">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="f1e30-193">*decimal value*</span></span> | <span data-ttu-id="f1e30-194">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="f1e30-194">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="f1e30-195">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f1e30-195">Example:</span></span>

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
> <span data-ttu-id="f1e30-196">*Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="f1e30-196">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f1e30-197">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="f1e30-197">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f1e30-198">Örneğin, Heap sayısını 16 ile sınırlamak için değerler JSON dosyası için 16, ortam değişkeni için 0x10 veya 10 olur.</span><span class="sxs-lookup"><span data-stu-id="f1e30-198">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="f1e30-199">System. GC. ısıpaffinitizemask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="f1e30-199">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="f1e30-200">Çöp toplayıcı iş parçacıklarının kullanması gereken tam işlemcileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-200">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="f1e30-201">[GC işlemci benzeşimi](#systemgcnoaffinitizecomplus_gcnoaffinitize) devre dışıysa, bu ayar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-201">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="f1e30-202">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-202">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="f1e30-203">Değer, işlem için kullanılabilir olan işlemcileri tanımlayan bir bit maskesidir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-203">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="f1e30-204">Örneğin, bir 1023 ondalık değeri (veya ortam değişkenini kullanıyorsanız, 0x3FF veya 3FF onaltılı değeri), ikili gösterimde 0011 1111 1111 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-204">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="f1e30-205">Bu, ilk 10 işlemcinin kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-205">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="f1e30-206">Sıradaki 10 işlemciyi belirtmek için, işlemci 10-19 ' 1047552 nin ondalık değerini (veya 0xFFC00 ya da FFC00) bir 1111 1111 1100 0000 0000 ikili değere eşdeğer bir değere belirleyin.</span><span class="sxs-lookup"><span data-stu-id="f1e30-206">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="f1e30-207">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="f1e30-207">Setting name</span></span> | <span data-ttu-id="f1e30-208">Değerler</span><span class="sxs-lookup"><span data-stu-id="f1e30-208">Values</span></span> | <span data-ttu-id="f1e30-209">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f1e30-209">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f1e30-210">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f1e30-210">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="f1e30-211">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="f1e30-211">*decimal value*</span></span> | <span data-ttu-id="f1e30-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f1e30-212">.NET Core 3.0</span></span> |
| <span data-ttu-id="f1e30-213">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="f1e30-213">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="f1e30-214">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="f1e30-214">*hexadecimal value*</span></span> | <span data-ttu-id="f1e30-215">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f1e30-215">.NET Core 3.0</span></span> |
| <span data-ttu-id="f1e30-216">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="f1e30-216">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f1e30-217">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="f1e30-217">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="f1e30-218">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="f1e30-218">*decimal value*</span></span> | <span data-ttu-id="f1e30-219">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="f1e30-219">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="f1e30-220">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f1e30-220">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="f1e30-221">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="f1e30-221">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="f1e30-222">Çöp toplayıcı iş parçacıkları için kullanılacak işlemcilerin listesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-222">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="f1e30-223">Bu ayar [System. GC. Cenpaffinitizemask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask)ile benzerdir, ancak 64 'den fazla işlemci belirtmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-223">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="f1e30-224">Windows işletim sistemleri için, işlemci numarasını veya aralığını karşılık gelen [CPU grubuyla](/windows/win32/procthread/processor-groups)önek olarak ekleyin, örneğin, "0:1-10, 0:12, 1:50-52, 1:70".</span><span class="sxs-lookup"><span data-stu-id="f1e30-224">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="f1e30-225">[GC işlemci benzeşimi](#systemgcnoaffinitizecomplus_gcnoaffinitize) devre dışıysa, bu ayar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-225">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="f1e30-226">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-226">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="f1e30-227">Daha fazla bilgi için bkz. Maoni Stephens ' blogu üzerinde [> 64 CPU 'su olan MAKINELERDE GC için daha Iyi hale getirme](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) .</span><span class="sxs-lookup"><span data-stu-id="f1e30-227">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="f1e30-228">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="f1e30-228">Setting name</span></span> | <span data-ttu-id="f1e30-229">Değerler</span><span class="sxs-lookup"><span data-stu-id="f1e30-229">Values</span></span> | <span data-ttu-id="f1e30-230">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f1e30-230">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f1e30-231">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f1e30-231">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="f1e30-232">İşlemci numaralarının veya işlemci numarası aralıklarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="f1e30-232">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="f1e30-233">UNIX örneği: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="f1e30-233">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="f1e30-234">Windows örnek: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="f1e30-234">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="f1e30-235">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f1e30-235">.NET Core 3.0</span></span> |
| <span data-ttu-id="f1e30-236">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="f1e30-236">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="f1e30-237">İşlemci numaralarının veya işlemci numarası aralıklarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="f1e30-237">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="f1e30-238">UNIX örneği: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="f1e30-238">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="f1e30-239">Windows örnek: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="f1e30-239">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="f1e30-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f1e30-240">.NET Core 3.0</span></span> |

<span data-ttu-id="f1e30-241">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f1e30-241">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="f1e30-242">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="f1e30-242">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="f1e30-243">Çöp toplayıcının [CPU grupları](/windows/win32/procthread/processor-groups) kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-243">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="f1e30-244">64 bitlik bir Windows bilgisayarında birden çok CPU grubu olduğunda, diğer bir deyişle, 64 ' den fazla işlemci varsa, bu öğenin tüm CPU gruplarında çöp toplamayı genişletmelerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-244">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="f1e30-245">Çöp toplayıcı, Heap 'ler oluşturmak ve dengelemek için tüm çekirdekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-245">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="f1e30-246">Yalnızca 64-bit Windows işletim sistemlerinde sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-246">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="f1e30-247">Varsayılan: GC, CPU grupları arasında genişletilmez.</span><span class="sxs-lookup"><span data-stu-id="f1e30-247">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="f1e30-248">Bu değeri değerine ayarlamaya eşdeğerdir `0` .</span><span class="sxs-lookup"><span data-stu-id="f1e30-248">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="f1e30-249">Daha fazla bilgi için bkz. Maoni Stephens ' blogu üzerinde [> 64 CPU 'su olan MAKINELERDE GC için daha Iyi hale getirme](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) .</span><span class="sxs-lookup"><span data-stu-id="f1e30-249">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="f1e30-250">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="f1e30-250">Setting name</span></span> | <span data-ttu-id="f1e30-251">Değerler</span><span class="sxs-lookup"><span data-stu-id="f1e30-251">Values</span></span> | <span data-ttu-id="f1e30-252">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f1e30-252">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f1e30-253">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f1e30-253">**runtimeconfig.json**</span></span> | <span data-ttu-id="f1e30-254">Yok</span><span class="sxs-lookup"><span data-stu-id="f1e30-254">N/A</span></span> | <span data-ttu-id="f1e30-255">Yok</span><span class="sxs-lookup"><span data-stu-id="f1e30-255">N/A</span></span> | <span data-ttu-id="f1e30-256">Yok</span><span class="sxs-lookup"><span data-stu-id="f1e30-256">N/A</span></span> |
| <span data-ttu-id="f1e30-257">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="f1e30-257">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="f1e30-258">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="f1e30-258">`0` - disabled</span></span><br/><span data-ttu-id="f1e30-259">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="f1e30-259">`1` - enabled</span></span> | <span data-ttu-id="f1e30-260">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="f1e30-260">.NET Core 1.0</span></span> |
| <span data-ttu-id="f1e30-261">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="f1e30-261">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f1e30-262">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="f1e30-262">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="f1e30-263">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="f1e30-263">`false` - disabled</span></span><br/><span data-ttu-id="f1e30-264">`true`-etkin</span><span class="sxs-lookup"><span data-stu-id="f1e30-264">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="f1e30-265">Ortak dil çalışma zamanını (CLR) tüm CPU grupları arasında iş parçacığı havuzundan da dağıtmak üzere yapılandırmak için, [Thread_UseAllCpuGroups öğesi](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) seçeneğini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f1e30-265">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="f1e30-266">.NET Core uygulamaları için, ortam değişkeninin değerini olarak ayarlayarak bu seçeneği etkinleştirebilirsiniz `COMPlus_Thread_UseAllCpuGroups` `1` .</span><span class="sxs-lookup"><span data-stu-id="f1e30-266">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="f1e30-267">System. GC. Noafınitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="f1e30-267">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="f1e30-268">*Çöp toplama* iş parçacıklarının işlemcilerle kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-268">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="f1e30-269">Bir GC iş parçacığını eklemek için yalnızca belirli bir CPU üzerinde çalışabilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-269">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="f1e30-270">Her GC iş parçacığı için bir yığın oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f1e30-270">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="f1e30-271">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-271">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="f1e30-272">Varsayılan: işlemcilere sahip çöp toplama iş parçacıklarını ön olarak başlatma.</span><span class="sxs-lookup"><span data-stu-id="f1e30-272">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="f1e30-273">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="f1e30-273">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="f1e30-274">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="f1e30-274">Setting name</span></span> | <span data-ttu-id="f1e30-275">Değerler</span><span class="sxs-lookup"><span data-stu-id="f1e30-275">Values</span></span> | <span data-ttu-id="f1e30-276">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f1e30-276">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f1e30-277">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f1e30-277">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="f1e30-278">`false`-afze</span><span class="sxs-lookup"><span data-stu-id="f1e30-278">`false` - affinitize</span></span><br/><span data-ttu-id="f1e30-279">`true`-yok etme</span><span class="sxs-lookup"><span data-stu-id="f1e30-279">`true` - don't affinitize</span></span> | <span data-ttu-id="f1e30-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f1e30-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="f1e30-281">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="f1e30-281">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="f1e30-282">`0`-afze</span><span class="sxs-lookup"><span data-stu-id="f1e30-282">`0` - affinitize</span></span><br/><span data-ttu-id="f1e30-283">`1`-yok etme</span><span class="sxs-lookup"><span data-stu-id="f1e30-283">`1` - don't affinitize</span></span> | <span data-ttu-id="f1e30-284">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f1e30-284">.NET Core 3.0</span></span> |
| <span data-ttu-id="f1e30-285">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="f1e30-285">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f1e30-286">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="f1e30-286">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="f1e30-287">`false`-afze</span><span class="sxs-lookup"><span data-stu-id="f1e30-287">`false` - affinitize</span></span><br/><span data-ttu-id="f1e30-288">`true`-yok etme</span><span class="sxs-lookup"><span data-stu-id="f1e30-288">`true` - don't affinitize</span></span> | <span data-ttu-id="f1e30-289">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="f1e30-289">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="f1e30-290">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f1e30-290">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="f1e30-291">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="f1e30-291">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="f1e30-292">GC yığını ve GC booksaklanması için bayt cinsinden en fazla tamamlama boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-292">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="f1e30-293">Bu ayar yalnızca 64 bitlik bilgisayarlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-293">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="f1e30-294">Yalnızca belirli durumlarda geçerli olan varsayılan değer, kapsayıcıdaki bellek sınırının 20 MB veya %75 ' sinden daha fazladır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-294">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="f1e30-295">Varsayılan değer şu durumlarda geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="f1e30-295">The default value applies if:</span></span>

  - <span data-ttu-id="f1e30-296">İşlem belirtilen bellek sınırına sahip bir kapsayıcı içinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="f1e30-296">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="f1e30-297">[System. GC. HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="f1e30-297">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="f1e30-298">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="f1e30-298">Setting name</span></span> | <span data-ttu-id="f1e30-299">Değerler</span><span class="sxs-lookup"><span data-stu-id="f1e30-299">Values</span></span> | <span data-ttu-id="f1e30-300">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f1e30-300">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f1e30-301">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f1e30-301">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="f1e30-302">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="f1e30-302">*decimal value*</span></span> | <span data-ttu-id="f1e30-303">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f1e30-303">.NET Core 3.0</span></span> |
| <span data-ttu-id="f1e30-304">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="f1e30-304">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="f1e30-305">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="f1e30-305">*hexadecimal value*</span></span> | <span data-ttu-id="f1e30-306">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f1e30-306">.NET Core 3.0</span></span> |

<span data-ttu-id="f1e30-307">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f1e30-307">Example:</span></span>

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
> <span data-ttu-id="f1e30-308">*Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="f1e30-308">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f1e30-309">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="f1e30-309">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f1e30-310">Örneğin, 200 mebibytes (MIB) yığın sabit sınırı belirtmek için, değerler JSON dosyası için 209715200 ve ortam değişkeni için 0xC800000 veya C800000 olur.</span><span class="sxs-lookup"><span data-stu-id="f1e30-310">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="f1e30-311">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="f1e30-311">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="f1e30-312">Toplam fiziksel belleğin yüzdesi olarak izin verilen GC yığın kullanımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-312">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="f1e30-313">[System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) da ayarlandıysa, bu ayar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-313">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="f1e30-314">Bu ayar yalnızca 64 bitlik bilgisayarlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-314">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="f1e30-315">İşlem belirtilen bellek sınırına sahip bir kapsayıcı içinde çalışıyorsa, yüzde bu bellek sınırının yüzdesi olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-315">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="f1e30-316">Yalnızca belirli durumlarda geçerli olan varsayılan değer, kapsayıcıda bellek sınırının 20 MB veya %75 ' si kadar küçüktür.</span><span class="sxs-lookup"><span data-stu-id="f1e30-316">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="f1e30-317">Varsayılan değer şu durumlarda geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="f1e30-317">The default value applies if:</span></span>

  - <span data-ttu-id="f1e30-318">İşlem belirtilen bellek sınırına sahip bir kapsayıcı içinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="f1e30-318">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="f1e30-319">[System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="f1e30-319">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="f1e30-320">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="f1e30-320">Setting name</span></span> | <span data-ttu-id="f1e30-321">Değerler</span><span class="sxs-lookup"><span data-stu-id="f1e30-321">Values</span></span> | <span data-ttu-id="f1e30-322">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f1e30-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f1e30-323">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f1e30-323">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="f1e30-324">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="f1e30-324">*decimal value*</span></span> | <span data-ttu-id="f1e30-325">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f1e30-325">.NET Core 3.0</span></span> |
| <span data-ttu-id="f1e30-326">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="f1e30-326">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="f1e30-327">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="f1e30-327">*hexadecimal value*</span></span> | <span data-ttu-id="f1e30-328">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f1e30-328">.NET Core 3.0</span></span> |

<span data-ttu-id="f1e30-329">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f1e30-329">Example:</span></span>

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
> <span data-ttu-id="f1e30-330">*Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="f1e30-330">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f1e30-331">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="f1e30-331">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f1e30-332">Örneğin, yığın kullanımını %30 olarak sınırlandırmak için değerler JSON dosyası için 30, ortam değişkeni için 0x1E veya 1E olur.</span><span class="sxs-lookup"><span data-stu-id="f1e30-332">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="f1e30-333">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="f1e30-333">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="f1e30-334">Silinmesi gereken segmentlerin ileride kullanılmak üzere bir bekleme listesine mi yerleştirileceğini, yoksa işletim sistemine (OS) geri mi bırakılacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-334">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="f1e30-335">Varsayılan: kesimleri işletim sistemine geri bırakın.</span><span class="sxs-lookup"><span data-stu-id="f1e30-335">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="f1e30-336">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="f1e30-336">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="f1e30-337">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="f1e30-337">Setting name</span></span> | <span data-ttu-id="f1e30-338">Değerler</span><span class="sxs-lookup"><span data-stu-id="f1e30-338">Values</span></span> | <span data-ttu-id="f1e30-339">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f1e30-339">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f1e30-340">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f1e30-340">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="f1e30-341">`false`-işletim sistemine yayın</span><span class="sxs-lookup"><span data-stu-id="f1e30-341">`false` - release to OS</span></span><br/><span data-ttu-id="f1e30-342">`true`-bekleme durumuna koy</span><span class="sxs-lookup"><span data-stu-id="f1e30-342">`true` - put on standby</span></span> | <span data-ttu-id="f1e30-343">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="f1e30-343">.NET Core 1.0</span></span> |
| <span data-ttu-id="f1e30-344">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="f1e30-344">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="f1e30-345">`false`-işletim sistemine yayın</span><span class="sxs-lookup"><span data-stu-id="f1e30-345">`false` - release to OS</span></span><br/><span data-ttu-id="f1e30-346">`true`-bekleme durumuna koy</span><span class="sxs-lookup"><span data-stu-id="f1e30-346">`true` - put on standby</span></span> | <span data-ttu-id="f1e30-347">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="f1e30-347">.NET Core 1.0</span></span> |
| <span data-ttu-id="f1e30-348">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="f1e30-348">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="f1e30-349">`0`-işletim sistemine yayın</span><span class="sxs-lookup"><span data-stu-id="f1e30-349">`0` - release to OS</span></span><br/><span data-ttu-id="f1e30-350">`1`-bekleme durumuna koy</span><span class="sxs-lookup"><span data-stu-id="f1e30-350">`1` - put on standby</span></span> | <span data-ttu-id="f1e30-351">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="f1e30-351">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="f1e30-352">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f1e30-352">Examples</span></span>

<span data-ttu-id="f1e30-353">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="f1e30-353">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="f1e30-354">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="f1e30-354">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="f1e30-355">Büyük sayfalar</span><span class="sxs-lookup"><span data-stu-id="f1e30-355">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="f1e30-356">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="f1e30-356">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="f1e30-357">Bir yığın sabit sınırı ayarlandığında büyük sayfaların kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-357">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="f1e30-358">Varsayılan: bir yığın sabit sınırı ayarlandığında büyük sayfalar kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="f1e30-358">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="f1e30-359">Bu değeri değerine ayarlamaya eşdeğerdir `0` .</span><span class="sxs-lookup"><span data-stu-id="f1e30-359">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="f1e30-360">Bu bir deneysel ayardır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-360">This is an experimental setting.</span></span>

| | <span data-ttu-id="f1e30-361">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="f1e30-361">Setting name</span></span> | <span data-ttu-id="f1e30-362">Değerler</span><span class="sxs-lookup"><span data-stu-id="f1e30-362">Values</span></span> | <span data-ttu-id="f1e30-363">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f1e30-363">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f1e30-364">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f1e30-364">**runtimeconfig.json**</span></span> | <span data-ttu-id="f1e30-365">Yok</span><span class="sxs-lookup"><span data-stu-id="f1e30-365">N/A</span></span> | <span data-ttu-id="f1e30-366">Yok</span><span class="sxs-lookup"><span data-stu-id="f1e30-366">N/A</span></span> | <span data-ttu-id="f1e30-367">Yok</span><span class="sxs-lookup"><span data-stu-id="f1e30-367">N/A</span></span> |
| <span data-ttu-id="f1e30-368">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="f1e30-368">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="f1e30-369">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="f1e30-369">`0` - disabled</span></span><br/><span data-ttu-id="f1e30-370">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="f1e30-370">`1` - enabled</span></span> | <span data-ttu-id="f1e30-371">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f1e30-371">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="f1e30-372">Büyük nesneler</span><span class="sxs-lookup"><span data-stu-id="f1e30-372">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="f1e30-373">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="f1e30-373">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="f1e30-374">Toplam boyuttaki 2 gigabayttan (GB) büyük olan diziler için 64 bitlik platformlarda çöp toplayıcı desteğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-374">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="f1e30-375">Varsayılan: GC 2 GB 'tan büyük dizileri destekler.</span><span class="sxs-lookup"><span data-stu-id="f1e30-375">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="f1e30-376">Bu değeri değerine ayarlamaya eşdeğerdir `1` .</span><span class="sxs-lookup"><span data-stu-id="f1e30-376">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="f1e30-377">Bu seçenek, .NET 'in gelecek bir sürümünde kullanımdan kalkabilir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-377">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="f1e30-378">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="f1e30-378">Setting name</span></span> | <span data-ttu-id="f1e30-379">Değerler</span><span class="sxs-lookup"><span data-stu-id="f1e30-379">Values</span></span> | <span data-ttu-id="f1e30-380">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f1e30-380">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f1e30-381">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f1e30-381">**runtimeconfig.json**</span></span> | <span data-ttu-id="f1e30-382">Yok</span><span class="sxs-lookup"><span data-stu-id="f1e30-382">N/A</span></span> | <span data-ttu-id="f1e30-383">Yok</span><span class="sxs-lookup"><span data-stu-id="f1e30-383">N/A</span></span> | <span data-ttu-id="f1e30-384">Yok</span><span class="sxs-lookup"><span data-stu-id="f1e30-384">N/A</span></span> |
| <span data-ttu-id="f1e30-385">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="f1e30-385">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="f1e30-386">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="f1e30-386">`1` - enabled</span></span><br/> <span data-ttu-id="f1e30-387">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="f1e30-387">`0` - disabled</span></span> | <span data-ttu-id="f1e30-388">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="f1e30-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="f1e30-389">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="f1e30-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f1e30-390">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="f1e30-390">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="f1e30-391">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="f1e30-391">`1` - enabled</span></span><br/> <span data-ttu-id="f1e30-392">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="f1e30-392">`0` - disabled</span></span> | <span data-ttu-id="f1e30-393">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="f1e30-393">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="f1e30-394">Büyük nesne yığın eşiği</span><span class="sxs-lookup"><span data-stu-id="f1e30-394">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="f1e30-395">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="f1e30-395">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="f1e30-396">Nesnelerin büyük nesne yığınında (LOH) geçmesine neden olan eşik boyutunu bayt cinsinden belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-396">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="f1e30-397">Varsayılan eşik 85.000 bayttır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-397">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="f1e30-398">Belirttiğiniz değer varsayılan eşikten büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1e30-398">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="f1e30-399">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="f1e30-399">Setting name</span></span> | <span data-ttu-id="f1e30-400">Değerler</span><span class="sxs-lookup"><span data-stu-id="f1e30-400">Values</span></span> | <span data-ttu-id="f1e30-401">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f1e30-401">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f1e30-402">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f1e30-402">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="f1e30-403">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="f1e30-403">*decimal value*</span></span> | <span data-ttu-id="f1e30-404">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="f1e30-404">.NET Core 1.0</span></span> |
| <span data-ttu-id="f1e30-405">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="f1e30-405">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="f1e30-406">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="f1e30-406">*hexadecimal value*</span></span> | <span data-ttu-id="f1e30-407">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="f1e30-407">.NET Core 1.0</span></span> |
| <span data-ttu-id="f1e30-408">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="f1e30-408">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="f1e30-409">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="f1e30-409">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="f1e30-410">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="f1e30-410">*decimal value*</span></span> | <span data-ttu-id="f1e30-411"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="f1e30-411">.NET Framework 4.8</span></span> |

<span data-ttu-id="f1e30-412">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f1e30-412">Example:</span></span>

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
> <span data-ttu-id="f1e30-413">*Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="f1e30-413">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="f1e30-414">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="f1e30-414">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="f1e30-415">Örneğin, 120.000 baytlık bir eşik boyutu ayarlamak için, değerler JSON dosyası için 120000, ve ortam değişkeni için 0x1D4C0 ya da 1D4C0 olur.</span><span class="sxs-lookup"><span data-stu-id="f1e30-415">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="f1e30-416">Tek başına GC</span><span class="sxs-lookup"><span data-stu-id="f1e30-416">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="f1e30-417">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="f1e30-417">COMPlus_GCName</span></span>

- <span data-ttu-id="f1e30-418">Çalışma zamanının yüklemeyi amaçladığı çöp toplayıcısını içeren kitaplığın yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1e30-418">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="f1e30-419">Daha fazla bilgi için bkz. [tek BAŞıNA GC yükleyici tasarımı](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="f1e30-419">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="f1e30-420">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="f1e30-420">Setting name</span></span> | <span data-ttu-id="f1e30-421">Değerler</span><span class="sxs-lookup"><span data-stu-id="f1e30-421">Values</span></span> | <span data-ttu-id="f1e30-422">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f1e30-422">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="f1e30-423">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="f1e30-423">**runtimeconfig.json**</span></span> | <span data-ttu-id="f1e30-424">Yok</span><span class="sxs-lookup"><span data-stu-id="f1e30-424">N/A</span></span> | <span data-ttu-id="f1e30-425">Yok</span><span class="sxs-lookup"><span data-stu-id="f1e30-425">N/A</span></span> | <span data-ttu-id="f1e30-426">Yok</span><span class="sxs-lookup"><span data-stu-id="f1e30-426">N/A</span></span> |
| <span data-ttu-id="f1e30-427">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="f1e30-427">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="f1e30-428">*string_path*</span><span class="sxs-lookup"><span data-stu-id="f1e30-428">*string_path*</span></span> | <span data-ttu-id="f1e30-429">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="f1e30-429">.NET Core 2.0</span></span> |
