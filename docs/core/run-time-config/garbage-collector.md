---
title: Çöp toplayıcı config ayarları
description: Çöp toplayıcısının .NET Core uygulamalarının belleği nasıl yönettiğini yapılandırmak için çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 044083d69601f5092724a46d358b2ee5673d428d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733522"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="8957c-103">Çöp toplama için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="8957c-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="8957c-104">Bu sayfa, çalışma zamanında değiştirilebilen çöp toplayıcı (GC) ayarları hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="8957c-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="8957c-105">Çalışan bir uygulamanın en yüksek performansını elde etmeye çalışıyorsanız, bu ayarları kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="8957c-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="8957c-106">Ancak, varsayılanlar, tipik durumlarda çoğu uygulama için en iyi performansı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8957c-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="8957c-107">Ayarlar bu sayfada gruplar halinde düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="8957c-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="8957c-108">Her grup içindeki ayarlar, belirli bir sonuca ulaşmak için genellikle birbiriyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8957c-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="8957c-109">Bu ayarlar çalışırken uygulama tarafından dinamik olarak değiştirilebilir, böylece ayarladığınız çalışma zamanı ayarları geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="8957c-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="8957c-110">[Gecikme düzeyi](../../standard/garbage-collection/latency.md)gibi bazı ayarlar genellikle tasarım zamanında yalnızca API üzerinden ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="8957c-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="8957c-111">Bu tür ayarlar bu sayfadan atlanır.</span><span class="sxs-lookup"><span data-stu-id="8957c-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="8957c-112">Sayı değerleri için *runtimeconfig.json* dosyasındaki ayarlar için ondalık gösterimi ve ortam değişken ayarları için hexadecimal gösterimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="8957c-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="8957c-113">Hexadecimal değerler için, "0x" öneki ile veya olmadan belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8957c-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="8957c-114">Çöp toplama tatları</span><span class="sxs-lookup"><span data-stu-id="8957c-114">Flavors of garbage collection</span></span>

<span data-ttu-id="8957c-115">Çöp toplamanın iki ana tadı iş istasyonu GC ve sunucu GC vardır.</span><span class="sxs-lookup"><span data-stu-id="8957c-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="8957c-116">İkisi arasındaki farklar hakkında daha fazla bilgi [için, çöp toplamanın temelleri](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8957c-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="8957c-117">Çöp toplama alt tatlar arka plan ve eşzamanlı değildir.</span><span class="sxs-lookup"><span data-stu-id="8957c-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="8957c-118">Çöp toplama tatlarını seçmek için aşağıdaki ayarları kullanın:</span><span class="sxs-lookup"><span data-stu-id="8957c-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="8957c-119">System.GC.Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="8957c-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="8957c-120">Uygulamanın iş istasyonu çöp toplamayı mı yoksa sunucu çöp toplamayı mı kullandığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8957c-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="8957c-121">Varsayılan: İş istasyonu`false`çöp toplama ( ).</span><span class="sxs-lookup"><span data-stu-id="8957c-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="8957c-122">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="8957c-122">Setting name</span></span> | <span data-ttu-id="8957c-123">Değerler</span><span class="sxs-lookup"><span data-stu-id="8957c-123">Values</span></span> | <span data-ttu-id="8957c-124">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="8957c-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8957c-125">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="8957c-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="8957c-126">`false`- iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="8957c-126">`false` - workstation</span></span><br/><span data-ttu-id="8957c-127">`true`- sunucu</span><span class="sxs-lookup"><span data-stu-id="8957c-127">`true` - server</span></span> | <span data-ttu-id="8957c-128">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="8957c-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="8957c-129">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="8957c-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="8957c-130">`false`- iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="8957c-130">`false` - workstation</span></span><br/><span data-ttu-id="8957c-131">`true`- sunucu</span><span class="sxs-lookup"><span data-stu-id="8957c-131">`true` - server</span></span> | <span data-ttu-id="8957c-132">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="8957c-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="8957c-133">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="8957c-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="8957c-134">`0`- iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="8957c-134">`0` - workstation</span></span><br/><span data-ttu-id="8957c-135">`1`- sunucu</span><span class="sxs-lookup"><span data-stu-id="8957c-135">`1` - server</span></span> | <span data-ttu-id="8957c-136">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="8957c-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="8957c-137">**.NET Framework için app.config**</span><span class="sxs-lookup"><span data-stu-id="8957c-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8957c-138">GCServer</span><span class="sxs-lookup"><span data-stu-id="8957c-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="8957c-139">`false`- iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="8957c-139">`false` - workstation</span></span><br/><span data-ttu-id="8957c-140">`true`- sunucu</span><span class="sxs-lookup"><span data-stu-id="8957c-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="8957c-141">Örnekler</span><span class="sxs-lookup"><span data-stu-id="8957c-141">Examples</span></span>

