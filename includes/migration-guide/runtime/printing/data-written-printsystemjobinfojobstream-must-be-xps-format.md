---
ms.openlocfilehash: 74f00821f2304664729faa8de2f0163c6611f513
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235888"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a>PrintSystemJobInfo.JobStream için yazılan veri XPS biçiminde olmalıdır

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Printing.PrintSystemJobInfo.JobStream> Özelliğini bir yazdırma işi akışını gösterir. Kullanıcı bu akışa yazarak temel işletim sistemi yazdırma bileşeni ham veriler gönderebilir. Bu akışa yazılan veriler, Windows 8 ve Windows işletim sisteminin sonraki sürümlerini .NET Framework 4.5 ile başlayarak, bir paket akışı olarak XPS biçiminde olmalıdır.|
|Öneri|Çıkış içeriği yazdırmak için aşağıdakilerden birini yapabilirsiniz:<ul><li>Kullanım <xref:System.Windows.Xps.XpsDocumentWriter> çıkış içeriği yazdırmak için sınıf. Önerilen seçenek budur.</li><li>Tarafından döndürülen akışa gönderilen veriler <xref:System.Printing.PrintSystemJobInfo.JobStream> XPS biçiminde bir paket akışı olarak özelliğidir.</li></ul>|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|
