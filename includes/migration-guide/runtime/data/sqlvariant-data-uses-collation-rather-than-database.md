---
ms.openlocfilehash: fb339fb35cdcbba4f1c860fae9c17162c4cff596
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497096"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a>Sql_variant veriler veritabanı harmanlaması yerine sql_variant harmanlama kullanır

#### <a name="details"></a>Ayrıntılar

<code>sql_variant</code> veriler <code>sql_variant</code> veritabanı harmanlaması yerine harmanlamayı kullanır.

#### <a name="suggestion"></a>Öneri

Veritabanı harmanlaması harmanlamadan farklıysa bu değişiklik olası veri bozulmasına yöneliktir <code>sql_variant</code> . Bozulmuş verilere dayanan uygulamalar hatayla karşılaşabilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Geçirgen|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
