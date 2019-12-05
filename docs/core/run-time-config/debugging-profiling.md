---
title: Profil oluşturma yapılandırması ayarları hata ayıklaması
description: .NET Core uygulamaları için hata ayıklamayı ve profil oluşturmayı yapılandıran çalışma zamanı ayarları hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802801"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="a973d-103">Hata ayıklama ve profil oluşturma için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="a973d-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="a973d-104">Tanılamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="a973d-104">Enable diagnostics</span></span>

- <span data-ttu-id="a973d-105">Hata ayıklayıcı, profil oluşturucu ve EventPipe tanılamaları 'nın etkin veya devre dışı olup olmadığını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a973d-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="a973d-106">Varsayılan: etkin (`1`).</span><span class="sxs-lookup"><span data-stu-id="a973d-106">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="a973d-107">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="a973d-107">Setting name</span></span> | <span data-ttu-id="a973d-108">Değerler</span><span class="sxs-lookup"><span data-stu-id="a973d-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a973d-109">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a973d-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="a973d-110">YOK</span><span class="sxs-lookup"><span data-stu-id="a973d-110">N/A</span></span> | <span data-ttu-id="a973d-111">YOK</span><span class="sxs-lookup"><span data-stu-id="a973d-111">N/A</span></span> |
| <span data-ttu-id="a973d-112">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="a973d-112">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="a973d-113">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="a973d-113">`1` - enabled</span></span><br/><span data-ttu-id="a973d-114">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="a973d-114">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="a973d-115">Profil oluşturmayı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="a973d-115">Enable profiling</span></span>

- <span data-ttu-id="a973d-116">, Çalışmakta olan işlem için profil oluşturmanın etkinleştirilip etkinleştirilmeyeceğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a973d-116">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="a973d-117">Varsayılan: devre dışı (`0`).</span><span class="sxs-lookup"><span data-stu-id="a973d-117">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="a973d-118">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="a973d-118">Setting name</span></span> | <span data-ttu-id="a973d-119">Değerler</span><span class="sxs-lookup"><span data-stu-id="a973d-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a973d-120">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a973d-120">**runtimeconfig.json**</span></span> | <span data-ttu-id="a973d-121">YOK</span><span class="sxs-lookup"><span data-stu-id="a973d-121">N/A</span></span> | <span data-ttu-id="a973d-122">YOK</span><span class="sxs-lookup"><span data-stu-id="a973d-122">N/A</span></span> |
| <span data-ttu-id="a973d-123">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="a973d-123">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="a973d-124">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="a973d-124">`0` - disabled</span></span><br/><span data-ttu-id="a973d-125">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="a973d-125">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="a973d-126">Profil Oluşturucu GUID 'SI</span><span class="sxs-lookup"><span data-stu-id="a973d-126">Profiler GUID</span></span>

- <span data-ttu-id="a973d-127">O anda çalışan işleme yüklenecek profil oluşturucunun GUID 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a973d-127">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="a973d-128">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="a973d-128">Setting name</span></span> | <span data-ttu-id="a973d-129">Değerler</span><span class="sxs-lookup"><span data-stu-id="a973d-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a973d-130">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a973d-130">**runtimeconfig.json**</span></span> | <span data-ttu-id="a973d-131">YOK</span><span class="sxs-lookup"><span data-stu-id="a973d-131">N/A</span></span> | <span data-ttu-id="a973d-132">YOK</span><span class="sxs-lookup"><span data-stu-id="a973d-132">N/A</span></span> |
| <span data-ttu-id="a973d-133">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="a973d-133">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="a973d-134">*dize-GUID*</span><span class="sxs-lookup"><span data-stu-id="a973d-134">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="a973d-135">Profil Oluşturucu konumu</span><span class="sxs-lookup"><span data-stu-id="a973d-135">Profiler location</span></span>