<span data-ttu-id="8957c-142">*runtimeconfig.json* dosyası:</span><span class="sxs-lookup"><span data-stu-id="8957c-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="8957c-143">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="8957c-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="8957c-144">System.GC.Eşzamanlı/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="8957c-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="8957c-145">Arka plan (eşzamanlı) çöp toplamanın etkin olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8957c-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="8957c-146">Varsayılan: Etkin`true`( ).</span><span class="sxs-lookup"><span data-stu-id="8957c-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="8957c-147">Daha fazla bilgi için Bkz. [Arka Plan çöp toplama](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) ve Arka Plan sunucusu çöp [toplama.](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection)</span><span class="sxs-lookup"><span data-stu-id="8957c-147">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="8957c-148">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="8957c-148">Setting name</span></span> | <span data-ttu-id="8957c-149">Değerler</span><span class="sxs-lookup"><span data-stu-id="8957c-149">Values</span></span> | <span data-ttu-id="8957c-150">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="8957c-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8957c-151">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="8957c-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="8957c-152">`true`- arka plan GC</span><span class="sxs-lookup"><span data-stu-id="8957c-152">`true` - background GC</span></span><br/><span data-ttu-id="8957c-153">`false`- eşzamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="8957c-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="8957c-154">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="8957c-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="8957c-155">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="8957c-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="8957c-156">`true`- arka plan GC</span><span class="sxs-lookup"><span data-stu-id="8957c-156">`true` - background GC</span></span><br/><span data-ttu-id="8957c-157">`false`- eşzamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="8957c-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="8957c-158">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="8957c-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="8957c-159">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="8957c-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="8957c-160">`true`- arka plan GC</span><span class="sxs-lookup"><span data-stu-id="8957c-160">`true` - background GC</span></span><br/><span data-ttu-id="8957c-161">`false`- eşzamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="8957c-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="8957c-162">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="8957c-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="8957c-163">**.NET Framework için app.config**</span><span class="sxs-lookup"><span data-stu-id="8957c-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8957c-164">gcEşzamanlı akım</span><span class="sxs-lookup"><span data-stu-id="8957c-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="8957c-165">`true`- arka plan GC</span><span class="sxs-lookup"><span data-stu-id="8957c-165">`true` - background GC</span></span><br/><span data-ttu-id="8957c-166">`false`- eşzamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="8957c-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="8957c-167">Örnekler</span><span class="sxs-lookup"><span data-stu-id="8957c-167">Examples</span></span>

<span data-ttu-id="8957c-168">*runtimeconfig.json* dosyası:</span><span class="sxs-lookup"><span data-stu-id="8957c-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="8957c-169">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="8957c-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="8957c-170">Kaynak kullanımını yönetme</span><span class="sxs-lookup"><span data-stu-id="8957c-170">Manage resource usage</span></span>

