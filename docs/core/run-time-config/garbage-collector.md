---
title: Çöp toplayıcı yapılandırma ayarları
description: Çöp toplayıcının .NET Core uygulamaları için belleği nasıl yönettiğini yapılandırmak üzere çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: d7e3d040cd634eeb020beff806c60f834cc02585
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761986"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="5f5e0-103">Çöp toplama için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="5f5e0-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="5f5e0-104">Bu sayfa, çalışma zamanında değiştirilebilen çöp toplayıcı (GC) ayarları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="5f5e0-105">Çalışan bir uygulamanın en yüksek performans düzeyine ulaşmak istiyorsanız bu ayarları kullanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="5f5e0-106">Bununla birlikte, varsayılan olarak, çoğu uygulama için tipik durumlarda en iyi performansı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="5f5e0-107">Ayarlar bu sayfadaki gruplar halinde düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="5f5e0-108">Her grup içindeki ayarlar, belirli bir sonuca ulaşmak için genellikle birbirleriyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="5f5e0-109">Bu ayarlar ayrıca uygulama çalışırken dinamik olarak değiştirilebilir, bu nedenle ayarladığınız tüm çalışma zamanı ayarları geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="5f5e0-110">[Gecikme düzeyi](../../standard/garbage-collection/latency.md)gibi bazı ayarlar tipik olarak yalnızca TASARıM zamanında API aracılığıyla ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="5f5e0-111">Bu tür ayarlar bu sayfadan çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="5f5e0-112">Sayı değerleri için, *runtimeconfig. JSON* dosyasındaki ayarlar için ondalık gösterimi ve ortam değişkeni ayarları için onaltılık gösterimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="5f5e0-113">Onaltılık değerler için, bunları "0x" öneki olmadan veya olmadan belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="5f5e0-114">Çöp toplamanın türleri</span><span class="sxs-lookup"><span data-stu-id="5f5e0-114">Flavors of garbage collection</span></span>

<span data-ttu-id="5f5e0-115">Çöp toplamanın iki ana özellikleri, iş istasyonu GC ve sunucu GC ' dir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="5f5e0-116">İkisi arasındaki farklılıklar hakkında daha fazla bilgi için bkz. [Workstation and Server çöp toplama](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="5f5e0-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="5f5e0-117">Çöp toplamanın alt türleri arka plan ve eş zamanlı değil.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="5f5e0-118">Çöp toplamanın türlerini seçmek için aşağıdaki ayarları kullanın:</span><span class="sxs-lookup"><span data-stu-id="5f5e0-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="5f5e0-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="5f5e0-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="5f5e0-120">Uygulamanın iş istasyonu çöp toplamayı veya sunucu çöp toplamayı kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="5f5e0-121">Varsayılan: Iş Istasyonu atık toplama.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-121">Default: Workstation garbage collection.</span></span> <span data-ttu-id="5f5e0-122">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="5f5e0-122">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="5f5e0-123">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-123">Setting name</span></span> | <span data-ttu-id="5f5e0-124">Değerler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-124">Values</span></span> | <span data-ttu-id="5f5e0-125">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f5e0-125">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5f5e0-126">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-126">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="5f5e0-127">`false`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="5f5e0-127">`false` - workstation</span></span><br/><span data-ttu-id="5f5e0-128">`true`-sunucu</span><span class="sxs-lookup"><span data-stu-id="5f5e0-128">`true` - server</span></span> | <span data-ttu-id="5f5e0-129">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-129">.NET Core 1.0</span></span> |
| <span data-ttu-id="5f5e0-130">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-130">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="5f5e0-131">`false`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="5f5e0-131">`false` - workstation</span></span><br/><span data-ttu-id="5f5e0-132">`true`-sunucu</span><span class="sxs-lookup"><span data-stu-id="5f5e0-132">`true` - server</span></span> | <span data-ttu-id="5f5e0-133">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-133">.NET Core 1.0</span></span> |
| <span data-ttu-id="5f5e0-134">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-134">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="5f5e0-135">`0`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="5f5e0-135">`0` - workstation</span></span><br/><span data-ttu-id="5f5e0-136">`1`-sunucu</span><span class="sxs-lookup"><span data-stu-id="5f5e0-136">`1` - server</span></span> | <span data-ttu-id="5f5e0-137">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-137">.NET Core 1.0</span></span> |
| <span data-ttu-id="5f5e0-138">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-138">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5f5e0-139">GCServer</span><span class="sxs-lookup"><span data-stu-id="5f5e0-139">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="5f5e0-140">`false`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="5f5e0-140">`false` - workstation</span></span><br/><span data-ttu-id="5f5e0-141">`true`-sunucu</span><span class="sxs-lookup"><span data-stu-id="5f5e0-141">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="5f5e0-142">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-142">Examples</span></span>

