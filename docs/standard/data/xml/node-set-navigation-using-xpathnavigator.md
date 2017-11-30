---
title: "Düğüm kümesi Gezinti XPathNavigator kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9ac0135227599d6a72813bcf57b209705545da66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="node-set-navigation-using-xpathnavigator"></a><span data-ttu-id="88eda-102">Düğüm kümesi Gezinti XPathNavigator kullanma</span><span class="sxs-lookup"><span data-stu-id="88eda-102">Node Set Navigation Using XPathNavigator</span></span>
<span data-ttu-id="88eda-103">Düğümler üzerinden gidebilirsiniz bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> düğüm kümesi gezinti yöntemlerini kullanarak nesne <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="88eda-103">You can navigate over nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="88eda-104">Tüm düğümleri veya seçili bir seçim yöntemlerini biri tarafından döndürülen düğümleri kümesi üzerinden gidebilirsiniz <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="88eda-104">You can navigate over all the nodes or over a selected set of nodes returned by one of the selection methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="element-node-set-navigation"></a><span data-ttu-id="88eda-105">Öğe düğüm kümesi gezinme</span><span class="sxs-lookup"><span data-stu-id="88eda-105">Element Node Set Navigation</span></span>  
 <span data-ttu-id="88eda-106"><xref:System.Xml.XPath.XPathNavigator> Sınıfı öğe düğümlerinin gezinmek için kullanılan birkaç yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="88eda-106">The <xref:System.Xml.XPath.XPathNavigator> class provides several methods used to navigate element nodes.</span></span> <span data-ttu-id="88eda-107">Aşağıdaki tabloda kullanılabilir Gezinti yöntemleri ve nasıl hareket açıklaması gösterir; Bu öznitelik ve ad alanı düğümleri gitmek için kullanılan yöntemler içermez.</span><span class="sxs-lookup"><span data-stu-id="88eda-107">The following table shows the navigation methods available and a description of how they move; this does not include methods used to navigate attribute and namespace nodes.</span></span>  
  
 <span data-ttu-id="88eda-108">Düğümler seçme hakkında daha fazla bilgi için bir <xref:System.Xml.XPath.XPathNavigator> nesne için bkz: [seçme, Evaluating ve eşleşen XML XPathNavigator kullanarak verileri](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="88eda-108">For more information about selecting nodes in an <xref:System.Xml.XPath.XPathNavigator> object, see [Selecting, Evaluating and Matching XML Data using XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span></span> <span data-ttu-id="88eda-109">Öznitelik ve ad alanı düğümleri gezinme hakkında daha fazla bilgi için bkz: [özniteliği ve Namespace düğümü Gezinti kullanarak XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="88eda-109">For more information about navigating attribute and namespace nodes, see [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span></span>  
  
|<span data-ttu-id="88eda-110">Yöntem</span><span class="sxs-lookup"><span data-stu-id="88eda-110">Method</span></span>|<span data-ttu-id="88eda-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88eda-111">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|<span data-ttu-id="88eda-112">Taşır <xref:System.Xml.XPath.XPathNavigator> aynı konumuna <xref:System.Xml.XPath.XPathNavigator> belirtilen.</span><span class="sxs-lookup"><span data-stu-id="88eda-112">Moves the <xref:System.Xml.XPath.XPathNavigator> to the same position of the <xref:System.Xml.XPath.XPathNavigator> specified.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|<span data-ttu-id="88eda-113">Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün bir alt düğümü.</span><span class="sxs-lookup"><span data-stu-id="88eda-113">Moves the <xref:System.Xml.XPath.XPathNavigator> to a child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<span data-ttu-id="88eda-114">Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün ilk eşdüzey düğümü.</span><span class="sxs-lookup"><span data-stu-id="88eda-114">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<span data-ttu-id="88eda-115">Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün ilk alt düğümü.</span><span class="sxs-lookup"><span data-stu-id="88eda-115">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<span data-ttu-id="88eda-116">Taşır <xref:System.Xml.XPath.XPathNavigator> belge sırada belirtilen öğeye.</span><span class="sxs-lookup"><span data-stu-id="88eda-116">Moves the <xref:System.Xml.XPath.XPathNavigator> to the specified element in document order.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|<span data-ttu-id="88eda-117">Taşır <xref:System.Xml.XPath.XPathNavigator> türü bir özniteliğin sahip düğümüne `ID` eşleşen bir değeri ile verilen <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="88eda-117">Moves the <xref:System.Xml.XPath.XPathNavigator> to the node that has an attribute of type `ID` with a value that matches the given <xref:System.String>.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<span data-ttu-id="88eda-118">Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün sonraki eşdüzey düğümü.</span><span class="sxs-lookup"><span data-stu-id="88eda-118">Moves the <xref:System.Xml.XPath.XPathNavigator> to the next sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|<span data-ttu-id="88eda-119">Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün üst düğüme.</span><span class="sxs-lookup"><span data-stu-id="88eda-119">Moves the <xref:System.Xml.XPath.XPathNavigator> to the parent node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<span data-ttu-id="88eda-120">Taşır <xref:System.Xml.XPath.XPathNavigator> geçerli düğümünün önceki Eşdüzey Düğüm için.</span><span class="sxs-lookup"><span data-stu-id="88eda-120">Moves the <xref:System.Xml.XPath.XPathNavigator> to the previous sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|<span data-ttu-id="88eda-121">Taşır <xref:System.Xml.XPath.XPathNavigator> XML belgesinin kök düğüme.</span><span class="sxs-lookup"><span data-stu-id="88eda-121">Moves the <xref:System.Xml.XPath.XPathNavigator> to the root node of the XML document.</span></span>|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a><span data-ttu-id="88eda-122">Yorumlar ve işleme yönergesi düğümü gezinme</span><span class="sxs-lookup"><span data-stu-id="88eda-122">Comments and Processing Instruction Node Navigation</span></span>  
 <span data-ttu-id="88eda-123">Aşağıdaki <xref:System.Xml.XPath.XPathNavigator> sınıfı yöntemleri yorumları taşıma veya bir XML belgesi diğer düğümlerden yönergeleri işlemek için geçerli.</span><span class="sxs-lookup"><span data-stu-id="88eda-123">The following <xref:System.Xml.XPath.XPathNavigator> class methods are valid for moving to comments or processing instructions from other nodes in an XML document.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a><span data-ttu-id="88eda-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="88eda-124">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="88eda-125">XPath veri modelini kullanarak işlem XML verileri</span><span class="sxs-lookup"><span data-stu-id="88eda-125">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="88eda-126">Özniteliği ve XPathNavigator kullanarak Namespace düğümü gezinme</span><span class="sxs-lookup"><span data-stu-id="88eda-126">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [<span data-ttu-id="88eda-127">XPathNavigator kullanarak XML veri ayıklamak</span><span class="sxs-lookup"><span data-stu-id="88eda-127">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="88eda-128">XML verilerini XPathNavigator kullanarak yazılan kesinlikle erişme</span><span class="sxs-lookup"><span data-stu-id="88eda-128">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
