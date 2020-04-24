---
title: XPathNavigator Kullanarak Düğüm Kümesinde Gezinme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
ms.openlocfilehash: 91115af03b635d7660721fac5ce8bd749953e4ff
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710576"
---
# <a name="node-set-navigation-using-xpathnavigator"></a>XPathNavigator Kullanarak Düğüm Kümesinde Gezinme
Sınıfın düğüm kümesi gezinti yöntemlerini kullanarak bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesindeki düğümlerin üzerinde gezinebilirsiniz. <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator> Sınıfın seçim yöntemlerinden biri tarafından döndürülen tüm düğümlerin veya seçili düğüm kümesinin üzerinde gezinebilirsiniz.  
  
## <a name="element-node-set-navigation"></a>Öğe düğümü kümesi gezintisi  
 Sınıfı <xref:System.Xml.XPath.XPathNavigator> , öğe düğümlerinde gezinmek için kullanılan birkaç yöntem sağlar. Aşağıdaki tabloda kullanılabilir gezinti yöntemleri ve bunların nasıl taşındıklarından bir açıklama gösterilmektedir; Bu, öznitelik ve ad alanı düğümlerinde gezinmek için kullanılan yöntemleri içermez.  
  
 Bir <xref:System.Xml.XPath.XPathNavigator> nesnedeki düğümleri seçme hakkında daha fazla bilgi için bkz. [XPathNavigator kullanarak XML verilerini seçme, değerlendirme ve eşleştirme](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md). Öznitelik ve ad alanı düğümlerine gitme hakkında daha fazla bilgi için bkz. [XPathNavigator kullanarak öznitelik ve ad alanı düğümü gezintisi](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|<xref:System.Xml.XPath.XPathNavigator> ' İ <xref:System.Xml.XPath.XPathNavigator> belirtilen konumuna gider.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|<xref:System.Xml.XPath.XPathNavigator> Öğesini geçerli düğümün alt düğümüne gider.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<xref:System.Xml.XPath.XPathNavigator> Geçerli düğümün ilk eşdüzey düğümüne gider.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<xref:System.Xml.XPath.XPathNavigator> Geçerli düğümün ilk alt düğümüne gider.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<xref:System.Xml.XPath.XPathNavigator> Belge düzeninde belirtilen öğeye gider.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|' Öğesini <xref:System.Xml.XPath.XPathNavigator> , belirtilen `ID` <xref:System.String>ile eşleşen bir değeri olan bir özniteliğine sahip düğüme taşımıştır.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<xref:System.Xml.XPath.XPathNavigator> Geçerli düğümün sonraki eşdüzey düğümüne gider.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|<xref:System.Xml.XPath.XPathNavigator> Öğesini geçerli düğümün üst düğümüne kaydırır.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<xref:System.Xml.XPath.XPathNavigator> Geçerli düğümün önceki eşdüzey düğümüne gider.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|<xref:System.Xml.XPath.XPathNavigator> Öğesini XML belgesinin kök düğümüne gider.|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a>Açıklamalar ve Işleme yönergesi düğüm gezintisi  
 Aşağıdaki <xref:System.Xml.XPath.XPathNavigator> sınıf yöntemleri, bir XML belgesindeki diğer düğümlerden açıklamalara veya işleme talimatlarına geçmek için geçerlidir.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Ayıklama](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
