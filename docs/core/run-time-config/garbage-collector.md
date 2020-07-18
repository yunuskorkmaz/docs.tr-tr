---
title: Çöp toplayıcı yapılandırma ayarları
description: Çöp toplayıcının .NET Core uygulamaları için belleği nasıl yönettiğini yapılandırmak üzere çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 07/10/2020
ms.topic: reference
ms.openlocfilehash: 6ae5b7447fb0df4978ea9dcaa5e76fcc7a6cc4ca
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441419"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="7ae5e-103">Çöp toplama için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="7ae5e-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="7ae5e-104">Bu sayfa, çalışma zamanında değiştirilebilen çöp toplayıcı (GC) ayarları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="7ae5e-105">Çalışan bir uygulamanın en yüksek performans düzeyine ulaşmak istiyorsanız bu ayarları kullanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="7ae5e-106">Bununla birlikte, varsayılan olarak, çoğu uygulama için tipik durumlarda en iyi performansı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="7ae5e-107">Ayarlar bu sayfadaki gruplar halinde düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="7ae5e-108">Her grup içindeki ayarlar, belirli bir sonuca ulaşmak için genellikle birbirleriyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="7ae5e-109">Bu ayarlar ayrıca uygulama çalışırken dinamik olarak değiştirilebilir, bu nedenle ayarladığınız tüm çalışma zamanı ayarları geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="7ae5e-110">[Gecikme düzeyi](../../standard/garbage-collection/latency.md)gibi bazı ayarlar tipik olarak yalnızca TASARıM zamanında API aracılığıyla ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="7ae5e-111">Bu tür ayarlar bu sayfadan çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="7ae5e-112">Sayı değerleri için, dosyadaki *runtimeconfig.js* , ortam değişkeni ayarları için onaltılı gösterimdeki ayarlar için ondalık gösterimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="7ae5e-113">Onaltılık değerler için, bunları "0x" öneki olmadan veya olmadan belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="7ae5e-114">Çöp toplamanın türleri</span><span class="sxs-lookup"><span data-stu-id="7ae5e-114">Flavors of garbage collection</span></span>

<span data-ttu-id="7ae5e-115">Çöp toplamanın iki ana özellikleri, iş istasyonu GC ve sunucu GC ' dir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="7ae5e-116">İkisi arasındaki farklılıklar hakkında daha fazla bilgi için bkz. [Workstation and Server çöp toplama](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="7ae5e-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="7ae5e-117">Çöp toplamanın alt türleri arka plan ve eş zamanlı değil.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="7ae5e-118">Çöp toplamanın türlerini seçmek için aşağıdaki ayarları kullanın:</span><span class="sxs-lookup"><span data-stu-id="7ae5e-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="7ae5e-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="7ae5e-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="7ae5e-120">Uygulamanın iş istasyonu çöp toplamayı veya sunucu çöp toplamayı kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="7ae5e-121">Varsayılan: Iş Istasyonu atık toplama.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-121">Default: Workstation garbage collection.</span></span> <span data-ttu-id="7ae5e-122">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="7ae5e-122">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="7ae5e-123">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-123">Setting name</span></span> | <span data-ttu-id="7ae5e-124">Değerler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-124">Values</span></span> | <span data-ttu-id="7ae5e-125">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ae5e-125">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7ae5e-126">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-126">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="7ae5e-127">`false`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="7ae5e-127">`false` - workstation</span></span><br/><span data-ttu-id="7ae5e-128">`true`-sunucu</span><span class="sxs-lookup"><span data-stu-id="7ae5e-128">`true` - server</span></span> | <span data-ttu-id="7ae5e-129">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-129">.NET Core 1.0</span></span> |
| <span data-ttu-id="7ae5e-130">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-130">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="7ae5e-131">`false`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="7ae5e-131">`false` - workstation</span></span><br/><span data-ttu-id="7ae5e-132">`true`-sunucu</span><span class="sxs-lookup"><span data-stu-id="7ae5e-132">`true` - server</span></span> | <span data-ttu-id="7ae5e-133">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-133">.NET Core 1.0</span></span> |
| <span data-ttu-id="7ae5e-134">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-134">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="7ae5e-135">`0`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="7ae5e-135">`0` - workstation</span></span><br/><span data-ttu-id="7ae5e-136">`1`-sunucu</span><span class="sxs-lookup"><span data-stu-id="7ae5e-136">`1` - server</span></span> | <span data-ttu-id="7ae5e-137">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-137">.NET Core 1.0</span></span> |
| <span data-ttu-id="7ae5e-138">**.NET Framework içinapp.config**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-138">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="7ae5e-139">GCServer</span><span class="sxs-lookup"><span data-stu-id="7ae5e-139">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="7ae5e-140">`false`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="7ae5e-140">`false` - workstation</span></span><br/><span data-ttu-id="7ae5e-141">`true`-sunucu</span><span class="sxs-lookup"><span data-stu-id="7ae5e-141">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="7ae5e-142">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-142">Examples</span></span>

