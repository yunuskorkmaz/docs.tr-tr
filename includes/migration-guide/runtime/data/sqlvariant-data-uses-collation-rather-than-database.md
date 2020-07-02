---
ms.openlocfilehash: d606fbc4048421bc572cfe3db2e06bbcd4529e25
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620604"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a>Sql_variant veriler veritabanı harmanlaması yerine sql_variant harmanlama kullanır

#### <a name="details"></a>Ayrıntılar

<code>sql_variant</code>veriler <code>sql_variant</code> veritabanı harmanlaması yerine harmanlamayı kullanır.

#### <a name="suggestion"></a>Öneri

Veritabanı harmanlaması harmanlamadan farklıysa bu değişiklik olası veri bozulmasına yöneliktir <code>sql_variant</code> . Bozulmuş verilere dayanan uygulamalar hatayla karşılaşabilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Geçirgen|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|
