---
title: XPath sorguları tanınan düğüm türleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 005c5f4981a7ab1889678e391a6df6e0b7b43f71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569385"
---
# <a name="node-types-recognized-with-xpath-queries"></a>XPath sorguları tanınan düğüm türleri
Bir XPath sorgusu tanınan düğüm türlerini belge nesne modeli (DOM) bulunan aynı düğüm türleri değildir.  
  
## <a name="w3c-xpath-node-types"></a>W3C XPath düğüm türleri  
 Bir XPath sorgusu tanınan düğüm türlerini belge nesne modeli (DOM) düğüm türleri değildir. Tarafından temsil edilen XPath düğüm türleri verilmiştir <xref:System.Xml.XPath.XPathNodeType> numaralandırması.  
  
-   <xref:System.Xml.XPath.XPathNodeType.All>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Attribute>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Comment>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Element>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Namespace>  
  
-   <xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Root>  
  
-   <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Text>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Whitespace>  
  
 Bu düğüm türleri burada düğümleri kümesi XML bilgi elde edilen XPath veri modelini temel alır. <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> Ve <xref:System.Xml.XPath.XPathNodeType.Whitespace> düğüm türleridir XPath veri modelinde açıklanan temel düğüm türleri için Microsoft .NET Framework uzantıları.  
  
 Öznitelik düğümü türü DOM olandan farklı XPath veri modelinde kullanılır XPath veri modelindeki öğe düğümü ilgili öznitelik düğümleri kümesi vardır ve her öznitelik düğümünün üst öğesi düğümdür. Ancak, DOM'da sahibi ve üst öğe düğümü olur. Her iki modellerinde özniteliği ve ad alanı düğümleri öğesi düğümün alt öğelerinin dikkate alınmaz.  
  
 Ad alanı düğüm türü bir XPath veri modeli eklemeyi ve tanınan bir DOM düğüm türü değil.  
  
 Öğe, öznitelik ve ad alanı düğümleri gezinme hakkında daha fazla bilgi için bkz: [düğüm kümesi Gezinti kullanarak XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) ve [özniteliği ve Namespace düğümü Gezinti kullanarak XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) Konular.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XPathNavigator Kullanarak XML Verileri Seçme](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [XPathNavigator Kullanarak XPath İfadelerini Değerlendirme](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [XPathNavigator Kullanarak Düğümleri Eşleştirme](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [XPath Sorguları ve Ad Alanları](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Derlenmiş XPath İfadeleri](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
