---
title: Tabloların Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 52ffd3fe90eb491dd01acf8538276cc828fdb309
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784484"
---
# <a name="inferring-tables"></a>Tabloların Çıkarımını Yapma
Bir XML belgesinden bir <xref:System.Data.DataSet> şemayı kullanırken, ADO.net ilk olarak tabloları temsil eden XML öğelerini belirler. Aşağıdaki XML yapıları **veri kümesi** şemasının bir tablosu ile sonuçlanır:  
  
- Öznitelikleri olan öğeler  
  
- Alt öğeleri olan öğeler  
  
- Yinelenen öğeler  
  
## <a name="elements-with-attributes"></a>Öznitelikleri olan öğeler  
 Üzerlerinde belirtilen öznitelikleri olan öğeler, çıkartılan tablolarla sonuçlanır. Örneğin, aşağıdaki XML 'i göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 Çıkarım işlemi, "Element1" adlı bir tablo oluşturur.  
  
 **Veri kümesi** DocumentElement  
  
 **Tablosundan** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|value1||  
|value2|Text1|  
  
## <a name="elements-with-child-elements"></a>Alt öğeleri olan öğeler  
 Alt öğeleri olan öğeler, çıkarılan tablolara neden olabilir. Örneğin, aşağıdaki XML 'i göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 Çıkarım işlemi, "Element1" adlı bir tablo oluşturur.  
  
 **Veri kümesi** DocumentElement  
  
 **Tablosundan** Element1  
  
|ChildElement1|  
|-------------------|  
|Text1|  
  
 Belge veya kök öğe, sütun olarak gösterilen öznitelikler veya alt öğeler içeriyorsa, çıkarılan bir tabloyla sonuçlanır. Belge öğesinin hiç özniteliği yoksa ve sütun olarak çıkarsanmayacak alt öğe yoksa, öğe bir **veri kümesi**olarak algılanır. Örneğin, aşağıdaki XML 'i göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 Çıkarım işlemi, "DocumentElement" adlı bir tablo oluşturur.  
  
 **Veri kümesi** NewDataSet  
  
 **Tablosundan** DocumentElement  
  
|Element1|Element2|  
|--------------|--------------|  
|Text1|Metin2|  
  
 Alternatif olarak, aşağıdaki XML 'i göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Çıkarım işlemi, "Element1" adlı bir tablo içeren "DocumentElement" adlı bir **veri kümesi** oluşturur.  
  
 **Veri kümesi** DocumentElement  
  
 **Tablosundan** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="repeating-elements"></a>Yinelenen öğeler  
 Yinelenen öğeler, ortaya çıkarılan tek bir tabloyla sonuçlanır. Örneğin, aşağıdaki XML 'i göz önünde bulundurun:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Çıkarım işlemi, "Element1" adlı bir tablo oluşturur.  
  
 **Veri kümesi** DocumentElement  
  
 **Tablosundan** Element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Metin2|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML’den DataSet İlişkisel Yapısını Çıkarma](inferring-dataset-relational-structure-from-xml.md)
- [XML’den DataSet Yükleme](loading-a-dataset-from-xml.md)
- [XML’den DataSet Schema Bilgilerini Yükleme](loading-dataset-schema-information-from-xml.md)
- [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
