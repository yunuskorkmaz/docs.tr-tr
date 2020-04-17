---
title: Çöp toplayıcı config ayarları
description: Çöp toplayıcısının .NET Core uygulamalarının belleği nasıl yönettiğini yapılandırmak için çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: dfb641eeda03d1acaa4771bd6253fcb33c4082a6
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607816"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="0b40d-103">Çöp toplama için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="0b40d-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="0b40d-104">Bu sayfa, çalışma zamanında değiştirilebilen çöp toplayıcı (GC) ayarları hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="0b40d-105">Çalışan bir uygulamanın en yüksek performansını elde etmeye çalışıyorsanız, bu ayarları kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="0b40d-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="0b40d-106">Ancak, varsayılanlar, tipik durumlarda çoğu uygulama için en iyi performansı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b40d-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="0b40d-107">Ayarlar bu sayfada gruplar halinde düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="0b40d-108">Her grup içindeki ayarlar, belirli bir sonuca ulaşmak için genellikle birbiriyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="0b40d-109">Bu ayarlar çalışırken uygulama tarafından dinamik olarak değiştirilebilir, böylece ayarladığınız çalışma zamanı ayarları geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="0b40d-110">[Gecikme düzeyi](../../standard/garbage-collection/latency.md)gibi bazı ayarlar genellikle tasarım zamanında yalnızca API üzerinden ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="0b40d-111">Bu tür ayarlar bu sayfadan atlanır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="0b40d-112">Sayı değerleri için *runtimeconfig.json* dosyasındaki ayarlar için ondalık gösterimi ve ortam değişken ayarları için hexadecimal gösterimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="0b40d-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="0b40d-113">Hexadecimal değerler için, "0x" öneki ile veya olmadan belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b40d-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="0b40d-114">Çöp toplama tatları</span><span class="sxs-lookup"><span data-stu-id="0b40d-114">Flavors of garbage collection</span></span>

