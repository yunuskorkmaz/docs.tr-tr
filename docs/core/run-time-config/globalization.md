---
title: Genelleştirme yapılandırma ayarları
description: .NET Core uygulamasının Genelleştirme yönlerini yapılandıran çalışma zamanı ayarları hakkında bilgi edinin. Örneğin, Japonca tarihleri nasıl ayrıştırır.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 0571c64eff5b38aafa37026fb2ba7f4aef778beb
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802780"
---
# <a name="run-time-configuration-options-for-globalization"></a>Genelleştirme için çalışma zamanı yapılandırma seçenekleri

## <a name="invariant-mode"></a>Sabit mod

- .NET Core uygulamasının kültüre özgü verilere ve davranışa erişim olmadan Genelleştirme sabit modunda çalışıp çalışmadığını ya da kültürel verilerine erişip erişemeyeceğini belirler.
- Varsayılan: uygulamayı, kültürel verileri (`false`) erişimi ile çalıştırın.
- Daha fazla bilgi için bkz. [.NET Core Genelleştirme sabit modu](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `System.Globalization.Invariant` | `false`-kültürel verilerine erişim<br/>`true`-sabit modda çalıştır |
| **Ortam değişkeni** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0`-kültürel verilerine erişim<br/>`1`-sabit modda çalıştır |

## <a name="era-year-ranges"></a>Dönem yıl aralıkları

- Birden çok dönemi destekleyen takvimler için Aralık denetimlerinin gevşek olup olmadığını veya bir dönem tarih aralığını taşan tarihlerin <xref:System.ArgumentOutOfRangeException>oluşturmasını belirler.
- Varsayılan: Aralık denetimleri gevşek (`false`).
- Daha fazla bilgi için bkz. [takvimler, eras ve tarih aralıkları: gevşek Aralık denetimleri](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false` gevşek Aralık denetimleri<br/>`true`-taşmalar özel duruma neden olur |
| **Ortam değişkeni** | YOK | YOK |

## <a name="japanese-date-parsing"></a>Japonca Tarih ayrıştırma

- Yıl olarak "1" veya "gannen" içeren bir dizenin başarıyla ayrıştıranıp desteklenmediğini veya yalnızca "1" desteklenip desteklenmediğini belirler.
- Varsayılan: yıl (`false`) olarak "1" veya "gannen" içeren dizeleri ayrıştırın.
- Daha fazla bilgi için bkz. [birden çok dönemi ile takvimlerdeki tarihleri temsil](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)etme.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false`-"gannen" veya "1" destekleniyor<br/>`true`-yalnızca "1" destekleniyor |
| **Ortam değişkeni** | YOK | YOK |

## <a name="japanese-year-format"></a>Japon yıl biçimi

- Japonca takvim çağının ilk yılının "gannen" olarak mı yoksa sayı olarak mı biçimlendirildiğini belirler.
- Varsayılan: ilk yılı "gannen" (`false`) olarak biçimlendirin.
- Daha fazla bilgi için bkz. [birden çok dönemi ile takvimlerdeki tarihleri temsil](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)etme.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false`-"gannen" olarak Biçimlendir<br/>`true`-sayı olarak Biçimlendir |
| **Ortam değişkeni** | YOK | YOK |
