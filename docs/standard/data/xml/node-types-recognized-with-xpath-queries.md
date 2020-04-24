---
title: XPath Sorguları ile Tanınan Düğüm Türleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
ms.openlocfilehash: cc1aa668ccf6fc7f210f48a28cf76b364459c784
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710550"
---
# <a name="node-types-recognized-with-xpath-queries"></a>XPath Sorguları ile Tanınan Düğüm Türleri
Bir XPath sorgusunda tanınan düğümlerin türleri Belge Nesne Modeli (DOM) içinde bulunan aynı düğüm türleri değildir.  
  
## <a name="w3c-xpath-node-types"></a>W3C XPath düğüm türleri  
 Bir XPath sorgusunda tanınan düğümlerin türleri Belge Nesne Modeli (DOM) içinde bulunan düğümlerin türleri değildir. Aşağıda, <xref:System.Xml.XPath.XPathNodeType> sabit listesi tarafından temsil edilen XPath düğüm türleri verilmiştir.  
  
- <xref:System.Xml.XPath.XPathNodeType.All>  
  
- <xref:System.Xml.XPath.XPathNodeType.Attribute>  
  
- <xref:System.Xml.XPath.XPathNodeType.Comment>  
  
- <xref:System.Xml.XPath.XPathNodeType.Element>  
  
- <xref:System.Xml.XPath.XPathNodeType.Namespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>  
  
- <xref:System.Xml.XPath.XPathNodeType.Root>  
  
- <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.Text>  
  
- <xref:System.Xml.XPath.XPathNodeType.Whitespace>  
  
 Bu düğüm türleri, düğümlerin XML bilgi kümesinden türetildiği XPath veri modelini temel alır. <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> Ve <xref:System.Xml.XPath.XPathNodeType.Whitespace> düğüm türleri, XPath veri modelinde açıklanan temel düğüm türleri için Microsoft .NET Framework uzantılarıdır.  
  
 Öznitelik düğümü türü, XPath veri modelinde DOM 'da olduğundan farklı bir şekilde kullanılır. XPath veri modelinde, öğe düğümü kendisiyle ilişkili bir öznitelik düğümleri kümesine sahiptir ve öğe düğümü her öznitelik düğümünün üst öğesidir. Bununla birlikte, DOM 'da, öğe düğümü üst öğesi değil, sahip olur. Her iki modelde da öznitelik ve ad alanı düğümleri, öğe düğümünün alt düğümleri olarak değerlendirilmez.  
  
 Ad alanı düğüm türü, XPath veri modeline bir ektir ve tanınan bir DOM düğüm türü değildir.  
  
 Öğe, öznitelik ve ad alanı düğümlerine gitme hakkında daha fazla bilgi için bkz. XPathNavigator ve [Attribute ve ad alanı düğüm gezintisi](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) kullanarak XPathNavigator konuları kullanılarak [gezinme](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verileri Seçme](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XPath İfadelerini Değerlendirme](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Düğümleri Eşleştirme](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [XPath Sorguları ve Ad Alanları](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [Derlenmiş XPath İfadeleri](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
