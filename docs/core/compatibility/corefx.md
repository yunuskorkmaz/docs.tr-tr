---
title: Taban sınıf kitaplığı kesme değişiklikleri
description: Taban sınıf kitaplığı olan .NET CoreFx'teki son dakika değişikliklerini listeler.
ms.date: 09/20/2019
ms.openlocfilehash: 56a3cf4f4c00a79752d5a98bb086bb9f8c0614b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147581"
---
# <a name="corefx-breaking-changes"></a>CoreFx kesme değişiklikleri

CoreFx,.NET Core tarafından kullanılan ilkel ve diğer genel türleri sağlar.

Aşağıdaki kesme değişiklikleri bu sayfada belgelenmiştir:

| Son dakika değişikliği | Sürüm tanıtıldı |
| - | :-: |
| [Rapor sürümünü rapor eden API'ler artık ürünü rapor eder, dosya sürümünü bildirmez](#apis-that-report-version-now-report-product-and-not-file-version) | 3,0 |
| [Özel EncoderFallbackBuffer örnekleri özyinelemeli geri düşemez](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | 3,0 |
| [Kayan nokta biçimlendirme ve ayrıştirma davranış değişiklikleri](#floating-point-formatting-and-parsing-behavior-changed) | 3,0 |
| [Kayan nokta ayrışma işlemleri artık başarısız veya bir OverflowException atmak](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | 3,0 |
| [GeçersizAsynchronousStateException başka bir derlemetaşındı](#invalidasynchronousstateexception-moved-to-another-assembly) | 3,0 |
| [NET Core 3.0, kötü biçimlendirilmiş UTF-8 bayt dizilerini değiştirirken Unicode en iyi uygulamalarını takip eder](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | 3,0 |
| [TypeDescriptionProviderAttribute başka bir derleme taşındı](#typedescriptionproviderattribute-moved-to-another-assembly) | 3,0 |
| [ZipArchiveEntry artık tutarsız giriş boyutları ile arşivleri işler](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | 3,0 |
| [JSON serializer özel durum türü JsonException'dan NotSupportedException'a değiştirildi](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | 3,0 |
| [Utf8JsonWriter 'da (string)null semantik değişikliği](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | 3,0 |
| [JsonEncodedText.Encode yöntemleri ek bir JavaScriptEncoder argüman var](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | 3,0 |
| [JsonFactoryConverter.CreateConverter imzası değiştirildi](#jsonfactoryconvertercreateconverter-signature-changed) | 3,0 |
| [JsonElement API değişiklikleri](#jsonelement-api-changes) | 3,0 |
| [FieldInfo.SetValue statik, yalnızca init-only alanları için özel durum atar](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | 3,0 |
| [Yerleşik yapı türlerine eklenen özel alanlar](#private-fields-added-to-built-in-struct-types) | 2.1 |
| [UseShellExecute'ın varsayılan değerindeki değişiklik](#change-in-default-value-of-useshellexecute) | 2.1 |
| [macOS'ta OpenSSL sürümleri](#openssl-versions-on-macos) | 2.1 |
| [FileSystemInfo.Attributes tarafından atılan Yetkisiz ErişimÖzel Durum](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | 1.0 |

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

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a>.NET Çekirdek 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***
