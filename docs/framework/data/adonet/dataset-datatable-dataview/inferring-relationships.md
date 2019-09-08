---
title: İlişkilerin Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 4c9c13453e4a830fcda337e8163649ba6491a995
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785368"
---
# <a name="inferring-relationships"></a>İlişkilerin Çıkarımını Yapma
Tablo olarak gösterilen bir öğe, tablo olarak da gösterilen bir alt öğe içeriyorsa, iki tablo arasında bir <xref:System.Data.DataRelation> oluşturulur. Üst öğe için oluşturulan tabloya ve alt öğe için oluşturulan tabloya **ParentTableName_Id** adlı yeni bir sütun eklenir. Bu kimlik sütununun **ColumnMapping** özelliği **MappingType. Hidden**olarak ayarlanacak. Sütun üst tablo için otomatik olarak artan birincil anahtar olur ve iki tablo arasında **DataRelation** için kullanılacaktır. Eklenen kimlik sütununun veri türü, System. **String**olan diğer tüm çıkartılan sütunların veri türünden farklı olarak **System. Int32**olacaktır. Hem üst hem de alt tablolardaki yeni sütun kullanılarak **DeleteRule** = **Cascade** ilebirlikteoluşturulur.<xref:System.Data.ForeignKeyConstraint>  
  
 Örneğin, aşağıdaki XML 'i göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Çıkarım işlemi iki tablo oluşturacak: **Element1** ve **ChildElement1**.  
  
 **Element1** tablosunun iki sütunu olacaktır: **Element1_Id** ve **ChildElement2**. **Element1_Id** sütununun **ColumnMapping** özelliği **MappingType. Hidden**olarak ayarlanacak. **ChildElement2** sütununun **ColumnMapping** özelliği **MappingType. element**olarak ayarlanacak. **Element1_Id** sütunu, **Element1** tablosunun birincil anahtarı olarak ayarlanır.  
  
 **ChildElement1** tablosunda üç sütun olacak: **attr1**, **attr2** ve **Element1_Id**. **Attr1** ve **attr2** sütunlarının **ColumnMapping** özelliği **MappingType. Attribute**olarak ayarlanacak. **Element1_Id** sütununun **ColumnMapping** özelliği **MappingType. Hidden**olarak ayarlanacak.  
  
 Bir **DataRelation** ve **ForeignKeyConstraint** , her iki tablodan **Element1_Id** sütunları kullanılarak oluşturulacaktır.  
  
 **Veri kümesi** DocumentElement  
  
 **Tablosundan** Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Metin2|  
  
 **Tablosundan** ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|value1|value2|0|  
  
 **Nesnesinin** Element1_ChildElement1  
  
 **ParentTable:** Element1  
  
 **ParentColumn:** Element1_Id  
  
 **Childschema** ChildElement1  
  
 **ChildColumn:** Element1_Id  
  
 **Ble** Doğru  
  
 **ForeignKeyConstraint** Element1_ChildElement1  
  
 **Sütunuyla** Element1_Id  
  
 **ParentTable:** Element1  
  
 **Childschema** ChildElement1  
  
 **DeleteRule:** Seçilemez  
  
 **AcceptRejectRule:** Yok.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML’den DataSet İlişkisel Yapısını Çıkarma](inferring-dataset-relational-structure-from-xml.md)
- [XML’den DataSet Yükleme](loading-a-dataset-from-xml.md)
- [XML’den DataSet Schema Bilgilerini Yükleme](loading-dataset-schema-information-from-xml.md)
- [DataRelations’ı İç İçe Yerleştirme](nesting-datarelations.md)
- [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
