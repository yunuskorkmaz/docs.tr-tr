---
title: Tabloların Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 2c2a93d413f301dc3006b701e4bc7979a3fa7a1d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181837"
---
# <a name="inferring-tables"></a>Tabloların Çıkarımını Yapma
İçin bir şema çıkarımını yapma sırasında bir <xref:System.Data.DataSet> tablolar XML öğeleri temsil eden önce bir XML belgesinden ADO.NET belirler. Aşağıdaki XML yapıları için bir tabloyu neden **veri kümesi** şema:  
  
-   Öznitelikleri olan öğeleri  
  
-   Alt öğelerini  
  
-   Yinelenen öğeleri  
  
## <a name="elements-with-attributes"></a>Öznitelikleri olan öğeleri  
 İçinde belirtilen öznitelikler neden olan öğeler tabloları sonuçlandı. Örneğin, aşağıdaki XML göz önünde bulundurun:  
  
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
|Value2|text1|  
  
## <a name="elements-with-child-elements"></a>Alt öğelerini  
 Alt öğeleri sonucu olmayan öğeler tabloları sonuçlandı. Örneğin, aşağıdaki XML göz önünde bulundurun:  
  
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
|text1|  
  
 Belge veya kök öğe sonucu çıkarsanan tabloda öznitelikleri veya sütun olarak algılanır alt öğeleri varsa. Belge öğesi özniteliklere ve sütun olarak çıkarılan hiçbir alt öğeleri varsa öğe olarak algılanır bir **veri kümesi**. Örneğin, aşağıdaki XML göz önünde bulundurun:  
  
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
|text1|Text2|  
  
 Alternatif olarak, aşağıdaki XML göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Çıkarma işlemi ürettiği bir **veri kümesi** "" Element1."adlı bir tablo içeren DocumentElement" adlı  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|Değer1|Value2|  
  
## <a name="repeating-elements"></a>Yinelenen öğeleri  
 Tek bir çıkarsanan tablosundaki sonuç yineleyin öğeleri. Örneğin, aşağıdaki XML göz önünde bulundurun:  
  
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
|text1|  
|Text2|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML’den DataSet İlişkisel Yapısını Çıkarma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [XML’den DataSet Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [XML’den DataSet Schema Bilgilerini Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
