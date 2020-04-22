---
title: Taban sınıf kitaplığı kesme değişiklikleri
description: Çekirdek .NET kitaplıklarında kırılan değişiklikleri listeler.
ms.date: 09/20/2019
ms.openlocfilehash: 8cf90ca2bc8736101c1cb8d327a93d100148937b
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021834"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="0d696-103">Core .NET kitaplıkları değişiklikleri kırma</span><span class="sxs-lookup"><span data-stu-id="0d696-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="0d696-104">Çekirdek .NET kitaplıkları .NET Core tarafından kullanılan ilkel ve diğer genel türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d696-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="0d696-105">Aşağıdaki kesme değişiklikleri bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="0d696-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="0d696-106">Son dakika değişikliği</span><span class="sxs-lookup"><span data-stu-id="0d696-106">Breaking change</span></span> | <span data-ttu-id="0d696-107">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0d696-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="0d696-108">Rapor sürümünü rapor eden API'ler artık ürünü rapor eder, dosya sürümünü bildirmez</span><span class="sxs-lookup"><span data-stu-id="0d696-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="0d696-109">3,0</span><span class="sxs-lookup"><span data-stu-id="0d696-109">3.0</span></span> |
| [<span data-ttu-id="0d696-110">Özel EncoderFallbackBuffer örnekleri özyinelemeli geri düşemez</span><span class="sxs-lookup"><span data-stu-id="0d696-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="0d696-111">3,0</span><span class="sxs-lookup"><span data-stu-id="0d696-111">3.0</span></span> |
| [<span data-ttu-id="0d696-112">Kayan nokta biçimlendirme ve ayrıştirma davranış değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="0d696-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="0d696-113">3,0</span><span class="sxs-lookup"><span data-stu-id="0d696-113">3.0</span></span> |
| [<span data-ttu-id="0d696-114">Kayan nokta ayrışma işlemleri artık başarısız veya bir OverflowException atmak</span><span class="sxs-lookup"><span data-stu-id="0d696-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="0d696-115">3,0</span><span class="sxs-lookup"><span data-stu-id="0d696-115">3.0</span></span> |
| [<span data-ttu-id="0d696-116">GeçersizAsynchronousStateException başka bir derlemetaşındı</span><span class="sxs-lookup"><span data-stu-id="0d696-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="0d696-117">3,0</span><span class="sxs-lookup"><span data-stu-id="0d696-117">3.0</span></span> |
| [<span data-ttu-id="0d696-118">NET Core 3.0, kötü biçimlendirilmiş UTF-8 bayt dizilerini değiştirirken Unicode en iyi uygulamalarını takip eder</span><span class="sxs-lookup"><span data-stu-id="0d696-118">NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | <span data-ttu-id="0d696-119">3,0</span><span class="sxs-lookup"><span data-stu-id="0d696-119">3.0</span></span> |
| [<span data-ttu-id="0d696-120">TypeDescriptionProviderAttribute başka bir derleme taşındı</span><span class="sxs-lookup"><span data-stu-id="0d696-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="0d696-121">3,0</span><span class="sxs-lookup"><span data-stu-id="0d696-121">3.0</span></span> |
| [<span data-ttu-id="0d696-122">ZipArchiveEntry artık tutarsız giriş boyutları ile arşivleri işler</span><span class="sxs-lookup"><span data-stu-id="0d696-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="0d696-123">3,0</span><span class="sxs-lookup"><span data-stu-id="0d696-123">3.0</span></span> |
| [<span data-ttu-id="0d696-124">JSON serializer özel durum türü JsonException'dan NotSupportedException'a değiştirildi</span><span class="sxs-lookup"><span data-stu-id="0d696-124">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="0d696-125">3,0</span><span class="sxs-lookup"><span data-stu-id="0d696-125">3.0</span></span> |
| [<span data-ttu-id="0d696-126">Utf8JsonWriter 'da (string)null semantik değişikliği</span><span class="sxs-lookup"><span data-stu-id="0d696-126">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="0d696-127">3,0</span><span class="sxs-lookup"><span data-stu-id="0d696-127">3.0</span></span> |
| [<span data-ttu-id="0d696-128">JsonEncodedText.Encode yöntemleri ek bir JavaScriptEncoder argüman var</span><span class="sxs-lookup"><span data-stu-id="0d696-128">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="0d696-129">3,0</span><span class="sxs-lookup"><span data-stu-id="0d696-129">3.0</span></span> |
| [<span data-ttu-id="0d696-130">JsonFactoryConverter.CreateConverter imzası değiştirildi</span><span class="sxs-lookup"><span data-stu-id="0d696-130">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="0d696-131">3,0</span><span class="sxs-lookup"><span data-stu-id="0d696-131">3.0</span></span> |
| [<span data-ttu-id="0d696-132">JsonElement API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="0d696-132">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="0d696-133">3,0</span><span class="sxs-lookup"><span data-stu-id="0d696-133">3.0</span></span> |
| [<span data-ttu-id="0d696-134">FieldInfo.SetValue statik, yalnızca init-only alanları için özel durum atar</span><span class="sxs-lookup"><span data-stu-id="0d696-134">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="0d696-135">3,0</span><span class="sxs-lookup"><span data-stu-id="0d696-135">3.0</span></span> |
| [<span data-ttu-id="0d696-136">Yerleşik yapı türlerine eklenen özel alanlar</span><span class="sxs-lookup"><span data-stu-id="0d696-136">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="0d696-137">2.1</span><span class="sxs-lookup"><span data-stu-id="0d696-137">2.1</span></span> |
| [<span data-ttu-id="0d696-138">UseShellExecute'ın varsayılan değerindeki değişiklik</span><span class="sxs-lookup"><span data-stu-id="0d696-138">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="0d696-139">2.1</span><span class="sxs-lookup"><span data-stu-id="0d696-139">2.1</span></span> |
| [<span data-ttu-id="0d696-140">macOS'ta OpenSSL sürümleri</span><span class="sxs-lookup"><span data-stu-id="0d696-140">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="0d696-141">2.1</span><span class="sxs-lookup"><span data-stu-id="0d696-141">2.1</span></span> |
| [<span data-ttu-id="0d696-142">FileSystemInfo.Attributes tarafından atılan Yetkisiz ErişimÖzel Durum</span><span class="sxs-lookup"><span data-stu-id="0d696-142">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="0d696-143">1.0</span><span class="sxs-lookup"><span data-stu-id="0d696-143">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="0d696-144">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0d696-144">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="0d696-145">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0d696-145">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="0d696-146">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="0d696-146">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***
