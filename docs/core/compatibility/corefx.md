---
title: Temel sınıf kitaplığı bölünmesi değişiklikleri
description: Çekirdek .NET kitaplıklarında son değişiklikleri listeler.
ms.date: 09/20/2019
ms.openlocfilehash: 841003fdb114042466cc15b4846e133cf37de85c
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135652"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="ebe4c-103">Çekirdek .NET kitaplıklarının parçalara bölünmesi</span><span class="sxs-lookup"><span data-stu-id="ebe4c-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="ebe4c-104">Çekirdek .NET kitaplıkları, .NET Core tarafından kullanılan temel ve diğer genel türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ebe4c-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="ebe4c-105">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="ebe4c-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="ebe4c-106">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="ebe4c-106">Breaking change</span></span> | <span data-ttu-id="ebe4c-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="ebe4c-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="ebe4c-108">Sürümü şimdi rapor eden API 'Ler rapor ürünü ve dosya sürümü değil</span><span class="sxs-lookup"><span data-stu-id="ebe4c-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="ebe4c-109">3,0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-109">3.0</span></span> |
| [<span data-ttu-id="ebe4c-110">Özel EncoderFallbackBuffer örnekleri özyinelemeli olarak geri dönemez</span><span class="sxs-lookup"><span data-stu-id="ebe4c-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="ebe4c-111">3,0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-111">3.0</span></span> |
| [<span data-ttu-id="ebe4c-112">Kayan nokta biçimlendirme ve ayrıştırma davranışı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="ebe4c-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="ebe4c-113">3,0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-113">3.0</span></span> |
| [<span data-ttu-id="ebe4c-114">Kayan nokta ayrıştırma işlemleri artık başarısız olmaz veya bir OverflowException oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="ebe4c-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="ebe4c-115">3,0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-115">3.0</span></span> |
| [<span data-ttu-id="ebe4c-116">InvalidAsynchronousStateException başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="ebe4c-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="ebe4c-117">3,0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-117">3.0</span></span> |
| [<span data-ttu-id="ebe4c-118">NET Core 3,0 hatalı biçimlendirilmiş UTF-8 bayt dizilerini değiştirirken Unicode en iyi yöntemlerini izler</span><span class="sxs-lookup"><span data-stu-id="ebe4c-118">NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | <span data-ttu-id="ebe4c-119">3,0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-119">3.0</span></span> |
| [<span data-ttu-id="ebe4c-120">TypeDescriptionProviderAttribute başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="ebe4c-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="ebe4c-121">3,0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-121">3.0</span></span> |
| [<span data-ttu-id="ebe4c-122">ZipArchiveEntry artık tutarsız giriş boyutlarına sahip arşivleri işliyor</span><span class="sxs-lookup"><span data-stu-id="ebe4c-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="ebe4c-123">3,0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-123">3.0</span></span> |
| [<span data-ttu-id="ebe4c-124">JsonException iken NotSupportedException olarak değiştirilen JSON seri hale getirici özel durum türü</span><span class="sxs-lookup"><span data-stu-id="ebe4c-124">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="ebe4c-125">3,0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-125">3.0</span></span> |
| [<span data-ttu-id="ebe4c-126">Utf8JsonWriter içinde (String) null semantiğinin değiştirilmesi</span><span class="sxs-lookup"><span data-stu-id="ebe4c-126">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="ebe4c-127">3,0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-127">3.0</span></span> |
| [<span data-ttu-id="ebe4c-128">JsonEncodedText. Encode yöntemlerinde ek bir JavaScriptEncoder bağımsız değişkeni vardır</span><span class="sxs-lookup"><span data-stu-id="ebe4c-128">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="ebe4c-129">3,0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-129">3.0</span></span> |
| [<span data-ttu-id="ebe4c-130">JsonFactoryConverter. CreateConverter imzası değişti</span><span class="sxs-lookup"><span data-stu-id="ebe4c-130">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="ebe4c-131">3,0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-131">3.0</span></span> |
| [<span data-ttu-id="ebe4c-132">JsonElement API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="ebe4c-132">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="ebe4c-133">3,0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-133">3.0</span></span> |
| [<span data-ttu-id="ebe4c-134">FieldInfo. SetValue statik, yalnızca init alanları için özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="ebe4c-134">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="ebe4c-135">3,0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-135">3.0</span></span> |
| [<span data-ttu-id="ebe4c-136">Yerleşik yapı türlerine eklenen özel alanlar</span><span class="sxs-lookup"><span data-stu-id="ebe4c-136">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="ebe4c-137">2.1</span><span class="sxs-lookup"><span data-stu-id="ebe4c-137">2.1</span></span> |
| [<span data-ttu-id="ebe4c-138">UseShellExecute varsayılan değerindeki değişiklik</span><span class="sxs-lookup"><span data-stu-id="ebe4c-138">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="ebe4c-139">2.1</span><span class="sxs-lookup"><span data-stu-id="ebe4c-139">2.1</span></span> |
| [<span data-ttu-id="ebe4c-140">MacOS üzerinde OpenSSL sürümleri</span><span class="sxs-lookup"><span data-stu-id="ebe4c-140">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="ebe4c-141">2.1</span><span class="sxs-lookup"><span data-stu-id="ebe4c-141">2.1</span></span> |
| [<span data-ttu-id="ebe4c-142">Fılesystemınfo. Attributes tarafından oluşturulan UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="ebe4c-142">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="ebe4c-143">1.0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-143">1.0</span></span> |
| [<span data-ttu-id="ebe4c-144">Bozuk işlem durumu özel durumlarını işleme desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="ebe4c-144">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="ebe4c-145">1.0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-145">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="ebe4c-146">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-146">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="ebe4c-147">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ebe4c-147">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="ebe4c-148">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="ebe4c-148">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***
