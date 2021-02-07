---
description: 'Daha fazla bilgi edinin: XPath sorgularıyla tanınan düğüm türleri'
title: XPath Sorguları ile Tanınan Düğüm Türleri
ms.date: 03/30/2017
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
ms.openlocfilehash: 0fb310a7c2b353ecce14bb2f1a3ac8032fdde4d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675890"
---
# <a name="node-types-recognized-with-xpath-queries"></a>XPath Sorguları ile Tanınan Düğüm Türleri

Bir XPath sorgusunda tanınan düğümlerin türleri Belge Nesne Modeli (DOM) içinde bulunan aynı düğüm türleri değildir.  
  
## <a name="w3c-xpath-node-types"></a>W3C XPath düğüm türleri  

 Bir XPath sorgusunda tanınan düğümlerin türleri Belge Nesne Modeli (DOM) içinde bulunan düğümlerin türleri değildir. Aşağıda, sabit listesi tarafından temsil edilen XPath düğüm türleri verilmiştir <xref:System.Xml.XPath.XPathNodeType> .  
  
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
  
 Bu düğüm türleri, düğümlerin XML bilgi kümesinden türetildiği XPath veri modelini temel alır. <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>Ve <xref:System.Xml.XPath.XPathNodeType.Whitespace> düğüm türleri, XPath veri modelinde açıklanan temel düğüm türleri Için Microsoft .NET Framework uzantılarıdır.  
  
 Öznitelik düğümü türü, XPath veri modelinde DOM 'da olduğundan farklı bir şekilde kullanılır. XPath veri modelinde, öğe düğümü kendisiyle ilişkili bir öznitelik düğümleri kümesine sahiptir ve öğe düğümü her öznitelik düğümünün üst öğesidir. Bununla birlikte, DOM 'da, öğe düğümü üst öğesi değil, sahip olur. Her iki modelde da öznitelik ve ad alanı düğümleri, öğe düğümünün alt düğümleri olarak değerlendirilmez.  
  
 Ad alanı düğüm türü, XPath veri modeline bir ektir ve tanınan bir DOM düğüm türü değildir.  
  
 Öğe, öznitelik ve ad alanı düğümlerine gitme hakkında daha fazla bilgi için bkz. XPathNavigator ve [Attribute ve ad alanı düğüm gezintisi](attribute-and-namespace-node-navigation-using-xpathnavigator.md) kullanarak XPathNavigator konuları kullanılarak [gezinme](node-set-navigation-using-xpathnavigator.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verileri Seçme](select-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XPath İfadelerini Değerlendirme](evaluate-xpath-expressions-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Düğümleri Eşleştirme](matching-nodes-using-xpathnavigator.md)
- [XPath Sorguları ve Ad Alanları](xpath-queries-and-namespaces.md)
- [Derlenmiş XPath İfadeleri](compiled-xpath-expressions.md)
