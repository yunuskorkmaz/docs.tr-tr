---
title: DataSet Şema Çıkarımı İşleminin Özeti
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: b0dd22412ddda86aa2883a26353abb1516a94e17
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785948"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>DataSet Şema Çıkarımı İşleminin Özeti
Çıkarım işlemi ilk olarak XML belgesinden, hangi öğelerin tablo olarak gösterileceğini belirler. Kalan XML 'den, çıkarım işlemi bu tabloların sütunlarını belirler. İç içe tablolar için, çıkarım işlemi iç <xref:System.Data.DataRelation> içe <xref:System.Data.ForeignKeyConstraint> ve nesneler oluşturur.  
  
 Aşağıda, çıkarım kurallarının kısa bir özeti verilmiştir:  
  
- Öznitelikleri olan öğeler tablo olarak algılanır.  
  
- Alt öğeleri olan öğeler tablo olarak algılanır.  
  
- Yinelenen öğeler tek bir tablo olarak algılanır.  
  
- Belge, veya kök, öğe bir özniteliğe sahip değilse ve sütun olarak çıkarsanmayacak alt öğe yoksa, bir <xref:System.Data.DataSet>olarak algılanır. Aksi halde, belge öğesi tablo olarak algılanır.  
  
- Öznitelikler sütun olarak algılanır.  
  
- Öznitelikleri veya alt öğeleri olmayan ve tekrarsız öğeler sütun olarak algılanır.  
  
- Tablo olarak da gösterilen diğer öğeler içinde iç içe geçmiş tablolar olarak gösterilen öğeler için, iki tablo arasında iç içe bir **DataRelation** oluşturulur. Her iki tabloya da **TableName_Id** adlı yeni bir birincil anahtar sütunu eklenir ve **DataRelation**tarafından kullanılır. **TableName_Id** sütununu kullanan iki tablo arasında bir **ForeignKeyConstraint** oluşturulur.  
  
- Tablo olarak gösterilen ve metin içeren ancak hiç alt öğesi olmayan öğeler için, öğelerin her birinin metni için **TableName_Text** adlı yeni bir sütun oluşturulur. Bir öğe tablo olarak algılanır ve metin içeriyorsa, ancak alt öğeleri de varsa, metin yok sayılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML’den DataSet İlişkisel Yapısını Çıkarma](inferring-dataset-relational-structure-from-xml.md)
- [XML’den DataSet Yükleme](loading-a-dataset-from-xml.md)
- [XML’den DataSet Schema Bilgilerini Yükleme](loading-dataset-schema-information-from-xml.md)
- [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
