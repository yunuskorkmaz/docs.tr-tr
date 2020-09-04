---
title: Temel sınıf kitaplığı bölünmesi değişiklikleri
description: Çekirdek .NET kitaplıklarında son değişiklikleri listeler.
ms.date: 07/27/2020
ms.openlocfilehash: d8d886785ff71f22a3b2da65e973d899cf0371f6
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465899"
---
# <a name="core-net-libraries-breaking-changes"></a>Çekirdek .NET kitaplıklarının parçalara bölünmesi

Çekirdek .NET kitaplıkları, .NET Core tarafından kullanılan temel ve diğer genel türleri sağlar.

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Sunulan sürüm |
| - | :-: |
| [ConsoleLoggerOptions üzerinde kullanımdan kalkmış Özellikler](#obsolete-properties-on-consoleloggeroptions) | 5.0 |
| [Donanım iç tarafından desteklenen denetimler iç içe türler için farklılık gösterebilir](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | 5.0 |
| [Başvuru derlemelerindeki parametre adları değiştirildi](#parameter-names-changed-in-reference-assemblies) | 5.0 |
| [ASCII olmayan karakterler içeren URI yolları UNIX üzerinde doğru şekilde ayrıştırır](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | 5.0 |
| [UNIX üzerinde UNC yollarının URI tanıması](#uri-recognition-of-unc-paths-on-unix) | 5.0 |
| [Environment. OSVersion doğru işletim sistemi sürümünü döndürür](#environmentosversion-returns-the-correct-operating-system-version) | 5.0 |
| [LINQ OrderBy 'in karmaşıklığı. Ilk {OrDefault} artırılmış](#complexity-of-linq-orderbyfirstordefault-increased) | 5.0 |
| [IntPtr ve UIntPtr IFormattable 'ı uygular](#intptr-and-uintptr-implement-iformattable) | 5.0 |
| [PrincipalPermissionAttribute hata olarak kullanımdan kalktı](#principalpermissionattribute-is-obsolete-as-error) | 5.0 |
| [BinaryFormatter serileştirme yöntemleri artık kullanılmıyor ve ASP.NET uygulamalarında yasaklanmış](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | 5.0 |
| [UTF-7 kod yolları artık kullanılmıyor](#utf-7-code-paths-are-obsolete) | 5.0 |
| [Vektör, \<T> Desteklenmeyen türler için her zaman NotSupportedException oluşturur](#vectort-always-throws-notsupportedexception-for-unsupported-types) | 5.0 |
| [Varsayılan Activityıdformat W3C](#default-activityidformat-is-w3c) | 5.0 |
| [Vector2. Lerp ve Vector4. Lerp için davranış değişikliği](#behavior-change-for-vector2lerp-and-vector4lerp) | 5.0 |
| [SSE ve SSE2 CompareGreaterThan yöntemleri NaN girdilerini doğru bir şekilde işler](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | 5.0 |
| [CounterSet. CreateCounterSetInstance şimdi örnek zaten varsa InvalidOperationException oluşturur](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | 5.0 |
| [Microsoft. DotNet. PlatformAbstractions paketi kaldırıldı](#microsoftdotnetplatformabstractions-package-removed) | 5.0 |
| [Sürümü şimdi rapor eden API 'Ler rapor ürünü ve dosya sürümü değil](#apis-that-report-version-now-report-product-and-not-file-version) | 3.0 |
| [Özel EncoderFallbackBuffer örnekleri özyinelemeli olarak geri dönemez](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | 3.0 |
| [Kayan nokta biçimlendirme ve ayrıştırma davranışı değişiklikleri](#floating-point-formatting-and-parsing-behavior-changed) | 3.0 |
| [Kayan nokta ayrıştırma işlemleri artık başarısız olmaz veya bir OverflowException oluşturmaz](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | 3.0 |
| [InvalidAsynchronousStateException başka bir derlemeye taşındı](#invalidasynchronousstateexception-moved-to-another-assembly) | 3.0 |
| [Hatalı biçimlendirilmiş UTF-8 bayt dizilerini değiştirme Unicode yönergelerine uyar](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | 3.0 |
| [TypeDescriptionProviderAttribute başka bir derlemeye taşındı](#typedescriptionproviderattribute-moved-to-another-assembly) | 3.0 |
| [ZipArchiveEntry artık tutarsız giriş boyutlarına sahip arşivleri işliyor](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | 3.0 |
| [FieldInfo. SetValue statik, yalnızca init alanları için özel durum oluşturur](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | 3.0 |
| [Yerleşik yapı türlerine eklenen özel alanlar](#private-fields-added-to-built-in-struct-types) | 2.1 |
| [UseShellExecute varsayılan değerindeki değişiklik](#change-in-default-value-of-useshellexecute) | 2.1 |
| [MacOS üzerinde OpenSSL sürümleri](#openssl-versions-on-macos) | 2.1 |
| [Fılesystemınfo. Attributes tarafından oluşturulan UnauthorizedAccessException](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | 1.0 |
| [Bozuk işlem durumu özel durumlarını işleme desteklenmiyor](#handling-corrupted-state-exceptions-is-not-supported) | 1.0 |
| [UriBuilder özellikleri artık önde gelen karakterlerin önüne alınmaz](#uribuilder-properties-no-longer-prepend-leading-characters) | 1.0 |
| [Process. StartInfo, başlatmadığınız işlemler için InvalidOperationException 'yi oluşturur](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | 1.0 |

## <a name="net-50"></a>.NET 5,0

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

## <a name="net-core-30"></a>.NET Core 3.0

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

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a>.NET Core 1,0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
