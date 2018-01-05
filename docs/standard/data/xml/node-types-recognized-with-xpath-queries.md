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
# <a name="node-types-recognized-with-xpath-queries"></a><span data-ttu-id="4fe4c-102">XPath sorguları tanınan düğüm türleri</span><span class="sxs-lookup"><span data-stu-id="4fe4c-102">Node Types Recognized with XPath Queries</span></span>
<span data-ttu-id="4fe4c-103">Bir XPath sorgusu tanınan düğüm türlerini belge nesne modeli (DOM) bulunan aynı düğüm türleri değildir.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-103">The types of nodes recognized in an XPath query are not the same node types found in the Document Object Model (DOM).</span></span>  
  
## <a name="w3c-xpath-node-types"></a><span data-ttu-id="4fe4c-104">W3C XPath düğüm türleri</span><span class="sxs-lookup"><span data-stu-id="4fe4c-104">W3C XPath Node Types</span></span>  
 <span data-ttu-id="4fe4c-105">Bir XPath sorgusu tanınan düğüm türlerini belge nesne modeli (DOM) düğüm türleri değildir.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-105">The types of nodes recognized in an XPath query are not the types of nodes found in the Document Object Model (DOM).</span></span> <span data-ttu-id="4fe4c-106">Tarafından temsil edilen XPath düğüm türleri verilmiştir <xref:System.Xml.XPath.XPathNodeType> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-106">The following are the XPath node types represented by the <xref:System.Xml.XPath.XPathNodeType> enumeration.</span></span>  
  
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
  
 <span data-ttu-id="4fe4c-107">Bu düğüm türleri burada düğümleri kümesi XML bilgi elde edilen XPath veri modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-107">These node types are based on the XPath data model, where the nodes are derived from the XML Information Set.</span></span> <span data-ttu-id="4fe4c-108"><xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> Ve <xref:System.Xml.XPath.XPathNodeType.Whitespace> düğüm türleridir XPath veri modelinde açıklanan temel düğüm türleri için Microsoft .NET Framework uzantıları.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-108">The <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> and <xref:System.Xml.XPath.XPathNodeType.Whitespace> node types are Microsoft .NET Framework extensions to the base node types described in the XPath data model.</span></span>  
  
 <span data-ttu-id="4fe4c-109">Öznitelik düğümü türü DOM olandan farklı XPath veri modelinde kullanılır</span><span class="sxs-lookup"><span data-stu-id="4fe4c-109">The attribute node type is used differently in the XPath data model than it is in the DOM.</span></span> <span data-ttu-id="4fe4c-110">XPath veri modelindeki öğe düğümü ilgili öznitelik düğümleri kümesi vardır ve her öznitelik düğümünün üst öğesi düğümdür.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-110">In the XPath data model, the element node has a set of attribute nodes related to it and the element node is the parent of each attribute node.</span></span> <span data-ttu-id="4fe4c-111">Ancak, DOM'da sahibi ve üst öğe düğümü olur.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-111">However, in the DOM, the element node is the owner and not the parent.</span></span> <span data-ttu-id="4fe4c-112">Her iki modellerinde özniteliği ve ad alanı düğümleri öğesi düğümün alt öğelerinin dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-112">In both models, attribute and namespace nodes are not considered child nodes of the element node.</span></span>  
  
 <span data-ttu-id="4fe4c-113">Ad alanı düğüm türü bir XPath veri modeli eklemeyi ve tanınan bir DOM düğüm türü değil.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-113">The namespace node type is an addition to the XPath data model and is not a recognized DOM node type.</span></span>  
  
 <span data-ttu-id="4fe4c-114">Öğe, öznitelik ve ad alanı düğümleri gezinme hakkında daha fazla bilgi için bkz: [düğüm kümesi Gezinti kullanarak XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) ve [özniteliği ve Namespace düğümü Gezinti kullanarak XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) Konular.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-114">For more information about navigating element, attribute, and namespace nodes, see the [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) and [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fe4c-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4fe4c-115">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="4fe4c-116">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="4fe4c-116">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="4fe4c-117">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="4fe4c-117">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="4fe4c-118">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="4fe4c-118">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="4fe4c-119">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="4fe4c-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="4fe4c-120">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="4fe4c-120">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="4fe4c-121">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="4fe4c-121">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
