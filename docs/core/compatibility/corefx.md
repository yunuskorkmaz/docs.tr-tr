---
title: .NET kitaplığı son değişiklikleri
description: .NET Core sürüm 1.0-3.0 için çekirdek .NET kitaplıklarında yapılan son değişiklikleri listeler.
ms.date: 07/27/2020
ms.openlocfilehash: 0f42429e44776fc70bb99ed3bdf346f0d5dbc9eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "96032049"
---
# <a name="core-net-libraries-breaking-changes-in-net-core-10-30"></a><span data-ttu-id="7526d-103">.NET Core 1.0-3.0 sürümündeki çekirdek .NET kitaplıkları önemli değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="7526d-103">Core .NET libraries breaking changes in .NET Core 1.0-3.0</span></span>

<span data-ttu-id="7526d-104">Çekirdek .NET kitaplıkları, .NET Core tarafından kullanılan temel ve diğer genel türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7526d-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="7526d-105">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="7526d-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="7526d-106">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="7526d-106">Breaking change</span></span> | <span data-ttu-id="7526d-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7526d-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="7526d-108">Sürümü şimdi rapor eden API 'Ler rapor ürünü ve dosya sürümü değil</span><span class="sxs-lookup"><span data-stu-id="7526d-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="7526d-109">3,0</span><span class="sxs-lookup"><span data-stu-id="7526d-109">3.0</span></span> |
| [<span data-ttu-id="7526d-110">Özel EncoderFallbackBuffer örnekleri özyinelemeli olarak geri dönemez</span><span class="sxs-lookup"><span data-stu-id="7526d-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="7526d-111">3,0</span><span class="sxs-lookup"><span data-stu-id="7526d-111">3.0</span></span> |
| [<span data-ttu-id="7526d-112">Kayan nokta biçimlendirme ve ayrıştırma davranışı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="7526d-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="7526d-113">3,0</span><span class="sxs-lookup"><span data-stu-id="7526d-113">3.0</span></span> |
| [<span data-ttu-id="7526d-114">Kayan nokta ayrıştırma işlemleri artık başarısız olmaz veya bir OverflowException oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="7526d-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="7526d-115">3,0</span><span class="sxs-lookup"><span data-stu-id="7526d-115">3.0</span></span> |
| [<span data-ttu-id="7526d-116">InvalidAsynchronousStateException başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="7526d-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="7526d-117">3,0</span><span class="sxs-lookup"><span data-stu-id="7526d-117">3.0</span></span> |
| [<span data-ttu-id="7526d-118">Hatalı biçimlendirilmiş UTF-8 bayt dizilerini değiştirme Unicode yönergelerine uyar</span><span class="sxs-lookup"><span data-stu-id="7526d-118">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="7526d-119">3,0</span><span class="sxs-lookup"><span data-stu-id="7526d-119">3.0</span></span> |
| [<span data-ttu-id="7526d-120">TypeDescriptionProviderAttribute başka bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="7526d-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="7526d-121">3,0</span><span class="sxs-lookup"><span data-stu-id="7526d-121">3.0</span></span> |
| [<span data-ttu-id="7526d-122">ZipArchiveEntry artık tutarsız giriş boyutlarına sahip arşivleri işliyor</span><span class="sxs-lookup"><span data-stu-id="7526d-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="7526d-123">3,0</span><span class="sxs-lookup"><span data-stu-id="7526d-123">3.0</span></span> |
| [<span data-ttu-id="7526d-124">FieldInfo. SetValue statik, yalnızca init alanları için özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="7526d-124">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="7526d-125">3,0</span><span class="sxs-lookup"><span data-stu-id="7526d-125">3.0</span></span> |
| [<span data-ttu-id="7526d-126">Yerleşik yapı türlerine eklenen özel alanlar</span><span class="sxs-lookup"><span data-stu-id="7526d-126">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="7526d-127">2.1</span><span class="sxs-lookup"><span data-stu-id="7526d-127">2.1</span></span> |
| [<span data-ttu-id="7526d-128">UseShellExecute varsayılan değerindeki değişiklik</span><span class="sxs-lookup"><span data-stu-id="7526d-128">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="7526d-129">2.1</span><span class="sxs-lookup"><span data-stu-id="7526d-129">2.1</span></span> |
| [<span data-ttu-id="7526d-130">MacOS üzerinde OpenSSL sürümleri</span><span class="sxs-lookup"><span data-stu-id="7526d-130">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="7526d-131">2.1</span><span class="sxs-lookup"><span data-stu-id="7526d-131">2.1</span></span> |
| [<span data-ttu-id="7526d-132">Fılesystemınfo. Attributes tarafından oluşturulan UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="7526d-132">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="7526d-133">1,0</span><span class="sxs-lookup"><span data-stu-id="7526d-133">1.0</span></span> |
| [<span data-ttu-id="7526d-134">Bozuk işlem durumu özel durumlarını işleme desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="7526d-134">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="7526d-135">1,0</span><span class="sxs-lookup"><span data-stu-id="7526d-135">1.0</span></span> |
| [<span data-ttu-id="7526d-136">UriBuilder özellikleri artık önde gelen karakterlerin önüne alınmaz</span><span class="sxs-lookup"><span data-stu-id="7526d-136">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="7526d-137">1,0</span><span class="sxs-lookup"><span data-stu-id="7526d-137">1.0</span></span> |
| [<span data-ttu-id="7526d-138">Process. StartInfo, başlatmadığınız işlemler için InvalidOperationException 'yi oluşturur</span><span class="sxs-lookup"><span data-stu-id="7526d-138">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="7526d-139">1,0</span><span class="sxs-lookup"><span data-stu-id="7526d-139">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="7526d-140">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7526d-140">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

<span data-ttu-id="7526d-141">\*\*_</span><span class="sxs-lookup"><span data-stu-id="7526d-141">\*\*_</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="7526d-142">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="7526d-142">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

_*_

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

_*_

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

_*_

## <a name="net-core-10"></a><span data-ttu-id="7526d-143">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="7526d-143">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

_*_

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

_*_

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

_*_

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

<span data-ttu-id="7526d-144">_\*\*</span><span class="sxs-lookup"><span data-stu-id="7526d-144">_\*\*</span></span>
