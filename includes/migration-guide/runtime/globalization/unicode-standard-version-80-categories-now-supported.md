---
ms.openlocfilehash: a20fad5f9c95e59c14ffd91f4921cf8bfab443cd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621375"
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
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
