---
title: Küreselleşme config ayarları
description: Bir .NET Core uygulamasının küreselleşme yönlerini yapılandıran çalışma zamanı ayarları hakkında bilgi edinin, örneğin Japonca tarihleri nasıl ayrıştırdığı hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 3764d0eb714c094b44ae843a1e626073ff8d82e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733458"
---
# <a name="run-time-configuration-options-for-globalization"></a>Küreselleşme için çalışma zamanı yapılandırma seçenekleri

## <a name="invariant-mode"></a>Değişmez mod

- Bir .NET Core uygulamasının kültüre özgü verilere ve davranışlara erişmeden küreselleşme değişmez modunda çalışıp çalışmadığını veya kültürel verilere erişimi olup olmadığını belirler.
- Varsayılan: Uygulamayı kültürel verilere erişerek`false`çalıştırın ( ).
- Daha fazla bilgi için [bkz.](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | `System.Globalization.Invariant` | `false`- kültürel verilere erişim<br/>`true`- değişmez modda çalıştırın |
| **MSBuild özelliği** | `InvariantGlobalization` | `false`- kültürel verilere erişim<br/>`true`- değişmez modda çalıştırın |
| **Ortam değişkeni** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0`- kültürel verilere erişim<br/>`1`- değişmez modda çalıştırın |

### <a name="examples"></a>Örnekler

*runtimeconfig.json* dosyası:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

Proje dosyası:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a>Dönem yıl aralıkları

- Birden çok dönemi destekleyen takvimler için aralık denetimlerinin rahat olup olmadığını veya bir dönemin <xref:System.ArgumentOutOfRangeException>tarih aralığını tarayan tarihlerin bir .
- Varsayılan: Aralık denetimleri`false`rahat ( ).
- Daha fazla bilgi için [Takvimler, eralar ve tarih aralıklarına bakın: Rahat aralık denetimleri.](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks)

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false`- rahat aralık kontrolleri<br/>`true`- taşmalar bir özel durum neden |
| **Ortam değişkeni** | Yok | Yok |

## <a name="japanese-date-parsing"></a>Japon tarih ayrışma

- Yıl başarılı bir şekilde parses olarak "1" veya "Gannen" içeren bir dize ya da sadece "1" desteklenir olup olmadığını belirler.
- Varsayılan: Yıl olarak "1" veya "Gannen" içeren ayrıştırıcı dizeleri (`false`).
- Daha fazla bilgi için, [birden çok erya sahip takvimlerde temsil tarihlerine](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)bakın.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false`- "Gannen" veya "1" desteklenir<br/>`true`- sadece "1" desteklenir |
| **Ortam değişkeni** | Yok | Yok |

## <a name="japanese-year-format"></a>Japonca yıl biçimi

- Bir Japon takvim döneminin ilk yılının "Gannen" olarak mı yoksa sayı olarak mı biçimlendirilir sini belirler.
- Varsayılan: İlk yılı "Gannen"`false`( ) olarak biçimlendirin.
- Daha fazla bilgi için, [birden çok erya sahip takvimlerde temsil tarihlerine](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)bakın.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false`- "Gannen" olarak biçimlendirme<br/>`true`- sayı olarak biçimlendirme |
| **Ortam değişkeni** | Yok | Yok |
