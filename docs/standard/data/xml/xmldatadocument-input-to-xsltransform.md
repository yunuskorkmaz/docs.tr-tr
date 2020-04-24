---
title: XslTransform’a XmlDataDocument Girişi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
ms.openlocfilehash: 5f2a7ef22eb07bb221b6a145db4453996ad8bf8c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709861"
---
# <a name="xmldatadocument-input-to-xsltransform"></a>XslTransform’a XmlDataDocument Girişi
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Sınıf .NET Framework 2,0 ' de kullanılmıyor. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfını kullanarak dönüşümler Için Genişletilebilir Stil sayfası DILI (XSLT) dönüşümleri gerçekleştirebilirsiniz. Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Microsoft .NET Framework XML belgelerindeki verilere erişim sağlamak için XML Belge Nesne Modeli (DOM) ve XML belgelerinde okuma, yazma ve gitme için ek sınıflar uygular. Ad alanında bulunan, ' deki ilişkisel verilerle eşitlenebilme özelliği ile verilere ilişkisel erişim sağlar <xref:System.Data.DataSet> <xref:System.Xml.XmlDataDocument> <xref:System.Xml> Yapılandırılmış XML ' nin ilişkisel temsili aracılığıyla aynı anda görüntüleyebilir ve işleyebilir <xref:System.Data.DataSet> ya da yarı yapılandırılmış XML 'ı öğesinin Dom temsili aracılığıyla yönetebilirsiniz. <xref:System.Xml.XmlDataDocument> <xref:System.Xml.XmlDataDocument> Bu nedenle, XML ve ilişkisel çalışma LDS sınırlarını keser.  
  
 Veriler ilişkisel bir yapıda depolanıyorsa ve bir XSLT dönüşümüne giriş olmasını istiyorsanız ilişkisel verileri bir <xref:System.Data.DataSet> öğesine yükleyebilir ve ile ilişkilendirebilirsiniz. <xref:System.Xml.XmlDataDocument> <xref:System.Xml.XPath.XPathNavigator>, ' A giriş, <xref:System.Xml.XPath.IXPathNavigable> arabirimi <xref:System.Xml.Xsl.XslTransform> <xref:System.Xml.XmlDataDocument> aracılığıyla öğesine uygulanır. İlişkisel verileri alarak, bir <xref:System.Data.DataSet>öğesine yükleyerek ve içinde <xref:System.Xml.XmlDataDocument>eşitlemeyi kullanarak, ILIŞKISEL veriler artık üzerinde XSLT dönüştürmeleri gerçekleştirebilir.  
  
 İlişkisel verilere dönüşüm uygulama hakkında daha fazla bilgi için bkz. [DataSet 'e XSLT dönüşümü uygulama](../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDataDocument>
- [DataSet ve XmlDataDocument Eşitlemesi](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)
- [XslTransform Sınıfı ile XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [Dönüşümlerde XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [Dönüşümlerde XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [XslTransform’a XPathDocument Girişi](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [XslTransform’a XmlDocument Girişi](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
