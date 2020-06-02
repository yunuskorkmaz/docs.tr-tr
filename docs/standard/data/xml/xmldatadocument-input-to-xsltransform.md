---
title: XslTransform’a XmlDataDocument Girişi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
ms.openlocfilehash: 01c6ba8b14f8de167892ee9eeaff615f1f9ca37d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290272"
---
# <a name="xmldatadocument-input-to-xsltransform"></a>XslTransform’a XmlDataDocument Girişi
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor. Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> . Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .  
  
 Microsoft .NET Framework XML belgelerindeki verilere erişim sağlamak için XML Belge Nesne Modeli (DOM) ve XML belgelerinde okuma, yazma ve gitme için ek sınıflar uygular. <xref:System.Xml.XmlDataDocument>Ad alanında bulunan, ' <xref:System.Xml> deki ilişkisel verilerle eşitlenebilme özelliği ile verilere ilişkisel erişim sağlar <xref:System.Data.DataSet> . Yapılandırılmış XML ' nin ilişkisel temsili aracılığıyla aynı anda görüntüleyebilir ve işleyebilir ya da <xref:System.Data.DataSet> yarı YAPıLANDıRıLMıŞ XML 'i ÖĞESININ Dom temsili aracılığıyla yönetebilirsiniz <xref:System.Xml.XmlDataDocument> . <xref:System.Xml.XmlDataDocument>Bu nedenle, XML ve ilişkisel çalışma LDS sınırlarını keser.  
  
 Veriler ilişkisel bir yapıda depolanıyorsa ve bir XSLT dönüşümüne giriş olmasını istiyorsanız ilişkisel verileri bir öğesine yükleyebilir <xref:System.Data.DataSet> ve ile ilişkilendirebilirsiniz <xref:System.Xml.XmlDataDocument> . , ' A <xref:System.Xml.XPath.XPathNavigator> giriş, <xref:System.Xml.Xsl.XslTransform> <xref:System.Xml.XmlDataDocument> arabirimi aracılığıyla öğesine uygulanır <xref:System.Xml.XPath.IXPathNavigable> . İlişkisel verileri alarak, bir öğesine yükleyerek <xref:System.Data.DataSet> ve içinde eşitlemeyi kullanarak, <xref:System.Xml.XmlDataDocument> ilişkisel veriler artık üzerinde XSLT dönüştürmeleri gerçekleştirebilir.  
  
 İlişkisel verilere dönüşüm uygulama hakkında daha fazla bilgi için bkz. [DataSet 'e XSLT dönüşümü uygulama](../../../framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDataDocument>
- [DataSet ve XmlDataDocument Eşitlemesi](../../../framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)
- [XslTransform Sınıfı ile XSLT Dönüşümleri](xslt-transformations-with-the-xsltransform-class.md)
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](xsltransform-class-implements-the-xslt-processor.md)
- [Dönüşümlerde XPathNavigator](xpathnavigator-in-transformations.md)
- [Dönüşümlerde XPathNodeIterator](xpathnodeiterator-in-transformations.md)
- [XslTransform’a XPathDocument Girişi](xpathdocument-input-to-xsltransform.md)
- [XslTransform’a XmlDocument Girişi](xmldocument-input-to-xsltransform.md)
