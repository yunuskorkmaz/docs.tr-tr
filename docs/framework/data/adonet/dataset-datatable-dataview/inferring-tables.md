---
title: "Tabloları çıkarımını yapma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: dacf3518f77067a34b0da3a8e6438b813fca3912
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="inferring-tables"></a>Tabloları çıkarımını yapma
İçin bir şema çıkarımını yapma olduğunda bir <xref:System.Data.DataSet> hangi XML öğeleri tabloları temsil eden önce bir XML belgesinden ADO.NET belirler. Bir tablo için aşağıdaki XML yapıları sonucunda **DataSet** şeması:  
  
-   Öznitelikleri olan öğeleri  
  
-   Alt öğelerin  
  
-   Yinelenen öğeleri  
  
## <a name="elements-with-attributes"></a>Öznitelikleri olan öğeleri  
 Bunları belirtilen öznitelikler neden olan öğenin tabloları sonuçlandı. Örneğin, aşağıdaki XML göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 Çıkarma işlemi "Element1." adlı bir tablo oluşturur  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|Değer1||  
|Value2|Metin1|  
  
## <a name="elements-with-child-elements"></a>Alt öğelerin  
 Alt öğeler sonucu olan öğenin tabloları sonuçlandı. Örneğin, aşağıdaki XML göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 Çıkarma işlemi "Element1." adlı bir tablo oluşturur  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|ChildElement1|  
|-------------------|  
|Metin1|  
  
 Belge veya kök öğesi sonuç öznitelikleri ya da sütun olarak algılanır alt öğeleri varsa oluşturulursa bir tabloda. Belge öğenin özniteliklere ve sütun olarak ortaya alt öğeleri varsa öğe olarak algılanır bir **DataSet**. Örneğin, aşağıdaki XML göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 Çıkarma işlemi "DocumentElement." adlı bir tablo oluşturur  
  
 **Veri kümesi:** NewDataSet  
  
 **Tablo:** DocumentElement  
  
|Element1|Element2|  
|--------------|--------------|  
|Metin1|Metin2|  
  
 Alternatif olarak, aşağıdaki XML göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Çıkarma işlemi üreten bir **DataSet** "" Element1."adlı bir tablo içeriyor DocumentElement" adlı  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|Değer1|Value2|  
  
## <a name="repeating-elements"></a>Yinelenen öğeleri  
 Tek bir oluşturulursa tablo sonucunda yineleyin öğeleri. Örneğin, aşağıdaki XML göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Çıkarma işlemi "Element1." adlı bir tablo oluşturur  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|Element1_Text|  
|--------------------|  
|Metin1|  
|Metin2|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML’den DataSet İlişkisel Yapısını Çıkarma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [XML’den DataSet Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [XML’den DataSet Schema Bilgilerini Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