- <span data-ttu-id="a973d-136">Şu anda çalışan işleme (veya 32-bit veya 64 bit işlem) yüklenecek profil oluşturucu DLL dosyasının yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a973d-136">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="a973d-137">Birden fazla değişken ayarlandıysa, bit genişliğine özgü değişkenler öncelik kazanır.</span><span class="sxs-lookup"><span data-stu-id="a973d-137">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="a973d-138">Profil oluşturucunun hangi bit hale getirinin yükleneceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="a973d-138">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="a973d-139">Daha fazla bilgi için bkz. [Profil Oluşturucu kitaplığını bulma](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span><span class="sxs-lookup"><span data-stu-id="a973d-139">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="a973d-140">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="a973d-140">Setting name</span></span> | <span data-ttu-id="a973d-141">Değerler</span><span class="sxs-lookup"><span data-stu-id="a973d-141">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a973d-142">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="a973d-142">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="a973d-143">*dize yolu*</span><span class="sxs-lookup"><span data-stu-id="a973d-143">*string-path*</span></span> |
| <span data-ttu-id="a973d-144">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="a973d-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="a973d-145">*dize yolu*</span><span class="sxs-lookup"><span data-stu-id="a973d-145">*string-path*</span></span> |
| <span data-ttu-id="a973d-146">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="a973d-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="a973d-147">*dize yolu*</span><span class="sxs-lookup"><span data-stu-id="a973d-147">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="a973d-148">Perf haritasını yaz</span><span class="sxs-lookup"><span data-stu-id="a973d-148">Write perf map</span></span>

- <span data-ttu-id="a973d-149">Linux sistemlerinde */t MP/perf-$pid. Map* yazma veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="a973d-149">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="a973d-150">Varsayılan: devre dışı (`0`).</span><span class="sxs-lookup"><span data-stu-id="a973d-150">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="a973d-151">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="a973d-151">Setting name</span></span> | <span data-ttu-id="a973d-152">Değerler</span><span class="sxs-lookup"><span data-stu-id="a973d-152">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a973d-153">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a973d-153">**runtimeconfig.json**</span></span> | <span data-ttu-id="a973d-154">YOK</span><span class="sxs-lookup"><span data-stu-id="a973d-154">N/A</span></span> | <span data-ttu-id="a973d-155">YOK</span><span class="sxs-lookup"><span data-stu-id="a973d-155">N/A</span></span> |
| <span data-ttu-id="a973d-156">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="a973d-156">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="a973d-157">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="a973d-157">`0` - disabled</span></span><br/><span data-ttu-id="a973d-158">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="a973d-158">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="a973d-159">Performans günlüğü işaretçileri</span><span class="sxs-lookup"><span data-stu-id="a973d-159">Perf log markers</span></span>

- <span data-ttu-id="a973d-160">`COMPlus_PerfMapEnabled` `1`olarak ayarlandığında, belirtilen sinyalin performans günlüklerinde işaret olarak kabul edilip yoksayılmasını sağlar veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="a973d-160">When `COMPlus_PerfMapEnabled` is set to `1`, enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="a973d-161">Varsayılan: devre dışı (`0`).</span><span class="sxs-lookup"><span data-stu-id="a973d-161">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="a973d-162">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="a973d-162">Setting name</span></span> | <span data-ttu-id="a973d-163">Değerler</span><span class="sxs-lookup"><span data-stu-id="a973d-163">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a973d-164">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a973d-164">**runtimeconfig.json**</span></span> | <span data-ttu-id="a973d-165">YOK</span><span class="sxs-lookup"><span data-stu-id="a973d-165">N/A</span></span> | <span data-ttu-id="a973d-166">YOK</span><span class="sxs-lookup"><span data-stu-id="a973d-166">N/A</span></span> |
| <span data-ttu-id="a973d-167">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="a973d-167">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="a973d-168">`0`-devre dışı</span><span class="sxs-lookup"><span data-stu-id="a973d-168">`0` - disabled</span></span><br/><span data-ttu-id="a973d-169">`1` etkin</span><span class="sxs-lookup"><span data-stu-id="a973d-169">`1` - enabled</span></span> |