<span data-ttu-id="0b40d-115">Çöp toplamanın iki ana tadı iş istasyonu GC ve sunucu GC vardır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="0b40d-116">İkisi arasındaki farklar hakkında daha fazla bilgi [için, çöp toplamanın temelleri](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0b40d-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="0b40d-117">Çöp toplama alt tatlar arka plan ve eşzamanlı değildir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="0b40d-118">Çöp toplama tatlarını seçmek için aşağıdaki ayarları kullanın:</span><span class="sxs-lookup"><span data-stu-id="0b40d-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="0b40d-119">System.GC.Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="0b40d-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="0b40d-120">Uygulamanın iş istasyonu çöp toplamayı mı yoksa sunucu çöp toplamayı mı kullandığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="0b40d-121">Varsayılan: İş istasyonu`false`çöp toplama ( ).</span><span class="sxs-lookup"><span data-stu-id="0b40d-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="0b40d-122">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0b40d-122">Setting name</span></span> | <span data-ttu-id="0b40d-123">Değerler</span><span class="sxs-lookup"><span data-stu-id="0b40d-123">Values</span></span> | <span data-ttu-id="0b40d-124">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0b40d-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="0b40d-125">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0b40d-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="0b40d-126">`false`- iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="0b40d-126">`false` - workstation</span></span><br/><span data-ttu-id="0b40d-127">`true`- sunucu</span><span class="sxs-lookup"><span data-stu-id="0b40d-127">`true` - server</span></span> | <span data-ttu-id="0b40d-128">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="0b40d-129">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="0b40d-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="0b40d-130">`false`- iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="0b40d-130">`false` - workstation</span></span><br/><span data-ttu-id="0b40d-131">`true`- sunucu</span><span class="sxs-lookup"><span data-stu-id="0b40d-131">`true` - server</span></span> | <span data-ttu-id="0b40d-132">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="0b40d-133">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0b40d-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="0b40d-134">`0`- iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="0b40d-134">`0` - workstation</span></span><br/><span data-ttu-id="0b40d-135">`1`- sunucu</span><span class="sxs-lookup"><span data-stu-id="0b40d-135">`1` - server</span></span> | <span data-ttu-id="0b40d-136">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="0b40d-137">**.NET Framework için app.config**</span><span class="sxs-lookup"><span data-stu-id="0b40d-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="0b40d-138">GCServer</span><span class="sxs-lookup"><span data-stu-id="0b40d-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="0b40d-139">`false`- iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="0b40d-139">`false` - workstation</span></span><br/><span data-ttu-id="0b40d-140">`true`- sunucu</span><span class="sxs-lookup"><span data-stu-id="0b40d-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="0b40d-141">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0b40d-141">Examples</span></span>

<span data-ttu-id="0b40d-142">*runtimeconfig.json* dosyası:</span><span class="sxs-lookup"><span data-stu-id="0b40d-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="0b40d-143">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="0b40d-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="0b40d-144">System.GC.Eşzamanlı/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="0b40d-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="0b40d-145">Arka plan (eşzamanlı) çöp toplamanın etkin olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="0b40d-146">Varsayılan: Etkin`true`( ).</span><span class="sxs-lookup"><span data-stu-id="0b40d-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="0b40d-147">Daha fazla bilgi için Bkz. [Arka Plan çöp toplama](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) ve Arka Plan sunucusu çöp [toplama.](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection)</span><span class="sxs-lookup"><span data-stu-id="0b40d-147">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="0b40d-148">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0b40d-148">Setting name</span></span> | <span data-ttu-id="0b40d-149">Değerler</span><span class="sxs-lookup"><span data-stu-id="0b40d-149">Values</span></span> | <span data-ttu-id="0b40d-150">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0b40d-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="0b40d-151">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0b40d-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="0b40d-152">`true`- arka plan GC</span><span class="sxs-lookup"><span data-stu-id="0b40d-152">`true` - background GC</span></span><br/><span data-ttu-id="0b40d-153">`false`- eşzamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="0b40d-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="0b40d-154">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="0b40d-155">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="0b40d-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="0b40d-156">`true`- arka plan GC</span><span class="sxs-lookup"><span data-stu-id="0b40d-156">`true` - background GC</span></span><br/><span data-ttu-id="0b40d-157">`false`- eşzamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="0b40d-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="0b40d-158">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="0b40d-159">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0b40d-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="0b40d-160">`true`- arka plan GC</span><span class="sxs-lookup"><span data-stu-id="0b40d-160">`true` - background GC</span></span><br/><span data-ttu-id="0b40d-161">`false`- eşzamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="0b40d-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="0b40d-162">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="0b40d-163">**.NET Framework için app.config**</span><span class="sxs-lookup"><span data-stu-id="0b40d-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="0b40d-164">gcEşzamanlı akım</span><span class="sxs-lookup"><span data-stu-id="0b40d-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="0b40d-165">`true`- arka plan GC</span><span class="sxs-lookup"><span data-stu-id="0b40d-165">`true` - background GC</span></span><br/><span data-ttu-id="0b40d-166">`false`- eşzamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="0b40d-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="0b40d-167">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0b40d-167">Examples</span></span>

<span data-ttu-id="0b40d-168">*runtimeconfig.json* dosyası:</span><span class="sxs-lookup"><span data-stu-id="0b40d-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="0b40d-169">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="0b40d-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="0b40d-170">Kaynak kullanımını yönetme</span><span class="sxs-lookup"><span data-stu-id="0b40d-170">Manage resource usage</span></span>

<span data-ttu-id="0b40d-171">Çöp toplayıcının bellek ve işlemci kullanımını yönetmek için bu bölümde açıklanan ayarları kullanın.</span><span class="sxs-lookup"><span data-stu-id="0b40d-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="0b40d-172">Bu ayarların bazıları hakkında daha fazla bilgi için [iş istasyonu ve sunucu GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog girişi arasındaki Orta zemine bakın.</span><span class="sxs-lookup"><span data-stu-id="0b40d-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="0b40d-173">System.GC.HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="0b40d-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="0b40d-174">Çöp toplayıcısı tarafından oluşturulan yığın sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="0b40d-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="0b40d-175">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="0b40d-176">[GC işlemci afinitesi](#systemgcnoaffinitizecomplus_gcnoaffinitize) etkinse, ki bu varsayılan değerdir, `n` yığın sayısı ayarı GC `n` yığınları/iş parçacığı ile ilk işlemcilere affeder.</span><span class="sxs-lookup"><span data-stu-id="0b40d-176">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="0b40d-177">[(Affinitize maskesini](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) veya [affinitize aralıkları](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) ayarlarını kullanarak tam olarak hangi işlemcilerin affinitize olacağını belirtin.)</span><span class="sxs-lookup"><span data-stu-id="0b40d-177">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="0b40d-178">[GC işlemci yakınlığı](#systemgcnoaffinitizecomplus_gcnoaffinitize) devre dışı bırakılırsa, bu ayar GC yığınlarının sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="0b40d-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="0b40d-179">Daha fazla bilgi için [GCHeapCount açıklamalarına](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)bakın.</span><span class="sxs-lookup"><span data-stu-id="0b40d-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="0b40d-180">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0b40d-180">Setting name</span></span> | <span data-ttu-id="0b40d-181">Değerler</span><span class="sxs-lookup"><span data-stu-id="0b40d-181">Values</span></span> | <span data-ttu-id="0b40d-182">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0b40d-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="0b40d-183">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0b40d-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="0b40d-184">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="0b40d-184">*decimal value*</span></span> | <span data-ttu-id="0b40d-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="0b40d-186">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0b40d-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="0b40d-187">*hexadecimal değeri*</span><span class="sxs-lookup"><span data-stu-id="0b40d-187">*hexadecimal value*</span></span> | <span data-ttu-id="0b40d-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="0b40d-189">**.NET Framework için app.config**</span><span class="sxs-lookup"><span data-stu-id="0b40d-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="0b40d-190">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="0b40d-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="0b40d-191">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="0b40d-191">*decimal value*</span></span> | <span data-ttu-id="0b40d-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="0b40d-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="0b40d-193">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0b40d-193">Example:</span></span>

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
> <span data-ttu-id="0b40d-194">*Runtimeconfig.json'da*seçeneği ayarlıyorsanız, ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="0b40d-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="0b40d-195">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, hexadecimal değeri belirtin.</span><span class="sxs-lookup"><span data-stu-id="0b40d-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="0b40d-196">Örneğin, yığın sayısını 16 ile sınırlamak için değerler JSON dosyası için 16, ortam değişkeni için 0x10 veya 10 olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="0b40d-197">System.GC.HeapAffinitizeMaske/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="0b40d-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="0b40d-198">Çöp toplayıcı iş parçacıklarının kullanması gereken tam işlemcileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="0b40d-199">[GC işlemci afinitedevre](#systemgcnoaffinitizecomplus_gcnoaffinitize) dışı bırakılırsa, bu ayar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-199">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="0b40d-200">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="0b40d-201">Değer, işlem için kullanılabilir işlemcileri tanımlayan bir bit maskesidir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="0b40d-202">Örneğin, 1023 ondalık değeri (veya ortam değişkenini kullanıyorsanız 0x3FF veya 3FF'nin hexadecimal değeri) ikili gösterimde 0011 1111 1111'dir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="0b40d-203">Bu, ilk 10 işlemcinin kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="0b40d-204">Sonraki 10 işlemciyi belirtmek için, yani 10-19 işlemciler, 1111 1111 1100 0000 0000 ikili değere eşdeğer olan 1047552 (veya 0xFFC00 veya FFC00 hexadecimal değeri) ondalık değerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="0b40d-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="0b40d-205">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0b40d-205">Setting name</span></span> | <span data-ttu-id="0b40d-206">Değerler</span><span class="sxs-lookup"><span data-stu-id="0b40d-206">Values</span></span> | <span data-ttu-id="0b40d-207">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0b40d-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="0b40d-208">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0b40d-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="0b40d-209">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="0b40d-209">*decimal value*</span></span> | <span data-ttu-id="0b40d-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="0b40d-211">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0b40d-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="0b40d-212">*hexadecimal değeri*</span><span class="sxs-lookup"><span data-stu-id="0b40d-212">*hexadecimal value*</span></span> | <span data-ttu-id="0b40d-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="0b40d-214">**.NET Framework için app.config**</span><span class="sxs-lookup"><span data-stu-id="0b40d-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="0b40d-215">GCHeapAffinitizeMaske</span><span class="sxs-lookup"><span data-stu-id="0b40d-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="0b40d-216">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="0b40d-216">*decimal value*</span></span> | <span data-ttu-id="0b40d-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="0b40d-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="0b40d-218">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0b40d-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="0b40d-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="0b40d-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="0b40d-220">Çöp toplayıcı iş parçacıkları için kullanılacak işlemcilistesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="0b40d-221">Bu ayar [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask)benzer , 64'ten fazla işlemcibelirtmenizi sağlar dışında.</span><span class="sxs-lookup"><span data-stu-id="0b40d-221">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="0b40d-222">Windows işletim sistemleri için işlemci numarasını veya aralığını ilgili [CPU grubuyla](/windows/win32/procthread/processor-groups)(örneğin, "0:1-10,0:12,1:50-52,1:70" olarak öneleyin.</span><span class="sxs-lookup"><span data-stu-id="0b40d-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="0b40d-223">[GC işlemci afinitedevre](#systemgcnoaffinitizecomplus_gcnoaffinitize) dışı bırakılırsa, bu ayar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-223">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="0b40d-224">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="0b40d-225">Daha fazla bilgi için, Maoni Stephens'ın blogunda [64 işlemci> > makinelerde GC için CPU yapılandırması daha iyi hale](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) getirilmesine bakın.</span><span class="sxs-lookup"><span data-stu-id="0b40d-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="0b40d-226">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0b40d-226">Setting name</span></span> | <span data-ttu-id="0b40d-227">Değerler</span><span class="sxs-lookup"><span data-stu-id="0b40d-227">Values</span></span> | <span data-ttu-id="0b40d-228">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0b40d-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="0b40d-229">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0b40d-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="0b40d-230">İşlemci numaralarının veya işlemci numaralarının aralıklarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="0b40d-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="0b40d-231">Unix örnek: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="0b40d-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="0b40d-232">Windows örneği: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="0b40d-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="0b40d-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="0b40d-234">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0b40d-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="0b40d-235">İşlemci numaralarının veya işlemci numaralarının aralıklarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="0b40d-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="0b40d-236">Unix örnek: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="0b40d-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="0b40d-237">Windows örneği: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="0b40d-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="0b40d-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-238">.NET Core 3.0</span></span> |

<span data-ttu-id="0b40d-239">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0b40d-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="0b40d-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="0b40d-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="0b40d-241">Çöp toplayıcısının CPU [grupları](/windows/win32/procthread/processor-groups) kullanıp kullanmayacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="0b40d-242">64 bit Windows bilgisayarınbirden çok CPU grubu varsa, diğer bir süre 64'ten fazla işlemci vardır ve bu öğenin çöp toplamayı tüm CPU gruplarına yaymasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b40d-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="0b40d-243">Çöp toplayıcı yığınlar oluşturmak ve dengelemek için tüm çekirdekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="0b40d-244">Yalnızca 64 bit Windows işlem sistemlerinde sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="0b40d-245">Varsayılan: Devre`0`Dışı ( ).</span><span class="sxs-lookup"><span data-stu-id="0b40d-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="0b40d-246">Daha fazla bilgi için, Maoni Stephens'ın blogunda [64 işlemci> > makinelerde GC için CPU yapılandırması daha iyi hale](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) getirilmesine bakın.</span><span class="sxs-lookup"><span data-stu-id="0b40d-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="0b40d-247">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0b40d-247">Setting name</span></span> | <span data-ttu-id="0b40d-248">Değerler</span><span class="sxs-lookup"><span data-stu-id="0b40d-248">Values</span></span> | <span data-ttu-id="0b40d-249">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0b40d-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="0b40d-250">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0b40d-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="0b40d-251">Yok</span><span class="sxs-lookup"><span data-stu-id="0b40d-251">N/A</span></span> | <span data-ttu-id="0b40d-252">Yok</span><span class="sxs-lookup"><span data-stu-id="0b40d-252">N/A</span></span> | <span data-ttu-id="0b40d-253">Yok</span><span class="sxs-lookup"><span data-stu-id="0b40d-253">N/A</span></span> |
| <span data-ttu-id="0b40d-254">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0b40d-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="0b40d-255">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="0b40d-255">`0` - disabled</span></span><br/><span data-ttu-id="0b40d-256">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="0b40d-256">`1` - enabled</span></span> | <span data-ttu-id="0b40d-257">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="0b40d-258">**.NET Framework için app.config**</span><span class="sxs-lookup"><span data-stu-id="0b40d-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="0b40d-259">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="0b40d-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="0b40d-260">`false`- engelli</span><span class="sxs-lookup"><span data-stu-id="0b40d-260">`false` - disabled</span></span><br/><span data-ttu-id="0b40d-261">`true`- etkin</span><span class="sxs-lookup"><span data-stu-id="0b40d-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="0b40d-262">İş parçacığı havuzundan iş parçacığı tüm CPU gruplarına dağıtmak için ortak dil çalışma süresini (CLR) yapılandırmak için [Thread_UseAllCpuGroups öğesi](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) seçeneğini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="0b40d-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="0b40d-263">.NET Core uygulamaları `COMPlus_Thread_UseAllCpuGroups` için, ortam değişkeninin değerini `1`' ye ayarlayarak bu seçeneği etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b40d-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="0b40d-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="0b40d-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="0b40d-265">*Çöp* toplama iş parçacığının işlemcilerle uyumlu hale gelip gelmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="0b40d-266">Bir GC iş parçacığı affinitize etmek için sadece kendi özel CPU üzerinde çalıştırabilirsiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="0b40d-267">Her GC iş parçacığı için bir yığın oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0b40d-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="0b40d-268">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="0b40d-269">Varsayılan: Çöp toplama iş parçacıklarını işlemcilerle`false`affinitize edin ( ).</span><span class="sxs-lookup"><span data-stu-id="0b40d-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="0b40d-270">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0b40d-270">Setting name</span></span> | <span data-ttu-id="0b40d-271">Değerler</span><span class="sxs-lookup"><span data-stu-id="0b40d-271">Values</span></span> | <span data-ttu-id="0b40d-272">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0b40d-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="0b40d-273">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0b40d-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="0b40d-274">`false`- affinitize</span><span class="sxs-lookup"><span data-stu-id="0b40d-274">`false` - affinitize</span></span><br/><span data-ttu-id="0b40d-275">`true`- affinitize etmeyin</span><span class="sxs-lookup"><span data-stu-id="0b40d-275">`true` - don't affinitize</span></span> | <span data-ttu-id="0b40d-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="0b40d-277">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0b40d-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="0b40d-278">`0`- affinitize</span><span class="sxs-lookup"><span data-stu-id="0b40d-278">`0` - affinitize</span></span><br/><span data-ttu-id="0b40d-279">`1`- affinitize etmeyin</span><span class="sxs-lookup"><span data-stu-id="0b40d-279">`1` - don't affinitize</span></span> | <span data-ttu-id="0b40d-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="0b40d-281">**.NET Framework için app.config**</span><span class="sxs-lookup"><span data-stu-id="0b40d-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="0b40d-282">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="0b40d-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="0b40d-283">`false`- affinitize</span><span class="sxs-lookup"><span data-stu-id="0b40d-283">`false` - affinitize</span></span><br/><span data-ttu-id="0b40d-284">`true`- affinitize etmeyin</span><span class="sxs-lookup"><span data-stu-id="0b40d-284">`true` - don't affinitize</span></span> | <span data-ttu-id="0b40d-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="0b40d-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="0b40d-286">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0b40d-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="0b40d-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="0b40d-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="0b40d-288">GC yığını ve GC muhasebesi için baytlarda maksimum taahhüt boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="0b40d-289">Bu ayar yalnızca 64 bit bilgisayarlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-289">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="0b40d-290">Yalnızca belirli durumlarda geçerli olan varsayılan değer, 20 MB'dan daha az veya kapsayıcıdaki bellek sınırının %75'i kadardır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-290">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="0b40d-291">Aşağıdaki ler için varsayılan değer uygulanır:</span><span class="sxs-lookup"><span data-stu-id="0b40d-291">The default value applies if:</span></span>

  - <span data-ttu-id="0b40d-292">İşlem, belirli bir bellek sınırı olan bir kapsayıcı içinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="0b40d-292">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="0b40d-293">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) ayarlanmaz.</span><span class="sxs-lookup"><span data-stu-id="0b40d-293">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="0b40d-294">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0b40d-294">Setting name</span></span> | <span data-ttu-id="0b40d-295">Değerler</span><span class="sxs-lookup"><span data-stu-id="0b40d-295">Values</span></span> | <span data-ttu-id="0b40d-296">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0b40d-296">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="0b40d-297">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0b40d-297">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="0b40d-298">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="0b40d-298">*decimal value*</span></span> | <span data-ttu-id="0b40d-299">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-299">.NET Core 3.0</span></span> |
| <span data-ttu-id="0b40d-300">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0b40d-300">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="0b40d-301">*hexadecimal değeri*</span><span class="sxs-lookup"><span data-stu-id="0b40d-301">*hexadecimal value*</span></span> | <span data-ttu-id="0b40d-302">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-302">.NET Core 3.0</span></span> |

<span data-ttu-id="0b40d-303">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0b40d-303">Example:</span></span>

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
> <span data-ttu-id="0b40d-304">*Runtimeconfig.json'da*seçeneği ayarlıyorsanız, ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="0b40d-304">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="0b40d-305">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, hexadecimal değeri belirtin.</span><span class="sxs-lookup"><span data-stu-id="0b40d-305">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="0b40d-306">Örneğin, 200 mebibayt (MiB) bir yığın sabit sınır belirtmek için, değerleri JSON dosyası için 209715200 ve çevre değişkeni için 0xC800000 veya C800000 olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-306">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="0b40d-307">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="0b40d-307">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="0b40d-308">İzin verilebilen GC yığın kullanımını toplam fiziksel belleğin yüzdesi olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-308">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="0b40d-309">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) de ayarlanmışsa, bu ayar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-309">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="0b40d-310">Bu ayar yalnızca 64 bit bilgisayarlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-310">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="0b40d-311">İşlem, belirli bir bellek sınırı olan bir kapsayıcıiçinde çalışıyorsa, yüzde bu bellek sınırının yüzdesi olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-311">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="0b40d-312">Yalnızca belirli durumlarda geçerli olan varsayılan değer, 20 MB'dan daha az veya kapsayıcıdaki bellek sınırının %75'i kadardır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-312">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="0b40d-313">Aşağıdaki ler için varsayılan değer uygulanır:</span><span class="sxs-lookup"><span data-stu-id="0b40d-313">The default value applies if:</span></span>

  - <span data-ttu-id="0b40d-314">İşlem, belirli bir bellek sınırı olan bir kapsayıcı içinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="0b40d-314">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="0b40d-315">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) ayarlanmaz.</span><span class="sxs-lookup"><span data-stu-id="0b40d-315">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="0b40d-316">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0b40d-316">Setting name</span></span> | <span data-ttu-id="0b40d-317">Değerler</span><span class="sxs-lookup"><span data-stu-id="0b40d-317">Values</span></span> | <span data-ttu-id="0b40d-318">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0b40d-318">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="0b40d-319">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0b40d-319">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="0b40d-320">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="0b40d-320">*decimal value*</span></span> | <span data-ttu-id="0b40d-321">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-321">.NET Core 3.0</span></span> |