<span data-ttu-id="8957c-171">Çöp toplayıcının bellek ve işlemci kullanımını yönetmek için bu bölümde açıklanan ayarları kullanın.</span><span class="sxs-lookup"><span data-stu-id="8957c-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="8957c-172">Bu ayarların bazıları hakkında daha fazla bilgi için [iş istasyonu ve sunucu GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog girişi arasındaki Orta zemine bakın.</span><span class="sxs-lookup"><span data-stu-id="8957c-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="8957c-173">System.GC.HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="8957c-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="8957c-174">Çöp toplayıcısı tarafından oluşturulan yığın sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="8957c-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="8957c-175">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8957c-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="8957c-176">GC işlemci afinitesi etkinse, ki bu varsayılan değerdir, `n` yığın sayısı ayarı GC `n` yığınları/iş parçacığı ile ilk işlemcilere affeder.</span><span class="sxs-lookup"><span data-stu-id="8957c-176">If GC processor affinity is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="8957c-177">(Affinitize maskesini veya affinitize aralıkları ayarlarını kullanarak tam olarak hangi işlemcilerin affinitize olacağını belirtin.)</span><span class="sxs-lookup"><span data-stu-id="8957c-177">(Use the affinitize mask or affinitize ranges settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="8957c-178">GC işlemci yakınlığı devre dışı bırakılırsa, bu ayar GC yığınlarının sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="8957c-178">If GC processor affinity is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="8957c-179">Daha fazla bilgi için [GCHeapCount açıklamalarına](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)bakın.</span><span class="sxs-lookup"><span data-stu-id="8957c-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="8957c-180">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="8957c-180">Setting name</span></span> | <span data-ttu-id="8957c-181">Değerler</span><span class="sxs-lookup"><span data-stu-id="8957c-181">Values</span></span> | <span data-ttu-id="8957c-182">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="8957c-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8957c-183">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="8957c-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="8957c-184">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="8957c-184">*decimal value*</span></span> | <span data-ttu-id="8957c-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8957c-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="8957c-186">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="8957c-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="8957c-187">*hexadecimal değeri*</span><span class="sxs-lookup"><span data-stu-id="8957c-187">*hexadecimal value*</span></span> | <span data-ttu-id="8957c-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8957c-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="8957c-189">**.NET Framework için app.config**</span><span class="sxs-lookup"><span data-stu-id="8957c-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8957c-190">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="8957c-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="8957c-191">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="8957c-191">*decimal value*</span></span> | <span data-ttu-id="8957c-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="8957c-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="8957c-193">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8957c-193">Example:</span></span>

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
> <span data-ttu-id="8957c-194">*Runtimeconfig.json'da*seçeneği ayarlıyorsanız, ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="8957c-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="8957c-195">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, hexadecimal değeri belirtin.</span><span class="sxs-lookup"><span data-stu-id="8957c-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="8957c-196">Örneğin, yığın sayısını 16 ile sınırlamak için değerler JSON dosyası için 16, ortam değişkeni için 0x10 veya 10 olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8957c-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="8957c-197">System.GC.HeapAffinitizeMaske/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="8957c-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="8957c-198">Çöp toplayıcı iş parçacıklarının kullanması gereken tam işlemcileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8957c-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="8957c-199">İşlemci ayarı `System.GC.NoAffinitize` tarafından devre `true`dışı bırakılırsa, bu ayar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="8957c-199">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="8957c-200">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8957c-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="8957c-201">Değer, işlem için kullanılabilir işlemcileri tanımlayan bir bit maskesidir.</span><span class="sxs-lookup"><span data-stu-id="8957c-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="8957c-202">Örneğin, 1023 ondalık değeri (veya ortam değişkenini kullanıyorsanız 0x3FF veya 3FF'nin hexadecimal değeri) ikili gösterimde 0011 1111 1111'dir.</span><span class="sxs-lookup"><span data-stu-id="8957c-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="8957c-203">Bu, ilk 10 işlemcinin kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8957c-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="8957c-204">Sonraki 10 işlemciyi belirtmek için, yani 10-19 işlemciler, 1111 1111 1100 0000 0000 ikili değere eşdeğer olan 1047552 (veya 0xFFC00 veya FFC00 hexadecimal değeri) ondalık değerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="8957c-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="8957c-205">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="8957c-205">Setting name</span></span> | <span data-ttu-id="8957c-206">Değerler</span><span class="sxs-lookup"><span data-stu-id="8957c-206">Values</span></span> | <span data-ttu-id="8957c-207">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="8957c-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8957c-208">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="8957c-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="8957c-209">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="8957c-209">*decimal value*</span></span> | <span data-ttu-id="8957c-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8957c-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="8957c-211">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="8957c-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="8957c-212">*hexadecimal değeri*</span><span class="sxs-lookup"><span data-stu-id="8957c-212">*hexadecimal value*</span></span> | <span data-ttu-id="8957c-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8957c-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="8957c-214">**.NET Framework için app.config**</span><span class="sxs-lookup"><span data-stu-id="8957c-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8957c-215">GCHeapAffinitizeMaske</span><span class="sxs-lookup"><span data-stu-id="8957c-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="8957c-216">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="8957c-216">*decimal value*</span></span> | <span data-ttu-id="8957c-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="8957c-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="8957c-218">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8957c-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="8957c-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="8957c-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="8957c-220">Çöp toplayıcı iş parçacıkları için kullanılacak işlemcilistesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8957c-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="8957c-221">Bu `System.GC.HeapAffinitizeMask`ayar, 64'ten fazla işlemci belirtmenize izin vermese de benzerdir.</span><span class="sxs-lookup"><span data-stu-id="8957c-221">This setting is similar to `System.GC.HeapAffinitizeMask`, except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="8957c-222">Windows işletim sistemleri için işlemci numarasını veya aralığını ilgili [CPU grubuyla](/windows/win32/procthread/processor-groups)(örneğin, "0:1-10,0:12,1:50-52,1:70" olarak öneleyin.</span><span class="sxs-lookup"><span data-stu-id="8957c-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="8957c-223">İşlemci ayarı `System.GC.NoAffinitize` tarafından devre `true`dışı bırakılırsa, bu ayar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="8957c-223">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="8957c-224">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8957c-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="8957c-225">Daha fazla bilgi için, Maoni Stephens'ın blogunda [64 işlemci> > makinelerde GC için CPU yapılandırması daha iyi hale](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) getirilmesine bakın.</span><span class="sxs-lookup"><span data-stu-id="8957c-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="8957c-226">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="8957c-226">Setting name</span></span> | <span data-ttu-id="8957c-227">Değerler</span><span class="sxs-lookup"><span data-stu-id="8957c-227">Values</span></span> | <span data-ttu-id="8957c-228">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="8957c-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8957c-229">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="8957c-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="8957c-230">İşlemci numaralarının veya işlemci numaralarının aralıklarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="8957c-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="8957c-231">Unix örnek: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="8957c-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="8957c-232">Windows örneği: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="8957c-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="8957c-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8957c-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="8957c-234">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="8957c-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="8957c-235">İşlemci numaralarının veya işlemci numaralarının aralıklarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="8957c-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="8957c-236">Unix örnek: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="8957c-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="8957c-237">Windows örneği: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="8957c-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="8957c-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8957c-238">.NET Core 3.0</span></span> |

<span data-ttu-id="8957c-239">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8957c-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="8957c-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="8957c-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="8957c-241">Çöp toplayıcısının CPU [grupları](/windows/win32/procthread/processor-groups) kullanıp kullanmayacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8957c-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="8957c-242">64 bit Windows bilgisayarınbirden çok CPU grubu varsa, diğer bir süre 64'ten fazla işlemci vardır ve bu öğenin çöp toplamayı tüm CPU gruplarına yaymasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8957c-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="8957c-243">Çöp toplayıcı yığınlar oluşturmak ve dengelemek için tüm çekirdekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="8957c-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="8957c-244">Yalnızca 64 bit Windows işlem sistemlerinde sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8957c-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="8957c-245">Varsayılan: Devre`0`Dışı ( ).</span><span class="sxs-lookup"><span data-stu-id="8957c-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="8957c-246">Daha fazla bilgi için, Maoni Stephens'ın blogunda [64 işlemci> > makinelerde GC için CPU yapılandırması daha iyi hale](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) getirilmesine bakın.</span><span class="sxs-lookup"><span data-stu-id="8957c-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="8957c-247">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="8957c-247">Setting name</span></span> | <span data-ttu-id="8957c-248">Değerler</span><span class="sxs-lookup"><span data-stu-id="8957c-248">Values</span></span> | <span data-ttu-id="8957c-249">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="8957c-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8957c-250">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="8957c-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="8957c-251">Yok</span><span class="sxs-lookup"><span data-stu-id="8957c-251">N/A</span></span> | <span data-ttu-id="8957c-252">Yok</span><span class="sxs-lookup"><span data-stu-id="8957c-252">N/A</span></span> | <span data-ttu-id="8957c-253">Yok</span><span class="sxs-lookup"><span data-stu-id="8957c-253">N/A</span></span> |
| <span data-ttu-id="8957c-254">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="8957c-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="8957c-255">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="8957c-255">`0` - disabled</span></span><br/><span data-ttu-id="8957c-256">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="8957c-256">`1` - enabled</span></span> | <span data-ttu-id="8957c-257">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="8957c-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="8957c-258">**.NET Framework için app.config**</span><span class="sxs-lookup"><span data-stu-id="8957c-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8957c-259">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="8957c-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="8957c-260">`false`- engelli</span><span class="sxs-lookup"><span data-stu-id="8957c-260">`false` - disabled</span></span><br/><span data-ttu-id="8957c-261">`true`- etkin</span><span class="sxs-lookup"><span data-stu-id="8957c-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="8957c-262">İş parçacığı havuzundan iş parçacığı tüm CPU gruplarına dağıtmak için ortak dil çalışma süresini (CLR) yapılandırmak için [Thread_UseAllCpuGroups öğesi](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) seçeneğini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="8957c-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="8957c-263">.NET Core uygulamaları `COMPlus_Thread_UseAllCpuGroups` için, ortam değişkeninin değerini `1`' ye ayarlayarak bu seçeneği etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8957c-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="8957c-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="8957c-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="8957c-265">*Çöp* toplama iş parçacığının işlemcilerle uyumlu hale gelip gelmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8957c-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="8957c-266">Bir GC iş parçacığı affinitize etmek için sadece kendi özel CPU üzerinde çalıştırabilirsiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8957c-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="8957c-267">Her GC iş parçacığı için bir yığın oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8957c-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="8957c-268">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8957c-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="8957c-269">Varsayılan: Çöp toplama iş parçacıklarını işlemcilerle`false`affinitize edin ( ).</span><span class="sxs-lookup"><span data-stu-id="8957c-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="8957c-270">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="8957c-270">Setting name</span></span> | <span data-ttu-id="8957c-271">Değerler</span><span class="sxs-lookup"><span data-stu-id="8957c-271">Values</span></span> | <span data-ttu-id="8957c-272">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="8957c-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8957c-273">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="8957c-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="8957c-274">`false`- affinitize</span><span class="sxs-lookup"><span data-stu-id="8957c-274">`false` - affinitize</span></span><br/><span data-ttu-id="8957c-275">`true`- affinitize etmeyin</span><span class="sxs-lookup"><span data-stu-id="8957c-275">`true` - don't affinitize</span></span> | <span data-ttu-id="8957c-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8957c-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="8957c-277">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="8957c-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="8957c-278">`0`- affinitize</span><span class="sxs-lookup"><span data-stu-id="8957c-278">`0` - affinitize</span></span><br/><span data-ttu-id="8957c-279">`1`- affinitize etmeyin</span><span class="sxs-lookup"><span data-stu-id="8957c-279">`1` - don't affinitize</span></span> | <span data-ttu-id="8957c-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8957c-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="8957c-281">**.NET Framework için app.config**</span><span class="sxs-lookup"><span data-stu-id="8957c-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8957c-282">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="8957c-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="8957c-283">`false`- affinitize</span><span class="sxs-lookup"><span data-stu-id="8957c-283">`false` - affinitize</span></span><br/><span data-ttu-id="8957c-284">`true`- affinitize etmeyin</span><span class="sxs-lookup"><span data-stu-id="8957c-284">`true` - don't affinitize</span></span> | <span data-ttu-id="8957c-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="8957c-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="8957c-286">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8957c-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="8957c-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="8957c-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="8957c-288">GC yığını ve GC muhasebesi için baytlarda maksimum taahhüt boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8957c-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>

| | <span data-ttu-id="8957c-289">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="8957c-289">Setting name</span></span> | <span data-ttu-id="8957c-290">Değerler</span><span class="sxs-lookup"><span data-stu-id="8957c-290">Values</span></span> | <span data-ttu-id="8957c-291">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="8957c-291">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8957c-292">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="8957c-292">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="8957c-293">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="8957c-293">*decimal value*</span></span> | <span data-ttu-id="8957c-294">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8957c-294">.NET Core 3.0</span></span> |
| <span data-ttu-id="8957c-295">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="8957c-295">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="8957c-296">*hexadecimal değeri*</span><span class="sxs-lookup"><span data-stu-id="8957c-296">*hexadecimal value*</span></span> | <span data-ttu-id="8957c-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8957c-297">.NET Core 3.0</span></span> |

<span data-ttu-id="8957c-298">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8957c-298">Example:</span></span>

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
> <span data-ttu-id="8957c-299">*Runtimeconfig.json'da*seçeneği ayarlıyorsanız, ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="8957c-299">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="8957c-300">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, hexadecimal değeri belirtin.</span><span class="sxs-lookup"><span data-stu-id="8957c-300">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="8957c-301">Örneğin, 200 mebibayt (MiB) bir yığın sabit sınır belirtmek için, değerleri JSON dosyası için 209715200 ve çevre değişkeni için 0xC800000 veya C800000 olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8957c-301">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="8957c-302">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="8957c-302">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="8957c-303">GC yığın kullanımını toplam belleğin yüzdesi olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="8957c-303">Specifies the GC heap usage as a percentage of the total memory.</span></span>

| | <span data-ttu-id="8957c-304">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="8957c-304">Setting name</span></span> | <span data-ttu-id="8957c-305">Değerler</span><span class="sxs-lookup"><span data-stu-id="8957c-305">Values</span></span> | <span data-ttu-id="8957c-306">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="8957c-306">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8957c-307">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="8957c-307">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="8957c-308">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="8957c-308">*decimal value*</span></span> | <span data-ttu-id="8957c-309">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8957c-309">.NET Core 3.0</span></span> |
| <span data-ttu-id="8957c-310">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="8957c-310">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="8957c-311">*hexadecimal değeri*</span><span class="sxs-lookup"><span data-stu-id="8957c-311">*hexadecimal value*</span></span> | <span data-ttu-id="8957c-312">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8957c-312">.NET Core 3.0</span></span> |

<span data-ttu-id="8957c-313">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8957c-313">Example:</span></span>

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
> <span data-ttu-id="8957c-314">*Runtimeconfig.json'da*seçeneği ayarlıyorsanız, ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="8957c-314">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="8957c-315">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, hexadecimal değeri belirtin.</span><span class="sxs-lookup"><span data-stu-id="8957c-315">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="8957c-316">Örneğin, yığın kullanımını %30 ile sınırlamak için, değerler JSON dosyası için 30, ortam değişkeni için 0x1E veya 1E olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8957c-316">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="8957c-317">System.GC.RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="8957c-317">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="8957c-318">Silinmesi gereken segmentlerin ileride kullanılmak üzere bekleme listesine alınıp alınmayacağını veya işletim sistemine (OS) geri salınıp salınmayacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8957c-318">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="8957c-319">Varsayılan: Segmentleri işletim sistemine geri`false`bırakın ( ).</span><span class="sxs-lookup"><span data-stu-id="8957c-319">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="8957c-320">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="8957c-320">Setting name</span></span> | <span data-ttu-id="8957c-321">Değerler</span><span class="sxs-lookup"><span data-stu-id="8957c-321">Values</span></span> | <span data-ttu-id="8957c-322">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="8957c-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8957c-323">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="8957c-323">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="8957c-324">`false`- işletim sistemi için sürüm</span><span class="sxs-lookup"><span data-stu-id="8957c-324">`false` - release to OS</span></span><br/><span data-ttu-id="8957c-325">`true`- beklemeye</span><span class="sxs-lookup"><span data-stu-id="8957c-325">`true` - put on standby</span></span> | <span data-ttu-id="8957c-326">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="8957c-326">.NET Core 1.0</span></span> |
| <span data-ttu-id="8957c-327">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="8957c-327">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="8957c-328">`false`- işletim sistemi için sürüm</span><span class="sxs-lookup"><span data-stu-id="8957c-328">`false` - release to OS</span></span><br/><span data-ttu-id="8957c-329">`true`- beklemeye</span><span class="sxs-lookup"><span data-stu-id="8957c-329">`true` - put on standby</span></span> | <span data-ttu-id="8957c-330">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="8957c-330">.NET Core 1.0</span></span> |
| <span data-ttu-id="8957c-331">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="8957c-331">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="8957c-332">`0`- işletim sistemi için sürüm</span><span class="sxs-lookup"><span data-stu-id="8957c-332">`0` - release to OS</span></span><br/><span data-ttu-id="8957c-333">`1`- beklemeye</span><span class="sxs-lookup"><span data-stu-id="8957c-333">`1` - put on standby</span></span> | <span data-ttu-id="8957c-334">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="8957c-334">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="8957c-335">Örnekler</span><span class="sxs-lookup"><span data-stu-id="8957c-335">Examples</span></span>

<span data-ttu-id="8957c-336">*runtimeconfig.json* dosyası:</span><span class="sxs-lookup"><span data-stu-id="8957c-336">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="8957c-337">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="8957c-337">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="8957c-338">Büyük sayfalar</span><span class="sxs-lookup"><span data-stu-id="8957c-338">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="8957c-339">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="8957c-339">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="8957c-340">Yığın sabit sınır ayarlandığında büyük sayfaların kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8957c-340">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="8957c-341">Varsayılan: Devre`0`Dışı ( ).</span><span class="sxs-lookup"><span data-stu-id="8957c-341">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="8957c-342">Bu deneysel bir ayar.</span><span class="sxs-lookup"><span data-stu-id="8957c-342">This is an experimental setting.</span></span>

| | <span data-ttu-id="8957c-343">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="8957c-343">Setting name</span></span> | <span data-ttu-id="8957c-344">Değerler</span><span class="sxs-lookup"><span data-stu-id="8957c-344">Values</span></span> | <span data-ttu-id="8957c-345">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="8957c-345">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8957c-346">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="8957c-346">**runtimeconfig.json**</span></span> | <span data-ttu-id="8957c-347">Yok</span><span class="sxs-lookup"><span data-stu-id="8957c-347">N/A</span></span> | <span data-ttu-id="8957c-348">Yok</span><span class="sxs-lookup"><span data-stu-id="8957c-348">N/A</span></span> | <span data-ttu-id="8957c-349">Yok</span><span class="sxs-lookup"><span data-stu-id="8957c-349">N/A</span></span> |
| <span data-ttu-id="8957c-350">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="8957c-350">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="8957c-351">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="8957c-351">`0` - disabled</span></span><br/><span data-ttu-id="8957c-352">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="8957c-352">`1` - enabled</span></span> | <span data-ttu-id="8957c-353">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8957c-353">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="8957c-354">Büyük nesneler</span><span class="sxs-lookup"><span data-stu-id="8957c-354">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="8957c-355">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="8957c-355">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="8957c-356">Toplam boyutu 2 gigabayttan (GB) büyük diziler için 64 bit platformlarda çöp toplayıcı desteğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8957c-356">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="8957c-357">Varsayılan: Etkin`1`( ).</span><span class="sxs-lookup"><span data-stu-id="8957c-357">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="8957c-358">Bu seçenek ,NET'in gelecekteki sürümünde geçersiz hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="8957c-358">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="8957c-359">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="8957c-359">Setting name</span></span> | <span data-ttu-id="8957c-360">Değerler</span><span class="sxs-lookup"><span data-stu-id="8957c-360">Values</span></span> | <span data-ttu-id="8957c-361">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="8957c-361">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8957c-362">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="8957c-362">**runtimeconfig.json**</span></span> | <span data-ttu-id="8957c-363">Yok</span><span class="sxs-lookup"><span data-stu-id="8957c-363">N/A</span></span> | <span data-ttu-id="8957c-364">Yok</span><span class="sxs-lookup"><span data-stu-id="8957c-364">N/A</span></span> | <span data-ttu-id="8957c-365">Yok</span><span class="sxs-lookup"><span data-stu-id="8957c-365">N/A</span></span> |
| <span data-ttu-id="8957c-366">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="8957c-366">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="8957c-367">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="8957c-367">`1` - enabled</span></span><br/> <span data-ttu-id="8957c-368">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="8957c-368">`0` - disabled</span></span> | <span data-ttu-id="8957c-369">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="8957c-369">.NET Core 1.0</span></span> |
| <span data-ttu-id="8957c-370">**.NET Framework için app.config**</span><span class="sxs-lookup"><span data-stu-id="8957c-370">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8957c-371">gcAllowVeryLargeNesneler</span><span class="sxs-lookup"><span data-stu-id="8957c-371">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="8957c-372">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="8957c-372">`1` - enabled</span></span><br/> <span data-ttu-id="8957c-373">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="8957c-373">`0` - disabled</span></span> | <span data-ttu-id="8957c-374">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="8957c-374">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="8957c-375">Büyük nesne yığını eşiği</span><span class="sxs-lookup"><span data-stu-id="8957c-375">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="8957c-376">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="8957c-376">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="8957c-377">Nesnelerin büyük nesne yığınına (LOH) gitmesine neden olan eşik boyutunu baytlar olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="8957c-377">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="8957c-378">Varsayılan eşik 85.000 bayttır.</span><span class="sxs-lookup"><span data-stu-id="8957c-378">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="8957c-379">Belirttiğiniz değer varsayılan eşiğe göre daha büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8957c-379">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="8957c-380">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="8957c-380">Setting name</span></span> | <span data-ttu-id="8957c-381">Değerler</span><span class="sxs-lookup"><span data-stu-id="8957c-381">Values</span></span> | <span data-ttu-id="8957c-382">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="8957c-382">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8957c-383">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="8957c-383">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="8957c-384">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="8957c-384">*decimal value*</span></span> | <span data-ttu-id="8957c-385">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="8957c-385">.NET Core 1.0</span></span> |
| <span data-ttu-id="8957c-386">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="8957c-386">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="8957c-387">*hexadecimal değeri*</span><span class="sxs-lookup"><span data-stu-id="8957c-387">*hexadecimal value*</span></span> | <span data-ttu-id="8957c-388">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="8957c-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="8957c-389">**.NET Framework için app.config**</span><span class="sxs-lookup"><span data-stu-id="8957c-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="8957c-390">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="8957c-390">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="8957c-391">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="8957c-391">*decimal value*</span></span> | <span data-ttu-id="8957c-392"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="8957c-392">.NET Framework 4.8</span></span> |

<span data-ttu-id="8957c-393">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8957c-393">Example:</span></span>

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
> <span data-ttu-id="8957c-394">*Runtimeconfig.json'da*seçeneği ayarlıyorsanız, ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="8957c-394">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="8957c-395">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, hexadecimal değeri belirtin.</span><span class="sxs-lookup"><span data-stu-id="8957c-395">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="8957c-396">Örneğin, 120.000 bayt lık bir eşik boyutu ayarlamak için değerler JSON dosyası için 120000 ve ortam değişkeni için 0x1D4C0 veya 1D4C0 olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8957c-396">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="8957c-397">Bağımsız GC</span><span class="sxs-lookup"><span data-stu-id="8957c-397">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="8957c-398">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="8957c-398">COMPlus_GCName</span></span>

- <span data-ttu-id="8957c-399">Çalışma zamanının yüklemeyi planladığı çöp toplayıcısını içeren kitaplık için bir yol belirtir.</span><span class="sxs-lookup"><span data-stu-id="8957c-399">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="8957c-400">Daha fazla bilgi için, [Bkz. Bağımsız GC yükleyici tasarımı.](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md)</span><span class="sxs-lookup"><span data-stu-id="8957c-400">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="8957c-401">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="8957c-401">Setting name</span></span> | <span data-ttu-id="8957c-402">Değerler</span><span class="sxs-lookup"><span data-stu-id="8957c-402">Values</span></span> | <span data-ttu-id="8957c-403">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="8957c-403">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="8957c-404">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="8957c-404">**runtimeconfig.json**</span></span> | <span data-ttu-id="8957c-405">Yok</span><span class="sxs-lookup"><span data-stu-id="8957c-405">N/A</span></span> | <span data-ttu-id="8957c-406">Yok</span><span class="sxs-lookup"><span data-stu-id="8957c-406">N/A</span></span> | <span data-ttu-id="8957c-407">Yok</span><span class="sxs-lookup"><span data-stu-id="8957c-407">N/A</span></span> |
| <span data-ttu-id="8957c-408">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="8957c-408">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="8957c-409">*string_path*</span><span class="sxs-lookup"><span data-stu-id="8957c-409">*string_path*</span></span> | <span data-ttu-id="8957c-410">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="8957c-410">.NET Core 2.0</span></span> |
