---
title: Temel sınıf kitaplığı bölünmesi değişiklikleri
description: Çekirdek .NET kitaplıklarında son değişiklikleri listeler.
ms.date: 07/27/2020
ms.openlocfilehash: c3207ac7630d794f77c793cc6d1d52e158c0c084
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738833"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="0e12a-103">Çekirdek .NET kitaplıklarının parçalara bölünmesi</span><span class="sxs-lookup"><span data-stu-id="0e12a-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="0e12a-104">Çekirdek .NET kitaplıkları, .NET Core tarafından kullanılan temel ve diğer genel türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e12a-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="0e12a-105">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="0e12a-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="0e12a-106">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="0e12a-106">Breaking change</span></span> | <span data-ttu-id="0e12a-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="0e12a-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="0e12a-108">RC1 'de parametre adları değişti</span><span class="sxs-lookup"><span data-stu-id="0e12a-108">Parameter names changed in RC1</span></span>](#parameter-names-changed-in-rc1) | <span data-ttu-id="0e12a-109">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-109">5.0</span></span> |
| [<span data-ttu-id="0e12a-110">OSPlatform öznitelikleri yeniden adlandırıldı veya kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="0e12a-110">OSPlatform attributes renamed or removed</span></span>](#osplatform-attributes-renamed-or-removed) | <span data-ttu-id="0e12a-111">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-111">5.0</span></span> |
| [<span data-ttu-id="0e12a-112">Thread. Abort artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="0e12a-112">Thread.Abort is obsolete</span></span>](#threadabort-is-obsolete) | <span data-ttu-id="0e12a-113">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-113">5.0</span></span> |
| [<span data-ttu-id="0e12a-114">ConsoleLoggerOptions üzerinde kullanımdan kalkmış Özellikler</span><span class="sxs-lookup"><span data-stu-id="0e12a-114">Obsolete properties on ConsoleLoggerOptions</span></span>](#obsolete-properties-on-consoleloggeroptions) | <span data-ttu-id="0e12a-115">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-115">5.0</span></span> |
| [<span data-ttu-id="0e12a-116">Donanım iç tarafından desteklenen denetimler iç içe türler için farklılık gösterebilir</span><span class="sxs-lookup"><span data-stu-id="0e12a-116">Hardware intrinsic IsSupported checks may differ for nested types</span></span>](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | <span data-ttu-id="0e12a-117">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-117">5.0</span></span> |
| [<span data-ttu-id="0e12a-118">Başvuru derlemelerindeki parametre adları değiştirildi</span><span class="sxs-lookup"><span data-stu-id="0e12a-118">Parameter names changed in reference assemblies</span></span>](#parameter-names-changed-in-reference-assemblies) | <span data-ttu-id="0e12a-119">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-119">5.0</span></span> |
| [<span data-ttu-id="0e12a-120">ASCII olmayan karakterler içeren URI yolları UNIX üzerinde doğru şekilde ayrıştırır</span><span class="sxs-lookup"><span data-stu-id="0e12a-120">URI paths with non-ASCII characters parse correctly on Unix</span></span>](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | <span data-ttu-id="0e12a-121">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-121">5.0</span></span> |
| [<span data-ttu-id="0e12a-122">UNIX üzerinde UNC yollarının URI tanıması</span><span class="sxs-lookup"><span data-stu-id="0e12a-122">Uri recognition of UNC paths on Unix</span></span>](#uri-recognition-of-unc-paths-on-unix) | <span data-ttu-id="0e12a-123">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-123">5.0</span></span> |
| [<span data-ttu-id="0e12a-124">Environment. OSVersion doğru işletim sistemi sürümünü döndürür</span><span class="sxs-lookup"><span data-stu-id="0e12a-124">Environment.OSVersion returns the correct operating system version</span></span>](#environmentosversion-returns-the-correct-operating-system-version) | <span data-ttu-id="0e12a-125">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-125">5.0</span></span> |
| [<span data-ttu-id="0e12a-126">LINQ OrderBy 'in karmaşıklığı. Ilk {OrDefault} artırılmış</span><span class="sxs-lookup"><span data-stu-id="0e12a-126">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>](#complexity-of-linq-orderbyfirstordefault-increased) | <span data-ttu-id="0e12a-127">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-127">5.0</span></span> |
| [<span data-ttu-id="0e12a-128">IntPtr ve UIntPtr IFormattable 'ı uygular</span><span class="sxs-lookup"><span data-stu-id="0e12a-128">IntPtr and UIntPtr implement IFormattable</span></span>](#intptr-and-uintptr-implement-iformattable) | <span data-ttu-id="0e12a-129">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-129">5.0</span></span> |
| [<span data-ttu-id="0e12a-130">PrincipalPermissionAttribute hata olarak kullanımdan kalktı</span><span class="sxs-lookup"><span data-stu-id="0e12a-130">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="0e12a-131">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-131">5.0</span></span> |
| [<span data-ttu-id="0e12a-132">BinaryFormatter serileştirme yöntemleri artık kullanılmıyor ve ASP.NET uygulamalarında yasaklanmış</span><span class="sxs-lookup"><span data-stu-id="0e12a-132">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="0e12a-133">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-133">5.0</span></span> |
| [<span data-ttu-id="0e12a-134">UTF-7 kod yolları artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="0e12a-134">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="0e12a-135">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-135">5.0</span></span> |
| [<span data-ttu-id="0e12a-136">Vektör, \<T> Desteklenmeyen türler için her zaman NotSupportedException oluşturur</span><span class="sxs-lookup"><span data-stu-id="0e12a-136">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="0e12a-137">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-137">5.0</span></span> |
| [<span data-ttu-id="0e12a-138">Varsayılan Activityıdformat W3C</span><span class="sxs-lookup"><span data-stu-id="0e12a-138">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="0e12a-139">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-139">5.0</span></span> |
| [<span data-ttu-id="0e12a-140">Vector2. Lerp ve Vector4. Lerp için davranış değişikliği</span><span class="sxs-lookup"><span data-stu-id="0e12a-140">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="0e12a-141">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-141">5.0</span></span> |
| [<span data-ttu-id="0e12a-142">SSE ve SSE2 CompareGreaterThan yöntemleri NaN girdilerini doğru bir şekilde işler</span><span class="sxs-lookup"><span data-stu-id="0e12a-142">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="0e12a-143">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-143">5.0</span></span> |
| [<span data-ttu-id="0e12a-144">CounterSet. CreateCounterSetInstance şimdi örnek zaten varsa InvalidOperationException oluşturur</span><span class="sxs-lookup"><span data-stu-id="0e12a-144">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="0e12a-145">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-145">5.0</span></span> |
| [<span data-ttu-id="0e12a-146">Microsoft. DotNet. PlatformAbstractions paketi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="0e12a-146">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="0e12a-147">5.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-147">5.0</span></span> |
| [<span data-ttu-id="0e12a-148">Sürümü şimdi rapor eden API 'Ler rapor ürünü ve dosya sürümü değil</span><span class="sxs-lookup"><span data-stu-id="0e12a-148">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="0e12a-149">3.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-149">3.0</span></span> |
| [<span data-ttu-id="0e12a-150">Özel EncoderFallbackBuffer örnekleri özyinelemeli olarak geri dönemez</span><span class="sxs-lookup"><span data-stu-id="0e12a-150">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="0e12a-151">3.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-151">3.0</span></span> |
| [<span data-ttu-id="0e12a-152">Kayan nokta biçimlendirme ve ayrıştırma davranışı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="0e12a-152">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="0e12a-153">3.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-153">3.0</span></span> |
| [<span data-ttu-id="0e12a-154">Kayan nokta ayrıştırma işlemleri artık başarısız olmaz veya bir OverflowException oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="0e12a-154">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="0e12a-155">3.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-155">3.0</span></span> |
| [<span data-ttu-id="0e12a-156">InvalidAsynchronousStateException başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="0e12a-156">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="0e12a-157">3.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-157">3.0</span></span> |
| [<span data-ttu-id="0e12a-158">Hatalı biçimlendirilmiş UTF-8 bayt dizilerini değiştirme Unicode yönergelerine uyar</span><span class="sxs-lookup"><span data-stu-id="0e12a-158">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="0e12a-159">3.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-159">3.0</span></span> |
| [<span data-ttu-id="0e12a-160">TypeDescriptionProviderAttribute başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="0e12a-160">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="0e12a-161">3.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-161">3.0</span></span> |
| [<span data-ttu-id="0e12a-162">ZipArchiveEntry artık tutarsız giriş boyutlarına sahip arşivleri işliyor</span><span class="sxs-lookup"><span data-stu-id="0e12a-162">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="0e12a-163">3.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-163">3.0</span></span> |
| [<span data-ttu-id="0e12a-164">FieldInfo. SetValue statik, yalnızca init alanları için özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="0e12a-164">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="0e12a-165">3.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-165">3.0</span></span> |
| [<span data-ttu-id="0e12a-166">Yerleşik yapı türlerine eklenen özel alanlar</span><span class="sxs-lookup"><span data-stu-id="0e12a-166">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="0e12a-167">2.1</span><span class="sxs-lookup"><span data-stu-id="0e12a-167">2.1</span></span> |
| [<span data-ttu-id="0e12a-168">UseShellExecute varsayılan değerindeki değişiklik</span><span class="sxs-lookup"><span data-stu-id="0e12a-168">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="0e12a-169">2.1</span><span class="sxs-lookup"><span data-stu-id="0e12a-169">2.1</span></span> |
| [<span data-ttu-id="0e12a-170">MacOS üzerinde OpenSSL sürümleri</span><span class="sxs-lookup"><span data-stu-id="0e12a-170">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="0e12a-171">2.1</span><span class="sxs-lookup"><span data-stu-id="0e12a-171">2.1</span></span> |
| [<span data-ttu-id="0e12a-172">Fılesystemınfo. Attributes tarafından oluşturulan UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="0e12a-172">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="0e12a-173">1.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-173">1.0</span></span> |
| [<span data-ttu-id="0e12a-174">Bozuk işlem durumu özel durumlarını işleme desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="0e12a-174">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="0e12a-175">1.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-175">1.0</span></span> |
| [<span data-ttu-id="0e12a-176">UriBuilder özellikleri artık önde gelen karakterlerin önüne alınmaz</span><span class="sxs-lookup"><span data-stu-id="0e12a-176">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="0e12a-177">1.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-177">1.0</span></span> |
| [<span data-ttu-id="0e12a-178">Process. StartInfo, başlatmadığınız işlemler için InvalidOperationException 'yi oluşturur</span><span class="sxs-lookup"><span data-stu-id="0e12a-178">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="0e12a-179">1.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-179">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="0e12a-180">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="0e12a-180">.NET 5.0</span></span>

[!INCLUDE [reference-assembly-parameter-names-rc1](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names-rc1.md)]

***

[!INCLUDE [os-platform-attributes-renamed](../../../includes/core-changes/corefx/5.0/os-platform-attributes-renamed.md)]

***

[!INCLUDE [thread-abort-obsolete](../../../includes/core-changes/corefx/5.0/thread-abort-obsolete.md)]

***

[!INCLUDE [obsolete-consoleloggeroptions-properties](../../../includes/core-changes/corefx/5.0/obsolete-consoleloggeroptions-properties.md)]

***

[!INCLUDE [hardware-instrinsics-issupported-checks](../../../includes/core-changes/corefx/5.0/hardware-instrinsics-issupported-checks.md)]

***

[!INCLUDE [reference-assembly-parameter-names](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names.md)]

***

[!INCLUDE [non-ascii-chars-in-uri-parsed-correctly](../../../includes/core-changes/corefx/5.0/non-ascii-chars-in-uri-parsed-correctly.md)]

***

[!INCLUDE [unc-path-recognition-unix](../../../includes/core-changes/corefx/5.0/unc-path-recognition-unix.md)]

***

[!INCLUDE [environment-osversion-returns-correct-version](../../../includes/core-changes/corefx/5.0/environment-osversion-returns-correct-version.md)]

***

[!INCLUDE [orderby-firstordefault-complexity-increase](../../../includes/core-changes/corefx/5.0/orderby-firstordefault-complexity-increase.md)]

***

[!INCLUDE [intptr-uintptr-implement-iformattable](../../../includes/core-changes/corefx/5.0/intptr-uintptr-implement-iformattable.md)]

***

[!INCLUDE [principalpermissionattribute-obsolete](../../../includes/core-changes/corefx/5.0/principalpermissionattribute-obsolete.md)]

***

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

***

[!INCLUDE [utf-7-code-paths-obsolete](../../../includes/core-changes/corefx/5.0/utf-7-code-paths-obsolete.md)]

***

[!INCLUDE [vectort-throws-notsupportedexception](../../../includes/core-changes/corefx/5.0/vectort-throws-notsupportedexception.md)]

***

[!INCLUDE [default-activityidformat-changed](../../../includes/core-changes/corefx/5.0/default-activityidformat-changed.md)]

***

[!INCLUDE [vector-lerp-behavior-change](../../../includes/core-changes/corefx/5.0/vector-lerp-behavior-change.md)]

***

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

***

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="0e12a-181">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0e12a-181">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="0e12a-182">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0e12a-182">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="0e12a-183">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="0e12a-183">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