| <span data-ttu-id="0b40d-322">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0b40d-322">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="0b40d-323">*hexadecimal değeri*</span><span class="sxs-lookup"><span data-stu-id="0b40d-323">*hexadecimal value*</span></span> | <span data-ttu-id="0b40d-324">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-324">.NET Core 3.0</span></span> |

<span data-ttu-id="0b40d-325">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0b40d-325">Example:</span></span>

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
> <span data-ttu-id="0b40d-326">*Runtimeconfig.json'da*seçeneği ayarlıyorsanız, ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="0b40d-326">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="0b40d-327">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, hexadecimal değeri belirtin.</span><span class="sxs-lookup"><span data-stu-id="0b40d-327">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="0b40d-328">Örneğin, yığın kullanımını %30 ile sınırlamak için, değerler JSON dosyası için 30, ortam değişkeni için 0x1E veya 1E olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-328">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="0b40d-329">System.GC.RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="0b40d-329">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="0b40d-330">Silinmesi gereken segmentlerin ileride kullanılmak üzere bekleme listesine alınıp alınmayacağını veya işletim sistemine (OS) geri salınıp salınmayacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-330">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="0b40d-331">Varsayılan: Segmentleri işletim sistemine geri`false`bırakın ( ).</span><span class="sxs-lookup"><span data-stu-id="0b40d-331">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="0b40d-332">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0b40d-332">Setting name</span></span> | <span data-ttu-id="0b40d-333">Değerler</span><span class="sxs-lookup"><span data-stu-id="0b40d-333">Values</span></span> | <span data-ttu-id="0b40d-334">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0b40d-334">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="0b40d-335">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0b40d-335">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="0b40d-336">`false`- işletim sistemi için sürüm</span><span class="sxs-lookup"><span data-stu-id="0b40d-336">`false` - release to OS</span></span><br/><span data-ttu-id="0b40d-337">`true`- beklemeye</span><span class="sxs-lookup"><span data-stu-id="0b40d-337">`true` - put on standby</span></span> | <span data-ttu-id="0b40d-338">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-338">.NET Core 1.0</span></span> |
| <span data-ttu-id="0b40d-339">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="0b40d-339">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="0b40d-340">`false`- işletim sistemi için sürüm</span><span class="sxs-lookup"><span data-stu-id="0b40d-340">`false` - release to OS</span></span><br/><span data-ttu-id="0b40d-341">`true`- beklemeye</span><span class="sxs-lookup"><span data-stu-id="0b40d-341">`true` - put on standby</span></span> | <span data-ttu-id="0b40d-342">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-342">.NET Core 1.0</span></span> |
| <span data-ttu-id="0b40d-343">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0b40d-343">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="0b40d-344">`0`- işletim sistemi için sürüm</span><span class="sxs-lookup"><span data-stu-id="0b40d-344">`0` - release to OS</span></span><br/><span data-ttu-id="0b40d-345">`1`- beklemeye</span><span class="sxs-lookup"><span data-stu-id="0b40d-345">`1` - put on standby</span></span> | <span data-ttu-id="0b40d-346">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-346">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="0b40d-347">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0b40d-347">Examples</span></span>

