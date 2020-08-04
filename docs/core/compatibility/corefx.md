---
title: Temel sınıf kitaplığı bölünmesi değişiklikleri
description: Çekirdek .NET kitaplıklarında son değişiklikleri listeler.
ms.date: 07/27/2020
ms.openlocfilehash: 558aa1d76831cd15e2028c17d2b0b2e82f64ef9a
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517339"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="22a05-103">Çekirdek .NET kitaplıklarının parçalara bölünmesi</span><span class="sxs-lookup"><span data-stu-id="22a05-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="22a05-104">Çekirdek .NET kitaplıkları, .NET Core tarafından kullanılan temel ve diğer genel türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="22a05-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="22a05-105">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="22a05-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="22a05-106">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="22a05-106">Breaking change</span></span> | <span data-ttu-id="22a05-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="22a05-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="22a05-108">BinaryFormatter serileştirme yöntemleri artık kullanılmıyor ve ASP.NET uygulamalarında yasaklanmış</span><span class="sxs-lookup"><span data-stu-id="22a05-108">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="22a05-109">5.0</span><span class="sxs-lookup"><span data-stu-id="22a05-109">5.0</span></span> |
| [<span data-ttu-id="22a05-110">UTF-7 kod yolları artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="22a05-110">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="22a05-111">5.0</span><span class="sxs-lookup"><span data-stu-id="22a05-111">5.0</span></span> |
| [<span data-ttu-id="22a05-112">Vektör, \<T> Desteklenmeyen türler için her zaman NotSupportedException oluşturur</span><span class="sxs-lookup"><span data-stu-id="22a05-112">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="22a05-113">5.0</span><span class="sxs-lookup"><span data-stu-id="22a05-113">5.0</span></span> |
| [<span data-ttu-id="22a05-114">Varsayılan Activityıdformat W3C</span><span class="sxs-lookup"><span data-stu-id="22a05-114">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="22a05-115">5.0</span><span class="sxs-lookup"><span data-stu-id="22a05-115">5.0</span></span> |
| [<span data-ttu-id="22a05-116">Vector2. Lerp ve Vector4. Lerp için davranış değişikliği</span><span class="sxs-lookup"><span data-stu-id="22a05-116">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="22a05-117">5.0</span><span class="sxs-lookup"><span data-stu-id="22a05-117">5.0</span></span> |
| [<span data-ttu-id="22a05-118">SSE ve SSE2 CompareGreaterThan yöntemleri NaN girdilerini doğru bir şekilde işler</span><span class="sxs-lookup"><span data-stu-id="22a05-118">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="22a05-119">5.0</span><span class="sxs-lookup"><span data-stu-id="22a05-119">5.0</span></span> |
| [<span data-ttu-id="22a05-120">CounterSet. CreateCounterSetInstance şimdi örnek zaten varsa InvalidOperationException oluşturur</span><span class="sxs-lookup"><span data-stu-id="22a05-120">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="22a05-121">5.0</span><span class="sxs-lookup"><span data-stu-id="22a05-121">5.0</span></span> |
| [<span data-ttu-id="22a05-122">Microsoft. DotNet. PlatformAbstractions paketi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="22a05-122">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="22a05-123">5.0</span><span class="sxs-lookup"><span data-stu-id="22a05-123">5.0</span></span> |
| [<span data-ttu-id="22a05-124">Sürümü şimdi rapor eden API 'Ler rapor ürünü ve dosya sürümü değil</span><span class="sxs-lookup"><span data-stu-id="22a05-124">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="22a05-125">3,0</span><span class="sxs-lookup"><span data-stu-id="22a05-125">3.0</span></span> |
| [<span data-ttu-id="22a05-126">Özel EncoderFallbackBuffer örnekleri özyinelemeli olarak geri dönemez</span><span class="sxs-lookup"><span data-stu-id="22a05-126">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="22a05-127">3,0</span><span class="sxs-lookup"><span data-stu-id="22a05-127">3.0</span></span> |
| [<span data-ttu-id="22a05-128">Kayan nokta biçimlendirme ve ayrıştırma davranışı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="22a05-128">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="22a05-129">3,0</span><span class="sxs-lookup"><span data-stu-id="22a05-129">3.0</span></span> |
| [<span data-ttu-id="22a05-130">Kayan nokta ayrıştırma işlemleri artık başarısız olmaz veya bir OverflowException oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="22a05-130">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="22a05-131">3,0</span><span class="sxs-lookup"><span data-stu-id="22a05-131">3.0</span></span> |
| [<span data-ttu-id="22a05-132">InvalidAsynchronousStateException başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="22a05-132">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="22a05-133">3,0</span><span class="sxs-lookup"><span data-stu-id="22a05-133">3.0</span></span> |
| [<span data-ttu-id="22a05-134">Hatalı biçimlendirilmiş UTF-8 bayt dizilerini değiştirme Unicode yönergelerine uyar</span><span class="sxs-lookup"><span data-stu-id="22a05-134">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="22a05-135">3,0</span><span class="sxs-lookup"><span data-stu-id="22a05-135">3.0</span></span> |
| [<span data-ttu-id="22a05-136">TypeDescriptionProviderAttribute başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="22a05-136">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="22a05-137">3,0</span><span class="sxs-lookup"><span data-stu-id="22a05-137">3.0</span></span> |
| [<span data-ttu-id="22a05-138">ZipArchiveEntry artık tutarsız giriş boyutlarına sahip arşivleri işliyor</span><span class="sxs-lookup"><span data-stu-id="22a05-138">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="22a05-139">3,0</span><span class="sxs-lookup"><span data-stu-id="22a05-139">3.0</span></span> |
| [<span data-ttu-id="22a05-140">Utf8JsonWriter içinde (String) null semantiğinin değiştirilmesi</span><span class="sxs-lookup"><span data-stu-id="22a05-140">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="22a05-141">3,0</span><span class="sxs-lookup"><span data-stu-id="22a05-141">3.0</span></span> |
| [<span data-ttu-id="22a05-142">JsonEncodedText. Encode yöntemlerinde ek bir JavaScriptEncoder bağımsız değişkeni vardır</span><span class="sxs-lookup"><span data-stu-id="22a05-142">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="22a05-143">3,0</span><span class="sxs-lookup"><span data-stu-id="22a05-143">3.0</span></span> |
| [<span data-ttu-id="22a05-144">JsonFactoryConverter. CreateConverter imzası değişti</span><span class="sxs-lookup"><span data-stu-id="22a05-144">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="22a05-145">3,0</span><span class="sxs-lookup"><span data-stu-id="22a05-145">3.0</span></span> |
| [<span data-ttu-id="22a05-146">JsonElement API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="22a05-146">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="22a05-147">3,0</span><span class="sxs-lookup"><span data-stu-id="22a05-147">3.0</span></span> |
| [<span data-ttu-id="22a05-148">FieldInfo. SetValue statik, yalnızca init alanları için özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="22a05-148">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="22a05-149">3,0</span><span class="sxs-lookup"><span data-stu-id="22a05-149">3.0</span></span> |
| [<span data-ttu-id="22a05-150">Yerleşik yapı türlerine eklenen özel alanlar</span><span class="sxs-lookup"><span data-stu-id="22a05-150">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="22a05-151">2.1</span><span class="sxs-lookup"><span data-stu-id="22a05-151">2.1</span></span> |
| [<span data-ttu-id="22a05-152">UseShellExecute varsayılan değerindeki değişiklik</span><span class="sxs-lookup"><span data-stu-id="22a05-152">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="22a05-153">2.1</span><span class="sxs-lookup"><span data-stu-id="22a05-153">2.1</span></span> |
| [<span data-ttu-id="22a05-154">MacOS üzerinde OpenSSL sürümleri</span><span class="sxs-lookup"><span data-stu-id="22a05-154">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="22a05-155">2.1</span><span class="sxs-lookup"><span data-stu-id="22a05-155">2.1</span></span> |
| [<span data-ttu-id="22a05-156">Fılesystemınfo. Attributes tarafından oluşturulan UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="22a05-156">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="22a05-157">1,0</span><span class="sxs-lookup"><span data-stu-id="22a05-157">1.0</span></span> |
| [<span data-ttu-id="22a05-158">Bozuk işlem durumu özel durumlarını işleme desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="22a05-158">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="22a05-159">1,0</span><span class="sxs-lookup"><span data-stu-id="22a05-159">1.0</span></span> |
| [<span data-ttu-id="22a05-160">UriBuilder özellikleri artık önde gelen karakterlerin önüne alınmaz</span><span class="sxs-lookup"><span data-stu-id="22a05-160">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="22a05-161">1,0</span><span class="sxs-lookup"><span data-stu-id="22a05-161">1.0</span></span> |
| [<span data-ttu-id="22a05-162">Process. StartInfo, başlatmadığınız işlemler için InvalidOperationException 'yi oluşturur</span><span class="sxs-lookup"><span data-stu-id="22a05-162">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="22a05-163">1,0</span><span class="sxs-lookup"><span data-stu-id="22a05-163">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="22a05-164">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="22a05-164">.NET 5.0</span></span>

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

## <a name="net-core-30"></a><span data-ttu-id="22a05-165">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="22a05-165">.NET Core 3.0</span></span>

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

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="22a05-166">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="22a05-166">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="22a05-167">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="22a05-167">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
