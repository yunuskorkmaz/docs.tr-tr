---
title: İlişkilerin çıkarımını yapma
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 7dc3fb0c6098d636e640aaf52b72a404c1486492
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46288202"
---
# <a name="inferring-relationships"></a>İlişkilerin çıkarımını yapma
Tablo olarak ortaya çıkan bir öğe ayrıca bir tablo olarak ortaya çıkan bir alt öğe varsa bir <xref:System.Data.DataRelation> iki tablo arasında oluşturulur. Yeni bir sütun adıyla **ParentTableName_Id** üst öğe için oluşturulan tabloyu hem alt öğe için oluşturulan tabloyu eklenir. **Columnmapping'in** bu kimlik sütununun özellik ayarlanacak **MappingType.Hidden**. Sütun üst tablo için otomatik artırma birincil anahtarı olacaktır ve kullanılacak **DataRelation** iki tablo arasında. Eklenen kimlik sütununun veri türünün **System.Int32**, veri türü diğer tüm çıkarsanan sütun olduğu **System.String**. A <xref:System.Data.ForeignKeyConstraint> ile **DeleteRule** = **Cascade** ayrıca yeni bir sütun üst ve alt tablolarında kullanılarak oluşturulur.  
  
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
  
 **Element1** tablo iki sütun vardır: **Element1_Id** ve **ChildElement2**. **Columnmapping'in** özelliği **Element1_Id** sütun ayarlanacak **MappingType.Hidden**. **Columnmapping'in** özelliği **ChildElement2** sütun ayarlanacak **MappingType.Element**. **Element1_Id** sütun birincil anahtarı olarak ayarlanacak **Element1** tablo.  
  
 **ChildElement1** tablo üç sütun vardır: **attr1**, **attr2** ve **Element1_Id**. **Columnmapping'in** özelliği **attr1** ve **attr2** sütunları ayarlanacak **MappingType.Attribute**. **Columnmapping'in** özelliği **Element1_Id** sütun ayarlanacak **MappingType.Hidden**.  
  
 A **DataRelation** ve **ForeignKeyConstraint** kullanılarak oluşturulan **Element1_Id** her iki tablonun sütunlarından.  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Text2|  
  
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
  
 **DeleteRule:** basamakla  
  
 **AcceptRejectRule:** yok  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML’den DataSet İlişkisel Yapısını Çıkarma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [XML’den DataSet Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [XML’den DataSet Schema Bilgilerini Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [DataRelations’ı İç İçe Yerleştirme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
