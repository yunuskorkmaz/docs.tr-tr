---
title: XPathNavigator Kullanarak Düğüm Kümesinde Gezinme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
ms.openlocfilehash: 132154afdfd3e5bd6769bfcce338e598136e7515
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288764"
---
# <a name="node-set-navigation-using-xpathnavigator"></a>XPathNavigator Kullanarak Düğüm Kümesinde Gezinme
<xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> Sınıfın düğüm kümesi gezinti yöntemlerini kullanarak bir veya nesnesindeki düğümlerin üzerinde gezinebilirsiniz <xref:System.Xml.XPath.XPathNavigator> . Sınıfın seçim yöntemlerinden biri tarafından döndürülen tüm düğümlerin veya seçili düğüm kümesinin üzerinde gezinebilirsiniz <xref:System.Xml.XPath.XPathNavigator> .  
  
## <a name="element-node-set-navigation"></a>Öğe düğümü kümesi gezintisi  
 <xref:System.Xml.XPath.XPathNavigator>Sınıfı, öğe düğümlerinde gezinmek için kullanılan birkaç yöntem sağlar. Aşağıdaki tabloda kullanılabilir gezinti yöntemleri ve bunların nasıl taşındıklarından bir açıklama gösterilmektedir; Bu, öznitelik ve ad alanı düğümlerinde gezinmek için kullanılan yöntemleri içermez.  
  
 Bir nesnedeki düğümleri seçme hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> bkz. [XPATHNAVIGATOR kullanarak XML verilerini seçme, değerlendirme ve eşleştirme](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md). Öznitelik ve ad alanı düğümlerine gitme hakkında daha fazla bilgi için bkz. [XPathNavigator kullanarak öznitelik ve ad alanı düğümü gezintisi](attribute-and-namespace-node-navigation-using-xpathnavigator.md).  
  
|Yöntem|Description|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|' İ <xref:System.Xml.XPath.XPathNavigator> belirtilen konumuna gider <xref:System.Xml.XPath.XPathNavigator> .|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|Öğesini <xref:System.Xml.XPath.XPathNavigator> geçerli düğümün alt düğümüne gider.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<xref:System.Xml.XPath.XPathNavigator>Geçerli düğümün ilk eşdüzey düğümüne gider.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<xref:System.Xml.XPath.XPathNavigator>Geçerli düğümün ilk alt düğümüne gider.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<xref:System.Xml.XPath.XPathNavigator>Belge düzeninde belirtilen öğeye gider.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|' Öğesini, <xref:System.Xml.XPath.XPathNavigator> `ID` belirtilen ile eşleşen bir değeri olan bir özniteliğine sahip düğüme taşımıştır <xref:System.String> .|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<xref:System.Xml.XPath.XPathNavigator>Geçerli düğümün sonraki eşdüzey düğümüne gider.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|Öğesini <xref:System.Xml.XPath.XPathNavigator> geçerli düğümün üst düğümüne kaydırır.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<xref:System.Xml.XPath.XPathNavigator>Geçerli düğümün önceki eşdüzey düğümüne gider.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|Öğesini <xref:System.Xml.XPath.XPathNavigator> XML belgesinin kök düğümüne gider.|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a>Açıklamalar ve Işleme yönergesi düğüm gezintisi  
 Aşağıdaki <xref:System.Xml.XPath.XPathNavigator> sınıf yöntemleri, BIR XML belgesindeki diğer düğümlerden açıklamalara veya işleme talimatlarına geçmek için geçerlidir.  
  
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
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme](attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Ayıklama](extract-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
