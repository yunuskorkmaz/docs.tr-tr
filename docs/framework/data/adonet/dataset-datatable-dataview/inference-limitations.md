---
title: Çıkarım Sınırlamaları
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 308d2ffdd9e2cb16626861e25613657f341a4ccb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879651"
---
# <a name="inference-limitations"></a>Çıkarım Sınırlamaları
Çıkarma işleminin bir <xref:System.Data.DataSet> XML şemasından XML öğeleri kullanıma bağlı olarak farklı şemalar sonuçlanabilir. Örneğin, aşağıdaki XML belgeleri göz önünde bulundurun.  
  
 Document1:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Document2:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 Çıkarma işlemi "Document1 için" ürettiği bir **veri kümesi** "Element1" yinelenen bir öğe olduğu için "DocumentElement" ve "Element1" adlı bir tablo adı.  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|Element1_Text|  
|--------------------|  
|text1|  
|Text2|  
  
 Ancak, "Document2 için" çıkarımı işlemi ürettiği bir **veri kümesi** "NewDataSet" ve "DocumentElement." adlı bir tablo adı Öznitelikleri ve alt öğe yok olduğundan "Element1" bir sütun olarak algılanır.  
  
 **Veri kümesi:** NewDataSet  
  
 **Tablo:** DocumentElement  
  
|Element1|  
|--------------|  
|text1|  
  
 Bu iki XML belgeleri şemasına üretmek için hedeflenen, ancak çıkarımı işleminin her belge içerilen öğelerin göre çok farklı sonuçlar üretir.  
  
 Şema XML belgesinden oluşturulurken oluşabilecek Tutarsızlıklardan kaçınmak için bir şema XML Şeması Tanım Dili (XSD) veya XML verileri azaltılmış (XDR) yüklenirken kullanılarak açıkça belirtmeniz önerilir bir **veri kümesi** gelen XML. Açıkça belirtme hakkında daha fazla bilgi için bir **veri kümesi** XML Şeması, şema bakın [türetme DataSet ilişkisel yapısını XML Şeması (XSD) öğesinden](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML’den DataSet İlişkisel Yapısını Çıkarma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [XML’den DataSet Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [XML’den DataSet Schema Bilgilerini Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
