---
title: "XPath sorguları tanınan düğüm türleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: db309bf0d04dfab4fd9fbdd2c8b145c1705d8428
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
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
