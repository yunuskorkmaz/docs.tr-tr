---
title: Öğe Metni Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: d8d64c0cbb0aecf736a54fa6816e286ab7efa191
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203535"
---
# <a name="inferring-element-text"></a>Öğe Metni Çıkarımını Yapma
Bir öğe metin içeriyorsa ve tablo olarak (öznitelikler veya yinelenen öğeler içeren öğeler gibi) çıkarsmayacak alt öğe içermiyorsa, **TableName_Text** adlı yeni bir sütun, öğe için çıkartılan tabloya eklenir. Öğesinde bulunan metin, tablodaki bir satıra eklenir ve yeni sütunda depolanır. Yeni sütunun **ColumnMapping** özelliği **MappingType. simpleContent**olarak ayarlanır.  
  
 Örneğin, aşağıdaki XML 'i göz önünde bulundurun.  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 Çıkarım işlemi, iki sütunlu **Element1** adlı bir tablo oluşturur: **attr1** ve **Element1_Text**. **Attr1** sütununun **ColumnMapping** özelliği **MappingType. Attribute**olarak ayarlanacak. **Element1_Text** sütununun **ColumnMapping** özelliği **MappingType. simpleContent**olarak ayarlanır.  
  
 **Veri kümesi** DocumentElement  
  
 **Tablosundan** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|value1|Text1|  
  
 Bir öğe metin içeriyorsa, ancak aynı zamanda metin içeren alt öğelere sahipse, öğesinde içerilen metni depolamak için tabloya bir sütun eklenmez. Öğesinde içerilen metin yok sayılır, ancak alt öğelerdeki metin, tablodaki bir satıra dahil edilir. Örneğin, aşağıdaki XML 'i göz önünde bulundurun.  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 Çıkarım işlemi, **ChildElement1**adlı tek sütunlu **Element1** adlı bir tablo oluşturur. **ChildElement1** öğesinin metni, tablodaki bir satıra dahil edilir. Diğer metin yok sayılacak. **ChildElement1** sütununun **ColumnMapping** özelliği **MappingType. element**olarak ayarlanacak.  
  
 **Veri kümesi** DocumentElement  
  
 **Tablosundan** Element1  
  
|ChildElement1|  
|-------------------|  
|Metin2|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML’den DataSet İlişkisel Yapısını Çıkarma](inferring-dataset-relational-structure-from-xml.md)
- [XML’den DataSet Yükleme](loading-a-dataset-from-xml.md)
- [XML’den DataSet Schema Bilgilerini Yükleme](loading-dataset-schema-information-from-xml.md)
- [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
