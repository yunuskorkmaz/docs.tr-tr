---
title: Sütunların Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 45d27b78b5d83d333c16192e172e7b7e3dd88c10
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164707"
---
# <a name="inferring-columns"></a>Sütunların Çıkarımını Yapma

ADO.NET, bir XML belgesinden bir için tablo olarak hangi öğelerin çıkarması gerektiğini belirledikten sonra <xref:System.Data.DataSet> , bu tablolar için sütunları algılar. ADO.NET 2,0, her **simpleType** öğe için kesin olarak belirlenmiş bir veri türünü gösteren yeni bir şema çıkarımı altyapısı sunmuştur. Önceki sürümlerde, gösterilen bir **simpleType** öğenin veri türü her zaman **xsd: String**idi.  
  
## <a name="migration-and-backward-compatibility"></a>Geçiş ve geri uyumluluk  

 **ReadXml** yöntemi **ınsetype**türünde bir bağımsız değişken alır. Bu bağımsız değişken, önceki sürümlerle uyumlu çıkarım davranışı belirtmenize olanak tanır. **Inseschema** numaralandırması için kullanılabilir değerler aşağıdaki tabloda gösterilmiştir.  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 , Bir basit türü her zaman olarak değiştirerek geriye dönük uyumluluk sağlar <xref:System.String> .  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 Kesin tür belirtilmiş bir veri türünü haller. İle kullanılırsa bir özel durum oluşturur <xref:System.Data.DataTable> .  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 Herhangi bir satır içi şemayı yoksayar ve verileri var olan <xref:System.Data.DataSet> şemaya okur.  
  
## <a name="attributes"></a>Öznitelikler  

 [Tablolarda](inferring-tables.md)tanımlandığı gibi, öznitelikleri olan bir öğesi tablo olarak çıkarsolur. Daha sonra bu öğenin öznitelikleri tablo için sütun olarak algılanır. Şema XML 'e geri yazılmışsa sütun adlarının öznitelik olarak yazılmasını sağlamak için sütunların **ColumnMapping** özelliği **MappingType. Attribute**olarak ayarlanır. Özniteliklerin değerleri tablodaki bir satırda depolanır. Örneğin, aşağıdaki XML 'i göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Çıkarım işlemi, **Element1** adında, **attr1** ve **attr2**olmak üzere iki sütunlu bir tablo oluşturur. Her iki sütunun **ColumnMapping** özelliği **MappingType. Attribute**olarak ayarlanır.  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="elements-without-attributes-or-child-elements"></a>Öznitelikleri veya alt öğeleri olmayan öğeler  

 Bir öğenin alt öğesi veya özniteliği yoksa, sütun olarak algılanır. Sütunun **ColumnMapping** özelliği **MappingType. element**olarak ayarlanacak. Alt öğeler için metin, tablodaki bir satırda saklanır. Örneğin, aşağıdaki XML 'i göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Çıkarım işlemi, **Element1** adında, **ChildElement1** ve **ChildElement2**olmak üzere iki sütunlu bir tablo oluşturur. Her iki sütunun **ColumnMapping** özelliği **MappingType. element**olarak ayarlanır.  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Text1|Metin2|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML’den DataSet İlişkisel Yapısını Çıkarma](inferring-dataset-relational-structure-from-xml.md)
- [XML’den DataSet Yükleme](loading-a-dataset-from-xml.md)
- [XML’den DataSet Schema Bilgilerini Yükleme](loading-dataset-schema-information-from-xml.md)
- [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
