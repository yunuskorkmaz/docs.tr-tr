---
ms.openlocfilehash: 415eb1960c20fb662469e126560d6f366309eb0d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497458"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Kılavuz yıldıza yönelik iyileştirmeler-satırlar alan ayırma algoritması

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,7 ' de tanıtılan bir hata, [boyutları ayırma algoritmasında](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)düzeltildi) <xref:System.Windows.Controls.Grid> .  Boş satırlar içeren bir ızgara gibi bazı durumlarda, <code>Height=&quot;Auto&quot;</code> satırlar yanlış konuma düzenleniyordu, muhtemelen ızgara dışında.

#### <a name="suggestion"></a>Öneri

Uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4,8 veya sonraki bir sürümde çalışmalıdır.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Ana|
|Sürüm|4,8|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
