---
title: Profil oluşturma yapılandırması ayarları hata ayıklaması
description: .NET Core uygulamaları için hata ayıklamayı ve profil oluşturmayı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 5efd0f776da4b7ce6ff7f3bdfda24feec6e00f79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761999"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="bfc17-103">Hata ayıklama ve profil oluşturma için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="bfc17-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="bfc17-104">Tanılamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="bfc17-104">Enable diagnostics</span></span>

- <span data-ttu-id="bfc17-105">Hata ayıklayıcı, profil oluşturucu ve EventPipe tanılamaları 'nın etkin veya devre dışı olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="bfc17-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="bfc17-106">Bu ayarı atlarsanız, Tanılamalar etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bfc17-106">If you omit this setting, diagnostics are enabled.</span></span> <span data-ttu-id="bfc17-107">Bu değeri değerine ayarlamaya eşdeğerdir `1` .</span><span class="sxs-lookup"><span data-stu-id="bfc17-107">This is equivalent to setting the value to `1`.</span></span>

| | <span data-ttu-id="bfc17-108">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="bfc17-108">Setting name</span></span> | <span data-ttu-id="bfc17-109">Değerler</span><span class="sxs-lookup"><span data-stu-id="bfc17-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="bfc17-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="bfc17-110">**runtimeconfig.json**</span></span> | <span data-ttu-id="bfc17-111">Yok</span><span class="sxs-lookup"><span data-stu-id="bfc17-111">N/A</span></span> | <span data-ttu-id="bfc17-112">Yok</span><span class="sxs-lookup"><span data-stu-id="bfc17-112">N/A</span></span> |
| <span data-ttu-id="bfc17-113">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="bfc17-113">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="bfc17-114">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="bfc17-114">`1` - enabled</span></span><br/><span data-ttu-id="bfc17-115">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="bfc17-115">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="bfc17-116">Profil oluşturmayı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="bfc17-116">Enable profiling</span></span>

- <span data-ttu-id="bfc17-117">, Çalışmakta olan işlem için profil oluşturmanın etkinleştirilip etkinleştirilmeyeceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="bfc17-117">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="bfc17-118">Bu ayarı atlarsanız profil oluşturma devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="bfc17-118">If you omit this setting, profiling is disabled.</span></span> <span data-ttu-id="bfc17-119">Bu değeri değerine ayarlamaya eşdeğerdir `0` .</span><span class="sxs-lookup"><span data-stu-id="bfc17-119">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="bfc17-120">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="bfc17-120">Setting name</span></span> | <span data-ttu-id="bfc17-121">Değerler</span><span class="sxs-lookup"><span data-stu-id="bfc17-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="bfc17-122">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="bfc17-122">**runtimeconfig.json**</span></span> | <span data-ttu-id="bfc17-123">Yok</span><span class="sxs-lookup"><span data-stu-id="bfc17-123">N/A</span></span> | <span data-ttu-id="bfc17-124">Yok</span><span class="sxs-lookup"><span data-stu-id="bfc17-124">N/A</span></span> |
| <span data-ttu-id="bfc17-125">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="bfc17-125">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="bfc17-126">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="bfc17-126">`0` - disabled</span></span><br/><span data-ttu-id="bfc17-127">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="bfc17-127">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="bfc17-128">Profil Oluşturucu GUID 'SI</span><span class="sxs-lookup"><span data-stu-id="bfc17-128">Profiler GUID</span></span>

- <span data-ttu-id="bfc17-129">O anda çalışan işleme yüklenecek profil oluşturucunun GUID 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bfc17-129">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="bfc17-130">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="bfc17-130">Setting name</span></span> | <span data-ttu-id="bfc17-131">Değerler</span><span class="sxs-lookup"><span data-stu-id="bfc17-131">Values</span></span> |
| - | - | - |
| <span data-ttu-id="bfc17-132">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="bfc17-132">**runtimeconfig.json**</span></span> | <span data-ttu-id="bfc17-133">Yok</span><span class="sxs-lookup"><span data-stu-id="bfc17-133">N/A</span></span> | <span data-ttu-id="bfc17-134">Yok</span><span class="sxs-lookup"><span data-stu-id="bfc17-134">N/A</span></span> |
| <span data-ttu-id="bfc17-135">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="bfc17-135">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="bfc17-136">*dize-GUID*</span><span class="sxs-lookup"><span data-stu-id="bfc17-136">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="bfc17-137">Profil Oluşturucu konumu</span><span class="sxs-lookup"><span data-stu-id="bfc17-137">Profiler location</span></span>

