---
description: 'Hakkında daha fazla bilgi edinin: XML şeması (XSD) kısıtlamalarını veri kümesi kısıtlamalarına eşleme'
title: XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: b1a958029e541b6ac95b5c509665005c9006adfa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651892"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme

XML şeması tanım dili (XSD), kısıtlama tanımladığı öğeler ve özniteliklerde kısıtlamaların belirtilmesini sağlar. Bir XML şemasını bir ' deki ilişkisel şemayla eşlerken <xref:System.Data.DataSet> , XML şeması kısıtlamaları **veri kümesindeki** tablolar ve sütunlarda uygun ilişkisel kısıtlamalara eşlenir.  
  
 Bu bölüm, aşağıdaki XML şeması kısıtlamalarının eşlemesini anlatmaktadır:  
  
- **Unique** öğesi kullanılarak belirtilen benzersizlik kısıtlaması.  
  
- **Key** öğesi kullanılarak belirtilen anahtar kısıtlaması.  
  
- **Keyref öğesi kullanılarak** belirtilen keyref kısıtlaması.  
  
 Bir öğe veya öznitelik üzerinde bir kısıtlama kullanarak, herhangi bir belgenin örneğindeki öğe değerleri üzerinde belirli kısıtlamalar belirtirsiniz. Örneğin, şemadaki bir **Müşteri** öğesinin **MüşteriNo** alt öğesinde bir anahtar kısıtlaması, **MüşteriNo** alt öğesinin değerlerinin herhangi bir belge örneğinde benzersiz olması gerektiğini ve null değerlere izin verilmediğini gösterir.  
  
 Belge içinde ilişki kurmak için bir belgedeki öğeler ve öznitelikler arasında da bir kısıtlama belirtilebilir. Anahtar ve keyref kısıtlamaları, belge içindeki kısıtlamaları belirtmek için şemada kullanılır ve belge öğeleri ile öznitelikler arasında bir ilişki elde edilir.  
  
 Eşleme işlemi, bu şema kısıtlamalarını **veri kümesi** içinde oluşturulan tablolardaki uygun kısıtlamalara dönüştürür.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Bir **veri kümesinde** benzersiz kısıtlamalar oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.  
  
 [Anahtar XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Bir **veri kümesinde** anahtar kısıtlamalarını (null değerlere izin verilmeyen benzersiz kısıtlamalar) oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.  
  
 [Keyref XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Bir **veri kümesinde** keyref (yabancı anahtar) kısıtlamalarını oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 XSD şemasından oluşturulan bir **veri kümesinin** ilişkisel yapısını veya şemasını açıklar.  
  
 [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](generating-dataset-relations-from-xml-schema-xsd.md)  
 Bir **veri kümesindeki** tablo sütunları arasında ilişki oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
