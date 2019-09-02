---
title: XML’den DataSet İlişkisel Yapısını Çıkarma
ms.date: 03/30/2017
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
ms.openlocfilehash: 9b1932807058777a532457c99efc49f3ddfdf4ae
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204810"
---
# <a name="inferring-dataset-relational-structure-from-xml"></a>XML’den DataSet İlişkisel Yapısını Çıkarma
Öğesinin <xref:System.Data.DataSet> ilişkisel yapısı veya şeması tablo, sütun, kısıtlama ve ilişkilerinden oluşur. XML <xref:System.Data.DataSet> 'den yükleme yaparken, şema önceden tanımlanmış olabilir veya yüklenen XML 'den açık ya da çıkarım aracılığıyla oluşturulabilir. XML 'den bir <xref:System.Data.DataSet> öğesinin şemasını ve içeriğini yükleme hakkında daha fazla bilgi için, bkz. xml 'den [veri kümesi yükleme](loading-a-dataset-from-xml.md) ve [XML 'den veri kümesi şema bilgilerini yükleme](loading-dataset-schema-information-from-xml.md).  
  
 XML 'den bir <xref:System.Data.DataSet> şeması oluşturulduysa, tercih edilen yöntem, XML şeması tanım dili (xsd) kullanarak şemayı açıkça belirtmektir ( [xml şemasından (xsd) DataSet ilişkisel yapısını türetmede](deriving-dataset-relational-structure-from-xml-schema-xsd.md)açıklandığı gibi) veya XML verileri azaltılmış (XDR). XML 'de XML şeması veya xdr şeması kullanılabilir değilse, öğesinin <xref:System.Data.DataSet> şeması XML öğelerinin ve özniteliklerin yapısından çıkarsanamıyor.  
  
 Bu bölümde, XML öğelerini ve <xref:System.Data.DataSet> özniteliklerini ve bunların yapısını ve ortaya çıkarılan <xref:System.Data.DataSet> şemayı gösteren şema çıkarımı kuralları açıklanmaktadır.  
  
 Bir XML belgesinde bulunan özniteliklerin hepsi çıkarım işlemine dahil edilmelidir. Ad alanı nitelikli öznitelikler, XML belgesi için önemli olan ancak <xref:System.Data.DataSet> şema için önemli olan meta verileri içerebilir. Kullanarak <xref:System.Data.DataSet.InferXmlSchema%2A>, çıkarım işlemi sırasında yok sayılacak ad alanlarını belirtebilirsiniz. Daha fazla bilgi için bkz. [XML 'Den veri kümesi şema bilgilerini yükleme](loading-dataset-schema-information-from-xml.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataSet Şema Çıkarımı İşleminin Özeti](summary-of-the-dataset-schema-inference-process.md)  
 XML 'nin şemasını <xref:System.Data.DataSet> göstermek için kurallara ilişkin üst düzey bir Özet sağlar.  
  
 [Tabloların Çıkarımını Yapma](inferring-tables.md)  
 İçinde tablo olarak çıkartılan XML öğelerini açıklar <xref:System.Data.DataSet>.  
  
 [Sütunların Çıkarımını Yapma](inferring-columns.md)  
 Tablo sütunları olarak gösterilen XML öğelerini ve özniteliklerini açıklar.  
  
 [İlişkilerin Çıkarımını Yapma](inferring-relationships.md)  
 İç içe yerleştirilmiş <xref:System.Data.ForeignKeyConstraint> , çıkartılan tablolar için oluşturulan venesneleriniaçıklar.<xref:System.Data.DataRelation>  
  
 [Öğe Metni Çıkarımını Yapma](inferring-element-text.md)  
 XML öğelerinde metin için oluşturulan sütunları açıklar ve XML öğelerinde metin yok sayıldığında açıklar.  
  
 [Çıkarım Sınırlamaları](inference-limitations.md)  
 Şema çıkarımı kısıtlamalarını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)  
 <xref:System.Data.DataSet> Nesnesinin XML verileriyle nasıl etkileşime gireceğini açıklar.  
  
 [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 XML şeması tanım dili (xsd) şemasından oluşturulan bir <xref:System.Data.DataSet> öğesinin ilişkisel yapısını veya şemasını açıklar.  
  
 [ADO.NET’e Genel Bakış](../ado-net-overview.md)  
 ADO.NET mimarisini ve bileşenlerini ve bunların mevcut veri kaynaklarına erişmek ve uygulama verilerini yönetmek için nasıl kullanılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
