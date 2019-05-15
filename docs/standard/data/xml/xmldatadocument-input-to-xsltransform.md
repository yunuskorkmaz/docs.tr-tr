---
title: XslTransform’a XmlDataDocument Girişi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 811c513e6c8c613801c0ca60c11a9e5577672183
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592759"
---
# <a name="xmldatadocument-input-to-xsltransform"></a>XslTransform’a XmlDataDocument Girişi
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 Microsoft .NET Framework XML belgeleri ve okuma, yazma ve XML belgelerinde gezinmek için ek sınıfları verilere erişim sağlamak için XML belge nesne modeli'nı (DOM) uygular. <xref:System.Xml.XmlDataDocument>Bölümüyle <xref:System.Xml> ad alanı, ilişkisel verilerle eşitleme olanağı ile ilişkisel verilere erişim sağlar <xref:System.Data.DataSet>. Aynı anda görüntüleyebilir ve ilişkisel temsili aracılığıyla yapılandırılmış XML işlemek <xref:System.Data.DataSet> veya yarı yapılandırılmış XML DOM temsili aracılığıyla <xref:System.Xml.XmlDataDocument>. <xref:System.Xml.XmlDataDocument> Sınırları XML ilişkisel dünyaları ve bu nedenle aştığında.  
  
 Veriler, ilişkisel bir yapıda depolanır ve girdi olmaya uygun bir XSLT dönüşümü istediğiniz, ilişkisel verileri yükleyebilir bir <xref:System.Data.DataSet> ilişkilendirin <xref:System.Xml.XmlDataDocument>. <xref:System.Xml.XPath.XPathNavigator>, Giriş <xref:System.Xml.Xsl.XslTransform>, üzerinde uygulanan <xref:System.Xml.XmlDataDocument> aracılığıyla <xref:System.Xml.XPath.IXPathNavigable> arabirimi. İlişkisel veri yararlanarak, içine yüklenirken bir <xref:System.Data.DataSet>ve içinde eşitleme kullanarak <xref:System.Xml.XmlDataDocument>, ilişkisel veriler üzerinde gerçekleştirilen XSLT dönüşümleri artık sahip olabilir.  
  
 İlişkisel verilere dönüşüm uygulamadan daha fazla bilgi için bkz: [bir veri kümesi için bir XSLT dönüştürme uygulama](../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDataDocument>
- [DataSet ve XmlDataDocument Eşitlemesi](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)
- [XslTransform Sınıfı ile XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [Dönüşümlerde XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [Dönüşümlerde XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [XslTransform’a XPathDocument Girişi](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [XslTransform’a XmlDocument Girişi](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
