---
title: "Çıkarım sınırlamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 98ea3d5fa4427b391ef06b3fc6ace9a05dfb819a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="inference-limitations"></a>Çıkarım sınırlamaları
Çıkarımını yapma işlemi bir <xref:System.Data.DataSet> XML Şeması, her bir belgenin XML öğeleri bağlı olarak farklı şemalarda sonuçlanabilir. Örneğin, aşağıdaki XML belgelerini göz önünde bulundurun.  
  
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
  
 Çıkarma işlemi "Document1 için" üreten bir **DataSet** "Element1" yinelenen bir öğe olduğundan "DocumentElement" ve "Element1," adlı bir tablo adında.  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|Element1_Text|  
|--------------------|  
|Metin1|  
|Metin2|  
  
 Ancak, "Document2 için" çıkarım işlem üreten bir **DataSet** "NewDataSet" ve "DocumentElement." adlı bir tablo adında Özniteliklere ve hiçbir alt öğeler içerdiğinden "Element1" bir sütun olarak algılanır.  
  
 **Veri kümesi:** NewDataSet  
  
 **Tablo:** DocumentElement  
  
|Element1|  
|--------------|  
|Metin1|  
  
 Bu iki XML belgeleri aynı şema üretmek için hedeflenen, ancak çıkarım işlemi her belgede bulunan öğeleri dayalı çok farklı sonuçlar üretir.  
  
 Bir XML belgesinden şema oluşturma sırasında oluşabilecek Tutarsızlıklardan kaçınmak için XML Şeması Tanım Dili (XSD) veya XML verileri azaltılmış (XDR) yüklenirken kullanarak bir şema açıkça belirtilmesi önerilir bir **DataSet** gelen XML. Açıkça belirtme hakkında daha fazla bilgi için bir **DataSet** XML Şeması şemasıyla bkz [türetme DataSet ilişkisel yapısı XML Şeması'ndan (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri kümesi ilişkisel XML yapısından çıkarımını yapma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Bir veri kümesini XML dosyası şuradan yükleniyor](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [XML'den veri kümesi şema bilgileri yükleniyor](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Bir veri kümesini XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Veri kümeleri, DataTable ve DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
