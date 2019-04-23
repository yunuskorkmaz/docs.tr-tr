---
ms.openlocfilehash: a5b3e325c13d2f56532ebc6ebb5c259d565a4952
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805240"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a>XmlSchemaException artık satır konumlarını düzgün ayarlar

|   |   |
|---|---|
|Ayrıntılar|Varsa <xref:System.Xml.Linq.LoadOptions.SetLineInfo> yük yönteme geçirilen değer ve bir doğrulama hatası oluşursa, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> ve <xref:System.Xml.Schema.XmlSchemaException.LinePosition> özellikleri satır bilgileri içerir.|
|Öneri|Varsayar özel durum işleme kodları <xref:System.Xml.Schema.XmlSchemaException.LineNumber> ve <xref:System.Xml.Schema.XmlSchemaException.LinePosition> değişmeyecek SetLineInfo XML yüklenirken kullanıldığında bu özellikler artık düzgün şekilde ayarlanır bu yana kümesi güncelleştirilmelidir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