<span data-ttu-id="5f5e0-143">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="5f5e0-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="5f5e0-144">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="5f5e0-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="5f5e0-145">System. GC. eşzamanlı/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="5f5e0-145">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="5f5e0-146">Arka plan (eşzamanlı) Çöp toplamanın etkinleştirilip etkinleştirilmeyeceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-146">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="5f5e0-147">Varsayılan: arka plan GC kullanın.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-147">Default: Use background GC.</span></span> <span data-ttu-id="5f5e0-148">Bu değeri değerine ayarlamaya eşdeğerdir `true` .</span><span class="sxs-lookup"><span data-stu-id="5f5e0-148">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="5f5e0-149">Daha fazla bilgi için bkz. [arka plan atık toplama](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="5f5e0-149">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="5f5e0-150">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-150">Setting name</span></span> | <span data-ttu-id="5f5e0-151">Değerler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-151">Values</span></span> | <span data-ttu-id="5f5e0-152">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f5e0-152">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5f5e0-153">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-153">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="5f5e0-154">`true`-arka plan GC</span><span class="sxs-lookup"><span data-stu-id="5f5e0-154">`true` - background GC</span></span><br/><span data-ttu-id="5f5e0-155">`false`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="5f5e0-155">`false` - non-concurrent GC</span></span> | <span data-ttu-id="5f5e0-156">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-156">.NET Core 1.0</span></span> |
| <span data-ttu-id="5f5e0-157">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-157">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="5f5e0-158">`true`-arka plan GC</span><span class="sxs-lookup"><span data-stu-id="5f5e0-158">`true` - background GC</span></span><br/><span data-ttu-id="5f5e0-159">`false`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="5f5e0-159">`false` - non-concurrent GC</span></span> | <span data-ttu-id="5f5e0-160">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-160">.NET Core 1.0</span></span> |
| <span data-ttu-id="5f5e0-161">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-161">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="5f5e0-162">`true`-arka plan GC</span><span class="sxs-lookup"><span data-stu-id="5f5e0-162">`true` - background GC</span></span><br/><span data-ttu-id="5f5e0-163">`false`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="5f5e0-163">`false` - non-concurrent GC</span></span> | <span data-ttu-id="5f5e0-164">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-164">.NET Core 1.0</span></span> |
| <span data-ttu-id="5f5e0-165">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-165">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5f5e0-166">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="5f5e0-166">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="5f5e0-167">`true`-arka plan GC</span><span class="sxs-lookup"><span data-stu-id="5f5e0-167">`true` - background GC</span></span><br/><span data-ttu-id="5f5e0-168">`false`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="5f5e0-168">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="5f5e0-169">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-169">Examples</span></span>

<span data-ttu-id="5f5e0-170">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="5f5e0-170">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="5f5e0-171">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="5f5e0-171">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="5f5e0-172">Kaynak kullanımını yönetme</span><span class="sxs-lookup"><span data-stu-id="5f5e0-172">Manage resource usage</span></span>

<span data-ttu-id="5f5e0-173">Çöp toplayıcının bellek ve işlemci kullanımını yönetmek için bu bölümde açıklanan ayarları kullanın.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-173">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="5f5e0-174">Bu ayarlardan bazıları hakkında daha fazla bilgi için, bkz. [iş istasyonu ve sunucu GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blogu girişi.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-174">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="5f5e0-175">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="5f5e0-175">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="5f5e0-176">Çöp toplayıcı tarafından oluşturulan Heap sayısını sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-176">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="5f5e0-177">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-177">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="5f5e0-178">[GC işlemci benzeşimi](#systemgcnoaffinitizecomplus_gcnoaffinitize) etkinse, varsayılan olarak, yığın sayısı ayarı `n` GC sayfa@@/iş parçacıklarını ilk işlemcilere göre sayar `n` .</span><span class="sxs-lookup"><span data-stu-id="5f5e0-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="5f5e0-179">(Tam olarak hangi işlemcilerin olduğunu belirtmek için, bu [maskeyi](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) seçin veya [aralıklar](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) ayarlarını kesin olarak belirleyin.)</span><span class="sxs-lookup"><span data-stu-id="5f5e0-179">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="5f5e0-180">[GC işlemci benzeşimi](#systemgcnoaffinitizecomplus_gcnoaffinitize) devre dışıysa, bu ayar GC yığınlarının sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-180">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="5f5e0-181">Daha fazla bilgi için [Gcheapcount açıklamalarını](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)inceleyin.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-181">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="5f5e0-182">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-182">Setting name</span></span> | <span data-ttu-id="5f5e0-183">Değerler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-183">Values</span></span> | <span data-ttu-id="5f5e0-184">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f5e0-184">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5f5e0-185">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-185">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="5f5e0-186">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="5f5e0-186">*decimal value*</span></span> | <span data-ttu-id="5f5e0-187">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-187">.NET Core 3.0</span></span> |
| <span data-ttu-id="5f5e0-188">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-188">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="5f5e0-189">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="5f5e0-189">*hexadecimal value*</span></span> | <span data-ttu-id="5f5e0-190">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-190">.NET Core 3.0</span></span> |
| <span data-ttu-id="5f5e0-191">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-191">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5f5e0-192">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="5f5e0-192">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="5f5e0-193">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="5f5e0-193">*decimal value*</span></span> | <span data-ttu-id="5f5e0-194">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="5f5e0-194">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="5f5e0-195">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5f5e0-195">Example:</span></span>

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
> <span data-ttu-id="5f5e0-196">*Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-196">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="5f5e0-197">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-197">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="5f5e0-198">Örneğin, Heap sayısını 16 ile sınırlamak için değerler JSON dosyası için 16, ortam değişkeni için 0x10 veya 10 olur.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-198">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="5f5e0-199">System. GC. ısıpaffinitizemask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="5f5e0-199">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="5f5e0-200">Çöp toplayıcı iş parçacıklarının kullanması gereken tam işlemcileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-200">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="5f5e0-201">[GC işlemci benzeşimi](#systemgcnoaffinitizecomplus_gcnoaffinitize) devre dışıysa, bu ayar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-201">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="5f5e0-202">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-202">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="5f5e0-203">Değer, işlem için kullanılabilir olan işlemcileri tanımlayan bir bit maskesidir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-203">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="5f5e0-204">Örneğin, bir 1023 ondalık değeri (veya ortam değişkenini kullanıyorsanız, 0x3FF veya 3FF onaltılı değeri), ikili gösterimde 0011 1111 1111 ' dir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-204">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="5f5e0-205">Bu, ilk 10 işlemcinin kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-205">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="5f5e0-206">Sıradaki 10 işlemciyi belirtmek için, işlemci 10-19 ' 1047552 nin ondalık değerini (veya 0xFFC00 ya da FFC00) bir 1111 1111 1100 0000 0000 ikili değere eşdeğer bir değere belirleyin.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-206">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="5f5e0-207">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-207">Setting name</span></span> | <span data-ttu-id="5f5e0-208">Değerler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-208">Values</span></span> | <span data-ttu-id="5f5e0-209">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f5e0-209">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5f5e0-210">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-210">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="5f5e0-211">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="5f5e0-211">*decimal value*</span></span> | <span data-ttu-id="5f5e0-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-212">.NET Core 3.0</span></span> |
| <span data-ttu-id="5f5e0-213">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-213">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="5f5e0-214">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="5f5e0-214">*hexadecimal value*</span></span> | <span data-ttu-id="5f5e0-215">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-215">.NET Core 3.0</span></span> |
| <span data-ttu-id="5f5e0-216">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-216">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5f5e0-217">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="5f5e0-217">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="5f5e0-218">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="5f5e0-218">*decimal value*</span></span> | <span data-ttu-id="5f5e0-219">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="5f5e0-219">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="5f5e0-220">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5f5e0-220">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="5f5e0-221">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="5f5e0-221">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="5f5e0-222">Çöp toplayıcı iş parçacıkları için kullanılacak işlemcilerin listesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-222">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="5f5e0-223">Bu ayar [System. GC. Cenpaffinitizemask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask)ile benzerdir, ancak 64 'den fazla işlemci belirtmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-223">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="5f5e0-224">Windows işletim sistemleri için, işlemci numarasını veya aralığını karşılık gelen [CPU grubuyla](/windows/win32/procthread/processor-groups)önek olarak ekleyin, örneğin, "0:1-10, 0:12, 1:50-52, 1:70".</span><span class="sxs-lookup"><span data-stu-id="5f5e0-224">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="5f5e0-225">[GC işlemci benzeşimi](#systemgcnoaffinitizecomplus_gcnoaffinitize) devre dışıysa, bu ayar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-225">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="5f5e0-226">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-226">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="5f5e0-227">Daha fazla bilgi için bkz. Maoni Stephens ' blogu üzerinde [> 64 CPU 'su olan MAKINELERDE GC için daha Iyi hale getirme](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) .</span><span class="sxs-lookup"><span data-stu-id="5f5e0-227">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="5f5e0-228">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-228">Setting name</span></span> | <span data-ttu-id="5f5e0-229">Değerler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-229">Values</span></span> | <span data-ttu-id="5f5e0-230">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f5e0-230">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5f5e0-231">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-231">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="5f5e0-232">İşlemci numaralarının veya işlemci numarası aralıklarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-232">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="5f5e0-233">UNIX örneği: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="5f5e0-233">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="5f5e0-234">Windows örnek: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="5f5e0-234">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="5f5e0-235">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-235">.NET Core 3.0</span></span> |
| <span data-ttu-id="5f5e0-236">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-236">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="5f5e0-237">İşlemci numaralarının veya işlemci numarası aralıklarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-237">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="5f5e0-238">UNIX örneği: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="5f5e0-238">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="5f5e0-239">Windows örnek: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="5f5e0-239">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="5f5e0-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-240">.NET Core 3.0</span></span> |

<span data-ttu-id="5f5e0-241">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5f5e0-241">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="5f5e0-242">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="5f5e0-242">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="5f5e0-243">Çöp toplayıcının [CPU grupları](/windows/win32/procthread/processor-groups) kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-243">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="5f5e0-244">64 bitlik bir Windows bilgisayarında birden çok CPU grubu olduğunda, diğer bir deyişle, 64 ' den fazla işlemci varsa, bu öğenin tüm CPU gruplarında çöp toplamayı genişletmelerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-244">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="5f5e0-245">Çöp toplayıcı, Heap 'ler oluşturmak ve dengelemek için tüm çekirdekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-245">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="5f5e0-246">Yalnızca 64-bit Windows işletim sistemlerinde sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-246">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="5f5e0-247">Varsayılan: GC, CPU grupları arasında genişletilmez.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-247">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="5f5e0-248">Bu değeri değerine ayarlamaya eşdeğerdir `0` .</span><span class="sxs-lookup"><span data-stu-id="5f5e0-248">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="5f5e0-249">Daha fazla bilgi için bkz. Maoni Stephens ' blogu üzerinde [> 64 CPU 'su olan MAKINELERDE GC için daha Iyi hale getirme](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) .</span><span class="sxs-lookup"><span data-stu-id="5f5e0-249">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="5f5e0-250">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-250">Setting name</span></span> | <span data-ttu-id="5f5e0-251">Değerler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-251">Values</span></span> | <span data-ttu-id="5f5e0-252">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f5e0-252">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5f5e0-253">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-253">**runtimeconfig.json**</span></span> | <span data-ttu-id="5f5e0-254">Yok</span><span class="sxs-lookup"><span data-stu-id="5f5e0-254">N/A</span></span> | <span data-ttu-id="5f5e0-255">Yok</span><span class="sxs-lookup"><span data-stu-id="5f5e0-255">N/A</span></span> | <span data-ttu-id="5f5e0-256">Yok</span><span class="sxs-lookup"><span data-stu-id="5f5e0-256">N/A</span></span> |
| <span data-ttu-id="5f5e0-257">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-257">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="5f5e0-258">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-258">`0` - disabled</span></span><br/><span data-ttu-id="5f5e0-259">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="5f5e0-259">`1` - enabled</span></span> | <span data-ttu-id="5f5e0-260">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-260">.NET Core 1.0</span></span> |
| <span data-ttu-id="5f5e0-261">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-261">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5f5e0-262">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="5f5e0-262">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="5f5e0-263">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-263">`false` - disabled</span></span><br/><span data-ttu-id="5f5e0-264">`true`-etkin</span><span class="sxs-lookup"><span data-stu-id="5f5e0-264">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="5f5e0-265">Ortak dil çalışma zamanını (CLR) tüm CPU grupları arasında iş parçacığı havuzundan da dağıtmak üzere yapılandırmak için, [Thread_UseAllCpuGroups öğesi](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) seçeneğini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-265">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="5f5e0-266">.NET Core uygulamaları için, ortam değişkeninin değerini olarak ayarlayarak bu seçeneği etkinleştirebilirsiniz `COMPlus_Thread_UseAllCpuGroups` `1` .</span><span class="sxs-lookup"><span data-stu-id="5f5e0-266">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="5f5e0-267">System. GC. Noafınitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="5f5e0-267">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="5f5e0-268">*Çöp toplama* iş parçacıklarının işlemcilerle kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-268">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="5f5e0-269">Bir GC iş parçacığını eklemek için yalnızca belirli bir CPU üzerinde çalışabilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-269">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="5f5e0-270">Her GC iş parçacığı için bir yığın oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-270">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="5f5e0-271">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-271">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="5f5e0-272">Varsayılan: işlemcilere sahip çöp toplama iş parçacıklarını ön olarak başlatma.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-272">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="5f5e0-273">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="5f5e0-273">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="5f5e0-274">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-274">Setting name</span></span> | <span data-ttu-id="5f5e0-275">Değerler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-275">Values</span></span> | <span data-ttu-id="5f5e0-276">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f5e0-276">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5f5e0-277">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-277">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="5f5e0-278">`false`-afze</span><span class="sxs-lookup"><span data-stu-id="5f5e0-278">`false` - affinitize</span></span><br/><span data-ttu-id="5f5e0-279">`true`-yok etme</span><span class="sxs-lookup"><span data-stu-id="5f5e0-279">`true` - don't affinitize</span></span> | <span data-ttu-id="5f5e0-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="5f5e0-281">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-281">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="5f5e0-282">`0`-afze</span><span class="sxs-lookup"><span data-stu-id="5f5e0-282">`0` - affinitize</span></span><br/><span data-ttu-id="5f5e0-283">`1`-yok etme</span><span class="sxs-lookup"><span data-stu-id="5f5e0-283">`1` - don't affinitize</span></span> | <span data-ttu-id="5f5e0-284">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-284">.NET Core 3.0</span></span> |
| <span data-ttu-id="5f5e0-285">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-285">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5f5e0-286">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="5f5e0-286">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="5f5e0-287">`false`-afze</span><span class="sxs-lookup"><span data-stu-id="5f5e0-287">`false` - affinitize</span></span><br/><span data-ttu-id="5f5e0-288">`true`-yok etme</span><span class="sxs-lookup"><span data-stu-id="5f5e0-288">`true` - don't affinitize</span></span> | <span data-ttu-id="5f5e0-289">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="5f5e0-289">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="5f5e0-290">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5f5e0-290">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="5f5e0-291">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="5f5e0-291">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="5f5e0-292">GC yığını ve GC booksaklanması için bayt cinsinden en fazla tamamlama boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-292">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="5f5e0-293">Bu ayar yalnızca 64 bitlik bilgisayarlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-293">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="5f5e0-294">Yalnızca belirli durumlarda geçerli olan varsayılan değer, kapsayıcıdaki bellek sınırının 20 MB veya %75 ' sinden daha fazladır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-294">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="5f5e0-295">Varsayılan değer şu durumlarda geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="5f5e0-295">The default value applies if:</span></span>

  - <span data-ttu-id="5f5e0-296">İşlem belirtilen bellek sınırına sahip bir kapsayıcı içinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-296">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="5f5e0-297">[System. GC. HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-297">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="5f5e0-298">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-298">Setting name</span></span> | <span data-ttu-id="5f5e0-299">Değerler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-299">Values</span></span> | <span data-ttu-id="5f5e0-300">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f5e0-300">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5f5e0-301">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-301">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="5f5e0-302">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="5f5e0-302">*decimal value*</span></span> | <span data-ttu-id="5f5e0-303">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-303">.NET Core 3.0</span></span> |
| <span data-ttu-id="5f5e0-304">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-304">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="5f5e0-305">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="5f5e0-305">*hexadecimal value*</span></span> | <span data-ttu-id="5f5e0-306">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-306">.NET Core 3.0</span></span> |

<span data-ttu-id="5f5e0-307">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5f5e0-307">Example:</span></span>

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
> <span data-ttu-id="5f5e0-308">*Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-308">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="5f5e0-309">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-309">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="5f5e0-310">Örneğin, 200 mebibytes (MIB) yığın sabit sınırı belirtmek için, değerler JSON dosyası için 209715200 ve ortam değişkeni için 0xC800000 veya C800000 olur.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-310">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="5f5e0-311">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="5f5e0-311">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="5f5e0-312">Toplam fiziksel belleğin yüzdesi olarak izin verilen GC yığın kullanımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-312">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="5f5e0-313">[System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) da ayarlandıysa, bu ayar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-313">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="5f5e0-314">Bu ayar yalnızca 64 bitlik bilgisayarlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-314">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="5f5e0-315">İşlem belirtilen bellek sınırına sahip bir kapsayıcı içinde çalışıyorsa, yüzde bu bellek sınırının yüzdesi olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-315">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="5f5e0-316">Yalnızca belirli durumlarda geçerli olan varsayılan değer, kapsayıcıda bellek sınırının 20 MB veya %75 ' si kadar küçüktür.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-316">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="5f5e0-317">Varsayılan değer şu durumlarda geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="5f5e0-317">The default value applies if:</span></span>

  - <span data-ttu-id="5f5e0-318">İşlem belirtilen bellek sınırına sahip bir kapsayıcı içinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-318">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="5f5e0-319">[System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-319">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="5f5e0-320">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-320">Setting name</span></span> | <span data-ttu-id="5f5e0-321">Değerler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-321">Values</span></span> | <span data-ttu-id="5f5e0-322">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f5e0-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5f5e0-323">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-323">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="5f5e0-324">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="5f5e0-324">*decimal value*</span></span> | <span data-ttu-id="5f5e0-325">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-325">.NET Core 3.0</span></span> |
| <span data-ttu-id="5f5e0-326">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-326">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="5f5e0-327">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="5f5e0-327">*hexadecimal value*</span></span> | <span data-ttu-id="5f5e0-328">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-328">.NET Core 3.0</span></span> |

<span data-ttu-id="5f5e0-329">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5f5e0-329">Example:</span></span>

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
> <span data-ttu-id="5f5e0-330">*Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-330">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="5f5e0-331">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-331">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="5f5e0-332">Örneğin, yığın kullanımını %30 olarak sınırlandırmak için değerler JSON dosyası için 30, ortam değişkeni için 0x1E veya 1E olur.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-332">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="5f5e0-333">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="5f5e0-333">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="5f5e0-334">Silinmesi gereken segmentlerin ileride kullanılmak üzere bir bekleme listesine mi yerleştirileceğini, yoksa işletim sistemine (OS) geri mi bırakılacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-334">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="5f5e0-335">Varsayılan: kesimleri işletim sistemine geri bırakın.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-335">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="5f5e0-336">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="5f5e0-336">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="5f5e0-337">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-337">Setting name</span></span> | <span data-ttu-id="5f5e0-338">Değerler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-338">Values</span></span> | <span data-ttu-id="5f5e0-339">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f5e0-339">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5f5e0-340">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-340">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="5f5e0-341">`false`-işletim sistemine yayın</span><span class="sxs-lookup"><span data-stu-id="5f5e0-341">`false` - release to OS</span></span><br/><span data-ttu-id="5f5e0-342">`true`-bekleme durumuna koy</span><span class="sxs-lookup"><span data-stu-id="5f5e0-342">`true` - put on standby</span></span> | <span data-ttu-id="5f5e0-343">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-343">.NET Core 1.0</span></span> |
| <span data-ttu-id="5f5e0-344">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-344">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="5f5e0-345">`false`-işletim sistemine yayın</span><span class="sxs-lookup"><span data-stu-id="5f5e0-345">`false` - release to OS</span></span><br/><span data-ttu-id="5f5e0-346">`true`-bekleme durumuna koy</span><span class="sxs-lookup"><span data-stu-id="5f5e0-346">`true` - put on standby</span></span> | <span data-ttu-id="5f5e0-347">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-347">.NET Core 1.0</span></span> |
| <span data-ttu-id="5f5e0-348">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-348">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="5f5e0-349">`0`-işletim sistemine yayın</span><span class="sxs-lookup"><span data-stu-id="5f5e0-349">`0` - release to OS</span></span><br/><span data-ttu-id="5f5e0-350">`1`-bekleme durumuna koy</span><span class="sxs-lookup"><span data-stu-id="5f5e0-350">`1` - put on standby</span></span> | <span data-ttu-id="5f5e0-351">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-351">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="5f5e0-352">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-352">Examples</span></span>

<span data-ttu-id="5f5e0-353">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="5f5e0-353">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="5f5e0-354">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="5f5e0-354">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="5f5e0-355">Büyük sayfalar</span><span class="sxs-lookup"><span data-stu-id="5f5e0-355">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="5f5e0-356">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="5f5e0-356">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="5f5e0-357">Bir yığın sabit sınırı ayarlandığında büyük sayfaların kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-357">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="5f5e0-358">Varsayılan: bir yığın sabit sınırı ayarlandığında büyük sayfalar kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-358">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="5f5e0-359">Bu değeri değerine ayarlamaya eşdeğerdir `0` .</span><span class="sxs-lookup"><span data-stu-id="5f5e0-359">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="5f5e0-360">Bu bir deneysel ayardır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-360">This is an experimental setting.</span></span>

| | <span data-ttu-id="5f5e0-361">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-361">Setting name</span></span> | <span data-ttu-id="5f5e0-362">Değerler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-362">Values</span></span> | <span data-ttu-id="5f5e0-363">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f5e0-363">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5f5e0-364">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-364">**runtimeconfig.json**</span></span> | <span data-ttu-id="5f5e0-365">Yok</span><span class="sxs-lookup"><span data-stu-id="5f5e0-365">N/A</span></span> | <span data-ttu-id="5f5e0-366">Yok</span><span class="sxs-lookup"><span data-stu-id="5f5e0-366">N/A</span></span> | <span data-ttu-id="5f5e0-367">Yok</span><span class="sxs-lookup"><span data-stu-id="5f5e0-367">N/A</span></span> |
| <span data-ttu-id="5f5e0-368">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-368">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="5f5e0-369">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-369">`0` - disabled</span></span><br/><span data-ttu-id="5f5e0-370">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="5f5e0-370">`1` - enabled</span></span> | <span data-ttu-id="5f5e0-371">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-371">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="5f5e0-372">Büyük nesneler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-372">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="5f5e0-373">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="5f5e0-373">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="5f5e0-374">Toplam boyuttaki 2 gigabayttan (GB) büyük olan diziler için 64 bitlik platformlarda çöp toplayıcı desteğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-374">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="5f5e0-375">Varsayılan: GC 2 GB 'tan büyük dizileri destekler.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-375">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="5f5e0-376">Bu değeri değerine ayarlamaya eşdeğerdir `1` .</span><span class="sxs-lookup"><span data-stu-id="5f5e0-376">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="5f5e0-377">Bu seçenek, .NET 'in gelecek bir sürümünde kullanımdan kalkabilir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-377">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="5f5e0-378">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-378">Setting name</span></span> | <span data-ttu-id="5f5e0-379">Değerler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-379">Values</span></span> | <span data-ttu-id="5f5e0-380">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f5e0-380">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5f5e0-381">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-381">**runtimeconfig.json**</span></span> | <span data-ttu-id="5f5e0-382">Yok</span><span class="sxs-lookup"><span data-stu-id="5f5e0-382">N/A</span></span> | <span data-ttu-id="5f5e0-383">Yok</span><span class="sxs-lookup"><span data-stu-id="5f5e0-383">N/A</span></span> | <span data-ttu-id="5f5e0-384">Yok</span><span class="sxs-lookup"><span data-stu-id="5f5e0-384">N/A</span></span> |
| <span data-ttu-id="5f5e0-385">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-385">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="5f5e0-386">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="5f5e0-386">`1` - enabled</span></span><br/> <span data-ttu-id="5f5e0-387">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-387">`0` - disabled</span></span> | <span data-ttu-id="5f5e0-388">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="5f5e0-389">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5f5e0-390">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="5f5e0-390">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="5f5e0-391">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="5f5e0-391">`1` - enabled</span></span><br/> <span data-ttu-id="5f5e0-392">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-392">`0` - disabled</span></span> | <span data-ttu-id="5f5e0-393">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="5f5e0-393">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="5f5e0-394">Büyük nesne yığın eşiği</span><span class="sxs-lookup"><span data-stu-id="5f5e0-394">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="5f5e0-395">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="5f5e0-395">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="5f5e0-396">Nesnelerin büyük nesne yığınında (LOH) geçmesine neden olan eşik boyutunu bayt cinsinden belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-396">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="5f5e0-397">Varsayılan eşik 85.000 bayttır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-397">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="5f5e0-398">Belirttiğiniz değer varsayılan eşikten büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-398">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="5f5e0-399">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-399">Setting name</span></span> | <span data-ttu-id="5f5e0-400">Değerler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-400">Values</span></span> | <span data-ttu-id="5f5e0-401">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f5e0-401">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5f5e0-402">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-402">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="5f5e0-403">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="5f5e0-403">*decimal value*</span></span> | <span data-ttu-id="5f5e0-404">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-404">.NET Core 1.0</span></span> |
| <span data-ttu-id="5f5e0-405">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-405">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="5f5e0-406">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="5f5e0-406">*hexadecimal value*</span></span> | <span data-ttu-id="5f5e0-407">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-407">.NET Core 1.0</span></span> |
| <span data-ttu-id="5f5e0-408">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-408">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="5f5e0-409">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="5f5e0-409">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="5f5e0-410">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="5f5e0-410">*decimal value*</span></span> | <span data-ttu-id="5f5e0-411"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="5f5e0-411">.NET Framework 4.8</span></span> |

<span data-ttu-id="5f5e0-412">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5f5e0-412">Example:</span></span>

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
> <span data-ttu-id="5f5e0-413">*Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-413">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="5f5e0-414">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-414">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="5f5e0-415">Örneğin, 120.000 baytlık bir eşik boyutu ayarlamak için, değerler JSON dosyası için 120000, ve ortam değişkeni için 0x1D4C0 ya da 1D4C0 olur.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-415">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="5f5e0-416">Tek başına GC</span><span class="sxs-lookup"><span data-stu-id="5f5e0-416">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="5f5e0-417">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="5f5e0-417">COMPlus_GCName</span></span>

- <span data-ttu-id="5f5e0-418">Çalışma zamanının yüklemeyi amaçladığı çöp toplayıcısını içeren kitaplığın yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f5e0-418">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="5f5e0-419">Daha fazla bilgi için bkz. [tek BAŞıNA GC yükleyici tasarımı](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="5f5e0-419">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="5f5e0-420">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="5f5e0-420">Setting name</span></span> | <span data-ttu-id="5f5e0-421">Değerler</span><span class="sxs-lookup"><span data-stu-id="5f5e0-421">Values</span></span> | <span data-ttu-id="5f5e0-422">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f5e0-422">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="5f5e0-423">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-423">**runtimeconfig.json**</span></span> | <span data-ttu-id="5f5e0-424">Yok</span><span class="sxs-lookup"><span data-stu-id="5f5e0-424">N/A</span></span> | <span data-ttu-id="5f5e0-425">Yok</span><span class="sxs-lookup"><span data-stu-id="5f5e0-425">N/A</span></span> | <span data-ttu-id="5f5e0-426">Yok</span><span class="sxs-lookup"><span data-stu-id="5f5e0-426">N/A</span></span> |
| <span data-ttu-id="5f5e0-427">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="5f5e0-427">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="5f5e0-428">*string_path*</span><span class="sxs-lookup"><span data-stu-id="5f5e0-428">*string_path*</span></span> | <span data-ttu-id="5f5e0-429">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5f5e0-429">.NET Core 2.0</span></span> |
