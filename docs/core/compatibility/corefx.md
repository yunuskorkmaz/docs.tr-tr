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
# <a name="core-net-libraries-breaking-changes-in-net-core-10-30"></a>.NET Core 1.0-3.0 sürümündeki çekirdek .NET kitaplıkları önemli değişiklikleri

Çekirdek .NET kitaplıkları, .NET Core tarafından kullanılan temel ve diğer genel türleri sağlar.

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Sunulan sürüm |
| - | :-: |
| [GroupCollection 'ı IEnumerable alan genişletme yöntemlerine geçirme, \<T> Kesinleştirme gerektirir](#passing-groupcollection-to-extension-methods-taking-ienumerablet-requires-disambiguation) | 3,0 |
| [Sürümü şimdi rapor eden API 'Ler rapor ürünü ve dosya sürümü değil](#apis-that-report-version-now-report-product-and-not-file-version) | 3,0 |
| [Özel EncoderFallbackBuffer örnekleri özyinelemeli olarak geri dönemez](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | 3,0 |
| [Kayan nokta biçimlendirme ve ayrıştırma davranışı değişiklikleri](#floating-point-formatting-and-parsing-behavior-changed) | 3,0 |
| [Kayan nokta ayrıştırma işlemleri artık başarısız olmaz veya bir OverflowException oluşturmaz](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | 3,0 |
| [InvalidAsynchronousStateException başka bir derlemeye taşındı](#invalidasynchronousstateexception-moved-to-another-assembly) | 3,0 |
| [Hatalı biçimlendirilmiş UTF-8 bayt dizilerini değiştirme Unicode yönergelerine uyar](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | 3,0 |
| [TypeDescriptionProviderAttribute başka bir derlemeye taşındı](#typedescriptionproviderattribute-moved-to-another-assembly) | 3,0 |
| [ZipArchiveEntry artık tutarsız giriş boyutlarına sahip arşivleri işliyor](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | 3,0 |
| [FieldInfo. SetValue statik, yalnızca init alanları için özel durum oluşturur](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | 3,0 |
| [Yerleşik yapı türlerine eklenen özel alanlar](#private-fields-added-to-built-in-struct-types) | 2.1 |
| [UseShellExecute varsayılan değerindeki değişiklik](#change-in-default-value-of-useshellexecute) | 2.1 |
| [MacOS üzerinde OpenSSL sürümleri](#openssl-versions-on-macos) | 2.1 |
| [Fılesystemınfo. Attributes tarafından oluşturulan UnauthorizedAccessException](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | 1,0 |
| [Bozuk işlem durumu özel durumlarını işleme desteklenmiyor](#handling-corrupted-state-exceptions-is-not-supported) | 1,0 |
| [UriBuilder özellikleri artık önde gelen karakterlerin önüne alınmaz](#uribuilder-properties-no-longer-prepend-leading-characters) | 1,0 |
| [Process. StartInfo, başlatmadığınız işlemler için InvalidOperationException 'yi oluşturur](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | 1,0 |

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE [disambiguate-generic-type-for-groupcollection](../../../includes/core-changes/corefx/3.0/disambiguate-generic-type-for-groupcollection.md)]

***

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

**_

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

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

_*_

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

_*_

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

_*_

## <a name="net-core-10"></a>.NET Core 1,0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

_*_

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

_*_

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

_*_

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

_**
