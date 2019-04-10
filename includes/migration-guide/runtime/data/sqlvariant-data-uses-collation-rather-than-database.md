---
ms.openlocfilehash: e7a5a95a5d13f3396d396ad0d74a19a0efa3a967
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235836"
---
### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a>Veritabanı Harmanlama yerine sql_variant harmanlama sql_variant veri kullanır.

|   |   |
|---|---|
|Ayrıntılar|<code>sql_variant</code> Veri kaldırmanın <code>sql_variant</code> veritabanı harmanlama yerine harmanlama.|
|Öneri|Veritabanı harmanlaması farklı olması durumunda bu değişiklik olası veri bozulmasına çözüm <code>sql_variant</code> harmanlama. Bozulmuş verilere dayanan uygulamalar hatayla karşılaşabilir.|
|Kapsam|Geçirgen|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
