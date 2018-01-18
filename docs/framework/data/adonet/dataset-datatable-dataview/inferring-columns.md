---
title: "Sütunları çıkarımını yapma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 858a23fb8fec7b7f2eee95a1365d16e846beb548
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="inferring-columns"></a>Sütunları çıkarımını yapma
ADO.NET için tabloları olarak Infer hangi öğelerin bir XML belgesinden belirledi sonra bir <xref:System.Data.DataSet>, ardından bu tablo sütunlarını oluşturur. ADO.NET 2.0 sunulan her biri için kesin türü belirtilmiş veri türü oluşturur Yeni bir şema çıkarımı altyapısının **simpleType** öğesi. Önceki sürümlerde, veri türü bir oluşturulursa **simpleType** öğesi olan her zaman **xsd:string**.  
  
## <a name="migration-and-backward-compatibility"></a>Geçiş ve geriye dönük uyumluluk  
 **ReadXml** yöntemi alır türünde bir bağımsız değişken **InferSchema**. Bu bağımsız değişken çıkarım davranış önceki sürümleriyle uyumlu belirtmenize olanak tanır. Kullanılabilir değerler için **InferSchema** numaralandırma aşağıdaki tabloda gösterilmiştir.  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 Her zaman bir basit tür olarak çıkarımını yapma geriye dönük uyumluluk sağlar <xref:System.String>.  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 Kesin türü belirtilmiş veri türü oluşturur. Bir özel durum ile kullanılan döndürürse bir <xref:System.Data.DataTable>.  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 Herhangi bir satır içi şema yoksayar ve mevcut verileri okur <xref:System.Data.DataSet> şema.  
  
## <a name="attributes"></a>Öznitelikler  
 ' Da tanımlandığı gibi [çıkarımını yapma tabloları](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), öğenin özniteliklere sahip bir tablo olarak çıkarımı yapılan. Bu öğenin öznitelikleri tablosu için sütun olarak sonra olayla. **ColumnMapping** sütunların özellik ayarlanacak **MappingType.Attribute**, şemanın XML geri yazılmışsa sütun adları olarak öznitelikleri yazılmış emin olun. Özniteliklerin değerleri tablosunda bir satırı depolanır. Örneğin, aşağıdaki XML göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Çıkarma işlemi adlı bir tablo oluşturur **Element1** iki sütunlarla **attr1** ve **attr2**. **ColumnMapping** hem sütunların özellik ayarlanacak **MappingType.Attribute**.  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|Değer1|Value2|  
  
## <a name="elements-without-attributes-or-child-elements"></a>Öznitelik veya alt öğe olmadan öğeleri  
 Bir öğenin hiçbir alt öğe veya öznitelik varsa, bir sütun olarak olayla. **ColumnMapping** sütunun özelliği ayarlanacak **MappingType.Element**. Alt öğeler için metin tablosunda bir satırı depolanır. Örneğin, aşağıdaki XML göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Çıkarma işlemi adlı bir tablo oluşturur **Element1** iki sütunlarla **ChildElement1** ve **ChildElement2**. **ColumnMapping** hem sütunların özellik ayarlanacak **MappingType.Element**.  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Text1|Metin2|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML’den DataSet İlişkisel Yapısını Çıkarma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [XML’den DataSet Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [XML’den DataSet Schema Bilgilerini Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
