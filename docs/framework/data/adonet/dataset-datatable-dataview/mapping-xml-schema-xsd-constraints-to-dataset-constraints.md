---
title: XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: b0082b534b8df10ac5277cf2f5aa5b2d2e40c11b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204626"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
XML şeması tanım dili (XSD), kısıtlama tanımladığı öğeler ve özniteliklerde kısıtlamaların belirtilmesini sağlar. Bir XML şemasını bir <xref:System.Data.DataSet>' deki ilişkisel şemayla eşlerken, XML şeması kısıtlamaları **veri kümesindeki**tablolar ve sütunlarda uygun ilişkisel kısıtlamalara eşlenir.  
  
 Bu bölüm, aşağıdaki XML şeması kısıtlamalarının eşlemesini anlatmaktadır:  
  
- **Unique** öğesi kullanılarak belirtilen benzersizlik kısıtlaması.  
  
- **Key** öğesi kullanılarak belirtilen anahtar kısıtlaması.  
  
- Keyref öğesi kullanılarak belirtilen keyref kısıtlaması .  
  
 Bir öğe veya öznitelik üzerinde bir kısıtlama kullanarak, herhangi bir belgenin örneğindeki öğe değerleri üzerinde belirli kısıtlamalar belirtirsiniz. Örneğin, şemadaki bir **Müşteri** öğesinin **MüşteriNo** alt öğesinde bir anahtar kısıtlaması, **MüşteriNo** alt öğesinin değerlerinin herhangi bir belge örneğinde benzersiz olması gerektiğini ve null değerlere izin verilmediğini gösterir.  
  
 Belge içinde ilişki kurmak için bir belgedeki öğeler ve öznitelikler arasında da bir kısıtlama belirtilebilir. Anahtar ve keyref kısıtlamaları, belge içindeki kısıtlamaları belirtmek için şemada kullanılır ve belge öğeleri ile öznitelikler arasında bir ilişki elde edilir.  
  
 Eşleme işlemi, bu şema kısıtlamalarını **veri kümesi**içinde oluşturulan tablolardaki uygun kısıtlamalara dönüştürür.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Benzersiz XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Bir **veri kümesinde**benzersiz kısıtlamalar oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.  
  
 [Anahtar XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Bir **veri kümesinde**anahtar kısıtlamalarını (null değerlere izin verilmeyen benzersiz kısıtlamalar) oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.  
  
 [Keyref XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Bir **veri kümesinde**keyref (yabancı anahtar) kısıtlamalarını oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 XSD şemasından oluşturulan bir **veri kümesinin** ilişkisel yapısını veya şemasını açıklar.  
  
 [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](generating-dataset-relations-from-xml-schema-xsd.md)  
 Bir **veri kümesindeki**tablo sütunları arasında ilişki oluşturmak IÇIN kullanılan xml şema öğelerini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
