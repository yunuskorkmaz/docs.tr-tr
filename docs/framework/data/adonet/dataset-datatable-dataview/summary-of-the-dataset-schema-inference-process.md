---
title: DataSet Şema Çıkarımı İşleminin Özeti
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 272e5762b7afd9f3ab24cbdec5f31bb120364815
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116070"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>DataSet Şema Çıkarımı İşleminin Özeti
Çıkarım işlemi önce hangi öğelerin tablo olarak çıkarılan XML belgesinden belirler. Kalan XML'den çıkarımı işleminin bu tablonun sütunlarını belirler. İç içe tablolar için çıkarım işlem oluşturur iç içe geçmiş <xref:System.Data.DataRelation> ve <xref:System.Data.ForeignKeyConstraint> nesneleri.  
  
 Çıkarım kuralları kısa bir özeti aşağıda verilmiştir:  
  
-   Öznitelikleri olan öğeler, tablo olarak algılanır.  
  
-   Alt öğeleri olan öğeler, tablo olarak algılanır.  
  
-   Yinelenen öğeler tek bir tablo olarak algılanır.  
  
-   Belge veya kök öğe öznitelikleri ve sütun olarak çıkarılan hiçbir alt öğe varsa, olarak algılanır bir <xref:System.Data.DataSet>. Aksi takdirde, belge öğesi bir tablo olarak algılanır.  
  
-   Öznitelikleri sütun olarak algılanır.  
  
-   Hiçbir öznitelik veya alt öğeleri olan ve bu tekrarlamayın, öğeleri, sütunlar olarak algılanır.  
  
-   Ayrıca ortaya çıkan diğer öğeleri içinde iç içe geçmiş tablo olarak algılanan öğeler için farklı tabloları, iç içe bir **DataRelation** iki tablo arasında oluşturulur. Adlı yeni, birincil bir anahtar sütunu **Tablename_ıd** her iki tabloya eklenen ve tarafından kullanılan **DataRelation**. A **ForeignKeyConstraint** kullanarak iki tablo arasında oluşturulan **Tablename_ıd** sütun.  
  
-   Tablo olarak çıkarılan ve metin içeriyor ancak hiçbir alt öğeleri olan öğeler için yeni bir sütun adındaki **TableName_Text** metnini öğelerin her biri için oluşturulur. Tablo olarak algılanır ve metin ancak de alt öğeye sahip bir öğe, metin göz ardı edilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML’den DataSet İlişkisel Yapısını Çıkarma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [XML’den DataSet Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [XML’den DataSet Schema Bilgilerini Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
