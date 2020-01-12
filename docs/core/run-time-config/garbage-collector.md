---
title: Çöp toplayıcı yapılandırma ayarları
description: Çöp toplayıcının .NET Core uygulamaları için belleği nasıl yönettiğini yapılandırmak üzere çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 24e5c47de781e7eed5f76d2c551cac2dce1e8f05
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900102"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="901bf-103">Çöp toplama için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="901bf-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="901bf-104">Bu sayfa, çalışma zamanında değiştirilebilen çöp toplayıcı (GC) ayarları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="901bf-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="901bf-105">Çalışan bir uygulamanın en yüksek performans düzeyine ulaşmak istiyorsanız bu ayarları kullanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="901bf-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="901bf-106">Bununla birlikte, varsayılan olarak, çoğu uygulama için tipik durumlarda en iyi performansı sağlar.</span><span class="sxs-lookup"><span data-stu-id="901bf-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="901bf-107">Ayarlar bu sayfadaki gruplar halinde düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="901bf-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="901bf-108">Her grup içindeki ayarlar, belirli bir sonuca ulaşmak için genellikle birbirleriyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="901bf-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="901bf-109">Bu ayarlar ayrıca uygulama çalışırken dinamik olarak değiştirilebilir, bu nedenle ayarladığınız tüm çalışma zamanı ayarları geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="901bf-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="901bf-110">[Gecikme düzeyi](../../standard/garbage-collection/latency.md)gibi bazı ayarlar tipik olarak yalnızca TASARıM zamanında API aracılığıyla ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="901bf-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="901bf-111">Bu tür ayarlar bu sayfadan çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="901bf-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="901bf-112">Sayı değerleri için, *runtimeconfig. JSON* dosyasındaki ayarlar için ondalık gösterimi ve ortam değişkeni ayarları için onaltılık gösterimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="901bf-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="901bf-113">Onaltılık değerler için, bunları "0x" öneki olmadan veya olmadan belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="901bf-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="901bf-114">Çöp toplamanın türleri</span><span class="sxs-lookup"><span data-stu-id="901bf-114">Flavors of garbage collection</span></span>

<span data-ttu-id="901bf-115">Çöp toplamanın iki ana özellikleri, iş istasyonu GC ve sunucu GC ' dir.</span><span class="sxs-lookup"><span data-stu-id="901bf-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="901bf-116">İkisi arasındaki farklılıklar hakkında daha fazla bilgi için bkz. [çöp toplamanın temelleri](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="901bf-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="901bf-117">Çöp toplamanın alt türleri arka plan ve eş zamanlı değil.</span><span class="sxs-lookup"><span data-stu-id="901bf-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="901bf-118">Çöp toplamanın türlerini seçmek için aşağıdaki ayarları kullanın:</span><span class="sxs-lookup"><span data-stu-id="901bf-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="901bf-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="901bf-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="901bf-120">Uygulamanın iş istasyonu çöp toplamayı veya sunucu çöp toplamayı kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="901bf-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="901bf-121">Varsayılan: Iş Istasyonu atık toplama (`false`).</span><span class="sxs-lookup"><span data-stu-id="901bf-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="901bf-122">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="901bf-122">Setting name</span></span> | <span data-ttu-id="901bf-123">Değerler</span><span class="sxs-lookup"><span data-stu-id="901bf-123">Values</span></span> | <span data-ttu-id="901bf-124">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="901bf-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="901bf-125">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="901bf-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="901bf-126">`false`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="901bf-126">`false` - workstation</span></span><br/><span data-ttu-id="901bf-127">`true`-sunucu</span><span class="sxs-lookup"><span data-stu-id="901bf-127">`true` - server</span></span> | <span data-ttu-id="901bf-128">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="901bf-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="901bf-129">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="901bf-129">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="901bf-130">`0`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="901bf-130">`0` - workstation</span></span><br/><span data-ttu-id="901bf-131">`1`-sunucu</span><span class="sxs-lookup"><span data-stu-id="901bf-131">`1` - server</span></span> | <span data-ttu-id="901bf-132">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="901bf-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="901bf-133">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="901bf-133">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="901bf-134">GCServer</span><span class="sxs-lookup"><span data-stu-id="901bf-134">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="901bf-135">`false`-iş istasyonu</span><span class="sxs-lookup"><span data-stu-id="901bf-135">`false` - workstation</span></span><br/><span data-ttu-id="901bf-136">`true`-sunucu</span><span class="sxs-lookup"><span data-stu-id="901bf-136">`true` - server</span></span> |  |

