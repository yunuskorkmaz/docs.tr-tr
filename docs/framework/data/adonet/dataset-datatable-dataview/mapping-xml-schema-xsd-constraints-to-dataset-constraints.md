---
title: "Veri kümesi sınırlamaları için eşleme XML Şeması (XSD) kısıtlamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9ac8e64c02d96450d41233cfbe65e1db839df9e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>Veri kümesi sınırlamaları için eşleme XML Şeması (XSD) kısıtlamaları
XML Şeması Tanım Dili (XSD) kısıtlamaları öğeleri ve özniteliklerinin tanımladığı üzerinde belirtilmesine olanak sağlar. Bir XML Şeması ilişkisel şemada eşlerken bir <xref:System.Data.DataSet>, XML Şeması kısıtlamaları tablolar ve sütunlar içinde uygun ilişkisel kısıtlamalar eşlendiğinden **DataSet**.  
  
 Bu bölümde aşağıdaki XML Şeması kısıtlamaları eşleme ele alınmıştır:  
  
-   Benzersizlik kısıtlamasını kullanarak belirtilen **benzersiz** öğesi.  
  
-   Anahtar kısıtlamasını kullanarak belirtilen **anahtar** öğesi.  
  
-   Kullanarak belirtilen keyref kısıtlaması **keyref** öğesi.  
  
 Öğe veya öznitelik bir kısıtlama kullanarak bazı kısıtlamalar belge herhangi bir örneğine öğesinde değerleri belirtin. Örneğin, bir anahtar kısıtlaması bir **CustomerID** alt öğesi olan bir **müşteri** schema öğesinde gösterir değerlerini **CustomerID** alt öğesi olması gerekir herhangi bir belge örneğindeki benzersiz ve null değerlere izin verilmemektedir.  
  
 Kısıtlamaları da öğeleri ve özniteliklerinin bir belgede arasında belge içinde bir ilişkisi oluşturmak için belirtilebilir. Anahtar ve keyref kısıtlamaları şemada kısıtlamaları belge öğeleri ve özniteliklerinin arasında bir ilişki sonuçta belgenin içinde belirtmek için kullanılır.  
  
 Eşleme işlemini içinde oluşturulan tabloları uygun kısıtlamalar bu şema kısıtlamaları dönüştürür **DataSet**.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Veri kümesi sınırlamaları benzersiz XML Şeması (XSD) kısıtlamalar eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Benzersiz kısıtlamalar oluşturmak için kullanılan XML şema öğeleri açıklayan bir **DataSet**.  
  
 [Harita anahtar DataSet kısıtlamaları için XML Şeması (XSD) kısıtlamaları](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Anahtar kısıtlamalarını (benzersiz kısıtlamalar burada null değerlere izin vermiyor) oluşturmak için kullanılan XML şema öğeleri açıklanır bir **DataSet**.  
  
 [Harita keyref DataSet kısıtlamaları için XML Şeması (XSD) kısıtlamaları](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Keyref (yabancı anahtar) kısıtlamalar oluşturmak için kullanılan XML şema öğeleri açıklayan bir **DataSet**.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Türetilen DataSet ilişkisel yapısından XML Şeması (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 İlişkisel yapısı veya şema açıklayan bir **DataSet** XSD şema oluşturulur.  
  
 [DataSet ilişkileri XML Schema (XSD) oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Tablo sütunları arasındaki ilişkileri oluşturmak için kullanılan XML Şeması öğelerini açıklar bir **DataSet**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
