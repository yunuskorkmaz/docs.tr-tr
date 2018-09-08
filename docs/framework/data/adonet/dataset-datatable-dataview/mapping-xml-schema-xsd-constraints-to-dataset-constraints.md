---
title: XML Şeması (XSD) kısıtlamalarını DataSet kısıtlamaları ile eşleme
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: c9cd97535a0165b82f0823c1f17f621491d4255c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186961"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>XML Şeması (XSD) kısıtlamalarını DataSet kısıtlamaları ile eşleme
XML Şeması Tanım Dili (XSD) öğeleri ve öznitelikleri tanımlar belirtilmesi kısıtlamaları sağlar. Bir XML Şeması ilişkisel şemasında eşlerken bir <xref:System.Data.DataSet>, XML şema kısıtlamaları uygun ilişkisel tabloları ve sütunları kısıtlamalar eşleştirilmiş **veri kümesi**.  
  
 Bu bölümde, aşağıdaki XML şema kısıtlamaları eşleme ele alınmaktadır:  
  
-   Benzersizlik kısıtlamasını kullanarak belirtilen **benzersiz** öğesi.  
  
-   Anahtar kısıtlamasını kullanarak belirtilen **anahtar** öğesi.  
  
-   Kullanarak belirtilen keyref kısıtlama **keyref** öğesi.  
  
 Bir öğe veya öznitelik bir kısıtlama kullanarak belirli kısıtlamalara belgenin herhangi bir örneğindeki öğe değerlerini belirtin. Örneğin, bir anahtar kısıtlaması bir **CustomerID** alt öğesi bir **müşteri** şema öğesi gösterir değerlerini **CustomerID** alt öğesi olmalıdır. herhangi bir belge örneğindeki benzersiz ve null değerlere izin verilmemektedir.  
  
 Kısıtlamaları da arasında öğeleri ve özniteliklerinin belgede, belge içindeki bir ilişki kurmak için belirtilebilir. Anahtar ve keyref kısıtlamaları şemada kısıtlamaları belge öğeleri ve öznitelikleri arasında bir ilişki výsledek belgenin içinde belirtmek için kullanılır.  
  
 Bu şema kısıtlamaları eşleme işlemi içinde oluşturulmuş tablolarda uygun kısıtlamaları dönüştürür **veri kümesi**.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 İçinde benzersiz kısıtlamalar oluşturmak için kullanılan XML Şeması öğeleri açıklar bir **veri kümesi**.  
  
 [Anahtar XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 İçindeki anahtar kısıtlamaları (benzersiz kısıtlamalar burada null değerlere izin verilmez) oluşturmak için kullanılan XML Şeması öğeleri açıklar bir **veri kümesi**.  
  
 [Keyref XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Keyref (yabancı anahtar) kısıtlamalarını oluşturmak için kullanılan XML Şeması öğeleri açıklar bir **veri kümesi**.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 İlişkisel yapısını veya şema biri açıklar bir **veri kümesi** XSD şema oluşturuldu.  
  
 [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Tablo sütunlarını arasındaki ilişkileri oluşturmak için kullanılan XML Şeması öğeleri açıklar bir **veri kümesi**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
