---
title: Veri kümesi şemasını çıkarım işlem özeti
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 9bcc5ce1574eed60d2ef1aa35bdafe8c6050e44c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760277"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>Veri kümesi şemasını çıkarım işlem özeti
Çıkarım işlemi önce hangi öğelerin tabloları olarak çıkarımı yapılan XML belgesinden belirler. Kalan XML'den çıkarım işlemi bu tablo sütunlarını belirler. İç içe tablolar için çıkarım işlem oluşturur iç içe geçmiş <xref:System.Data.DataRelation> ve <xref:System.Data.ForeignKeyConstraint> nesneleri.  
  
 Çıkarım kuralları kısa bir özeti aşağıda verilmiştir:  
  
-   Özniteliklere sahip öğeler tablo olarak algılanır.  
  
-   Alt öğeleri olan öğeler tablo olarak algılanır.  
  
-   Yinelenen öğeler tek bir tablo olarak algılanır.  
  
-   Belge ya da kök öğesi özniteliklere ve sütun olarak ortaya alt öğe varsa, olarak algılanır bir <xref:System.Data.DataSet>. Aksi takdirde, belge öğesi bir tablo olarak algılanır.  
  
-   Öznitelikleri sütun olarak algılanır.  
  
-   Hiçbir öznitelik veya alt öğe varsa ve bu tekrarlamayın, öğeler sütun olarak algılanır.  
  
-   Ayrıca algılanır diğer öğeleri içinde iç içe tablo olarak algılanır öğelerin olarak tabloları, iç içe bir **DataRelation** iki tablo arasında oluşturulur. Adlı yeni, birincil bir anahtar sütunu **Tablename_ıd** her iki tabloyu eklenir ve tarafından kullanılan **DataRelation**. A **ForeignKeyConstraint** kullanarak iki tablo arasında oluşturulan **Tablename_ıd** sütun.  
  
-   Tablo olarak çıkarımı yapılan ve metin içeriyor ancak hiçbir alt öğelere sahip öğeleri için yeni bir sütun adında **TableName_Text** metnini öğelerin her biri için oluşturulur. Bir tablo olarak algılanır ve metin varsa ancak de alt öğeye sahip bir öğe, metin göz ardı edilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML’den DataSet İlişkisel Yapısını Çıkarma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [XML’den DataSet Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [XML’den DataSet Schema Bilgilerini Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
