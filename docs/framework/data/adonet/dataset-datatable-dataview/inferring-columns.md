---
title: Sütunların Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 53e77f624c5af8f61a32d5b1399d2728f32011a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034287"
---
# <a name="inferring-columns"></a>Sütunların Çıkarımını Yapma
ADO.NET için tabloları olarak çıkarsamak için hangi öğelerin bir XML belgesinden belirledi sonra bir <xref:System.Data.DataSet>, ardından bu tablonun sütunlarını algılar. ADO.NET 2.0 sunulan her biri için kesin türü belirtilmiş veri türünü çıkarsar yeni bir şema çıkarımı altyapısının **simpleType** öğesi. Önceki sürümlerde, veri türü bir çıkarsanan **simpleType** öğe bulunamadı her zaman **xsd: String'e**.  
  
## <a name="migration-and-backward-compatibility"></a>Geçiş ve geriye dönük uyumluluk  
 **ReadXml** yöntemi türünde bir bağımsız değişken alır **InferSchema**. Bu bağımsız değişken kesmesi davranışını önceki sürümleriyle uyumlu belirtmenizi sağlar. Kullanılabilir değerler için **InferSchema** numaralandırma aşağıdaki tabloda gösterilmiştir.  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 Her zaman olarak basit bir tür çıkarımını yapma geriye dönük uyumluluk sağlar <xref:System.String>.  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 Kesin türü belirtilmiş veri türü çıkarır. Birlikte kullanılırsa bir özel durum oluşturur. bir <xref:System.Data.DataTable>.  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 Herhangi bir satır içi şema yoksayar ve mevcut verileri okuyan <xref:System.Data.DataSet> şema.  
  
## <a name="attributes"></a>Öznitelikler  
 Sınıfında tanımlandığı gibi [tabloların çıkarımını yapma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), özniteliklere sahip bir öğe bir tablo çıkarılan. Bu öğenin öznitelikleri olarak tablonun sütunlarını ardından çıkarılan. **Columnmapping'in** sütunların özellik ayarlanacak **MappingType.Attribute**, XML şema geri yazılmışsa sütun adları öznitelik olarak yazılır emin olmak için. Öznitelik değerleri, tabloda bir satır depolanır. Örneğin, aşağıdaki XML göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Çıkarma işlemi adlı bir tablo oluşturur **Element1** iki sütunlu **attr1** ve **attr2**. **Columnmapping'in** hem sütunların özellik ayarlanacak **MappingType.Attribute**.  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|Değer1|Value2|  
  
## <a name="elements-without-attributes-or-child-elements"></a>Öğeler olmadan öznitelikleri veya alt öğeleri  
 Hiçbir alt öğeler veya öznitelikleri bir öğe varsa, bir sütun olarak çıkarılan. **Columnmapping'in** sütununun özellik ayarlanacak **MappingType.Element**. Alt öğelere metin tablosunda bir satıra depolanır. Örneğin, aşağıdaki XML göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Çıkarma işlemi adlı bir tablo oluşturur **Element1** iki sütunlu **ChildElement1** ve **ChildElement2**. **Columnmapping'in** hem sütunların özellik ayarlanacak **MappingType.Element**.  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|text1|Text2|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML’den DataSet İlişkisel Yapısını Çıkarma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [XML’den DataSet Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [XML’den DataSet Schema Bilgilerini Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
