---
title: Temel sınıf kitaplığı bölünmesi değişiklikleri
description: Çekirdek .NET kitaplıklarında son değişiklikleri listeler.
ms.date: 09/20/2019
ms.openlocfilehash: 1c56358e69d0dd6e8572a41229c1b9edbcdad795
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365628"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="f42d3-103">Çekirdek .NET kitaplıklarının parçalara bölünmesi</span><span class="sxs-lookup"><span data-stu-id="f42d3-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="f42d3-104">Çekirdek .NET kitaplıkları, .NET Core tarafından kullanılan temel ve diğer genel türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f42d3-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="f42d3-105">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="f42d3-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="f42d3-106">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="f42d3-106">Breaking change</span></span> | <span data-ttu-id="f42d3-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f42d3-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="f42d3-108">SSE ve SSE2 CompareGreaterThan yöntemleri NaN girdilerini doğru bir şekilde işler</span><span class="sxs-lookup"><span data-stu-id="f42d3-108">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="f42d3-109">5.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-109">5.0</span></span> |
| [<span data-ttu-id="f42d3-110">CounterSet. CreateCounterSetInstance şimdi örnek zaten varsa InvalidOperationException oluşturur</span><span class="sxs-lookup"><span data-stu-id="f42d3-110">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="f42d3-111">5.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-111">5.0</span></span> |
| [<span data-ttu-id="f42d3-112">Microsoft. DotNet. PlatformAbstractions paketi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="f42d3-112">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="f42d3-113">5.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-113">5.0</span></span> |
| [<span data-ttu-id="f42d3-114">Sürümü şimdi rapor eden API 'Ler rapor ürünü ve dosya sürümü değil</span><span class="sxs-lookup"><span data-stu-id="f42d3-114">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="f42d3-115">3.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-115">3.0</span></span> |
| [<span data-ttu-id="f42d3-116">Özel EncoderFallbackBuffer örnekleri özyinelemeli olarak geri dönemez</span><span class="sxs-lookup"><span data-stu-id="f42d3-116">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="f42d3-117">3.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-117">3.0</span></span> |
| [<span data-ttu-id="f42d3-118">Kayan nokta biçimlendirme ve ayrıştırma davranışı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="f42d3-118">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="f42d3-119">3.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-119">3.0</span></span> |
| [<span data-ttu-id="f42d3-120">Kayan nokta ayrıştırma işlemleri artık başarısız olmaz veya bir OverflowException oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="f42d3-120">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="f42d3-121">3.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-121">3.0</span></span> |
| [<span data-ttu-id="f42d3-122">InvalidAsynchronousStateException başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="f42d3-122">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="f42d3-123">3.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-123">3.0</span></span> |
| [<span data-ttu-id="f42d3-124">Hatalı biçimlendirilmiş UTF-8 bayt dizilerini değiştirme Unicode yönergelerine uyar</span><span class="sxs-lookup"><span data-stu-id="f42d3-124">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="f42d3-125">3.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-125">3.0</span></span> |
| [<span data-ttu-id="f42d3-126">TypeDescriptionProviderAttribute başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="f42d3-126">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="f42d3-127">3.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-127">3.0</span></span> |
| [<span data-ttu-id="f42d3-128">ZipArchiveEntry artık tutarsız giriş boyutlarına sahip arşivleri işliyor</span><span class="sxs-lookup"><span data-stu-id="f42d3-128">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="f42d3-129">3.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-129">3.0</span></span> |
| [<span data-ttu-id="f42d3-130">JsonException iken NotSupportedException olarak değiştirilen JSON seri hale getirici özel durum türü</span><span class="sxs-lookup"><span data-stu-id="f42d3-130">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="f42d3-131">3.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-131">3.0</span></span> |
| [<span data-ttu-id="f42d3-132">Utf8JsonWriter içinde (String) null semantiğinin değiştirilmesi</span><span class="sxs-lookup"><span data-stu-id="f42d3-132">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="f42d3-133">3.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-133">3.0</span></span> |
| [<span data-ttu-id="f42d3-134">JsonEncodedText. Encode yöntemlerinde ek bir JavaScriptEncoder bağımsız değişkeni vardır</span><span class="sxs-lookup"><span data-stu-id="f42d3-134">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="f42d3-135">3.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-135">3.0</span></span> |
| [<span data-ttu-id="f42d3-136">JsonFactoryConverter. CreateConverter imzası değişti</span><span class="sxs-lookup"><span data-stu-id="f42d3-136">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="f42d3-137">3.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-137">3.0</span></span> |
| [<span data-ttu-id="f42d3-138">JsonElement API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="f42d3-138">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="f42d3-139">3.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-139">3.0</span></span> |
| [<span data-ttu-id="f42d3-140">FieldInfo. SetValue statik, yalnızca init alanları için özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="f42d3-140">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="f42d3-141">3.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-141">3.0</span></span> |
| [<span data-ttu-id="f42d3-142">Yerleşik yapı türlerine eklenen özel alanlar</span><span class="sxs-lookup"><span data-stu-id="f42d3-142">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="f42d3-143">2.1</span><span class="sxs-lookup"><span data-stu-id="f42d3-143">2.1</span></span> |
| [<span data-ttu-id="f42d3-144">UseShellExecute varsayılan değerindeki değişiklik</span><span class="sxs-lookup"><span data-stu-id="f42d3-144">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="f42d3-145">2.1</span><span class="sxs-lookup"><span data-stu-id="f42d3-145">2.1</span></span> |
| [<span data-ttu-id="f42d3-146">MacOS üzerinde OpenSSL sürümleri</span><span class="sxs-lookup"><span data-stu-id="f42d3-146">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="f42d3-147">2.1</span><span class="sxs-lookup"><span data-stu-id="f42d3-147">2.1</span></span> |
| [<span data-ttu-id="f42d3-148">Fılesystemınfo. Attributes tarafından oluşturulan UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="f42d3-148">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="f42d3-149">1.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-149">1.0</span></span> |
| [<span data-ttu-id="f42d3-150">Bozuk işlem durumu özel durumlarını işleme desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="f42d3-150">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="f42d3-151">1.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-151">1.0</span></span> |
| [<span data-ttu-id="f42d3-152">UriBuilder özellikleri artık önde gelen karakterlerin önüne alınmaz</span><span class="sxs-lookup"><span data-stu-id="f42d3-152">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="f42d3-153">1.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-153">1.0</span></span> |
| [<span data-ttu-id="f42d3-154">Process. StartInfo, başlatmadığınız işlemler için InvalidOperationException 'yi oluşturur</span><span class="sxs-lookup"><span data-stu-id="f42d3-154">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="f42d3-155">1.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-155">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="f42d3-156">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f42d3-156">.NET 5.0</span></span>

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

***

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="f42d3-157">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f42d3-157">.NET Core 3.0</span></span>

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

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

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

## <a name="net-core-21"></a><span data-ttu-id="f42d3-158">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f42d3-158">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="f42d3-159">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="f42d3-159">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
