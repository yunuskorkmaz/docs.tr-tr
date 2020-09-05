---
ms.openlocfilehash: f389a9e9bcf4ac1777db66731a085d74889c4a98
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496304"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a>Unicode standart sürüm 8,0 kategorileri artık destekleniyor

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.2 ' de Unicode verileri, Unicode standart 6,3 sürümünden 8,0 sürümüne yükseltildi.  .NET Framework 4.6.2 ' de Unicode karakter kategorileri istenirken, bazı sonuçlar önceki .NET Framework sürümlerindeki sonuçlarla eşleşmeyebilir.  Bu değişiklik genellikle Çeroki heceleri ve yeni Day lü sesli işaretleri ve ses işaretlerini etkiler.

#### <a name="suggestion"></a>Öneri

Kodu gözden geçirin ve sabit kodlanmış Unicode karakter kategorilerine bağlı olan mantığı kaldırın/değiştirin.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType>
- <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType>
- <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Char.GetUnicodeCategory(System.Char)`
- `M:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)`
- `M:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)`

-->
