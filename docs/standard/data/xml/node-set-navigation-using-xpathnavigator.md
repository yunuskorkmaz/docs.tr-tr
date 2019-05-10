---
title: XPathNavigator Kullanarak Düğüm Kümesinde Gezinme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44b102cf160dcc4b3f188451d42d3b8dbefa5d1f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590192"
---
# <a name="node-set-navigation-using-xpathnavigator"></a><span data-ttu-id="fe332-102">XPathNavigator Kullanarak Düğüm Kümesinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="fe332-102">Node Set Navigation Using XPathNavigator</span></span>
<span data-ttu-id="fe332-103">Düğümler üzerinden gezinebileceğiniz bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> düğüm kümesi gezinme yöntemlerinden biri kullanılarak nesne <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fe332-103">You can navigate over nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="fe332-104">Tüm düğümleri veya seçili bir dizi seçimi yöntemlerini biri tarafından döndürülen düğümü üzerinden gidebilirsiniz <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fe332-104">You can navigate over all the nodes or over a selected set of nodes returned by one of the selection methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="element-node-set-navigation"></a><span data-ttu-id="fe332-105">Öğe düğüm kümesinde gezinme</span><span class="sxs-lookup"><span data-stu-id="fe332-105">Element Node Set Navigation</span></span>  
 <span data-ttu-id="fe332-106"><xref:System.Xml.XPath.XPathNavigator> Sınıfı öğe düğümlerinin gezinmek için kullanılan çeşitli yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe332-106">The <xref:System.Xml.XPath.XPathNavigator> class provides several methods used to navigate element nodes.</span></span> <span data-ttu-id="fe332-107">Aşağıdaki tabloda kullanılabilir gezinme yöntemlerinden ve nasıl hareket açıklaması gösterilmektedir; Bu öznitelik ve ad alanı düğümleri gezinmek için kullanılan yöntemleri içermez.</span><span class="sxs-lookup"><span data-stu-id="fe332-107">The following table shows the navigation methods available and a description of how they move; this does not include methods used to navigate attribute and namespace nodes.</span></span>  
  
 <span data-ttu-id="fe332-108">Düğümleri seçme hakkında daha fazla bilgi için bir <xref:System.Xml.XPath.XPathNavigator> nesne, bkz: [seçme, değerlendirme ve eşleştirme XPathNavigator kullanarak XML verilerini](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="fe332-108">For more information about selecting nodes in an <xref:System.Xml.XPath.XPathNavigator> object, see [Selecting, Evaluating and Matching XML Data using XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span></span> <span data-ttu-id="fe332-109">Öznitelik ve ad alanı düğümleri gezinme hakkında daha fazla bilgi için bkz. [özniteliği ve Namespace düğüm Gezinti XPathNavigator kullanarak](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="fe332-109">For more information about navigating attribute and namespace nodes, see [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span></span>  
  
|<span data-ttu-id="fe332-110">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fe332-110">Method</span></span>|<span data-ttu-id="fe332-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe332-111">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|<span data-ttu-id="fe332-112">Taşır <xref:System.Xml.XPath.XPathNavigator> aynı konuma <xref:System.Xml.XPath.XPathNavigator> belirtilen.</span><span class="sxs-lookup"><span data-stu-id="fe332-112">Moves the <xref:System.Xml.XPath.XPathNavigator> to the same position of the <xref:System.Xml.XPath.XPathNavigator> specified.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|<span data-ttu-id="fe332-113">Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümün alt düğümü için.</span><span class="sxs-lookup"><span data-stu-id="fe332-113">Moves the <xref:System.Xml.XPath.XPathNavigator> to a child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<span data-ttu-id="fe332-114">Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün ilk Eşdüzey Düğüm.</span><span class="sxs-lookup"><span data-stu-id="fe332-114">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<span data-ttu-id="fe332-115">Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün ilk alt düğüm.</span><span class="sxs-lookup"><span data-stu-id="fe332-115">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<span data-ttu-id="fe332-116">Taşır <xref:System.Xml.XPath.XPathNavigator> belge sırayla belirtilen öğe için.</span><span class="sxs-lookup"><span data-stu-id="fe332-116">Moves the <xref:System.Xml.XPath.XPathNavigator> to the specified element in document order.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|<span data-ttu-id="fe332-117">Taşır <xref:System.Xml.XPath.XPathNavigator> bir öznitelik türü sahip düğümüne `ID` eşleşen bir değere sahip belirli <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="fe332-117">Moves the <xref:System.Xml.XPath.XPathNavigator> to the node that has an attribute of type `ID` with a value that matches the given <xref:System.String>.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<span data-ttu-id="fe332-118">Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün sonraki Eşdüzey Düğüm için.</span><span class="sxs-lookup"><span data-stu-id="fe332-118">Moves the <xref:System.Xml.XPath.XPathNavigator> to the next sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|<span data-ttu-id="fe332-119">Taşır <xref:System.Xml.XPath.XPathNavigator> üst düğümünün geçerli düğüm için.</span><span class="sxs-lookup"><span data-stu-id="fe332-119">Moves the <xref:System.Xml.XPath.XPathNavigator> to the parent node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<span data-ttu-id="fe332-120">Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün önceki Eşdüzey Düğüm için.</span><span class="sxs-lookup"><span data-stu-id="fe332-120">Moves the <xref:System.Xml.XPath.XPathNavigator> to the previous sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|<span data-ttu-id="fe332-121">Taşır <xref:System.Xml.XPath.XPathNavigator> XML belgesi kök düğümü.</span><span class="sxs-lookup"><span data-stu-id="fe332-121">Moves the <xref:System.Xml.XPath.XPathNavigator> to the root node of the XML document.</span></span>|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a><span data-ttu-id="fe332-122">Açıklamalar ve işlem yönergesi düğümü Gezinti</span><span class="sxs-lookup"><span data-stu-id="fe332-122">Comments and Processing Instruction Node Navigation</span></span>  
 <span data-ttu-id="fe332-123">Aşağıdaki <xref:System.Xml.XPath.XPathNavigator> sınıf yöntemleridir yorumları taşıma veya diğer düğümleri bir XML belgesindeki yönergeleri işlemek için geçerli.</span><span class="sxs-lookup"><span data-stu-id="fe332-123">The following <xref:System.Xml.XPath.XPathNavigator> class methods are valid for moving to comments or processing instructions from other nodes in an XML document.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a><span data-ttu-id="fe332-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe332-124">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="fe332-125">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="fe332-125">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="fe332-126">XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme</span><span class="sxs-lookup"><span data-stu-id="fe332-126">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="fe332-127">XPathNavigator Kullanarak XML Verilerini Ayıklama</span><span class="sxs-lookup"><span data-stu-id="fe332-127">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="fe332-128">XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="fe332-128">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
