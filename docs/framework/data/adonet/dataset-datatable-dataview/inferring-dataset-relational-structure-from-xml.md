---
title: XML’den DataSet İlişkisel Yapısını Çıkarma
ms.date: 03/30/2017
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
ms.openlocfilehash: fca50491120346dea3e09c82324225f2114380fc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177585"
---
# <a name="inferring-dataset-relational-structure-from-xml"></a>XML’den DataSet İlişkisel Yapısını Çıkarma

Öğesinin ilişkisel yapısı veya şeması <xref:System.Data.DataSet> tablo, sütun, kısıtlama ve ilişkilerinden oluşur. <xref:System.Data.DataSet>XML 'den yükleme yaparken, şema önceden tanımlanmış olabilir veya yüklenen XML 'den açık ya da çıkarım aracılığıyla oluşturulabilir. XML 'den bir öğesinin şemasını ve içeriğini yükleme hakkında daha fazla bilgi için <xref:System.Data.DataSet> , bkz. xml 'Den [veri kümesi yükleme](loading-a-dataset-from-xml.md) ve [XML 'Den veri kümesi şema bilgilerini yükleme](loading-dataset-schema-information-from-xml.md).  
  
 <xref:System.Data.DataSet>XML 'den bir şeması oluşturulduysa, tercih edilen yöntem, XML şeması tanım dili (xsd) kullanarak şemayı açıkça belirtmektir ( [XML ŞEMASıNDAN (xsd) veri kümesi Ilişkisel yapısını türetmede](deriving-dataset-relational-structure-from-xml-schema-xsd.md)açıklandığı gıbı) veya XML VERILERI azaltılmış (xdr). XML 'de XML şeması veya XDR şeması kullanılabilir değilse, öğesinin şeması <xref:System.Data.DataSet> XML öğelerinin ve özniteliklerin yapısından çıkarsanamıyor.  
  
 Bu bölümde <xref:System.Data.DataSet> , XML öğelerini ve özniteliklerini ve bunların yapısını ve ortaya çıkarılan şemayı gösteren şema çıkarımı kuralları açıklanmaktadır <xref:System.Data.DataSet> .  
  
 Bir XML belgesinde bulunan özniteliklerin hepsi çıkarım işlemine dahil edilmelidir. Ad alanı nitelikli öznitelikler, XML belgesi için önemli olan ancak şema için önemli olan meta verileri içerebilir <xref:System.Data.DataSet> . Kullanarak <xref:System.Data.DataSet.InferXmlSchema%2A> , çıkarım işlemi sırasında yok sayılacak ad alanlarını belirtebilirsiniz. Daha fazla bilgi için bkz. [XML 'Den veri kümesi şema bilgilerini yükleme](loading-dataset-schema-information-from-xml.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [DataSet Şema Çıkarımı İşleminin Özeti](summary-of-the-dataset-schema-inference-process.md)  
 XML 'nin şemasını göstermek için kurallara ilişkin üst düzey bir Özet sağlar <xref:System.Data.DataSet> .  
  
 [Tabloların Çıkarımını Yapma](inferring-tables.md)  
 İçinde tablo olarak çıkartılan XML öğelerini açıklar <xref:System.Data.DataSet> .  
  
 [Sütunların Çıkarımını Yapma](inferring-columns.md)  
 Tablo sütunları olarak gösterilen XML öğelerini ve özniteliklerini açıklar.  
  
 [İlişkilerin Çıkarımını Yapma](inferring-relationships.md)  
 <xref:System.Data.DataRelation> <xref:System.Data.ForeignKeyConstraint> İç içe yerleştirilmiş, çıkartılan tablolar için oluşturulan ve nesnelerini açıklar.  
  
 [Öğe Metni Çıkarımını Yapma](inferring-element-text.md)  
 XML öğelerinde metin için oluşturulan sütunları açıklar ve XML öğelerinde metin yok sayıldığında açıklar.  
  
 [Çıkarım Sınırlamaları](inference-limitations.md)  
 Şema çıkarımı kısıtlamalarını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)  
 <xref:System.Data.DataSet>NESNESININ XML verileriyle nasıl etkileşime gireceğini açıklar.  
  
 [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <xref:System.Data.DataSet>XML şeması tanım dili (xsd) şemasından oluşturulan bir öğesinin ilişkisel yapısını veya şemasını açıklar.  
  
 [ADO.NET’e Genel Bakış](../ado-net-overview.md)  
 ADO.NET mimarisini ve bileşenlerini ve bunların mevcut veri kaynaklarına erişmek ve uygulama verilerini yönetmek için nasıl kullanılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
