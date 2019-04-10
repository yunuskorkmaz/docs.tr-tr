---
title: Öğe Metni Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 6ffe8f2fbf01fbe8dfa9d78f3dfb9e39b6e80b16
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224968"
---
# <a name="inferring-element-text"></a>Öğe Metni Çıkarımını Yapma
Bir öğenin metni içeren ve yeni bir sütun adıyla (öznitelikleri olan öğe) veya yinelenen öğeler gibi tablolar olarak çıkarılan için alt öğe yok **TableName_Text** öğe için ortaya çıkan tablosuna eklenir. Öğesinde bulunan metin tablosunda bir satıra eklenir ve yeni bir sütun depolanır. **Columnmapping'in** yeni sütunun özellik ayarlanacak **MappingType.SimpleContent**.  
  
 Örneğin, aşağıdaki XML göz önünde bulundurun.  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 Çıkarma işlemi adlı bir tablo oluşturur **Element1** iki sütunlu: **attr1** ve **Element1_Text**. **Columnmapping'in** özelliği **attr1** sütun ayarlanacak **MappingType.Attribute**. **Columnmapping'in** özelliği **Element1_Text** sütun ayarlanacak **MappingType.SimpleContent**.  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|Değer1|text1|  
  
 Bir öğenin metin içeriyor, ancak metin içeren alt öğeler de vardır, bir sütun öğesinde bulunan metin depolamaya yönelik tablo eklenmeyecek. Alt öğeleri metinde tablosunda bir satıra dahil ederken öğesinde bulunan metin yoksayılır. Örneğin, aşağıdaki XML göz önünde bulundurun.  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 Çıkarma işlemi adlı bir tablo oluşturur **Element1** adlı tek bir sütunu **ChildElement1**. Metni **ChildElement1** öğesi dahil edilecek tablosundaki bir satır. Diğer metin göz ardı edilir. **Columnmapping'in** özelliği **ChildElement1** sütun ayarlanacak **MappingType.Element**.  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|ChildElement1|  
|-------------------|  
|Text2|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML’den DataSet İlişkisel Yapısını Çıkarma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [XML’den DataSet Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [XML’den DataSet Schema Bilgilerini Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
