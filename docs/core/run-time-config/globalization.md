---
title: Genelleştirme yapılandırma ayarları
description: .NET Core uygulamasının Genelleştirme yönlerini yapılandıran çalışma zamanı ayarları hakkında bilgi edinin. Örneğin, Japonca tarihleri nasıl ayrıştırır.
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: 2561e66e6d18cb4036b0719f7e34ea66540fe095
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703133"
---
# <a name="run-time-configuration-options-for-globalization"></a>Genelleştirme için çalışma zamanı yapılandırma seçenekleri

## <a name="invariant-mode"></a>Sabit mod

- .NET Core uygulamasının kültüre özgü verilere ve davranışa erişim olmadan Genelleştirme sabit modunda çalışıp çalışmadığını belirler.
- Varsayılan: uygulamayı, kültürel verileri () erişimi ile çalıştırın `false` .
- Daha fazla bilgi için bkz. [.NET Core Genelleştirme sabit modu](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `System.Globalization.Invariant` | `false`-kültürel verilerine erişim<br/>`true`-Sabit modda çalıştır |
| **MSBuild özelliği** | `InvariantGlobalization` | `false`-kültürel verilerine erişim<br/>`true`-Sabit modda çalıştır |
| **Ortam değişkeni** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0`-kültürel verilerine erişim<br/>`1`-Sabit modda çalıştır |

### <a name="examples"></a>Örnekler

*runtimeconfig. JSON* dosyası:

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

- Birden çok dönemi destekleyen takvimler için Aralık denetimlerinin gevşek olduğunu veya bir dönem tarih aralığını taşan tarihlerin bir oluşturma yapıp olmadığını belirler <xref:System.ArgumentOutOfRangeException> .
- Varsayılan: Aralık denetimleri gevşek ( `false` ).
- Daha fazla bilgi için bkz. [takvimler, eras ve tarih aralıkları: gevşek Aralık denetimleri](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false`-gevşek Aralık denetimleri<br/>`true`-bir özel duruma neden olan taşmalar |
| **Ortam değişkeni** | Yok | Yok |

## <a name="japanese-date-parsing"></a>Japonca Tarih ayrıştırma

- Yıl olarak "1" veya "gannen" içeren bir dizenin başarıyla ayrıştıranıp desteklenmediğini veya yalnızca "1" desteklenip desteklenmediğini belirler.
- Varsayılan: yıl () olarak "1" veya "gannen" içeren dizeleri ayrıştırın `false` .
- Daha fazla bilgi için bkz. [birden çok dönemi ile takvimlerdeki tarihleri temsil](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)etme.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false`-"Gannen" veya "1" destekleniyor<br/>`true`-yalnızca "1" destekleniyor |
| **Ortam değişkeni** | Yok | Yok |

## <a name="japanese-year-format"></a>Japon yıl biçimi

- Japonca takvim çağının ilk yılının "gannen" olarak mı yoksa sayı olarak mı biçimlendirildiğini belirler.
- Varsayılan: ilk yılı "gannen" () olarak biçimlendirin `false` .
- Daha fazla bilgi için bkz. [birden çok dönemi ile takvimlerdeki tarihleri temsil](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)etme.

| | Ayar adı | Değerler |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false`"gannen" olarak biçimlendirin<br/>`true`-sayı olarak Biçimlendir |
| **Ortam değişkeni** | Yok | Yok |

## <a name="nls"></a>NLS

- .NET 'in, Windows uygulamaları için, Unicode (ıCU) genelleştirme API 'Leri için ulusal dil desteği (NLS) veya uluslararası bileşenleri kullanıp kullanmadığını belirler. .NET 5,0 ve sonraki sürümleri, Windows 10 Mayıs 2019 güncelleştirme ve sonraki sürümlerinde ıCU genelleştirme API 'Lerini kullanır.
- Bu ayarı atlarsanız, .NET varsayılan olarak ıCU genelleştirme API 'Lerini kullanır. Bu değeri değerine ayarlamaya eşdeğerdir `false` .
- Daha fazla bilgi için bkz. [genelleştirme API 'Leri Windows üzerinde IU kitaplıklarını kullanma](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).

| | Ayar adı | Değerler | Dağıtıla |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.Globalization.UseNls` | `false`-ICU genelleştirme API 'Lerini kullanma<br/>`true`-NLS genelleştirme API 'Lerini kullanma | .NET 5,0 |
| **Ortam değişkeni** | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | `false`-ICU genelleştirme API 'Lerini kullanma<br/>`true`-NLS genelleştirme API 'Lerini kullanma | .NET 5,0 |