<span data-ttu-id="0b40d-348">*runtimeconfig.json* dosyası:</span><span class="sxs-lookup"><span data-stu-id="0b40d-348">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="0b40d-349">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="0b40d-349">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="0b40d-350">Büyük sayfalar</span><span class="sxs-lookup"><span data-stu-id="0b40d-350">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="0b40d-351">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="0b40d-351">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="0b40d-352">Yığın sabit sınır ayarlandığında büyük sayfaların kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-352">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="0b40d-353">Varsayılan: Devre`0`Dışı ( ).</span><span class="sxs-lookup"><span data-stu-id="0b40d-353">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="0b40d-354">Bu deneysel bir ayar.</span><span class="sxs-lookup"><span data-stu-id="0b40d-354">This is an experimental setting.</span></span>

| | <span data-ttu-id="0b40d-355">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0b40d-355">Setting name</span></span> | <span data-ttu-id="0b40d-356">Değerler</span><span class="sxs-lookup"><span data-stu-id="0b40d-356">Values</span></span> | <span data-ttu-id="0b40d-357">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0b40d-357">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="0b40d-358">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0b40d-358">**runtimeconfig.json**</span></span> | <span data-ttu-id="0b40d-359">Yok</span><span class="sxs-lookup"><span data-stu-id="0b40d-359">N/A</span></span> | <span data-ttu-id="0b40d-360">Yok</span><span class="sxs-lookup"><span data-stu-id="0b40d-360">N/A</span></span> | <span data-ttu-id="0b40d-361">Yok</span><span class="sxs-lookup"><span data-stu-id="0b40d-361">N/A</span></span> |
| <span data-ttu-id="0b40d-362">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0b40d-362">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="0b40d-363">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="0b40d-363">`0` - disabled</span></span><br/><span data-ttu-id="0b40d-364">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="0b40d-364">`1` - enabled</span></span> | <span data-ttu-id="0b40d-365">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-365">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="0b40d-366">Büyük nesneler</span><span class="sxs-lookup"><span data-stu-id="0b40d-366">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="0b40d-367">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="0b40d-367">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="0b40d-368">Toplam boyutu 2 gigabayttan (GB) büyük diziler için 64 bit platformlarda çöp toplayıcı desteğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-368">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="0b40d-369">Varsayılan: Etkin`1`( ).</span><span class="sxs-lookup"><span data-stu-id="0b40d-369">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="0b40d-370">Bu seçenek ,NET'in gelecekteki sürümünde geçersiz hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-370">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="0b40d-371">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0b40d-371">Setting name</span></span> | <span data-ttu-id="0b40d-372">Değerler</span><span class="sxs-lookup"><span data-stu-id="0b40d-372">Values</span></span> | <span data-ttu-id="0b40d-373">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0b40d-373">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="0b40d-374">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0b40d-374">**runtimeconfig.json**</span></span> | <span data-ttu-id="0b40d-375">Yok</span><span class="sxs-lookup"><span data-stu-id="0b40d-375">N/A</span></span> | <span data-ttu-id="0b40d-376">Yok</span><span class="sxs-lookup"><span data-stu-id="0b40d-376">N/A</span></span> | <span data-ttu-id="0b40d-377">Yok</span><span class="sxs-lookup"><span data-stu-id="0b40d-377">N/A</span></span> |
| <span data-ttu-id="0b40d-378">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0b40d-378">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="0b40d-379">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="0b40d-379">`1` - enabled</span></span><br/> <span data-ttu-id="0b40d-380">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="0b40d-380">`0` - disabled</span></span> | <span data-ttu-id="0b40d-381">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-381">.NET Core 1.0</span></span> |
| <span data-ttu-id="0b40d-382">**.NET Framework için app.config**</span><span class="sxs-lookup"><span data-stu-id="0b40d-382">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="0b40d-383">gcAllowVeryLargeNesneler</span><span class="sxs-lookup"><span data-stu-id="0b40d-383">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="0b40d-384">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="0b40d-384">`1` - enabled</span></span><br/> <span data-ttu-id="0b40d-385">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="0b40d-385">`0` - disabled</span></span> | <span data-ttu-id="0b40d-386">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="0b40d-386">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="0b40d-387">Büyük nesne yığını eşiği</span><span class="sxs-lookup"><span data-stu-id="0b40d-387">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="0b40d-388">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="0b40d-388">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="0b40d-389">Nesnelerin büyük nesne yığınına (LOH) gitmesine neden olan eşik boyutunu baytlar olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-389">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="0b40d-390">Varsayılan eşik 85.000 bayttır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-390">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="0b40d-391">Belirttiğiniz değer varsayılan eşiğe göre daha büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-391">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="0b40d-392">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0b40d-392">Setting name</span></span> | <span data-ttu-id="0b40d-393">Değerler</span><span class="sxs-lookup"><span data-stu-id="0b40d-393">Values</span></span> | <span data-ttu-id="0b40d-394">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0b40d-394">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="0b40d-395">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0b40d-395">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="0b40d-396">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="0b40d-396">*decimal value*</span></span> | <span data-ttu-id="0b40d-397">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-397">.NET Core 1.0</span></span> |
| <span data-ttu-id="0b40d-398">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0b40d-398">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="0b40d-399">*hexadecimal değeri*</span><span class="sxs-lookup"><span data-stu-id="0b40d-399">*hexadecimal value*</span></span> | <span data-ttu-id="0b40d-400">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-400">.NET Core 1.0</span></span> |
| <span data-ttu-id="0b40d-401">**.NET Framework için app.config**</span><span class="sxs-lookup"><span data-stu-id="0b40d-401">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="0b40d-402">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="0b40d-402">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="0b40d-403">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="0b40d-403">*decimal value*</span></span> | <span data-ttu-id="0b40d-404"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="0b40d-404">.NET Framework 4.8</span></span> |