- <span data-ttu-id="bfc17-138">Şu anda çalışan işleme (veya 32-bit veya 64 bit işlem) yüklenecek profil oluşturucu DLL dosyasının yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="bfc17-138">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="bfc17-139">Birden fazla değişken ayarlandıysa, bit genişliğine özgü değişkenler öncelik kazanır.</span><span class="sxs-lookup"><span data-stu-id="bfc17-139">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="bfc17-140">Profil oluşturucunun hangi bit hale getirinin yükleneceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="bfc17-140">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="bfc17-141">Daha fazla bilgi için bkz. [Profil Oluşturucu kitaplığını bulma](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span><span class="sxs-lookup"><span data-stu-id="bfc17-141">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="bfc17-142">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="bfc17-142">Setting name</span></span> | <span data-ttu-id="bfc17-143">Değerler</span><span class="sxs-lookup"><span data-stu-id="bfc17-143">Values</span></span> |
| - | - | - |
| <span data-ttu-id="bfc17-144">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="bfc17-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="bfc17-145">*dize yolu*</span><span class="sxs-lookup"><span data-stu-id="bfc17-145">*string-path*</span></span> |
| <span data-ttu-id="bfc17-146">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="bfc17-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="bfc17-147">*dize yolu*</span><span class="sxs-lookup"><span data-stu-id="bfc17-147">*string-path*</span></span> |
| <span data-ttu-id="bfc17-148">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="bfc17-148">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="bfc17-149">*dize yolu*</span><span class="sxs-lookup"><span data-stu-id="bfc17-149">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="bfc17-150">Perf haritasını yaz</span><span class="sxs-lookup"><span data-stu-id="bfc17-150">Write perf map</span></span>

- <span data-ttu-id="bfc17-151">Linux sistemlerinde */t MP/perf-$pid. Map* yazma veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="bfc17-151">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="bfc17-152">Bu ayarı atlarsanız, perf haritasını yazmak devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="bfc17-152">If you omit this setting, writing the perf map is disabled.</span></span> <span data-ttu-id="bfc17-153">Bu değeri değerine ayarlamaya eşdeğerdir `0` .</span><span class="sxs-lookup"><span data-stu-id="bfc17-153">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="bfc17-154">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="bfc17-154">Setting name</span></span> | <span data-ttu-id="bfc17-155">Değerler</span><span class="sxs-lookup"><span data-stu-id="bfc17-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="bfc17-156">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="bfc17-156">**runtimeconfig.json**</span></span> | <span data-ttu-id="bfc17-157">Yok</span><span class="sxs-lookup"><span data-stu-id="bfc17-157">N/A</span></span> | <span data-ttu-id="bfc17-158">Yok</span><span class="sxs-lookup"><span data-stu-id="bfc17-158">N/A</span></span> |
| <span data-ttu-id="bfc17-159">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="bfc17-159">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="bfc17-160">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="bfc17-160">`0` - disabled</span></span><br/><span data-ttu-id="bfc17-161">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="bfc17-161">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="bfc17-162">Performans günlüğü işaretçileri</span><span class="sxs-lookup"><span data-stu-id="bfc17-162">Perf log markers</span></span>

- <span data-ttu-id="bfc17-163">Belirtilen sinyalin performans günlüklerinde işaret olarak kabul edilip yoksayılmasını sağlar veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="bfc17-163">Enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="bfc17-164">Bu ayarı atlarsanız, belirtilen sinyal yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="bfc17-164">If you omit this setting, the specified signal is not ignored.</span></span> <span data-ttu-id="bfc17-165">Bu değeri değerine ayarlamaya eşdeğerdir `0` .</span><span class="sxs-lookup"><span data-stu-id="bfc17-165">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="bfc17-166">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="bfc17-166">Setting name</span></span> | <span data-ttu-id="bfc17-167">Değerler</span><span class="sxs-lookup"><span data-stu-id="bfc17-167">Values</span></span> |
| - | - | - |
| <span data-ttu-id="bfc17-168">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="bfc17-168">**runtimeconfig.json**</span></span> | <span data-ttu-id="bfc17-169">Yok</span><span class="sxs-lookup"><span data-stu-id="bfc17-169">N/A</span></span> | <span data-ttu-id="bfc17-170">Yok</span><span class="sxs-lookup"><span data-stu-id="bfc17-170">N/A</span></span> |
| <span data-ttu-id="bfc17-171">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="bfc17-171">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="bfc17-172">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="bfc17-172">`0` - disabled</span></span><br/><span data-ttu-id="bfc17-173">`1`-etkin</span><span class="sxs-lookup"><span data-stu-id="bfc17-173">`1` - enabled</span></span> |

> [!NOTE]
> <span data-ttu-id="bfc17-174">[COMPlus_PerfMapEnabled](#write-perf-map) atlanırsa veya `0` (devre dışı) olarak ayarlandıysa bu ayar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="bfc17-174">This setting is ignored if [COMPlus_PerfMapEnabled](#write-perf-map) is omitted or set to `0` (that is, disabled).</span></span>
