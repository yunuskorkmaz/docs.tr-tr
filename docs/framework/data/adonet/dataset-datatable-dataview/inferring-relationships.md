---
title: İlişkileri çıkarımını yapma
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 9833966fa5a16bef70a6ae2b9ca618fde0e05fbb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759042"
---
# <a name="inferring-relationships"></a>İlişkileri çıkarımını yapma
Ayrıca bir tablo olarak algılanır bir alt öğesi bir tablo çıkarımı yapılan bir öğe varsa, bir <xref:System.Data.DataRelation> iki tablo arasında oluşturulur. Yeni bir sütun adıyla **ParentTableName_Id** üst öğe için oluşturulan tablo hem alt öğe için oluşturulan tablo eklenir. **ColumnMapping** bu kimlik sütunu özelliği ayarlanacak **MappingType.Hidden**. Sütunu bir otomatik artan tablo için birincil anahtar üst olacaktır ve kullanılacak **DataRelation** iki tablo arasında. Eklenen kimlik sütununun veri türü olacaktır **System.Int32**, diğer tüm çıkarsanan sütun veri türü olan **System.String**. A <xref:System.Data.ForeignKeyConstraint> ile **DeleteRule** = **Cascade** da yeni bir sütun üst ve alt tablolarda kullanılarak oluşturulacak.  
  
 Örneğin, aşağıdaki XML göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Çıkarma işlemi iki tablo oluşturur: **Element1** ve **ChildElement1**.  
  
 **Element1** tablosu iki sütuna sahip: **Element1_Id** ve **ChildElement2**. **ColumnMapping** özelliği **Element1_Id** sütun ayarlanacak **MappingType.Hidden**. **ColumnMapping** özelliği **ChildElement2** sütun ayarlanacak **MappingType.Element**. **Element1_Id** sütun birincil anahtarı olarak ayarlanacak **Element1** tablo.  
  
 **ChildElement1** tablo üç sütun bulunur: **attr1**, **attr2** ve **Element1_Id**. **ColumnMapping** özelliği için **attr1** ve **attr2** sütunlar ayarlanacak **MappingType.Attribute**. **ColumnMapping** özelliği **Element1_Id** sütun ayarlanacak **MappingType.Hidden**.  
  
 A **DataRelation** ve **ForeignKeyConstraint** kullanılarak oluşturulan **Element1_Id** her iki tablodan sütun.  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Metin2|  
  
 **Tablo:** ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|Değer1|Value2|0|  
  
 **DataRelation:** Element1_ChildElement1  
  
 **ParentTable:** Element1  
  
 **ParentColumn:** Element1_Id  
  
 **Geldiği:** ChildElement1  
  
 **ChildColumn:** Element1_Id  
  
 **İç içe:** True  
  
 **ForeignKeyConstraint:** Element1_ChildElement1  
  
 **Sütun:** Element1_Id  
  
 **ParentTable:** Element1  
  
 **Geldiği:** ChildElement1  
  
 **DeleteRule:** Cascade  
  
 **AcceptRejectRule:** yok  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML’den DataSet İlişkisel Yapısını Çıkarma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [XML’den DataSet Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [XML’den DataSet Schema Bilgilerini Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [DataRelations’ı İç İçe Yerleştirme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
