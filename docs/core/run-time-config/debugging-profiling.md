---
title: Profil oluşturma config ayarlarını hata ayıklama
description: .NET Core uygulamaları için hata ayıklama ve profil oluşturmayı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802801"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="aa295-103">Hata ayıklama ve profil oluşturma için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="aa295-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="aa295-104">Tanılamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="aa295-104">Enable diagnostics</span></span>

- <span data-ttu-id="aa295-105">Hata ayıklayıcının, profil oluşturucunun ve EventPipe tanılamanın etkin mi yoksa devre dışı mı olduğunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="aa295-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="aa295-106">Varsayılan: Etkin`1`( ).</span><span class="sxs-lookup"><span data-stu-id="aa295-106">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="aa295-107">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="aa295-107">Setting name</span></span> | <span data-ttu-id="aa295-108">Değerler</span><span class="sxs-lookup"><span data-stu-id="aa295-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="aa295-109">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="aa295-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="aa295-110">Yok</span><span class="sxs-lookup"><span data-stu-id="aa295-110">N/A</span></span> | <span data-ttu-id="aa295-111">Yok</span><span class="sxs-lookup"><span data-stu-id="aa295-111">N/A</span></span> |
| <span data-ttu-id="aa295-112">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="aa295-112">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="aa295-113">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="aa295-113">`1` - enabled</span></span><br/><span data-ttu-id="aa295-114">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="aa295-114">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="aa295-115">Profil oluşturmayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="aa295-115">Enable profiling</span></span>

- <span data-ttu-id="aa295-116">Şu anda çalışan işlem için profil oluşturmanın etkin olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="aa295-116">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="aa295-117">Varsayılan: Devre`0`Dışı ( ).</span><span class="sxs-lookup"><span data-stu-id="aa295-117">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="aa295-118">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="aa295-118">Setting name</span></span> | <span data-ttu-id="aa295-119">Değerler</span><span class="sxs-lookup"><span data-stu-id="aa295-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="aa295-120">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="aa295-120">**runtimeconfig.json**</span></span> | <span data-ttu-id="aa295-121">Yok</span><span class="sxs-lookup"><span data-stu-id="aa295-121">N/A</span></span> | <span data-ttu-id="aa295-122">Yok</span><span class="sxs-lookup"><span data-stu-id="aa295-122">N/A</span></span> |
| <span data-ttu-id="aa295-123">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="aa295-123">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="aa295-124">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="aa295-124">`0` - disabled</span></span><br/><span data-ttu-id="aa295-125">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="aa295-125">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="aa295-126">Profiler GUID</span><span class="sxs-lookup"><span data-stu-id="aa295-126">Profiler GUID</span></span>

- <span data-ttu-id="aa295-127">Şu anda çalışan işleme yüklemek için profiloluşturucu GUID belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa295-127">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="aa295-128">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="aa295-128">Setting name</span></span> | <span data-ttu-id="aa295-129">Değerler</span><span class="sxs-lookup"><span data-stu-id="aa295-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="aa295-130">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="aa295-130">**runtimeconfig.json**</span></span> | <span data-ttu-id="aa295-131">Yok</span><span class="sxs-lookup"><span data-stu-id="aa295-131">N/A</span></span> | <span data-ttu-id="aa295-132">Yok</span><span class="sxs-lookup"><span data-stu-id="aa295-132">N/A</span></span> |
| <span data-ttu-id="aa295-133">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="aa295-133">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="aa295-134">*dize kılavuz*</span><span class="sxs-lookup"><span data-stu-id="aa295-134">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="aa295-135">Profil oluşturucu konumu</span><span class="sxs-lookup"><span data-stu-id="aa295-135">Profiler location</span></span>

