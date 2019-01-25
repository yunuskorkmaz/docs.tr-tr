---
title: XPathNavigator kullanarak düğüm kümesinde gezinme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58adf0251fdc7427f493e8bf9947c081bfccd2a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618140"
---
# <a name="node-set-navigation-using-xpathnavigator"></a>XPathNavigator kullanarak düğüm kümesinde gezinme
Düğümler üzerinden gezinebileceğiniz bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> düğüm kümesi gezinme yöntemlerinden biri kullanılarak nesne <xref:System.Xml.XPath.XPathNavigator> sınıfı. Tüm düğümleri veya seçili bir dizi seçimi yöntemlerini biri tarafından döndürülen düğümü üzerinden gidebilirsiniz <xref:System.Xml.XPath.XPathNavigator> sınıfı.  
  
## <a name="element-node-set-navigation"></a>Öğe düğüm kümesinde gezinme  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı öğe düğümlerinin gezinmek için kullanılan çeşitli yöntemler sağlar. Aşağıdaki tabloda kullanılabilir gezinme yöntemlerinden ve nasıl hareket açıklaması gösterilmektedir; Bu öznitelik ve ad alanı düğümleri gezinmek için kullanılan yöntemleri içermez.  
  
 Düğümleri seçme hakkında daha fazla bilgi için bir <xref:System.Xml.XPath.XPathNavigator> nesne, bkz: [seçme, değerlendirme ve eşleştirme XPathNavigator kullanarak XML verilerini](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md). Öznitelik ve ad alanı düğümleri gezinme hakkında daha fazla bilgi için bkz. [özniteliği ve Namespace düğüm Gezinti XPathNavigator kullanarak](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> aynı konuma <xref:System.Xml.XPath.XPathNavigator> belirtilen.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümün alt düğümü için.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün ilk Eşdüzey Düğüm.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün ilk alt düğüm.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> belge sırayla belirtilen öğe için.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> bir öznitelik türü sahip düğümüne `ID` eşleşen bir değere sahip belirli <xref:System.String>.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün sonraki Eşdüzey Düğüm için.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> üst düğümünün geçerli düğüm için.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün önceki Eşdüzey Düğüm için.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|Taşır <xref:System.Xml.XPath.XPathNavigator> XML belgesi kök düğümü.|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a>Açıklamalar ve işlem yönergesi düğümü Gezinti  
 Aşağıdaki <xref:System.Xml.XPath.XPathNavigator> sınıf yöntemleridir yorumları taşıma veya diğer düğümleri bir XML belgesindeki yönergeleri işlemek için geçerli.  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Ayıklama](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
