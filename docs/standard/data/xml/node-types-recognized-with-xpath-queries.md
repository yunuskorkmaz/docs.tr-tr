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
# <a name="node-types-recognized-with-xpath-queries"></a><span data-ttu-id="73e9b-103">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="73e9b-103">Node Types Recognized with XPath Queries</span></span>

<span data-ttu-id="73e9b-104">Bir XPath sorgusunda tanınan düğümlerin türleri Belge Nesne Modeli (DOM) içinde bulunan aynı düğüm türleri değildir.</span><span class="sxs-lookup"><span data-stu-id="73e9b-104">The types of nodes recognized in an XPath query are not the same node types found in the Document Object Model (DOM).</span></span>  
  
## <a name="w3c-xpath-node-types"></a><span data-ttu-id="73e9b-105">W3C XPath düğüm türleri</span><span class="sxs-lookup"><span data-stu-id="73e9b-105">W3C XPath Node Types</span></span>  

 <span data-ttu-id="73e9b-106">Bir XPath sorgusunda tanınan düğümlerin türleri Belge Nesne Modeli (DOM) içinde bulunan düğümlerin türleri değildir.</span><span class="sxs-lookup"><span data-stu-id="73e9b-106">The types of nodes recognized in an XPath query are not the types of nodes found in the Document Object Model (DOM).</span></span> <span data-ttu-id="73e9b-107">Aşağıda, sabit listesi tarafından temsil edilen XPath düğüm türleri verilmiştir <xref:System.Xml.XPath.XPathNodeType> .</span><span class="sxs-lookup"><span data-stu-id="73e9b-107">The following are the XPath node types represented by the <xref:System.Xml.XPath.XPathNodeType> enumeration.</span></span>  
  
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
  
 <span data-ttu-id="73e9b-108">Bu düğüm türleri, düğümlerin XML bilgi kümesinden türetildiği XPath veri modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="73e9b-108">These node types are based on the XPath data model, where the nodes are derived from the XML Information Set.</span></span> <span data-ttu-id="73e9b-109"><xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>Ve <xref:System.Xml.XPath.XPathNodeType.Whitespace> düğüm türleri, XPath veri modelinde açıklanan temel düğüm türleri Için Microsoft .NET Framework uzantılarıdır.</span><span class="sxs-lookup"><span data-stu-id="73e9b-109">The <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> and <xref:System.Xml.XPath.XPathNodeType.Whitespace> node types are Microsoft .NET Framework extensions to the base node types described in the XPath data model.</span></span>  
  
 <span data-ttu-id="73e9b-110">Öznitelik düğümü türü, XPath veri modelinde DOM 'da olduğundan farklı bir şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="73e9b-110">The attribute node type is used differently in the XPath data model than it is in the DOM.</span></span> <span data-ttu-id="73e9b-111">XPath veri modelinde, öğe düğümü kendisiyle ilişkili bir öznitelik düğümleri kümesine sahiptir ve öğe düğümü her öznitelik düğümünün üst öğesidir.</span><span class="sxs-lookup"><span data-stu-id="73e9b-111">In the XPath data model, the element node has a set of attribute nodes related to it and the element node is the parent of each attribute node.</span></span> <span data-ttu-id="73e9b-112">Bununla birlikte, DOM 'da, öğe düğümü üst öğesi değil, sahip olur.</span><span class="sxs-lookup"><span data-stu-id="73e9b-112">However, in the DOM, the element node is the owner and not the parent.</span></span> <span data-ttu-id="73e9b-113">Her iki modelde da öznitelik ve ad alanı düğümleri, öğe düğümünün alt düğümleri olarak değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="73e9b-113">In both models, attribute and namespace nodes are not considered child nodes of the element node.</span></span>  
  
 <span data-ttu-id="73e9b-114">Ad alanı düğüm türü, XPath veri modeline bir ektir ve tanınan bir DOM düğüm türü değildir.</span><span class="sxs-lookup"><span data-stu-id="73e9b-114">The namespace node type is an addition to the XPath data model and is not a recognized DOM node type.</span></span>  
  
 <span data-ttu-id="73e9b-115">Öğe, öznitelik ve ad alanı düğümlerine gitme hakkında daha fazla bilgi için bkz. XPathNavigator ve [Attribute ve ad alanı düğüm gezintisi](attribute-and-namespace-node-navigation-using-xpathnavigator.md) kullanarak XPathNavigator konuları kullanılarak [gezinme](node-set-navigation-using-xpathnavigator.md) .</span><span class="sxs-lookup"><span data-stu-id="73e9b-115">For more information about navigating element, attribute, and namespace nodes, see the [Node Set Navigation Using XPathNavigator](node-set-navigation-using-xpathnavigator.md) and [Attribute and Namespace Node Navigation Using XPathNavigator](attribute-and-namespace-node-navigation-using-xpathnavigator.md) topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e9b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73e9b-116">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="73e9b-117">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="73e9b-117">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="73e9b-118">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="73e9b-118">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="73e9b-119">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="73e9b-119">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="73e9b-120">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="73e9b-120">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="73e9b-121">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="73e9b-121">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="73e9b-122">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="73e9b-122">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
