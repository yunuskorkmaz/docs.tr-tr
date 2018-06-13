---
title: Veri kümesi ilişkisel XML yapısından çıkarımını yapma
ms.date: 03/30/2017
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
ms.openlocfilehash: 6ded5e893ccca973f8be5f070f68d9d8c7e09678
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759689"
---
# <a name="inferring-dataset-relational-structure-from-xml"></a>Veri kümesi ilişkisel XML yapısından çıkarımını yapma
İlişkisel yapısı veya şema, bir <xref:System.Data.DataSet> tablolar, sütunlar, kısıtlamalar ve ilişkileri oluşur. Yüklenirken bir <xref:System.Data.DataSet> , XML'den şema önceden tanımlanmış ya da, açıkça veya yüklenen XML'den çıkarım aracılığıyla oluşturulamaz. Şema ve içeriğini yükleme hakkında daha fazla bilgi için bir <xref:System.Data.DataSet> , XML'den bkz [bir veri kümesini XML dosyası şuradan yükleniyor](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) ve [XML'den veri kümesi şema bilgileri yüklenirken](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).  
  
 Varsa şeması bir <xref:System.Data.DataSet> oluşturuluyor ya da XML Şeması Tanım Dili (XSD) kullanarak şemasını açıkça belirtmek için tercih edilen yöntem, XML'den olduğu (açıklandığı gibi [türetme DataSet ilişkisel yapısı XML Şeması'ndan (XSD) ](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)) veya XML verileri azaltılmış (XDR). XML, şeması XML Şeması veya XDR şema varsa <xref:System.Data.DataSet> XML öğeleri ve özniteliklerinin yapısından sonuçlandı.  
  
 Bu bölüm için kurallar açıklanmaktadır <xref:System.Data.DataSet> XML öğeleri ve öznitelikleri ve bunların yapısı ve olayla elde edilen göstererek şema çıkarım <xref:System.Data.DataSet> şema.  
  
 Tüm öznitelikleri bir XML belgesi mevcut Çıkarma işleminde yer alması gerekir. Namespace nitelenmiş öznitelikler için XML belgesi önemli meta veriler içerebilir ancak için <xref:System.Data.DataSet> şema. Kullanarak <xref:System.Data.DataSet.InferXmlSchema%2A>, çıkarma işlemi sırasında yok sayılacak ad alanları belirtebilirsiniz. Daha fazla bilgi için bkz: [XML'den veri kümesi şema bilgileri yüklenirken](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataSet Şema Çıkarımı İşleminin Özeti](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/summary-of-the-dataset-schema-inference-process.md)  
 Şeması çıkarımını yapma için kurallar üst düzey bir özeti verilmektedir bir <xref:System.Data.DataSet> XML'den.  
  
 [Tabloların Çıkarımını Yapma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)  
 Tablolarla olayla XML öğeleri açıklanır bir <xref:System.Data.DataSet>.  
  
 [Sütunların Çıkarımını Yapma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-columns.md)  
 XML öğeleri ve tablo sütun olarak algılanır öznitelikleri açıklanmaktadır.  
  
 [İlişkilerin Çıkarımını Yapma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-relationships.md)  
 Açıklar <xref:System.Data.DataRelation> ve <xref:System.Data.ForeignKeyConstraint> oluşturulan nesneler iç içe geçmiş için tabloları sonuçlandı.  
  
 [Öğe Metni Çıkarımını Yapma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-element-text.md)  
 XML öğeleri metin için oluşturulan sütunları ve ne zaman metin XML öğeleri yoksayılır açıklanmaktadır.  
  
 [Çıkarım Sınırlamaları](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inference-limitations.md)  
 Şema çıkarım sınırlamaları açıklanır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Açıklar nasıl <xref:System.Data.DataSet> nesne XML verileri ile etkileşim kurar.  
  
 [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 İlişkisel yapısı veya şema açıklayan bir <xref:System.Data.DataSet> XML Şeması Tanım Dili (XSD) şemadan oluşturulur.  
  
 [ADO.NET’e Genel Bakış](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 ADO.NET açıklar mimarisi ve bileşenleri ve bunları mevcut veri kaynaklarına erişmek ve uygulama verilerini yönetmek için kullanma.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
