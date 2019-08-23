---
title: XslTransform’a XmlDataDocument Girişi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5c2fb203a1a6975d2b30e47528b15a9005a2583
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916018"
---
# <a name="xmldatadocument-input-to-xsltransform"></a>XslTransform’a XmlDataDocument Girişi
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Sınıf .NET Framework 2,0 ' de kullanılmıyor. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz. Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Microsoft .NET Framework XML belgelerindeki verilere erişim sağlamak için XML Belge Nesne Modeli (DOM) ve XML belgelerinde okuma, yazma ve gitme için ek sınıflar uygular. <xref:System.Xml> <xref:System.Data.DataSet>Ad alanında bulunan, ' deki ilişkisel verilerle eşitlenebilme özelliği ile verilere <xref:System.Xml.XmlDataDocument>ilişkisel erişim sağlar. Yapılandırılmış XML ' nin <xref:System.Data.DataSet> ilişkisel temsili aracılığıyla aynı anda görüntüleyebilir ve işleyebilir ya da yarı yapılandırılmış XML 'i <xref:System.Xml.XmlDataDocument>öğesinin Dom temsili aracılığıyla yönetebilirsiniz. <xref:System.Xml.XmlDataDocument> Bu nedenle, XML ve ilişkisel çalışma LDS sınırlarını keser.  
  
 Veriler ilişkisel bir yapıda depolanıyorsa ve bir XSLT dönüşümüne giriş olmasını istiyorsanız ilişkisel verileri bir <xref:System.Data.DataSet> öğesine yükleyebilir ve <xref:System.Xml.XmlDataDocument>ile ilişkilendirebilirsiniz. , ' A giriş, <xref:System.Xml.XPath.IXPathNavigable> arabirimi <xref:System.Xml.Xsl.XslTransform> <xref:System.Xml.XmlDataDocument> aracılığıyla öğesine uygulanır. <xref:System.Xml.XPath.XPathNavigator> İlişkisel verileri alarak, bir <xref:System.Data.DataSet>öğesine yükleyerek ve <xref:System.Xml.XmlDataDocument>içinde eşitlemeyi kullanarak, ilişkisel veriler artık üzerinde XSLT dönüştürmeleri gerçekleştirebilir.  
  
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