- <span data-ttu-id="aa295-136">Şu anda çalışan işleme (veya 32-bit veya 64-bit işlem) yüklemek için profil oluşturucu DLL için yol belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa295-136">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="aa295-137">Birden fazla değişken ayarlanmışsa, bitness'e özgü değişkenler önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="aa295-137">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="aa295-138">Profilleyicinin hangi bitliğini yükleyeceklerini belirtirler.</span><span class="sxs-lookup"><span data-stu-id="aa295-138">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="aa295-139">Daha fazla bilgi için profil [oluşturucu kitaplığını bulma'ya](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="aa295-139">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="aa295-140">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="aa295-140">Setting name</span></span> | <span data-ttu-id="aa295-141">Değerler</span><span class="sxs-lookup"><span data-stu-id="aa295-141">Values</span></span> |
| - | - | - |
| <span data-ttu-id="aa295-142">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="aa295-142">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="aa295-143">*string-yol*</span><span class="sxs-lookup"><span data-stu-id="aa295-143">*string-path*</span></span> |
| <span data-ttu-id="aa295-144">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="aa295-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="aa295-145">*string-yol*</span><span class="sxs-lookup"><span data-stu-id="aa295-145">*string-path*</span></span> |
| <span data-ttu-id="aa295-146">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="aa295-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="aa295-147">*string-yol*</span><span class="sxs-lookup"><span data-stu-id="aa295-147">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="aa295-148">Perf haritası yaz</span><span class="sxs-lookup"><span data-stu-id="aa295-148">Write perf map</span></span>

- <span data-ttu-id="aa295-149">Linux sistemlerinde */tmp/perf-$pid.map* yazmayı etkinleştirir veya devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="aa295-149">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="aa295-150">Varsayılan: Devre`0`Dışı ( ).</span><span class="sxs-lookup"><span data-stu-id="aa295-150">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="aa295-151">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="aa295-151">Setting name</span></span> | <span data-ttu-id="aa295-152">Değerler</span><span class="sxs-lookup"><span data-stu-id="aa295-152">Values</span></span> |
| - | - | - |
| <span data-ttu-id="aa295-153">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="aa295-153">**runtimeconfig.json**</span></span> | <span data-ttu-id="aa295-154">Yok</span><span class="sxs-lookup"><span data-stu-id="aa295-154">N/A</span></span> | <span data-ttu-id="aa295-155">Yok</span><span class="sxs-lookup"><span data-stu-id="aa295-155">N/A</span></span> |
| <span data-ttu-id="aa295-156">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="aa295-156">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="aa295-157">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="aa295-157">`0` - disabled</span></span><br/><span data-ttu-id="aa295-158">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="aa295-158">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="aa295-159">Perf günlük işaretleri</span><span class="sxs-lookup"><span data-stu-id="aa295-159">Perf log markers</span></span>

- <span data-ttu-id="aa295-160">`COMPlus_PerfMapEnabled` Perf `1`günlüklerinde işaretçi olarak kabul edilecek ve yoksayılacak belirtilen sinyali etkinleştirir veya devre dışı eder.</span><span class="sxs-lookup"><span data-stu-id="aa295-160">When `COMPlus_PerfMapEnabled` is set to `1`, enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="aa295-161">Varsayılan: Devre`0`Dışı ( ).</span><span class="sxs-lookup"><span data-stu-id="aa295-161">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="aa295-162">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="aa295-162">Setting name</span></span> | <span data-ttu-id="aa295-163">Değerler</span><span class="sxs-lookup"><span data-stu-id="aa295-163">Values</span></span> |
| - | - | - |
| <span data-ttu-id="aa295-164">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="aa295-164">**runtimeconfig.json**</span></span> | <span data-ttu-id="aa295-165">Yok</span><span class="sxs-lookup"><span data-stu-id="aa295-165">N/A</span></span> | <span data-ttu-id="aa295-166">Yok</span><span class="sxs-lookup"><span data-stu-id="aa295-166">N/A</span></span> |
| <span data-ttu-id="aa295-167">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="aa295-167">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="aa295-168">`0`- engelli</span><span class="sxs-lookup"><span data-stu-id="aa295-168">`0` - disabled</span></span><br/><span data-ttu-id="aa295-169">`1`- etkin</span><span class="sxs-lookup"><span data-stu-id="aa295-169">`1` - enabled</span></span> |