<span data-ttu-id="7ae5e-143">*runtimeconfig.js* dosya:</span><span class="sxs-lookup"><span data-stu-id="7ae5e-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="7ae5e-144">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="7ae5e-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="7ae5e-145">System. GC. eşzamanlı/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="7ae5e-145">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="7ae5e-146">Arka plan (eşzamanlı) Çöp toplamanın etkinleştirilip etkinleştirilmeyeceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-146">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="7ae5e-147">Varsayılan: arka plan GC kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-147">Default: Use background GC.</span></span> <span data-ttu-id="7ae5e-148">Bu değeri değerine ayarlamaya eşdeğerdir `true` .</span><span class="sxs-lookup"><span data-stu-id="7ae5e-148">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="7ae5e-149">Daha fazla bilgi için bkz. [arka plan atık toplama](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="7ae5e-149">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="7ae5e-150">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-150">Setting name</span></span> | <span data-ttu-id="7ae5e-151">Değerler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-151">Values</span></span> | <span data-ttu-id="7ae5e-152">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ae5e-152">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7ae5e-153">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-153">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="7ae5e-154">`true`-arka plan GC</span><span class="sxs-lookup"><span data-stu-id="7ae5e-154">`true` - background GC</span></span><br/><span data-ttu-id="7ae5e-155">`false`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="7ae5e-155">`false` - non-concurrent GC</span></span> | <span data-ttu-id="7ae5e-156">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-156">.NET Core 1.0</span></span> |
| <span data-ttu-id="7ae5e-157">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-157">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="7ae5e-158">`true`-arka plan GC</span><span class="sxs-lookup"><span data-stu-id="7ae5e-158">`true` - background GC</span></span><br/><span data-ttu-id="7ae5e-159">`false`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="7ae5e-159">`false` - non-concurrent GC</span></span> | <span data-ttu-id="7ae5e-160">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-160">.NET Core 1.0</span></span> |
| <span data-ttu-id="7ae5e-161">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-161">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="7ae5e-162">`1`-arka plan GC</span><span class="sxs-lookup"><span data-stu-id="7ae5e-162">`1` - background GC</span></span><br/><span data-ttu-id="7ae5e-163">`0`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="7ae5e-163">`0` - non-concurrent GC</span></span> | <span data-ttu-id="7ae5e-164">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-164">.NET Core 1.0</span></span> |
| <span data-ttu-id="7ae5e-165">**.NET Framework içinapp.config**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-165">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="7ae5e-166">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="7ae5e-166">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="7ae5e-167">`true`-arka plan GC</span><span class="sxs-lookup"><span data-stu-id="7ae5e-167">`true` - background GC</span></span><br/><span data-ttu-id="7ae5e-168">`false`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="7ae5e-168">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="7ae5e-169">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-169">Examples</span></span>

<span data-ttu-id="7ae5e-170">*runtimeconfig.js* dosya:</span><span class="sxs-lookup"><span data-stu-id="7ae5e-170">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="7ae5e-171">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="7ae5e-171">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="7ae5e-172">Kaynak kullanımını yönetme</span><span class="sxs-lookup"><span data-stu-id="7ae5e-172">Manage resource usage</span></span>

<span data-ttu-id="7ae5e-173">Çöp toplayıcının bellek ve işlemci kullanımını yönetmek için bu bölümde açıklanan ayarları kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-173">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="7ae5e-174">Bu ayarlardan bazıları hakkında daha fazla bilgi için, bkz. [iş istasyonu ve sunucu GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blogu girişi.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-174">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="7ae5e-175">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="7ae5e-175">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="7ae5e-176">Çöp toplayıcı tarafından oluşturulan Heap sayısını sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-176">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="7ae5e-177">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-177">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="7ae5e-178">[GC işlemci benzeşimi](#systemgcnoaffinitizecomplus_gcnoaffinitize) etkinse, varsayılan olarak, yığın sayısı ayarı `n` GC sayfa@@/iş parçacıklarını ilk işlemcilere göre sayar `n` .</span><span class="sxs-lookup"><span data-stu-id="7ae5e-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="7ae5e-179">(Tam olarak hangi işlemcilerin olduğunu belirtmek için, bu [maskeyi](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) seçin veya [aralıklar](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) ayarlarını kesin olarak belirleyin.)</span><span class="sxs-lookup"><span data-stu-id="7ae5e-179">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="7ae5e-180">[GC işlemci benzeşimi](#systemgcnoaffinitizecomplus_gcnoaffinitize) devre dışıysa, bu ayar GC yığınlarının sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-180">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="7ae5e-181">Daha fazla bilgi için [Gcheapcount açıklamalarını](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)inceleyin.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-181">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="7ae5e-182">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-182">Setting name</span></span> | <span data-ttu-id="7ae5e-183">Değerler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-183">Values</span></span> | <span data-ttu-id="7ae5e-184">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ae5e-184">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7ae5e-185">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-185">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="7ae5e-186">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-186">*decimal value*</span></span> | <span data-ttu-id="7ae5e-187">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-187">.NET Core 3.0</span></span> |
| <span data-ttu-id="7ae5e-188">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-188">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="7ae5e-189">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-189">*hexadecimal value*</span></span> | <span data-ttu-id="7ae5e-190">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-190">.NET Core 3.0</span></span> |
| <span data-ttu-id="7ae5e-191">**.NET Framework içinapp.config**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-191">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="7ae5e-192">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="7ae5e-192">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="7ae5e-193">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-193">*decimal value*</span></span> | <span data-ttu-id="7ae5e-194">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="7ae5e-194">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="7ae5e-195">Örnek:</span><span class="sxs-lookup"><span data-stu-id="7ae5e-195">Example:</span></span>

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
> <span data-ttu-id="7ae5e-196">*Üzerinderuntimeconfig.js*seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-196">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="7ae5e-197">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-197">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="7ae5e-198">Örneğin, Heap sayısını 16 ile sınırlamak için değerler JSON dosyası için 16, ortam değişkeni için 0x10 veya 10 olur.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-198">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="7ae5e-199">System. GC. ısıpaffinitizemask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="7ae5e-199">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="7ae5e-200">Çöp toplayıcı iş parçacıklarının kullanması gereken tam işlemcileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-200">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="7ae5e-201">[GC işlemci benzeşimi](#systemgcnoaffinitizecomplus_gcnoaffinitize) devre dışıysa, bu ayar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-201">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="7ae5e-202">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-202">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="7ae5e-203">Değer, işlem için kullanılabilir olan işlemcileri tanımlayan bir bit maskesidir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-203">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="7ae5e-204">Örneğin, bir 1023 ondalık değeri (veya ortam değişkenini kullanıyorsanız, 0x3FF veya 3FF onaltılı değeri), ikili gösterimde 0011 1111 1111 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-204">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="7ae5e-205">Bu, ilk 10 işlemcinin kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-205">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="7ae5e-206">Sıradaki 10 işlemciyi belirtmek için, işlemci 10-19 ' 1047552 nin ondalık değerini (veya 0xFFC00 ya da FFC00) bir 1111 1111 1100 0000 0000 ikili değere eşdeğer bir değere belirleyin.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-206">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="7ae5e-207">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-207">Setting name</span></span> | <span data-ttu-id="7ae5e-208">Değerler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-208">Values</span></span> | <span data-ttu-id="7ae5e-209">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ae5e-209">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7ae5e-210">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-210">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="7ae5e-211">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-211">*decimal value*</span></span> | <span data-ttu-id="7ae5e-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-212">.NET Core 3.0</span></span> |
| <span data-ttu-id="7ae5e-213">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-213">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="7ae5e-214">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-214">*hexadecimal value*</span></span> | <span data-ttu-id="7ae5e-215">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-215">.NET Core 3.0</span></span> |
| <span data-ttu-id="7ae5e-216">**.NET Framework içinapp.config**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-216">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="7ae5e-217">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="7ae5e-217">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="7ae5e-218">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-218">*decimal value*</span></span> | <span data-ttu-id="7ae5e-219">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="7ae5e-219">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="7ae5e-220">Örnek:</span><span class="sxs-lookup"><span data-stu-id="7ae5e-220">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="7ae5e-221">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="7ae5e-221">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="7ae5e-222">Çöp toplayıcı iş parçacıkları için kullanılacak işlemcilerin listesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-222">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="7ae5e-223">Bu ayar [System. GC. Cenpaffinitizemask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask)ile benzerdir, ancak 64 'den fazla işlemci belirtmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-223">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="7ae5e-224">Windows işletim sistemleri için, işlemci numarasını veya aralığını karşılık gelen [CPU grubuyla](/windows/win32/procthread/processor-groups)önek olarak ekleyin, örneğin, "0:1-10, 0:12, 1:50-52, 1:70".</span><span class="sxs-lookup"><span data-stu-id="7ae5e-224">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="7ae5e-225">[GC işlemci benzeşimi](#systemgcnoaffinitizecomplus_gcnoaffinitize) devre dışıysa, bu ayar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-225">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="7ae5e-226">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-226">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="7ae5e-227">Daha fazla bilgi için bkz. Maoni Stephens ' blogu üzerinde [> 64 CPU 'su olan MAKINELERDE GC için daha Iyi hale getirme](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) .</span><span class="sxs-lookup"><span data-stu-id="7ae5e-227">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="7ae5e-228">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-228">Setting name</span></span> | <span data-ttu-id="7ae5e-229">Değerler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-229">Values</span></span> | <span data-ttu-id="7ae5e-230">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ae5e-230">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7ae5e-231">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-231">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="7ae5e-232">İşlemci numaralarının veya işlemci numarası aralıklarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-232">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="7ae5e-233">UNIX örneği: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="7ae5e-233">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="7ae5e-234">Windows örnek: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="7ae5e-234">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="7ae5e-235">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-235">.NET Core 3.0</span></span> |
| <span data-ttu-id="7ae5e-236">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-236">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="7ae5e-237">İşlemci numaralarının veya işlemci numarası aralıklarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-237">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="7ae5e-238">UNIX örneği: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="7ae5e-238">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="7ae5e-239">Windows örnek: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="7ae5e-239">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="7ae5e-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-240">.NET Core 3.0</span></span> |

<span data-ttu-id="7ae5e-241">Örnek:</span><span class="sxs-lookup"><span data-stu-id="7ae5e-241">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="7ae5e-242">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="7ae5e-242">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="7ae5e-243">Çöp toplayıcının [CPU grupları](/windows/win32/procthread/processor-groups) kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-243">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="7ae5e-244">64 bitlik bir Windows bilgisayarında birden çok CPU grubu olduğunda, diğer bir deyişle, 64 ' den fazla işlemci varsa, bu öğenin tüm CPU gruplarında çöp toplamayı genişletmelerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-244">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="7ae5e-245">Çöp toplayıcı, Heap 'ler oluşturmak ve dengelemek için tüm çekirdekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-245">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="7ae5e-246">Yalnızca 64-bit Windows işletim sistemlerinde sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-246">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="7ae5e-247">Varsayılan: GC, CPU grupları arasında genişletilmez.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-247">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="7ae5e-248">Bu değeri değerine ayarlamaya eşdeğerdir `0` .</span><span class="sxs-lookup"><span data-stu-id="7ae5e-248">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="7ae5e-249">Daha fazla bilgi için bkz. Maoni Stephens ' blogu üzerinde [> 64 CPU 'su olan MAKINELERDE GC için daha Iyi hale getirme](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) .</span><span class="sxs-lookup"><span data-stu-id="7ae5e-249">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="7ae5e-250">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-250">Setting name</span></span> | <span data-ttu-id="7ae5e-251">Değerler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-251">Values</span></span> | <span data-ttu-id="7ae5e-252">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ae5e-252">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7ae5e-253">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-253">**runtimeconfig.json**</span></span> | <span data-ttu-id="7ae5e-254">Yok</span><span class="sxs-lookup"><span data-stu-id="7ae5e-254">N/A</span></span> | <span data-ttu-id="7ae5e-255">Yok</span><span class="sxs-lookup"><span data-stu-id="7ae5e-255">N/A</span></span> | <span data-ttu-id="7ae5e-256">Yok</span><span class="sxs-lookup"><span data-stu-id="7ae5e-256">N/A</span></span> |
| <span data-ttu-id="7ae5e-257">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-257">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="7ae5e-258">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-258">`0` - disabled</span></span><br/><span data-ttu-id="7ae5e-259">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="7ae5e-259">`1` - enabled</span></span> | <span data-ttu-id="7ae5e-260">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-260">.NET Core 1.0</span></span> |
| <span data-ttu-id="7ae5e-261">**.NET Framework içinapp.config**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-261">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="7ae5e-262">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="7ae5e-262">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="7ae5e-263">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-263">`false` - disabled</span></span><br/><span data-ttu-id="7ae5e-264">`true`-etkin</span><span class="sxs-lookup"><span data-stu-id="7ae5e-264">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="7ae5e-265">Ortak dil çalışma zamanını (CLR) tüm CPU grupları arasında iş parçacığı havuzundan da dağıtmak üzere yapılandırmak için, [Thread_UseAllCpuGroups öğesi](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) seçeneğini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-265">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="7ae5e-266">.NET Core uygulamaları için, ortam değişkeninin değerini olarak ayarlayarak bu seçeneği etkinleştirebilirsiniz `COMPlus_Thread_UseAllCpuGroups` `1` .</span><span class="sxs-lookup"><span data-stu-id="7ae5e-266">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="7ae5e-267">System. GC. Noafınitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="7ae5e-267">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="7ae5e-268">*Çöp toplama* iş parçacıklarının işlemcilerle kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-268">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="7ae5e-269">Bir GC iş parçacığını eklemek için yalnızca belirli bir CPU üzerinde çalışabilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-269">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="7ae5e-270">Her GC iş parçacığı için bir yığın oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-270">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="7ae5e-271">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-271">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="7ae5e-272">Varsayılan: işlemcilere sahip çöp toplama iş parçacıklarını ön olarak başlatma.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-272">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="7ae5e-273">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="7ae5e-273">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="7ae5e-274">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-274">Setting name</span></span> | <span data-ttu-id="7ae5e-275">Değerler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-275">Values</span></span> | <span data-ttu-id="7ae5e-276">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ae5e-276">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7ae5e-277">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-277">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="7ae5e-278">`false`-afze</span><span class="sxs-lookup"><span data-stu-id="7ae5e-278">`false` - affinitize</span></span><br/><span data-ttu-id="7ae5e-279">`true`-yok etme</span><span class="sxs-lookup"><span data-stu-id="7ae5e-279">`true` - don't affinitize</span></span> | <span data-ttu-id="7ae5e-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="7ae5e-281">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-281">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="7ae5e-282">`0`-afze</span><span class="sxs-lookup"><span data-stu-id="7ae5e-282">`0` - affinitize</span></span><br/><span data-ttu-id="7ae5e-283">`1`-yok etme</span><span class="sxs-lookup"><span data-stu-id="7ae5e-283">`1` - don't affinitize</span></span> | <span data-ttu-id="7ae5e-284">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-284">.NET Core 3.0</span></span> |
| <span data-ttu-id="7ae5e-285">**.NET Framework içinapp.config**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-285">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="7ae5e-286">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="7ae5e-286">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="7ae5e-287">`false`-afze</span><span class="sxs-lookup"><span data-stu-id="7ae5e-287">`false` - affinitize</span></span><br/><span data-ttu-id="7ae5e-288">`true`-yok etme</span><span class="sxs-lookup"><span data-stu-id="7ae5e-288">`true` - don't affinitize</span></span> | <span data-ttu-id="7ae5e-289">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="7ae5e-289">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="7ae5e-290">Örnek:</span><span class="sxs-lookup"><span data-stu-id="7ae5e-290">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="7ae5e-291">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="7ae5e-291">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="7ae5e-292">GC yığını ve GC booksaklanması için bayt cinsinden en fazla tamamlama boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-292">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="7ae5e-293">Bu ayar yalnızca 64 bitlik bilgisayarlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-293">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="7ae5e-294">[Nesne başına yığın sınırları](#per-object-heap-limits) yapılandırılırsa Bu ayar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-294">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="7ae5e-295">Yalnızca belirli durumlarda geçerli olan varsayılan değer, kapsayıcıdaki bellek sınırının 20 MB veya %75 ' sinden daha fazladır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-295">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="7ae5e-296">Varsayılan değer şu durumlarda geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="7ae5e-296">The default value applies if:</span></span>

  - <span data-ttu-id="7ae5e-297">İşlem belirtilen bellek sınırına sahip bir kapsayıcı içinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-297">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="7ae5e-298">[System. GC. HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-298">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="7ae5e-299">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-299">Setting name</span></span> | <span data-ttu-id="7ae5e-300">Değerler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-300">Values</span></span> | <span data-ttu-id="7ae5e-301">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ae5e-301">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7ae5e-302">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-302">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="7ae5e-303">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-303">*decimal value*</span></span> | <span data-ttu-id="7ae5e-304">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-304">.NET Core 3.0</span></span> |
| <span data-ttu-id="7ae5e-305">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-305">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="7ae5e-306">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-306">*hexadecimal value*</span></span> | <span data-ttu-id="7ae5e-307">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-307">.NET Core 3.0</span></span> |

<span data-ttu-id="7ae5e-308">Örnek:</span><span class="sxs-lookup"><span data-stu-id="7ae5e-308">Example:</span></span>

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
> <span data-ttu-id="7ae5e-309">*Üzerinderuntimeconfig.js*seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-309">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="7ae5e-310">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-310">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="7ae5e-311">Örneğin, 200 mebibytes (MIB) yığın sabit sınırı belirtmek için, değerler JSON dosyası için 209715200 ve ortam değişkeni için 0xC800000 veya C800000 olur.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-311">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="7ae5e-312">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="7ae5e-312">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="7ae5e-313">Toplam fiziksel belleğin yüzdesi olarak izin verilen GC yığın kullanımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-313">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="7ae5e-314">[System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) da ayarlandıysa, bu ayar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-314">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="7ae5e-315">Bu ayar yalnızca 64 bitlik bilgisayarlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-315">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="7ae5e-316">İşlem belirtilen bellek sınırına sahip bir kapsayıcı içinde çalışıyorsa, yüzde bu bellek sınırının yüzdesi olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-316">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="7ae5e-317">[Nesne başına yığın sınırları](#per-object-heap-limits) yapılandırılırsa Bu ayar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-317">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="7ae5e-318">Yalnızca belirli durumlarda geçerli olan varsayılan değer, kapsayıcıda bellek sınırının 20 MB veya %75 ' si kadar küçüktür.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-318">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="7ae5e-319">Varsayılan değer şu durumlarda geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="7ae5e-319">The default value applies if:</span></span>

  - <span data-ttu-id="7ae5e-320">İşlem belirtilen bellek sınırına sahip bir kapsayıcı içinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-320">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="7ae5e-321">[System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-321">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="7ae5e-322">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-322">Setting name</span></span> | <span data-ttu-id="7ae5e-323">Değerler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-323">Values</span></span> | <span data-ttu-id="7ae5e-324">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ae5e-324">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7ae5e-325">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-325">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="7ae5e-326">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-326">*decimal value*</span></span> | <span data-ttu-id="7ae5e-327">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-327">.NET Core 3.0</span></span> |
| <span data-ttu-id="7ae5e-328">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-328">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="7ae5e-329">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-329">*hexadecimal value*</span></span> | <span data-ttu-id="7ae5e-330">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-330">.NET Core 3.0</span></span> |

<span data-ttu-id="7ae5e-331">Örnek:</span><span class="sxs-lookup"><span data-stu-id="7ae5e-331">Example:</span></span>

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
> <span data-ttu-id="7ae5e-332">*Üzerinderuntimeconfig.js*seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-332">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="7ae5e-333">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-333">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="7ae5e-334">Örneğin, yığın kullanımını %30 olarak sınırlandırmak için değerler JSON dosyası için 30, ortam değişkeni için 0x1E veya 1E olur.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-334">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="per-object-heap-limits"></a><span data-ttu-id="7ae5e-335">Nesne başına yığın sınırları</span><span class="sxs-lookup"><span data-stu-id="7ae5e-335">Per-object-heap limits</span></span>

<span data-ttu-id="7ae5e-336">GC 'nin izin verilen yığın kullanımını nesne başına yığın temelinde belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-336">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="7ae5e-337">Farklı sayfa@@ 'ler büyük nesne yığını (LOH), küçük nesne yığını (SoH) ve sabitlenmiş nesne yığını (POH).</span><span class="sxs-lookup"><span data-stu-id="7ae5e-337">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

#### <a name="complus_gcheaphardlimitsoh-complus_gcheaphardlimitloh-complus_gcheaphardlimitpoh"></a><span data-ttu-id="7ae5e-338">COMPLUS_GCHeapHardLimitSOH, COMPLUS_GCHeapHardLimitLOH, COMPLUS_GCHeapHardLimitPOH</span><span class="sxs-lookup"><span data-stu-id="7ae5e-338">COMPLUS_GCHeapHardLimitSOH, COMPLUS_GCHeapHardLimitLOH, COMPLUS_GCHeapHardLimitPOH</span></span>

- <span data-ttu-id="7ae5e-339">, Veya ayarlarından herhangi biri için bir değer belirtirseniz `COMPLUS_GCHeapHardLimitSOH` `COMPLUS_GCHeapHardLimitLOH` `COMPLUS_GCHeapHardLimitPOH` , ve için bir değer de belirtmeniz gerekir `COMPLUS_GCHeapHardLimitSOH` `COMPLUS_GCHeapHardLimitLOH` .</span><span class="sxs-lookup"><span data-stu-id="7ae5e-339">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, or `COMPLUS_GCHeapHardLimitPOH` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH`.</span></span> <span data-ttu-id="7ae5e-340">Aksi takdirde, çalışma zamanı başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-340">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="7ae5e-341">İçin varsayılan değer `COMPLUS_GCHeapHardLimitPOH` 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-341">The default value for `COMPLUS_GCHeapHardLimitPOH` is 0.</span></span> <span data-ttu-id="7ae5e-342">`COMPLUS_GCHeapHardLimitSOH`ve `COMPLUS_GCHeapHardLimitLOH` varsayılan değerlere sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-342">`COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH` don't have default values.</span></span>

| | <span data-ttu-id="7ae5e-343">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-343">Setting name</span></span> | <span data-ttu-id="7ae5e-344">Değerler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-344">Values</span></span> | <span data-ttu-id="7ae5e-345">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ae5e-345">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7ae5e-346">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-346">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOH` | <span data-ttu-id="7ae5e-347">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-347">*hexadecimal value*</span></span> | <span data-ttu-id="7ae5e-348">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-348">.NET 5.0</span></span> |
| <span data-ttu-id="7ae5e-349">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-349">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOH` | <span data-ttu-id="7ae5e-350">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-350">*hexadecimal value*</span></span> | <span data-ttu-id="7ae5e-351">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-351">.NET 5.0</span></span> |
| <span data-ttu-id="7ae5e-352">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-352">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOH` | <span data-ttu-id="7ae5e-353">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-353">*hexadecimal value*</span></span> | <span data-ttu-id="7ae5e-354">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-354">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="7ae5e-355">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-355">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="7ae5e-356">Örneğin, 200 mebibytes (MIB) yığın sabit sınırı belirtmek için, değer 0xC800000 veya C800000 olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-356">For example, to specify a heap hard limit of 200 mebibytes (MiB), the value would be 0xC800000 or C800000.</span></span>

#### <a name="complus_gcheaphardlimitsohpercent-complus_gcheaphardlimitlohpercent-complus_gcheaphardlimitpohpercent"></a><span data-ttu-id="7ae5e-357">COMPLUS_GCHeapHardLimitSOHPercent, COMPLUS_GCHeapHardLimitLOHPercent, COMPLUS_GCHeapHardLimitPOHPercent</span><span class="sxs-lookup"><span data-stu-id="7ae5e-357">COMPLUS_GCHeapHardLimitSOHPercent, COMPLUS_GCHeapHardLimitLOHPercent, COMPLUS_GCHeapHardLimitPOHPercent</span></span>

- <span data-ttu-id="7ae5e-358">, Veya ayarlarından herhangi biri için bir değer belirtirseniz `COMPLUS_GCHeapHardLimitSOHPercent` `COMPLUS_GCHeapHardLimitLOHPercent` `COMPLUS_GCHeapHardLimitPOHPercent` , ve için bir değer de belirtmeniz gerekir `COMPLUS_GCHeapHardLimitSOHPercent` `COMPLUS_GCHeapHardLimitLOHPercent` .</span><span class="sxs-lookup"><span data-stu-id="7ae5e-358">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOHPercent`, `COMPLUS_GCHeapHardLimitLOHPercent`, or `COMPLUS_GCHeapHardLimitPOHPercent` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOHPercent` and `COMPLUS_GCHeapHardLimitLOHPercent`.</span></span> <span data-ttu-id="7ae5e-359">Aksi takdirde, çalışma zamanı başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-359">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="7ae5e-360">`COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH` , Ve belirtildiğinde bu ayarlar yoksayılır `COMPLUS_GCHeapHardLimitPOH` .</span><span class="sxs-lookup"><span data-stu-id="7ae5e-360">These settings are ignored if `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, and `COMPLUS_GCHeapHardLimitPOH` are specified.</span></span>
- <span data-ttu-id="7ae5e-361">1 değeri, GC 'nin bu nesne yığını için toplam fiziksel belleğin %1 ' i kullanması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-361">A value of 1 means that GC uses 1% of total physical memory for that object heap.</span></span>
- <span data-ttu-id="7ae5e-362">Her değerin sıfırdan büyük ve 100 ' den küçük olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-362">Each value must be greater than zero and less than 100.</span></span> <span data-ttu-id="7ae5e-363">Ayrıca, üç yüzde değerinin toplamı 100 ' den az olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-363">Additionally, the sum of the three percentage values must be less than 100.</span></span> <span data-ttu-id="7ae5e-364">Aksi takdirde, çalışma zamanı başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-364">Otherwise, the runtime will fail to initialize.</span></span>

| | <span data-ttu-id="7ae5e-365">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-365">Setting name</span></span> | <span data-ttu-id="7ae5e-366">Değerler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-366">Values</span></span> | <span data-ttu-id="7ae5e-367">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ae5e-367">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7ae5e-368">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-368">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOHPercent` | <span data-ttu-id="7ae5e-369">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-369">*hexadecimal value*</span></span> | <span data-ttu-id="7ae5e-370">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-370">.NET 5.0</span></span> |
| <span data-ttu-id="7ae5e-371">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-371">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOHPercent` | <span data-ttu-id="7ae5e-372">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-372">*hexadecimal value*</span></span> | <span data-ttu-id="7ae5e-373">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-373">.NET 5.0</span></span> |
| <span data-ttu-id="7ae5e-374">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-374">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOHPercent` | <span data-ttu-id="7ae5e-375">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-375">*hexadecimal value*</span></span> | <span data-ttu-id="7ae5e-376">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-376">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="7ae5e-377">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-377">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="7ae5e-378">Örneğin, yığın kullanımını %30 olarak sınırlandırmak için değer 0x1E veya 1E olur.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-378">For example, to limit the heap usage to 30%, the value would be 0x1E or 1E.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="7ae5e-379">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="7ae5e-379">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="7ae5e-380">Silinmesi gereken segmentlerin ileride kullanılmak üzere bir bekleme listesine mi yerleştirileceğini, yoksa işletim sistemine (OS) geri mi bırakılacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-380">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="7ae5e-381">Varsayılan: kesimleri işletim sistemine geri bırakın.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-381">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="7ae5e-382">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="7ae5e-382">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="7ae5e-383">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-383">Setting name</span></span> | <span data-ttu-id="7ae5e-384">Değerler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-384">Values</span></span> | <span data-ttu-id="7ae5e-385">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ae5e-385">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7ae5e-386">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-386">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="7ae5e-387">`false`-işletim sistemine yayın</span><span class="sxs-lookup"><span data-stu-id="7ae5e-387">`false` - release to OS</span></span><br/><span data-ttu-id="7ae5e-388">`true`-bekleme durumuna koy</span><span class="sxs-lookup"><span data-stu-id="7ae5e-388">`true` - put on standby</span></span> | <span data-ttu-id="7ae5e-389">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-389">.NET Core 1.0</span></span> |
| <span data-ttu-id="7ae5e-390">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-390">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="7ae5e-391">`false`-işletim sistemine yayın</span><span class="sxs-lookup"><span data-stu-id="7ae5e-391">`false` - release to OS</span></span><br/><span data-ttu-id="7ae5e-392">`true`-bekleme durumuna koy</span><span class="sxs-lookup"><span data-stu-id="7ae5e-392">`true` - put on standby</span></span> | <span data-ttu-id="7ae5e-393">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-393">.NET Core 1.0</span></span> |
| <span data-ttu-id="7ae5e-394">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-394">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="7ae5e-395">`0`-işletim sistemine yayın</span><span class="sxs-lookup"><span data-stu-id="7ae5e-395">`0` - release to OS</span></span><br/><span data-ttu-id="7ae5e-396">`1`-bekleme durumuna koy</span><span class="sxs-lookup"><span data-stu-id="7ae5e-396">`1` - put on standby</span></span> | <span data-ttu-id="7ae5e-397">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-397">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="7ae5e-398">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-398">Examples</span></span>

<span data-ttu-id="7ae5e-399">*runtimeconfig.js* dosya:</span><span class="sxs-lookup"><span data-stu-id="7ae5e-399">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="7ae5e-400">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="7ae5e-400">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="7ae5e-401">Büyük sayfalar</span><span class="sxs-lookup"><span data-stu-id="7ae5e-401">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="7ae5e-402">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="7ae5e-402">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="7ae5e-403">Bir yığın sabit sınırı ayarlandığında büyük sayfaların kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-403">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="7ae5e-404">Varsayılan: bir yığın sabit sınırı ayarlandığında büyük sayfalar kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-404">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="7ae5e-405">Bu değeri değerine ayarlamaya eşdeğerdir `0` .</span><span class="sxs-lookup"><span data-stu-id="7ae5e-405">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="7ae5e-406">Bu bir deneysel ayardır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-406">This is an experimental setting.</span></span>

| | <span data-ttu-id="7ae5e-407">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-407">Setting name</span></span> | <span data-ttu-id="7ae5e-408">Değerler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-408">Values</span></span> | <span data-ttu-id="7ae5e-409">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ae5e-409">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7ae5e-410">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-410">**runtimeconfig.json**</span></span> | <span data-ttu-id="7ae5e-411">Yok</span><span class="sxs-lookup"><span data-stu-id="7ae5e-411">N/A</span></span> | <span data-ttu-id="7ae5e-412">Yok</span><span class="sxs-lookup"><span data-stu-id="7ae5e-412">N/A</span></span> | <span data-ttu-id="7ae5e-413">Yok</span><span class="sxs-lookup"><span data-stu-id="7ae5e-413">N/A</span></span> |
| <span data-ttu-id="7ae5e-414">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-414">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="7ae5e-415">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-415">`0` - disabled</span></span><br/><span data-ttu-id="7ae5e-416">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="7ae5e-416">`1` - enabled</span></span> | <span data-ttu-id="7ae5e-417">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-417">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="7ae5e-418">Büyük nesneler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-418">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="7ae5e-419">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="7ae5e-419">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="7ae5e-420">Toplam boyuttaki 2 gigabayttan (GB) büyük olan diziler için 64 bitlik platformlarda çöp toplayıcı desteğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-420">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="7ae5e-421">Varsayılan: GC 2 GB 'tan büyük dizileri destekler.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-421">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="7ae5e-422">Bu değeri değerine ayarlamaya eşdeğerdir `1` .</span><span class="sxs-lookup"><span data-stu-id="7ae5e-422">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="7ae5e-423">Bu seçenek, .NET 'in gelecek bir sürümünde kullanımdan kalkabilir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-423">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="7ae5e-424">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-424">Setting name</span></span> | <span data-ttu-id="7ae5e-425">Değerler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-425">Values</span></span> | <span data-ttu-id="7ae5e-426">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ae5e-426">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7ae5e-427">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-427">**runtimeconfig.json**</span></span> | <span data-ttu-id="7ae5e-428">Yok</span><span class="sxs-lookup"><span data-stu-id="7ae5e-428">N/A</span></span> | <span data-ttu-id="7ae5e-429">Yok</span><span class="sxs-lookup"><span data-stu-id="7ae5e-429">N/A</span></span> | <span data-ttu-id="7ae5e-430">Yok</span><span class="sxs-lookup"><span data-stu-id="7ae5e-430">N/A</span></span> |
| <span data-ttu-id="7ae5e-431">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-431">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="7ae5e-432">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="7ae5e-432">`1` - enabled</span></span><br/> <span data-ttu-id="7ae5e-433">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-433">`0` - disabled</span></span> | <span data-ttu-id="7ae5e-434">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-434">.NET Core 1.0</span></span> |
| <span data-ttu-id="7ae5e-435">**.NET Framework içinapp.config**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-435">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="7ae5e-436">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="7ae5e-436">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="7ae5e-437">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="7ae5e-437">`1` - enabled</span></span><br/> <span data-ttu-id="7ae5e-438">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-438">`0` - disabled</span></span> | <span data-ttu-id="7ae5e-439">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="7ae5e-439">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="7ae5e-440">Büyük nesne yığın eşiği</span><span class="sxs-lookup"><span data-stu-id="7ae5e-440">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="7ae5e-441">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="7ae5e-441">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="7ae5e-442">Nesnelerin büyük nesne yığınında (LOH) geçmesine neden olan eşik boyutunu bayt cinsinden belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-442">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="7ae5e-443">Varsayılan eşik 85.000 bayttır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-443">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="7ae5e-444">Belirttiğiniz değer varsayılan eşikten büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-444">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="7ae5e-445">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-445">Setting name</span></span> | <span data-ttu-id="7ae5e-446">Değerler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-446">Values</span></span> | <span data-ttu-id="7ae5e-447">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ae5e-447">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7ae5e-448">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-448">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="7ae5e-449">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-449">*decimal value*</span></span> | <span data-ttu-id="7ae5e-450">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-450">.NET Core 1.0</span></span> |
| <span data-ttu-id="7ae5e-451">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-451">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="7ae5e-452">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-452">*hexadecimal value*</span></span> | <span data-ttu-id="7ae5e-453">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-453">.NET Core 1.0</span></span> |
| <span data-ttu-id="7ae5e-454">**.NET Framework içinapp.config**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-454">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="7ae5e-455">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="7ae5e-455">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="7ae5e-456">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-456">*decimal value*</span></span> | <span data-ttu-id="7ae5e-457"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="7ae5e-457">.NET Framework 4.8</span></span> |

<span data-ttu-id="7ae5e-458">Örnek:</span><span class="sxs-lookup"><span data-stu-id="7ae5e-458">Example:</span></span>

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
> <span data-ttu-id="7ae5e-459">*Üzerinderuntimeconfig.js*seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-459">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="7ae5e-460">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-460">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="7ae5e-461">Örneğin, 120.000 baytlık bir eşik boyutu ayarlamak için, değerler JSON dosyası için 120000, ve ortam değişkeni için 0x1D4C0 ya da 1D4C0 olur.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-461">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="7ae5e-462">Tek başına GC</span><span class="sxs-lookup"><span data-stu-id="7ae5e-462">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="7ae5e-463">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="7ae5e-463">COMPlus_GCName</span></span>

- <span data-ttu-id="7ae5e-464">Çalışma zamanının yüklemeyi amaçladığı çöp toplayıcısını içeren kitaplığın yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ae5e-464">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="7ae5e-465">Daha fazla bilgi için bkz. [tek BAŞıNA GC yükleyici tasarımı](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="7ae5e-465">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="7ae5e-466">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="7ae5e-466">Setting name</span></span> | <span data-ttu-id="7ae5e-467">Değerler</span><span class="sxs-lookup"><span data-stu-id="7ae5e-467">Values</span></span> | <span data-ttu-id="7ae5e-468">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ae5e-468">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="7ae5e-469">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-469">**runtimeconfig.json**</span></span> | <span data-ttu-id="7ae5e-470">Yok</span><span class="sxs-lookup"><span data-stu-id="7ae5e-470">N/A</span></span> | <span data-ttu-id="7ae5e-471">Yok</span><span class="sxs-lookup"><span data-stu-id="7ae5e-471">N/A</span></span> | <span data-ttu-id="7ae5e-472">Yok</span><span class="sxs-lookup"><span data-stu-id="7ae5e-472">N/A</span></span> |
| <span data-ttu-id="7ae5e-473">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="7ae5e-473">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="7ae5e-474">*string_path*</span><span class="sxs-lookup"><span data-stu-id="7ae5e-474">*string_path*</span></span> | <span data-ttu-id="7ae5e-475">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="7ae5e-475">.NET Core 2.0</span></span> |