<span data-ttu-id="0b40d-405">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0b40d-405">Example:</span></span>

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
> <span data-ttu-id="0b40d-406">*Runtimeconfig.json'da*seçeneği ayarlıyorsanız, ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="0b40d-406">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="0b40d-407">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, hexadecimal değeri belirtin.</span><span class="sxs-lookup"><span data-stu-id="0b40d-407">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="0b40d-408">Örneğin, 120.000 bayt lık bir eşik boyutu ayarlamak için değerler JSON dosyası için 120000 ve ortam değişkeni için 0x1D4C0 veya 1D4C0 olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0b40d-408">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="0b40d-409">Bağımsız GC</span><span class="sxs-lookup"><span data-stu-id="0b40d-409">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="0b40d-410">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="0b40d-410">COMPlus_GCName</span></span>

- <span data-ttu-id="0b40d-411">Çalışma zamanının yüklemeyi planladığı çöp toplayıcısını içeren kitaplık için bir yol belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b40d-411">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="0b40d-412">Daha fazla bilgi için, [Bkz. Bağımsız GC yükleyici tasarımı.](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md)</span><span class="sxs-lookup"><span data-stu-id="0b40d-412">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="0b40d-413">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0b40d-413">Setting name</span></span> | <span data-ttu-id="0b40d-414">Değerler</span><span class="sxs-lookup"><span data-stu-id="0b40d-414">Values</span></span> | <span data-ttu-id="0b40d-415">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0b40d-415">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="0b40d-416">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0b40d-416">**runtimeconfig.json**</span></span> | <span data-ttu-id="0b40d-417">Yok</span><span class="sxs-lookup"><span data-stu-id="0b40d-417">N/A</span></span> | <span data-ttu-id="0b40d-418">Yok</span><span class="sxs-lookup"><span data-stu-id="0b40d-418">N/A</span></span> | <span data-ttu-id="0b40d-419">Yok</span><span class="sxs-lookup"><span data-stu-id="0b40d-419">N/A</span></span> |
| <span data-ttu-id="0b40d-420">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0b40d-420">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="0b40d-421">*string_path*</span><span class="sxs-lookup"><span data-stu-id="0b40d-421">*string_path*</span></span> | <span data-ttu-id="0b40d-422">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="0b40d-422">.NET Core 2.0</span></span> |
