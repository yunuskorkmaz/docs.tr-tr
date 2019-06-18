---
title: XslTransform’a XmlDataDocument Girişi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 308725ecc139d3c95ddff6bdf2d75746750673ce
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170850"
---
# <a name="xmldatadocument-input-to-xsltransform"></a>XslTransform’a XmlDataDocument Girişi
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıfı .NET Framework 2. 0'kullanılmıyor. Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
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
