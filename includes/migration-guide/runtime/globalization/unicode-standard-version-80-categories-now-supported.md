---
ms.openlocfilehash: efa0efaf40e2e432d477f1659d7bde3abc98241d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857475"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a>Unicode standart sürüm 8.0 kategorileri şimdi desteklenen

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2'de, Unicode verileri Unicode Standard sürüm 6.3'ten sürüm 8.0'a yükseltildi.  .NET Framework 4.6.2'de Unicode karakter kategorileri istenirken, bazı sonuçlar önceki .NET Framework sürümlerindeki sonuçlarla eşleşmeyebilir.  Bu değişiklik çoğunlukla Cherokee heceleri ve Yeni Tai Lue sesli harfler işaretleri ve sesi işaretleri etkiler.|
|Öneri|Kodu gözden geçirin ve sabit kodlanmış Unicode karakter kategorilerine bağlı olan kaldırma/değiştirme mantığı.|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
