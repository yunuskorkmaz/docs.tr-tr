---
title: Temel sınıf kitaplığı bölünmesi değişiklikleri
description: Çekirdek .NET kitaplıklarında son değişiklikleri listeler.
ms.date: 07/27/2020
ms.openlocfilehash: 35192ae078c6025b9b399d6638ea8b4f426aceda
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332945"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="5f2f8-103">Çekirdek .NET kitaplıklarının parçalara bölünmesi</span><span class="sxs-lookup"><span data-stu-id="5f2f8-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="5f2f8-104">Çekirdek .NET kitaplıkları, .NET Core tarafından kullanılan temel ve diğer genel türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f2f8-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="5f2f8-105">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="5f2f8-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="5f2f8-106">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="5f2f8-106">Breaking change</span></span> | <span data-ttu-id="5f2f8-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f2f8-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="5f2f8-108">Varsayılan olmayan tanılama kimlikleri ile API kullanımdan kaldırılmaları</span><span class="sxs-lookup"><span data-stu-id="5f2f8-108">API obsoletions with non-default diagnostic IDs</span></span>](#api-obsoletions-with-non-default-diagnostic-ids) | <span data-ttu-id="5f2f8-109">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-109">5.0</span></span> |
| [<span data-ttu-id="5f2f8-110">FrameworkDescription 'un değeri .NET Core yerine .NET</span><span class="sxs-lookup"><span data-stu-id="5f2f8-110">FrameworkDescription's value is .NET instead of .NET Core</span></span>](#frameworkdescriptions-value-is-net-instead-of-net-core) | <span data-ttu-id="5f2f8-111">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-111">5.0</span></span> |
| [<span data-ttu-id="5f2f8-112">Tek dosya yayımlama biçimi için derlemeden ilgili API davranışı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="5f2f8-112">Assembly-related API behavior changes for single-file publishing format</span></span>](#assembly-related-api-behavior-changes-for-single-file-publishing-format) | <span data-ttu-id="5f2f8-113">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-113">5.0</span></span> |
| [<span data-ttu-id="5f2f8-114">Etkinlik içindeki etiketlerin sırası. Etiketler tersine çevrilir</span><span class="sxs-lookup"><span data-stu-id="5f2f8-114">Order of tags in Activity.Tags is reversed</span></span>](#order-of-tags-in-activitytags-is-reversed) | <span data-ttu-id="5f2f8-115">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-115">5.0</span></span> |
| [<span data-ttu-id="5f2f8-116">RC1 'de parametre adları değişti</span><span class="sxs-lookup"><span data-stu-id="5f2f8-116">Parameter names changed in RC1</span></span>](#parameter-names-changed-in-rc1) | <span data-ttu-id="5f2f8-117">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-117">5.0</span></span> |
| [<span data-ttu-id="5f2f8-118">OSPlatform öznitelikleri yeniden adlandırıldı veya kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="5f2f8-118">OSPlatform attributes renamed or removed</span></span>](#osplatform-attributes-renamed-or-removed) | <span data-ttu-id="5f2f8-119">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-119">5.0</span></span> |
| [<span data-ttu-id="5f2f8-120">Thread. Abort artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="5f2f8-120">Thread.Abort is obsolete</span></span>](#threadabort-is-obsolete) | <span data-ttu-id="5f2f8-121">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-121">5.0</span></span> |
| [<span data-ttu-id="5f2f8-122">ConsoleLoggerOptions üzerinde kullanımdan kalkmış Özellikler</span><span class="sxs-lookup"><span data-stu-id="5f2f8-122">Obsolete properties on ConsoleLoggerOptions</span></span>](#obsolete-properties-on-consoleloggeroptions) | <span data-ttu-id="5f2f8-123">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-123">5.0</span></span> |
| [<span data-ttu-id="5f2f8-124">Donanım iç tarafından desteklenen denetimler iç içe türler için farklılık gösterebilir</span><span class="sxs-lookup"><span data-stu-id="5f2f8-124">Hardware intrinsic IsSupported checks may differ for nested types</span></span>](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | <span data-ttu-id="5f2f8-125">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-125">5.0</span></span> |
| [<span data-ttu-id="5f2f8-126">Başvuru derlemelerindeki parametre adları değiştirildi</span><span class="sxs-lookup"><span data-stu-id="5f2f8-126">Parameter names changed in reference assemblies</span></span>](#parameter-names-changed-in-reference-assemblies) | <span data-ttu-id="5f2f8-127">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-127">5.0</span></span> |
| [<span data-ttu-id="5f2f8-128">ASCII olmayan karakterler içeren URI yolları UNIX üzerinde doğru şekilde ayrıştırır</span><span class="sxs-lookup"><span data-stu-id="5f2f8-128">URI paths with non-ASCII characters parse correctly on Unix</span></span>](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | <span data-ttu-id="5f2f8-129">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-129">5.0</span></span> |
| [<span data-ttu-id="5f2f8-130">UNIX üzerinde UNC yollarının URI tanıması</span><span class="sxs-lookup"><span data-stu-id="5f2f8-130">Uri recognition of UNC paths on Unix</span></span>](#uri-recognition-of-unc-paths-on-unix) | <span data-ttu-id="5f2f8-131">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-131">5.0</span></span> |
| [<span data-ttu-id="5f2f8-132">Environment. OSVersion doğru işletim sistemi sürümünü döndürür</span><span class="sxs-lookup"><span data-stu-id="5f2f8-132">Environment.OSVersion returns the correct operating system version</span></span>](#environmentosversion-returns-the-correct-operating-system-version) | <span data-ttu-id="5f2f8-133">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-133">5.0</span></span> |
| [<span data-ttu-id="5f2f8-134">LINQ OrderBy 'in karmaşıklığı. Ilk {OrDefault} artırılmış</span><span class="sxs-lookup"><span data-stu-id="5f2f8-134">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>](#complexity-of-linq-orderbyfirstordefault-increased) | <span data-ttu-id="5f2f8-135">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-135">5.0</span></span> |
| [<span data-ttu-id="5f2f8-136">IntPtr ve UIntPtr IFormattable 'ı uygular</span><span class="sxs-lookup"><span data-stu-id="5f2f8-136">IntPtr and UIntPtr implement IFormattable</span></span>](#intptr-and-uintptr-implement-iformattable) | <span data-ttu-id="5f2f8-137">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-137">5.0</span></span> |
| [<span data-ttu-id="5f2f8-138">PrincipalPermissionAttribute hata olarak kullanımdan kalktı</span><span class="sxs-lookup"><span data-stu-id="5f2f8-138">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="5f2f8-139">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-139">5.0</span></span> |
| [<span data-ttu-id="5f2f8-140">BinaryFormatter serileştirme yöntemleri artık kullanılmıyor ve ASP.NET uygulamalarında yasaklanmış</span><span class="sxs-lookup"><span data-stu-id="5f2f8-140">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="5f2f8-141">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-141">5.0</span></span> |
| [<span data-ttu-id="5f2f8-142">UTF-7 kod yolları artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="5f2f8-142">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="5f2f8-143">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-143">5.0</span></span> |
| [<span data-ttu-id="5f2f8-144">Vektör, \<T> Desteklenmeyen türler için her zaman NotSupportedException oluşturur</span><span class="sxs-lookup"><span data-stu-id="5f2f8-144">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="5f2f8-145">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-145">5.0</span></span> |
| [<span data-ttu-id="5f2f8-146">Varsayılan Activityıdformat W3C</span><span class="sxs-lookup"><span data-stu-id="5f2f8-146">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="5f2f8-147">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-147">5.0</span></span> |
| [<span data-ttu-id="5f2f8-148">Vector2. Lerp ve Vector4. Lerp için davranış değişikliği</span><span class="sxs-lookup"><span data-stu-id="5f2f8-148">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="5f2f8-149">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-149">5.0</span></span> |
| [<span data-ttu-id="5f2f8-150">SSE ve SSE2 CompareGreaterThan yöntemleri NaN girdilerini doğru bir şekilde işler</span><span class="sxs-lookup"><span data-stu-id="5f2f8-150">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="5f2f8-151">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-151">5.0</span></span> |
| [<span data-ttu-id="5f2f8-152">CounterSet. CreateCounterSetInstance şimdi örnek zaten varsa InvalidOperationException oluşturur</span><span class="sxs-lookup"><span data-stu-id="5f2f8-152">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="5f2f8-153">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-153">5.0</span></span> |
| [<span data-ttu-id="5f2f8-154">Microsoft. DotNet. PlatformAbstractions paketi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="5f2f8-154">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="5f2f8-155">5.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-155">5.0</span></span> |
| [<span data-ttu-id="5f2f8-156">Sürümü şimdi rapor eden API 'Ler rapor ürünü ve dosya sürümü değil</span><span class="sxs-lookup"><span data-stu-id="5f2f8-156">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="5f2f8-157">3.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-157">3.0</span></span> |
| [<span data-ttu-id="5f2f8-158">Özel EncoderFallbackBuffer örnekleri özyinelemeli olarak geri dönemez</span><span class="sxs-lookup"><span data-stu-id="5f2f8-158">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="5f2f8-159">3.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-159">3.0</span></span> |
| [<span data-ttu-id="5f2f8-160">Kayan nokta biçimlendirme ve ayrıştırma davranışı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="5f2f8-160">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="5f2f8-161">3.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-161">3.0</span></span> |
| [<span data-ttu-id="5f2f8-162">Kayan nokta ayrıştırma işlemleri artık başarısız olmaz veya bir OverflowException oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="5f2f8-162">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="5f2f8-163">3.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-163">3.0</span></span> |
| [<span data-ttu-id="5f2f8-164">InvalidAsynchronousStateException başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="5f2f8-164">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="5f2f8-165">3.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-165">3.0</span></span> |
| [<span data-ttu-id="5f2f8-166">Hatalı biçimlendirilmiş UTF-8 bayt dizilerini değiştirme Unicode yönergelerine uyar</span><span class="sxs-lookup"><span data-stu-id="5f2f8-166">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="5f2f8-167">3.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-167">3.0</span></span> |
| [<span data-ttu-id="5f2f8-168">TypeDescriptionProviderAttribute başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="5f2f8-168">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="5f2f8-169">3.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-169">3.0</span></span> |
| [<span data-ttu-id="5f2f8-170">ZipArchiveEntry artık tutarsız giriş boyutlarına sahip arşivleri işliyor</span><span class="sxs-lookup"><span data-stu-id="5f2f8-170">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="5f2f8-171">3.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-171">3.0</span></span> |
| [<span data-ttu-id="5f2f8-172">FieldInfo. SetValue statik, yalnızca init alanları için özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="5f2f8-172">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="5f2f8-173">3.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-173">3.0</span></span> |
| [<span data-ttu-id="5f2f8-174">Yerleşik yapı türlerine eklenen özel alanlar</span><span class="sxs-lookup"><span data-stu-id="5f2f8-174">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="5f2f8-175">2.1</span><span class="sxs-lookup"><span data-stu-id="5f2f8-175">2.1</span></span> |
| [<span data-ttu-id="5f2f8-176">UseShellExecute varsayılan değerindeki değişiklik</span><span class="sxs-lookup"><span data-stu-id="5f2f8-176">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="5f2f8-177">2.1</span><span class="sxs-lookup"><span data-stu-id="5f2f8-177">2.1</span></span> |
| [<span data-ttu-id="5f2f8-178">MacOS üzerinde OpenSSL sürümleri</span><span class="sxs-lookup"><span data-stu-id="5f2f8-178">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="5f2f8-179">2.1</span><span class="sxs-lookup"><span data-stu-id="5f2f8-179">2.1</span></span> |
| [<span data-ttu-id="5f2f8-180">Fılesystemınfo. Attributes tarafından oluşturulan UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="5f2f8-180">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="5f2f8-181">1.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-181">1.0</span></span> |
| [<span data-ttu-id="5f2f8-182">Bozuk işlem durumu özel durumlarını işleme desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="5f2f8-182">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="5f2f8-183">1.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-183">1.0</span></span> |
| [<span data-ttu-id="5f2f8-184">UriBuilder özellikleri artık önde gelen karakterlerin önüne alınmaz</span><span class="sxs-lookup"><span data-stu-id="5f2f8-184">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="5f2f8-185">1.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-185">1.0</span></span> |
| [<span data-ttu-id="5f2f8-186">Process. StartInfo, başlatmadığınız işlemler için InvalidOperationException 'yi oluşturur</span><span class="sxs-lookup"><span data-stu-id="5f2f8-186">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="5f2f8-187">1.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-187">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="5f2f8-188">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-188">.NET 5.0</span></span>

[!INCLUDE [obsolete-apis-with-custom-diagnostics](../../../includes/core-changes/corefx/5.0/obsolete-apis-with-custom-diagnostics.md)]

***

[!INCLUDE [frameworkdescription-returns-net-not-net-core](../../../includes/core-changes/corefx/5.0/frameworkdescription-returns-net-not-net-core.md)]

<span data-ttu-id="5f2f8-189">\*\*_</span><span class="sxs-lookup"><span data-stu-id="5f2f8-189">\*\*_</span></span>

[!INCLUDE [assembly-api-behavior-changes-for-single-file-publish](../../../includes/core-changes/corefx/5.0/assembly-api-behavior-changes-for-single-file-publish.md)]

_*_

[!INCLUDE [reverse-order-of-tags-in-activity-property](../../../includes/core-changes/corefx/5.0/reverse-order-of-tags-in-activity-property.md)]

_*_

[!INCLUDE [reference-assembly-parameter-names-rc1](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names-rc1.md)]

_*_

[!INCLUDE [os-platform-attributes-renamed](../../../includes/core-changes/corefx/5.0/os-platform-attributes-renamed.md)]

_*_

[!INCLUDE [thread-abort-obsolete](../../../includes/core-changes/corefx/5.0/thread-abort-obsolete.md)]

_*_

[!INCLUDE [obsolete-consoleloggeroptions-properties](../../../includes/core-changes/corefx/5.0/obsolete-consoleloggeroptions-properties.md)]

_*_

[!INCLUDE [hardware-instrinsics-issupported-checks](../../../includes/core-changes/corefx/5.0/hardware-instrinsics-issupported-checks.md)]

_*_

[!INCLUDE [reference-assembly-parameter-names](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names.md)]

_*_

[!INCLUDE [non-ascii-chars-in-uri-parsed-correctly](../../../includes/core-changes/corefx/5.0/non-ascii-chars-in-uri-parsed-correctly.md)]

_*_

[!INCLUDE [unc-path-recognition-unix](../../../includes/core-changes/corefx/5.0/unc-path-recognition-unix.md)]

_*_

[!INCLUDE [environment-osversion-returns-correct-version](../../../includes/core-changes/corefx/5.0/environment-osversion-returns-correct-version.md)]

_*_

[!INCLUDE [orderby-firstordefault-complexity-increase](../../../includes/core-changes/corefx/5.0/orderby-firstordefault-complexity-increase.md)]

_*_

[!INCLUDE [intptr-uintptr-implement-iformattable](../../../includes/core-changes/corefx/5.0/intptr-uintptr-implement-iformattable.md)]

_*_

[!INCLUDE [principalpermissionattribute-obsolete](../../../includes/core-changes/corefx/5.0/principalpermissionattribute-obsolete.md)]

_*_

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

_*_

[!INCLUDE [utf-7-code-paths-obsolete](../../../includes/core-changes/corefx/5.0/utf-7-code-paths-obsolete.md)]

_*_

[!INCLUDE [vectort-throws-notsupportedexception](../../../includes/core-changes/corefx/5.0/vectort-throws-notsupportedexception.md)]

_*_

[!INCLUDE [default-activityidformat-changed](../../../includes/core-changes/corefx/5.0/default-activityidformat-changed.md)]

_*_

[!INCLUDE [vector-lerp-behavior-change](../../../includes/core-changes/corefx/5.0/vector-lerp-behavior-change.md)]

_*_

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

_*_

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

_*_

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

_*_

## <a name="net-core-30"></a><span data-ttu-id="5f2f8-190">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-190">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

_*_

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

_*_

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

_*_

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

_*_

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

_*_

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

_*_

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

_*_

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

_*_

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

_*_

## <a name="net-core-21"></a><span data-ttu-id="5f2f8-191">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5f2f8-191">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

_*_

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

_*_

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

_*_

## <a name="net-core-10"></a><span data-ttu-id="5f2f8-192">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="5f2f8-192">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

_*_

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

_*_

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

_*_

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

<span data-ttu-id="5f2f8-193">_\*\*</span><span class="sxs-lookup"><span data-stu-id="5f2f8-193">_\*\*</span></span>
