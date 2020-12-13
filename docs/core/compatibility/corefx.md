---
title: .NET kitaplığı son değişiklikleri
description: .NET Core sürüm 1.0-3.0 için çekirdek .NET kitaplıklarında yapılan son değişiklikleri listeler.
ms.date: 07/27/2020
ms.openlocfilehash: 092ff36a5e07c9e226fe2a67d5e7cfd391e9d16b
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366864"
---
# <a name="core-net-libraries-breaking-changes-in-net-core-10-30"></a><span data-ttu-id="eee60-103">.NET Core 1.0-3.0 sürümündeki çekirdek .NET kitaplıkları önemli değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="eee60-103">Core .NET libraries breaking changes in .NET Core 1.0-3.0</span></span>

<span data-ttu-id="eee60-104">Çekirdek .NET kitaplıkları, .NET Core tarafından kullanılan temel ve diğer genel türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="eee60-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="eee60-105">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="eee60-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="eee60-106">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="eee60-106">Breaking change</span></span> | <span data-ttu-id="eee60-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="eee60-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="eee60-108">GroupCollection 'ı IEnumerable alan genişletme yöntemlerine geçirme, \<T> Kesinleştirme gerektirir</span><span class="sxs-lookup"><span data-stu-id="eee60-108">Passing GroupCollection to extension methods taking IEnumerable\<T> requires disambiguation</span></span>](#passing-groupcollection-to-extension-methods-taking-ienumerablet-requires-disambiguation) | <span data-ttu-id="eee60-109">3,0</span><span class="sxs-lookup"><span data-stu-id="eee60-109">3.0</span></span> |
| [<span data-ttu-id="eee60-110">Sürümü şimdi rapor eden API 'Ler rapor ürünü ve dosya sürümü değil</span><span class="sxs-lookup"><span data-stu-id="eee60-110">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="eee60-111">3,0</span><span class="sxs-lookup"><span data-stu-id="eee60-111">3.0</span></span> |
| [<span data-ttu-id="eee60-112">Özel EncoderFallbackBuffer örnekleri özyinelemeli olarak geri dönemez</span><span class="sxs-lookup"><span data-stu-id="eee60-112">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="eee60-113">3,0</span><span class="sxs-lookup"><span data-stu-id="eee60-113">3.0</span></span> |
| [<span data-ttu-id="eee60-114">Kayan nokta biçimlendirme ve ayrıştırma davranışı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="eee60-114">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="eee60-115">3,0</span><span class="sxs-lookup"><span data-stu-id="eee60-115">3.0</span></span> |
| [<span data-ttu-id="eee60-116">Kayan nokta ayrıştırma işlemleri artık başarısız olmaz veya bir OverflowException oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="eee60-116">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="eee60-117">3,0</span><span class="sxs-lookup"><span data-stu-id="eee60-117">3.0</span></span> |
| [<span data-ttu-id="eee60-118">InvalidAsynchronousStateException başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="eee60-118">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="eee60-119">3,0</span><span class="sxs-lookup"><span data-stu-id="eee60-119">3.0</span></span> |
| [<span data-ttu-id="eee60-120">Hatalı biçimlendirilmiş UTF-8 bayt dizilerini değiştirme Unicode yönergelerine uyar</span><span class="sxs-lookup"><span data-stu-id="eee60-120">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="eee60-121">3,0</span><span class="sxs-lookup"><span data-stu-id="eee60-121">3.0</span></span> |
| [<span data-ttu-id="eee60-122">TypeDescriptionProviderAttribute başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="eee60-122">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="eee60-123">3,0</span><span class="sxs-lookup"><span data-stu-id="eee60-123">3.0</span></span> |
| [<span data-ttu-id="eee60-124">ZipArchiveEntry artık tutarsız giriş boyutlarına sahip arşivleri işliyor</span><span class="sxs-lookup"><span data-stu-id="eee60-124">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="eee60-125">3,0</span><span class="sxs-lookup"><span data-stu-id="eee60-125">3.0</span></span> |
| [<span data-ttu-id="eee60-126">FieldInfo. SetValue statik, yalnızca init alanları için özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="eee60-126">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="eee60-127">3,0</span><span class="sxs-lookup"><span data-stu-id="eee60-127">3.0</span></span> |
| [<span data-ttu-id="eee60-128">Yerleşik yapı türlerine eklenen özel alanlar</span><span class="sxs-lookup"><span data-stu-id="eee60-128">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="eee60-129">2.1</span><span class="sxs-lookup"><span data-stu-id="eee60-129">2.1</span></span> |
| [<span data-ttu-id="eee60-130">UseShellExecute varsayılan değerindeki değişiklik</span><span class="sxs-lookup"><span data-stu-id="eee60-130">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="eee60-131">2.1</span><span class="sxs-lookup"><span data-stu-id="eee60-131">2.1</span></span> |
| [<span data-ttu-id="eee60-132">MacOS üzerinde OpenSSL sürümleri</span><span class="sxs-lookup"><span data-stu-id="eee60-132">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="eee60-133">2.1</span><span class="sxs-lookup"><span data-stu-id="eee60-133">2.1</span></span> |
| [<span data-ttu-id="eee60-134">Fılesystemınfo. Attributes tarafından oluşturulan UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="eee60-134">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="eee60-135">1,0</span><span class="sxs-lookup"><span data-stu-id="eee60-135">1.0</span></span> |
| [<span data-ttu-id="eee60-136">Bozuk işlem durumu özel durumlarını işleme desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="eee60-136">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="eee60-137">1,0</span><span class="sxs-lookup"><span data-stu-id="eee60-137">1.0</span></span> |
| [<span data-ttu-id="eee60-138">UriBuilder özellikleri artık önde gelen karakterlerin önüne alınmaz</span><span class="sxs-lookup"><span data-stu-id="eee60-138">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="eee60-139">1,0</span><span class="sxs-lookup"><span data-stu-id="eee60-139">1.0</span></span> |
| [<span data-ttu-id="eee60-140">Process. StartInfo, başlatmadığınız işlemler için InvalidOperationException 'yi oluşturur</span><span class="sxs-lookup"><span data-stu-id="eee60-140">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="eee60-141">1,0</span><span class="sxs-lookup"><span data-stu-id="eee60-141">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="eee60-142">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="eee60-142">.NET Core 3.0</span></span>

[!INCLUDE [disambiguate-generic-type-for-groupcollection](../../../includes/core-changes/corefx/3.0/disambiguate-generic-type-for-groupcollection.md)]

***

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

<span data-ttu-id="eee60-143">\*\*_</span><span class="sxs-lookup"><span data-stu-id="eee60-143">\*\*_</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="eee60-144">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="eee60-144">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

_*_

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

_*_

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

_*_

## <a name="net-core-10"></a><span data-ttu-id="eee60-145">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="eee60-145">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

_*_

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

_*_

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

_*_

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

<span data-ttu-id="eee60-146">_\*\*</span><span class="sxs-lookup"><span data-stu-id="eee60-146">_\*\*</span></span>
