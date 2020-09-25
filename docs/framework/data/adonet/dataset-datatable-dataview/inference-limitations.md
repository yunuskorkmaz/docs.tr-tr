---
title: Çıkarım Sınırlamaları
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 9d8191be137661200e1a6b84d68328c1202880ca
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172781"
---
# <a name="inference-limitations"></a>Çıkarım Sınırlamaları

XML 'deki bir şemayı işleme işlemi, <xref:System.Data.DataSet> her BELGEDEKI XML öğelerine bağlı olarak farklı şemalar oluşmasına neden olabilir. Örneğin, aşağıdaki XML belgelerini göz önünde bulundurun.  
  
 Document1  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Document2  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 "Document1" için, çıkarım işlemi "DocumentElement" adlı bir **veri kümesi** ve "Element1" de yinelenen bir öğe olduğu Için "Element1" adlı bir tablo oluşturur.  
  
 **Veri kümesi:** DocumentElement  
  
 **Tablo:** Element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Metin2|  
  
 Ancak, "document2" için çıkarım işlemi "NewDataSet" adlı bir **veri kümesi** ve "DocumentElement" adlı bir tablo oluşturur. "Element1", hiç özniteliği olmadığından ve alt öğeleri bulunmadığından sütun olarak algılanır.  
  
 **Veri kümesi:** NewDataSet  
  
 **Tablo:** DocumentElement  
  
|Element1|  
|--------------|  
|Text1|  
  
 Bu iki XML belgesi aynı şemayı üretmeye yönelik olabilir, ancak çıkarım işlemi her belgedeki öğeleri temel alan çok farklı sonuçlar üretir.  
  
 XML belgesinden şema oluştururken oluşabilecek uyuşmazlıkları önlemek için, XML 'den bir **veri kümesi** yüklerken XML şeması tanım DILI (xsd) veya XML verileri AZALTıLMıŞ (xdr) kullanarak bir şemayı açıkça belirtmenizi öneririz. XML şeması ile bir **veri kümesi** şemasını açıkça belirtme hakkında daha fazla bilgi için, bkz. [xml şemasından (xsd) DataSet ilişkisel yapısını türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML’den DataSet İlişkisel Yapısını Çıkarma](inferring-dataset-relational-structure-from-xml.md)
- [XML’den DataSet Yükleme](loading-a-dataset-from-xml.md)
- [XML’den DataSet Schema Bilgilerini Yükleme](loading-dataset-schema-information-from-xml.md)
- [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
