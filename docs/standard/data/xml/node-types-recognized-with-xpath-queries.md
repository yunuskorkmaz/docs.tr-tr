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
# <a name="node-types-recognized-with-xpath-queries"></a><span data-ttu-id="7f131-102">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="7f131-102">Node Types Recognized with XPath Queries</span></span>
<span data-ttu-id="7f131-103">Bir XPath sorgusunda tanınan düğümlerin türleri Belge Nesne Modeli (DOM) içinde bulunan aynı düğüm türleri değildir.</span><span class="sxs-lookup"><span data-stu-id="7f131-103">The types of nodes recognized in an XPath query are not the same node types found in the Document Object Model (DOM).</span></span>  
  
## <a name="w3c-xpath-node-types"></a><span data-ttu-id="7f131-104">W3C XPath düğüm türleri</span><span class="sxs-lookup"><span data-stu-id="7f131-104">W3C XPath Node Types</span></span>  
 <span data-ttu-id="7f131-105">Bir XPath sorgusunda tanınan düğümlerin türleri Belge Nesne Modeli (DOM) içinde bulunan düğümlerin türleri değildir.</span><span class="sxs-lookup"><span data-stu-id="7f131-105">The types of nodes recognized in an XPath query are not the types of nodes found in the Document Object Model (DOM).</span></span> <span data-ttu-id="7f131-106">Aşağıda, <xref:System.Xml.XPath.XPathNodeType> sabit listesi tarafından temsil edilen XPath düğüm türleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7f131-106">The following are the XPath node types represented by the <xref:System.Xml.XPath.XPathNodeType> enumeration.</span></span>  
  
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
  
 <span data-ttu-id="7f131-107">Bu düğüm türleri, düğümlerin XML bilgi kümesinden türetildiği XPath veri modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="7f131-107">These node types are based on the XPath data model, where the nodes are derived from the XML Information Set.</span></span> <span data-ttu-id="7f131-108"><xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> Ve <xref:System.Xml.XPath.XPathNodeType.Whitespace> düğüm türleri, XPath veri modelinde açıklanan temel düğüm türleri için Microsoft .NET Framework uzantılarıdır.</span><span class="sxs-lookup"><span data-stu-id="7f131-108">The <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> and <xref:System.Xml.XPath.XPathNodeType.Whitespace> node types are Microsoft .NET Framework extensions to the base node types described in the XPath data model.</span></span>  
  
 <span data-ttu-id="7f131-109">Öznitelik düğümü türü, XPath veri modelinde DOM 'da olduğundan farklı bir şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f131-109">The attribute node type is used differently in the XPath data model than it is in the DOM.</span></span> <span data-ttu-id="7f131-110">XPath veri modelinde, öğe düğümü kendisiyle ilişkili bir öznitelik düğümleri kümesine sahiptir ve öğe düğümü her öznitelik düğümünün üst öğesidir.</span><span class="sxs-lookup"><span data-stu-id="7f131-110">In the XPath data model, the element node has a set of attribute nodes related to it and the element node is the parent of each attribute node.</span></span> <span data-ttu-id="7f131-111">Bununla birlikte, DOM 'da, öğe düğümü üst öğesi değil, sahip olur.</span><span class="sxs-lookup"><span data-stu-id="7f131-111">However, in the DOM, the element node is the owner and not the parent.</span></span> <span data-ttu-id="7f131-112">Her iki modelde da öznitelik ve ad alanı düğümleri, öğe düğümünün alt düğümleri olarak değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="7f131-112">In both models, attribute and namespace nodes are not considered child nodes of the element node.</span></span>  
  
 <span data-ttu-id="7f131-113">Ad alanı düğüm türü, XPath veri modeline bir ektir ve tanınan bir DOM düğüm türü değildir.</span><span class="sxs-lookup"><span data-stu-id="7f131-113">The namespace node type is an addition to the XPath data model and is not a recognized DOM node type.</span></span>  
  
 <span data-ttu-id="7f131-114">Öğe, öznitelik ve ad alanı düğümlerine gitme hakkında daha fazla bilgi için bkz. XPathNavigator ve [Attribute ve ad alanı düğüm gezintisi](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) kullanarak XPathNavigator konuları kullanılarak [gezinme](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) .</span><span class="sxs-lookup"><span data-stu-id="7f131-114">For more information about navigating element, attribute, and namespace nodes, see the [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) and [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f131-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f131-115">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="7f131-116">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="7f131-116">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="7f131-117">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="7f131-117">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="7f131-118">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="7f131-118">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="7f131-119">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="7f131-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="7f131-120">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="7f131-120">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="7f131-121">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="7f131-121">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
