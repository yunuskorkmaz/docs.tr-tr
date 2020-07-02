---
ms.openlocfilehash: a007022bf32ffe76861f6f9016a7edace17b0f61
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620645"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a>PrintSystemJobInfo. JobStream 'e yazılan veriler XPS biçiminde olmalıdır

#### <a name="details"></a>Ayrıntılar

<xref:System.Printing.PrintSystemJobInfo.JobStream>Özelliği, bir yazdırma işinin akışını gösterir. Kullanıcı, ham verileri, bu akışa yazarak temel işletim sistemi yazdırma bileşenlerine gönderebilir. Windows 8 ' de ve Windows işletim sisteminin sonraki sürümlerinde 4,5 .NET Framework başlayarak, bu akışa yazılan verilerin bir paket akışı olarak XPS biçiminde olması gerekir.

#### <a name="suggestion"></a>Öneri

Yazdırma içeriğini çıkarmak için aşağıdakilerden birini yapabilirsiniz:<ul><li><xref:System.Windows.Xps.XpsDocumentWriter>Yazdırma içeriğini çıkarmak için sınıfını kullanın. Önerilen seçenek budur.</li><li>Özelliği tarafından döndürülen akışa gönderilen verilerin <xref:System.Printing.PrintSystemJobInfo.JobStream> bir paket akışı olarak XPS biçiminde olduğundan emin olun.</li></ul>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|
