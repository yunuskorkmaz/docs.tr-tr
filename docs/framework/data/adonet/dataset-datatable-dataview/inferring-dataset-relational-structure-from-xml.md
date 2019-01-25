---
title: XML'den DataSet ilişkisel yapısını çıkarma
ms.date: 03/30/2017
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
ms.openlocfilehash: f5cbbcd148f13a630398e870124803d482f63698
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587654"
---
# <a name="inferring-dataset-relational-structure-from-xml"></a>XML'den DataSet ilişkisel yapısını çıkarma
İlişkisel yapısını veya şema biri bir <xref:System.Data.DataSet> tablolar, sütunlar, kısıtlamalar ve ilişkileri oluşur. Yüklenirken bir <xref:System.Data.DataSet> XML'den, önceden şema veya da, açıkça veya yüklenmekte XML'den çıkarım yoluyla oluşturulamaz. Şema ve içeriğini yükleme hakkında daha fazla bilgi için bir <xref:System.Data.DataSet> , XML'den bkz [XML'den DataSet yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) ve [XML'den DataSet şema bilgileri yüklenirken](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).  
  
 Varsa şemasını bir <xref:System.Data.DataSet> oluşturuluyor ya da XML Şeması Tanım Dili (XSD) kullanarak şemasını açıkça belirtmek için tercih edilen yöntem, XML'den olduğu (açıklandığı [türetme DataSet ilişkisel yapısını gelen XML Şeması (XSD) ](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)) veya XML verileri azaltılmış (XDR). XML, şeması XML Şeması veya XDR şema varsa <xref:System.Data.DataSet> XML öğeleri ve özniteliklerinin yapısından sonuçlandı.  
  
 Bu bölüm için kurallar açıklanmaktadır <xref:System.Data.DataSet> XML öğeleri ve öznitelikleri ve bunların yapısı ve ortaya çıkan sonuç göstererek şema çıkarımı <xref:System.Data.DataSet> şema.  
  
 Çıkarım işlemde bir XML belgesinde mevcut tüm öznitelikler eklenmelidir. Namespace koşullu öznitelikleri, XML belgesi için önemli olan meta veri içerebilir ancak <xref:System.Data.DataSet> şema. Kullanarak <xref:System.Data.DataSet.InferXmlSchema%2A>, çıkarma işlemi sırasında yok sayılacak ad belirtebilirsiniz. Daha fazla bilgi için [XML'den DataSet şema bilgileri yüklenirken](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataSet Şema Çıkarımı İşleminin Özeti](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/summary-of-the-dataset-schema-inference-process.md)  
 Şemasını çıkarımını yapma için kuralları üst düzey bir özeti sağlar bir <xref:System.Data.DataSet> XML.  
  
 [Tabloların Çıkarımını Yapma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)  
 Tablolarda olarak çıkarılan XML öğeleri açıklar bir <xref:System.Data.DataSet>.  
  
 [Sütunların Çıkarımını Yapma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-columns.md)  
 XML öğeleri ve tablo sütun olarak algılanır öznitelikleri açıklar.  
  
 [İlişkilerin Çıkarımını Yapma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-relationships.md)  
 Açıklar <xref:System.Data.DataRelation> ve <xref:System.Data.ForeignKeyConstraint> oluşturulan nesneler iç içe için çıkarılan tabloları.  
  
 [Öğe Metni Çıkarımını Yapma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-element-text.md)  
 Metin XML öğeleri için oluşturulan sütunları ve metin XML öğeleri ne zaman yoksayılır açıklanmaktadır.  
  
 [Çıkarım Sınırlamaları](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inference-limitations.md)  
 Şema çıkarımı sınırlamaları açıklanmaktadır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Açıklayan nasıl <xref:System.Data.DataSet> nesne XML verileri ile etkileşime geçer.  
  
 [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 İlişkisel yapısını veya şema biri açıklar bir <xref:System.Data.DataSet> XML Şeması Tanım Dili (XSD) şemaya oluşturulur.  
  
 [ADO.NET’e Genel Bakış](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 ADO.NET açıklar mimarisi ve bileşenleri ve mevcut veri kaynaklarına erişim ve uygulama verilerini yönetmek için bunları kullanmayı öğrenin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