<span data-ttu-id="901bf-137">Örnek:</span><span class="sxs-lookup"><span data-stu-id="901bf-137">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="901bf-138">System. GC. eşzamanlı/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="901bf-138">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="901bf-139">Arka plan (eşzamanlı) Çöp toplamanın etkinleştirilip etkinleştirilmeyeceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="901bf-139">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="901bf-140">Varsayılan: etkin (`true`).</span><span class="sxs-lookup"><span data-stu-id="901bf-140">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="901bf-141">Daha fazla bilgi için bkz. [arka plan atık toplama](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) ve [arka plan sunucusu çöp toplama](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="901bf-141">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="901bf-142">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="901bf-142">Setting name</span></span> | <span data-ttu-id="901bf-143">Değerler</span><span class="sxs-lookup"><span data-stu-id="901bf-143">Values</span></span> | <span data-ttu-id="901bf-144">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="901bf-144">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="901bf-145">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="901bf-145">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="901bf-146">`true` arka plan GC</span><span class="sxs-lookup"><span data-stu-id="901bf-146">`true` - background GC</span></span><br/><span data-ttu-id="901bf-147">`false`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="901bf-147">`false` - non-concurrent GC</span></span> | <span data-ttu-id="901bf-148">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="901bf-148">.NET Core 1.0</span></span> |
| <span data-ttu-id="901bf-149">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="901bf-149">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="901bf-150">`true` arka plan GC</span><span class="sxs-lookup"><span data-stu-id="901bf-150">`true` - background GC</span></span><br/><span data-ttu-id="901bf-151">`false`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="901bf-151">`false` - non-concurrent GC</span></span> | <span data-ttu-id="901bf-152">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="901bf-152">.NET Core 1.0</span></span> |
| <span data-ttu-id="901bf-153">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="901bf-153">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="901bf-154">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="901bf-154">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="901bf-155">`true` arka plan GC</span><span class="sxs-lookup"><span data-stu-id="901bf-155">`true` - background GC</span></span><br/><span data-ttu-id="901bf-156">`false`-eş zamanlı olmayan GC</span><span class="sxs-lookup"><span data-stu-id="901bf-156">`false` - non-concurrent GC</span></span> |  |

<span data-ttu-id="901bf-157">Örnek:</span><span class="sxs-lookup"><span data-stu-id="901bf-157">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

## <a name="manage-resource-usage"></a><span data-ttu-id="901bf-158">Kaynak kullanımını yönetme</span><span class="sxs-lookup"><span data-stu-id="901bf-158">Manage resource usage</span></span>

<span data-ttu-id="901bf-159">Çöp toplayıcının bellek ve işlemci kullanımını yönetmek için bu bölümde açıklanan ayarları kullanın.</span><span class="sxs-lookup"><span data-stu-id="901bf-159">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="901bf-160">Bu ayarlardan bazıları hakkında daha fazla bilgi için, bkz. [iş istasyonu ve sunucu GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blogu girişi.</span><span class="sxs-lookup"><span data-stu-id="901bf-160">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="901bf-161">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="901bf-161">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="901bf-162">Çöp toplayıcı tarafından oluşturulan Heap sayısını sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="901bf-162">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="901bf-163">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="901bf-163">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="901bf-164">GC işlemci benzeşimi etkinse, varsayılan olarak, yığın sayısı ayarı GC sayfa@@/iş parçacıklarını ilk `n` işlemcilere `n`.</span><span class="sxs-lookup"><span data-stu-id="901bf-164">If GC processor affinity is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="901bf-165">(Tam olarak hangi işlemcilerin olduğunu belirtmek için, bu maskeyi seçin veya aralıklar ayarlarını kesin olarak belirleyin.)</span><span class="sxs-lookup"><span data-stu-id="901bf-165">(Use the affinitize mask or affinitize ranges settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="901bf-166">GC işlemci benzeşimi devre dışıysa, bu ayar GC yığınlarının sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="901bf-166">If GC processor affinity is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="901bf-167">Daha fazla bilgi için [Gcheapcount açıklamalarını](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks)inceleyin.</span><span class="sxs-lookup"><span data-stu-id="901bf-167">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="901bf-168">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="901bf-168">Setting name</span></span> | <span data-ttu-id="901bf-169">Değerler</span><span class="sxs-lookup"><span data-stu-id="901bf-169">Values</span></span> | <span data-ttu-id="901bf-170">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="901bf-170">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="901bf-171">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="901bf-171">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="901bf-172">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="901bf-172">*decimal value*</span></span> | <span data-ttu-id="901bf-173">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="901bf-173">.NET Core 3.0</span></span> |
| <span data-ttu-id="901bf-174">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="901bf-174">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="901bf-175">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="901bf-175">*hexadecimal value*</span></span> | <span data-ttu-id="901bf-176">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="901bf-176">.NET Core 3.0</span></span> |
| <span data-ttu-id="901bf-177">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="901bf-177">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="901bf-178">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="901bf-178">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="901bf-179">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="901bf-179">*decimal value*</span></span> | <span data-ttu-id="901bf-180">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="901bf-180">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="901bf-181">Örnek:</span><span class="sxs-lookup"><span data-stu-id="901bf-181">Example:</span></span>

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
> <span data-ttu-id="901bf-182">*Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="901bf-182">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="901bf-183">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="901bf-183">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="901bf-184">Örneğin, Heap sayısını 16 ile sınırlamak için değerler JSON dosyası için 16, ortam değişkeni için 0x10 veya 10 olur.</span><span class="sxs-lookup"><span data-stu-id="901bf-184">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="901bf-185">System. GC. ısıpaffinitizemask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="901bf-185">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="901bf-186">Çöp toplayıcı iş parçacıklarının kullanması gereken tam işlemcileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="901bf-186">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="901bf-187">`System.GC.NoAffinitize` `true`olarak ayarlanarak, işlemci benzeşimi devre dışı bırakıldıysa, bu ayar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="901bf-187">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="901bf-188">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="901bf-188">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="901bf-189">Değer, işlem için kullanılabilir olan işlemcileri tanımlayan bir bit maskesidir.</span><span class="sxs-lookup"><span data-stu-id="901bf-189">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="901bf-190">Örneğin, bir 1023 ondalık değeri (veya ortam değişkenini kullanıyorsanız, 0x3FF veya 3FF onaltılı değeri), ikili gösterimde 0011 1111 1111 ' dir.</span><span class="sxs-lookup"><span data-stu-id="901bf-190">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="901bf-191">Bu, ilk 10 işlemcinin kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="901bf-191">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="901bf-192">Sıradaki 10 işlemciyi belirtmek için, işlemci 10-19 ' 1047552 nin ondalık değerini (veya 0xFFC00 ya da FFC00) bir 1111 1111 1100 0000 0000 ikili değere eşdeğer bir değere belirleyin.</span><span class="sxs-lookup"><span data-stu-id="901bf-192">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="901bf-193">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="901bf-193">Setting name</span></span> | <span data-ttu-id="901bf-194">Değerler</span><span class="sxs-lookup"><span data-stu-id="901bf-194">Values</span></span> | <span data-ttu-id="901bf-195">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="901bf-195">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="901bf-196">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="901bf-196">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="901bf-197">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="901bf-197">*decimal value*</span></span> | <span data-ttu-id="901bf-198">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="901bf-198">.NET Core 3.0</span></span> |
| <span data-ttu-id="901bf-199">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="901bf-199">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="901bf-200">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="901bf-200">*hexadecimal value*</span></span> | <span data-ttu-id="901bf-201">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="901bf-201">.NET Core 3.0</span></span> |
| <span data-ttu-id="901bf-202">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="901bf-202">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="901bf-203">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="901bf-203">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="901bf-204">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="901bf-204">*decimal value*</span></span> | <span data-ttu-id="901bf-205">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="901bf-205">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="901bf-206">Örnek:</span><span class="sxs-lookup"><span data-stu-id="901bf-206">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="901bf-207">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="901bf-207">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="901bf-208">Çöp toplayıcı iş parçacıkları için kullanılacak işlemcilerin listesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="901bf-208">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="901bf-209">Bu ayar `System.GC.HeapAffinitizeMask`benzerdir, ancak 64 'den fazla işlemciyi belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="901bf-209">This setting is similar to `System.GC.HeapAffinitizeMask`, except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="901bf-210">Windows işletim sistemleri için, işlemci numarasını veya aralığını karşılık gelen [CPU grubuyla](/windows/win32/procthread/processor-groups)önek olarak ekleyin, örneğin, "0:1-10, 0:12, 1:50-52, 1:70".</span><span class="sxs-lookup"><span data-stu-id="901bf-210">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="901bf-211">`System.GC.NoAffinitize` `true`olarak ayarlanarak, işlemci benzeşimi devre dışı bırakıldıysa, bu ayar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="901bf-211">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="901bf-212">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="901bf-212">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="901bf-213">Daha fazla bilgi için bkz. Maoni Stephens ' blogu üzerinde [> 64 CPU 'su olan MAKINELERDE GC için daha Iyi hale getirme](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) .</span><span class="sxs-lookup"><span data-stu-id="901bf-213">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="901bf-214">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="901bf-214">Setting name</span></span> | <span data-ttu-id="901bf-215">Değerler</span><span class="sxs-lookup"><span data-stu-id="901bf-215">Values</span></span> | <span data-ttu-id="901bf-216">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="901bf-216">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="901bf-217">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="901bf-217">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="901bf-218">İşlemci numaralarının veya işlemci numarası aralıklarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="901bf-218">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="901bf-219">UNIX örneği: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="901bf-219">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="901bf-220">Windows örnek: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="901bf-220">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="901bf-221">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="901bf-221">.NET Core 3.0</span></span> |
| <span data-ttu-id="901bf-222">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="901bf-222">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="901bf-223">İşlemci numaralarının veya işlemci numarası aralıklarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="901bf-223">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="901bf-224">UNIX örneği: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="901bf-224">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="901bf-225">Windows örnek: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="901bf-225">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="901bf-226">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="901bf-226">.NET Core 3.0</span></span> |

<span data-ttu-id="901bf-227">Örnek:</span><span class="sxs-lookup"><span data-stu-id="901bf-227">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="901bf-228">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="901bf-228">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="901bf-229">Çöp toplayıcının [CPU grupları](/windows/win32/procthread/processor-groups) kullanıp kullanmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="901bf-229">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="901bf-230">64 bitlik bir Windows bilgisayarında birden çok CPU grubu olduğunda, diğer bir deyişle, 64 ' den fazla işlemci varsa, bu öğenin tüm CPU gruplarında çöp toplamayı genişletmelerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="901bf-230">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="901bf-231">Çöp toplayıcı, Heap 'ler oluşturmak ve dengelemek için tüm çekirdekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="901bf-231">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="901bf-232">Yalnızca 64-bit Windows işletim sistemlerinde sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="901bf-232">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="901bf-233">Varsayılan: devre dışı (`0`).</span><span class="sxs-lookup"><span data-stu-id="901bf-233">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="901bf-234">Daha fazla bilgi için bkz. Maoni Stephens ' blogu üzerinde [> 64 CPU 'su olan MAKINELERDE GC için daha Iyi hale getirme](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) .</span><span class="sxs-lookup"><span data-stu-id="901bf-234">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="901bf-235">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="901bf-235">Setting name</span></span> | <span data-ttu-id="901bf-236">Değerler</span><span class="sxs-lookup"><span data-stu-id="901bf-236">Values</span></span> | <span data-ttu-id="901bf-237">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="901bf-237">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="901bf-238">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="901bf-238">**runtimeconfig.json**</span></span> | <span data-ttu-id="901bf-239">YOK</span><span class="sxs-lookup"><span data-stu-id="901bf-239">N/A</span></span> | <span data-ttu-id="901bf-240">YOK</span><span class="sxs-lookup"><span data-stu-id="901bf-240">N/A</span></span> | <span data-ttu-id="901bf-241">YOK</span><span class="sxs-lookup"><span data-stu-id="901bf-241">N/A</span></span> |
| <span data-ttu-id="901bf-242">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="901bf-242">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="901bf-243">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="901bf-243">`0` - disabled</span></span><br/><span data-ttu-id="901bf-244">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="901bf-244">`1` - enabled</span></span> | <span data-ttu-id="901bf-245">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="901bf-245">.NET Core 1.0</span></span> |
| <span data-ttu-id="901bf-246">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="901bf-246">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="901bf-247">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="901bf-247">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="901bf-248">`false`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="901bf-248">`false` - disabled</span></span><br/><span data-ttu-id="901bf-249">`true` etkin</span><span class="sxs-lookup"><span data-stu-id="901bf-249">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="901bf-250">Ortak dil çalışma zamanını (CLR) tüm CPU grupları arasında iş parçacığı havuzundan da dağıtmak üzere yapılandırmak için, [Thread_UseAllCpuGroups öğesi](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) seçeneğini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="901bf-250">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="901bf-251">.NET Core uygulamaları için `COMPlus_Thread_UseAllCpuGroups` ortam değişkeninin değerini `1`olarak ayarlayarak bu seçeneği etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="901bf-251">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="901bf-252">System. GC. Noafınitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="901bf-252">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="901bf-253">*Çöp toplama* iş parçacıklarının işlemcilerle kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="901bf-253">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="901bf-254">Bir GC iş parçacığını eklemek için yalnızca belirli bir CPU üzerinde çalışabilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="901bf-254">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="901bf-255">Her GC iş parçacığı için bir yığın oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="901bf-255">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="901bf-256">Yalnızca sunucu çöp toplama için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="901bf-256">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="901bf-257">Varsayılan: işlemciler (`false`) ile atık toplama iş parçacıklarını ön olarak başlatma.</span><span class="sxs-lookup"><span data-stu-id="901bf-257">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="901bf-258">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="901bf-258">Setting name</span></span> | <span data-ttu-id="901bf-259">Değerler</span><span class="sxs-lookup"><span data-stu-id="901bf-259">Values</span></span> | <span data-ttu-id="901bf-260">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="901bf-260">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="901bf-261">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="901bf-261">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="901bf-262">`false`-afze</span><span class="sxs-lookup"><span data-stu-id="901bf-262">`false` - affinitize</span></span><br/><span data-ttu-id="901bf-263">`true`-yok etme</span><span class="sxs-lookup"><span data-stu-id="901bf-263">`true` - don't affinitize</span></span> | <span data-ttu-id="901bf-264">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="901bf-264">.NET Core 3.0</span></span> |
| <span data-ttu-id="901bf-265">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="901bf-265">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="901bf-266">`0`-afze</span><span class="sxs-lookup"><span data-stu-id="901bf-266">`0` - affinitize</span></span><br/><span data-ttu-id="901bf-267">`1`-yok etme</span><span class="sxs-lookup"><span data-stu-id="901bf-267">`1` - don't affinitize</span></span> | <span data-ttu-id="901bf-268">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="901bf-268">.NET Core 3.0</span></span> |
| <span data-ttu-id="901bf-269">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="901bf-269">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="901bf-270">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="901bf-270">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="901bf-271">`false`-afze</span><span class="sxs-lookup"><span data-stu-id="901bf-271">`false` - affinitize</span></span><br/><span data-ttu-id="901bf-272">`true`-yok etme</span><span class="sxs-lookup"><span data-stu-id="901bf-272">`true` - don't affinitize</span></span> | <span data-ttu-id="901bf-273">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="901bf-273">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="901bf-274">Örnek:</span><span class="sxs-lookup"><span data-stu-id="901bf-274">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="901bf-275">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="901bf-275">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="901bf-276">GC yığını ve GC booksaklanması için bayt cinsinden en fazla tamamlama boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="901bf-276">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>

| | <span data-ttu-id="901bf-277">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="901bf-277">Setting name</span></span> | <span data-ttu-id="901bf-278">Değerler</span><span class="sxs-lookup"><span data-stu-id="901bf-278">Values</span></span> | <span data-ttu-id="901bf-279">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="901bf-279">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="901bf-280">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="901bf-280">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="901bf-281">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="901bf-281">*decimal value*</span></span> | <span data-ttu-id="901bf-282">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="901bf-282">.NET Core 3.0</span></span> |
| <span data-ttu-id="901bf-283">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="901bf-283">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="901bf-284">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="901bf-284">*hexadecimal value*</span></span> | <span data-ttu-id="901bf-285">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="901bf-285">.NET Core 3.0</span></span> |

<span data-ttu-id="901bf-286">Örnek:</span><span class="sxs-lookup"><span data-stu-id="901bf-286">Example:</span></span>

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
> <span data-ttu-id="901bf-287">*Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="901bf-287">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="901bf-288">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="901bf-288">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="901bf-289">Örneğin, 200 mebibytes (MIB) yığın sabit sınırı belirtmek için, değerler JSON dosyası için 209715200 ve ortam değişkeni için 0xC800000 veya C800000 olur.</span><span class="sxs-lookup"><span data-stu-id="901bf-289">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="901bf-290">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="901bf-290">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="901bf-291">Toplam belleğin yüzdesi olarak GC yığın kullanımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="901bf-291">Specifies the GC heap usage as a percentage of the total memory.</span></span>

| | <span data-ttu-id="901bf-292">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="901bf-292">Setting name</span></span> | <span data-ttu-id="901bf-293">Değerler</span><span class="sxs-lookup"><span data-stu-id="901bf-293">Values</span></span> | <span data-ttu-id="901bf-294">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="901bf-294">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="901bf-295">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="901bf-295">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="901bf-296">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="901bf-296">*decimal value*</span></span> | <span data-ttu-id="901bf-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="901bf-297">.NET Core 3.0</span></span> |
| <span data-ttu-id="901bf-298">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="901bf-298">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="901bf-299">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="901bf-299">*hexadecimal value*</span></span> | <span data-ttu-id="901bf-300">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="901bf-300">.NET Core 3.0</span></span> |

<span data-ttu-id="901bf-301">Örnek:</span><span class="sxs-lookup"><span data-stu-id="901bf-301">Example:</span></span>

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
> <span data-ttu-id="901bf-302">*Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="901bf-302">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="901bf-303">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="901bf-303">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="901bf-304">Örneğin, yığın kullanımını %30 olarak sınırlandırmak için değerler JSON dosyası için 30, ortam değişkeni için 0x1E veya 1E olur.</span><span class="sxs-lookup"><span data-stu-id="901bf-304">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="901bf-305">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="901bf-305">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="901bf-306">Silinmesi gereken segmentlerin ileride kullanılmak üzere bir bekleme listesine mi yerleştirileceğini, yoksa işletim sistemine (OS) geri mi bırakılacağını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="901bf-306">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="901bf-307">Varsayılan: kesimleri işletim sistemine (`false`) yeniden bırakın.</span><span class="sxs-lookup"><span data-stu-id="901bf-307">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="901bf-308">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="901bf-308">Setting name</span></span> | <span data-ttu-id="901bf-309">Değerler</span><span class="sxs-lookup"><span data-stu-id="901bf-309">Values</span></span> | <span data-ttu-id="901bf-310">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="901bf-310">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="901bf-311">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="901bf-311">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="901bf-312">`false`-işletim sistemine yayın</span><span class="sxs-lookup"><span data-stu-id="901bf-312">`false` - release to OS</span></span><br/><span data-ttu-id="901bf-313">`true`-bekleme üzerine koy</span><span class="sxs-lookup"><span data-stu-id="901bf-313">`true` - put on standby</span></span>| <span data-ttu-id="901bf-314">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="901bf-314">.NET Core 1.0</span></span> |
| <span data-ttu-id="901bf-315">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="901bf-315">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="901bf-316">`0`-işletim sistemine yayın</span><span class="sxs-lookup"><span data-stu-id="901bf-316">`0` - release to OS</span></span><br/><span data-ttu-id="901bf-317">`1`-bekleme üzerine koy</span><span class="sxs-lookup"><span data-stu-id="901bf-317">`1` - put on standby</span></span> | <span data-ttu-id="901bf-318">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="901bf-318">.NET Core 1.0</span></span> |

<span data-ttu-id="901bf-319">Örnek:</span><span class="sxs-lookup"><span data-stu-id="901bf-319">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

## <a name="large-pages"></a><span data-ttu-id="901bf-320">Büyük sayfalar</span><span class="sxs-lookup"><span data-stu-id="901bf-320">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="901bf-321">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="901bf-321">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="901bf-322">Bir yığın sabit sınırı ayarlandığında büyük sayfaların kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="901bf-322">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="901bf-323">Varsayılan: devre dışı (`0`).</span><span class="sxs-lookup"><span data-stu-id="901bf-323">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="901bf-324">Bu bir deneysel ayardır.</span><span class="sxs-lookup"><span data-stu-id="901bf-324">This is an experimental setting.</span></span>

| | <span data-ttu-id="901bf-325">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="901bf-325">Setting name</span></span> | <span data-ttu-id="901bf-326">Değerler</span><span class="sxs-lookup"><span data-stu-id="901bf-326">Values</span></span> | <span data-ttu-id="901bf-327">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="901bf-327">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="901bf-328">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="901bf-328">**runtimeconfig.json**</span></span> | <span data-ttu-id="901bf-329">YOK</span><span class="sxs-lookup"><span data-stu-id="901bf-329">N/A</span></span> | <span data-ttu-id="901bf-330">YOK</span><span class="sxs-lookup"><span data-stu-id="901bf-330">N/A</span></span> | <span data-ttu-id="901bf-331">YOK</span><span class="sxs-lookup"><span data-stu-id="901bf-331">N/A</span></span> |
| <span data-ttu-id="901bf-332">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="901bf-332">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="901bf-333">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="901bf-333">`0` - disabled</span></span><br/><span data-ttu-id="901bf-334">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="901bf-334">`1` - enabled</span></span> | <span data-ttu-id="901bf-335">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="901bf-335">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="901bf-336">Büyük nesneler</span><span class="sxs-lookup"><span data-stu-id="901bf-336">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="901bf-337">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="901bf-337">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="901bf-338">Toplam boyuttaki 2 gigabayttan (GB) büyük olan diziler için 64 bitlik platformlarda çöp toplayıcı desteğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="901bf-338">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="901bf-339">Varsayılan: etkin (`1`).</span><span class="sxs-lookup"><span data-stu-id="901bf-339">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="901bf-340">Bu seçenek, .NET 'in gelecek bir sürümünde kullanımdan kalkabilir.</span><span class="sxs-lookup"><span data-stu-id="901bf-340">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="901bf-341">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="901bf-341">Setting name</span></span> | <span data-ttu-id="901bf-342">Değerler</span><span class="sxs-lookup"><span data-stu-id="901bf-342">Values</span></span> | <span data-ttu-id="901bf-343">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="901bf-343">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="901bf-344">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="901bf-344">**runtimeconfig.json**</span></span> | <span data-ttu-id="901bf-345">YOK</span><span class="sxs-lookup"><span data-stu-id="901bf-345">N/A</span></span> | <span data-ttu-id="901bf-346">YOK</span><span class="sxs-lookup"><span data-stu-id="901bf-346">N/A</span></span> | <span data-ttu-id="901bf-347">YOK</span><span class="sxs-lookup"><span data-stu-id="901bf-347">N/A</span></span> |
| <span data-ttu-id="901bf-348">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="901bf-348">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="901bf-349">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="901bf-349">`1` - enabled</span></span><br/> <span data-ttu-id="901bf-350">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="901bf-350">`0` - disabled</span></span> | <span data-ttu-id="901bf-351">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="901bf-351">.NET Core 1.0</span></span> |
| <span data-ttu-id="901bf-352">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="901bf-352">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="901bf-353">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="901bf-353">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="901bf-354">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="901bf-354">`1` - enabled</span></span><br/> <span data-ttu-id="901bf-355">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="901bf-355">`0` - disabled</span></span> | <span data-ttu-id="901bf-356">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="901bf-356">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="901bf-357">Büyük nesne yığın eşiği</span><span class="sxs-lookup"><span data-stu-id="901bf-357">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="901bf-358">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="901bf-358">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="901bf-359">Nesnelerin büyük nesne yığınında (LOH) geçmesine neden olan eşik boyutunu bayt cinsinden belirtir.</span><span class="sxs-lookup"><span data-stu-id="901bf-359">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="901bf-360">Varsayılan eşik 85.000 bayttır.</span><span class="sxs-lookup"><span data-stu-id="901bf-360">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="901bf-361">Belirttiğiniz değer varsayılan eşikten büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="901bf-361">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="901bf-362">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="901bf-362">Setting name</span></span> | <span data-ttu-id="901bf-363">Değerler</span><span class="sxs-lookup"><span data-stu-id="901bf-363">Values</span></span> | <span data-ttu-id="901bf-364">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="901bf-364">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="901bf-365">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="901bf-365">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="901bf-366">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="901bf-366">*decimal value*</span></span> | <span data-ttu-id="901bf-367">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="901bf-367">.NET Core 1.0</span></span> |
| <span data-ttu-id="901bf-368">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="901bf-368">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="901bf-369">*onaltılık değer*</span><span class="sxs-lookup"><span data-stu-id="901bf-369">*hexadecimal value*</span></span> | <span data-ttu-id="901bf-370">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="901bf-370">.NET Core 1.0</span></span> |
| <span data-ttu-id="901bf-371">**.NET Framework için App. config**</span><span class="sxs-lookup"><span data-stu-id="901bf-371">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="901bf-372">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="901bf-372">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="901bf-373">*ondalık değer*</span><span class="sxs-lookup"><span data-stu-id="901bf-373">*decimal value*</span></span> | <span data-ttu-id="901bf-374">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="901bf-374">.NET Framework 4.8</span></span> |

<span data-ttu-id="901bf-375">Örnek:</span><span class="sxs-lookup"><span data-stu-id="901bf-375">Example:</span></span>

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
> <span data-ttu-id="901bf-376">*Runtimeconfig. JSON*içinde seçeneğini ayarlıyorsanız, bir ondalık değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="901bf-376">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="901bf-377">Seçeneği bir ortam değişkeni olarak ayarlıyorsanız, onaltılık bir değer belirtin.</span><span class="sxs-lookup"><span data-stu-id="901bf-377">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="901bf-378">Örneğin, 120.000 baytlık bir eşik boyutu ayarlamak için, değerler JSON dosyası için 120000, ve ortam değişkeni için 0x1D4C0 ya da 1D4C0 olur.</span><span class="sxs-lookup"><span data-stu-id="901bf-378">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="901bf-379">Tek başına GC</span><span class="sxs-lookup"><span data-stu-id="901bf-379">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="901bf-380">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="901bf-380">COMPlus_GCName</span></span>

- <span data-ttu-id="901bf-381">Çalışma zamanının yüklemeyi amaçladığı çöp toplayıcısını içeren kitaplığın yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="901bf-381">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="901bf-382">Daha fazla bilgi için bkz. [tek BAŞıNA GC yükleyici tasarımı](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="901bf-382">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="901bf-383">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="901bf-383">Setting name</span></span> | <span data-ttu-id="901bf-384">Değerler</span><span class="sxs-lookup"><span data-stu-id="901bf-384">Values</span></span> | <span data-ttu-id="901bf-385">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="901bf-385">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="901bf-386">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="901bf-386">**runtimeconfig.json**</span></span> | <span data-ttu-id="901bf-387">YOK</span><span class="sxs-lookup"><span data-stu-id="901bf-387">N/A</span></span> | <span data-ttu-id="901bf-388">YOK</span><span class="sxs-lookup"><span data-stu-id="901bf-388">N/A</span></span> | <span data-ttu-id="901bf-389">YOK</span><span class="sxs-lookup"><span data-stu-id="901bf-389">N/A</span></span> |
| <span data-ttu-id="901bf-390">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="901bf-390">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="901bf-391">*string_path*</span><span class="sxs-lookup"><span data-stu-id="901bf-391">*string_path*</span></span> | <span data-ttu-id="901bf-392">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="901bf-392">.NET Core 2.0</span></span> |
