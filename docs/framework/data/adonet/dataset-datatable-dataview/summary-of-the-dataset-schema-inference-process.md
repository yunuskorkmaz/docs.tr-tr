---
title: DataSet şeması çıkarımı Işleminin Özeti
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 35e9b67d2d0a47aa69eabdb4b7e94f95b0b9589f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833975"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>DataSet şeması çıkarımı Işleminin Özeti
Çıkarım işlemi ilk olarak XML belgesinden, hangi öğelerin tablo olarak gösterileceğini belirler. Kalan XML 'den, çıkarım işlemi bu tabloların sütunlarını belirler. İç içe tablolar için çıkarım işlemi iç içe <xref:System.Data.DataRelation> ve <xref:System.Data.ForeignKeyConstraint> nesneleri üretir.  
  
 Aşağıda, çıkarım kurallarının kısa bir özeti verilmiştir:  
  
- Öznitelikleri olan öğeler tablo olarak algılanır.  
  
- Alt öğeleri olan öğeler tablo olarak algılanır.  
  
- Yinelenen öğeler tek bir tablo olarak algılanır.  
  
- Belge, veya kök, öğe hiç bir özniteliğe sahip değilse ve sütun olarak çıkarsanmayacak alt öğe yoksa, @no__t 0 olarak algılanır. Aksi halde, belge öğesi tablo olarak algılanır.  
  
- Öznitelikler sütun olarak algılanır.  
  
- Öznitelikleri veya alt öğeleri olmayan ve tekrarsız öğeler sütun olarak algılanır.  
  
- Tablo olarak da gösterilen diğer öğeler içinde iç içe geçmiş tablolar olarak gösterilen öğeler için, iki tablo arasında iç içe bir **DataRelation** oluşturulur. Her iki tabloya da **TableName_Id** adlı yeni bir birincil anahtar sütunu eklenir ve **DataRelation**tarafından kullanılır. **TableName_Id** sütununu kullanan iki tablo arasında bir **ForeignKeyConstraint** oluşturulur.  
  
- Tablo olarak gösterilen ve metin içeren ancak hiç alt öğesi olmayan öğeler için, öğelerin her birinin metni için **TableName_Text** adlı yeni bir sütun oluşturulur. Bir öğe tablo olarak algılanır ve metin içeriyorsa, ancak alt öğeleri de varsa, metin yok sayılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML 'den veri kümesi Ilişkisel yapısını erteleme](inferring-dataset-relational-structure-from-xml.md)
- [XML 'den veri kümesi yükleme](loading-a-dataset-from-xml.md)
- [XML 'den veri kümesi şema bilgilerini yükleme](loading-dataset-schema-information-from-xml.md)
- [Bir veri kümesinde XML kullanma](using-xml-in-a-dataset.md)
- [Veri kümeleri, DataTable ve DataView](index.md)
- [ADO.NET genel bakış](../ado-net-overview.md)
