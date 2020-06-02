---
title: XPathNavigator Kullanarak Düğüm Kümesinde Gezinme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
ms.openlocfilehash: 132154afdfd3e5bd6769bfcce338e598136e7515
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288764"
---
# <a name="node-set-navigation-using-xpathnavigator"></a><span data-ttu-id="7f778-102">XPathNavigator Kullanarak Düğüm Kümesinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="7f778-102">Node Set Navigation Using XPathNavigator</span></span>
<span data-ttu-id="7f778-103"><xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> Sınıfın düğüm kümesi gezinti yöntemlerini kullanarak bir veya nesnesindeki düğümlerin üzerinde gezinebilirsiniz <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="7f778-103">You can navigate over nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="7f778-104">Sınıfın seçim yöntemlerinden biri tarafından döndürülen tüm düğümlerin veya seçili düğüm kümesinin üzerinde gezinebilirsiniz <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="7f778-104">You can navigate over all the nodes or over a selected set of nodes returned by one of the selection methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="element-node-set-navigation"></a><span data-ttu-id="7f778-105">Öğe düğümü kümesi gezintisi</span><span class="sxs-lookup"><span data-stu-id="7f778-105">Element Node Set Navigation</span></span>  
 <span data-ttu-id="7f778-106"><xref:System.Xml.XPath.XPathNavigator>Sınıfı, öğe düğümlerinde gezinmek için kullanılan birkaç yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f778-106">The <xref:System.Xml.XPath.XPathNavigator> class provides several methods used to navigate element nodes.</span></span> <span data-ttu-id="7f778-107">Aşağıdaki tabloda kullanılabilir gezinti yöntemleri ve bunların nasıl taşındıklarından bir açıklama gösterilmektedir; Bu, öznitelik ve ad alanı düğümlerinde gezinmek için kullanılan yöntemleri içermez.</span><span class="sxs-lookup"><span data-stu-id="7f778-107">The following table shows the navigation methods available and a description of how they move; this does not include methods used to navigate attribute and namespace nodes.</span></span>  
  
 <span data-ttu-id="7f778-108">Bir nesnedeki düğümleri seçme hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> bkz. [XPATHNAVIGATOR kullanarak XML verilerini seçme, değerlendirme ve eşleştirme](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="7f778-108">For more information about selecting nodes in an <xref:System.Xml.XPath.XPathNavigator> object, see [Selecting, Evaluating and Matching XML Data using XPathNavigator](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span></span> <span data-ttu-id="7f778-109">Öznitelik ve ad alanı düğümlerine gitme hakkında daha fazla bilgi için bkz. [XPathNavigator kullanarak öznitelik ve ad alanı düğümü gezintisi](attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="7f778-109">For more information about navigating attribute and namespace nodes, see [Attribute and Namespace Node Navigation Using XPathNavigator](attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span></span>  
  
|<span data-ttu-id="7f778-110">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7f778-110">Method</span></span>|<span data-ttu-id="7f778-111">Description</span><span class="sxs-lookup"><span data-stu-id="7f778-111">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|<span data-ttu-id="7f778-112">' İ <xref:System.Xml.XPath.XPathNavigator> belirtilen konumuna gider <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="7f778-112">Moves the <xref:System.Xml.XPath.XPathNavigator> to the same position of the <xref:System.Xml.XPath.XPathNavigator> specified.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|<span data-ttu-id="7f778-113">Öğesini <xref:System.Xml.XPath.XPathNavigator> geçerli düğümün alt düğümüne gider.</span><span class="sxs-lookup"><span data-stu-id="7f778-113">Moves the <xref:System.Xml.XPath.XPathNavigator> to a child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<span data-ttu-id="7f778-114"><xref:System.Xml.XPath.XPathNavigator>Geçerli düğümün ilk eşdüzey düğümüne gider.</span><span class="sxs-lookup"><span data-stu-id="7f778-114">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<span data-ttu-id="7f778-115"><xref:System.Xml.XPath.XPathNavigator>Geçerli düğümün ilk alt düğümüne gider.</span><span class="sxs-lookup"><span data-stu-id="7f778-115">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<span data-ttu-id="7f778-116"><xref:System.Xml.XPath.XPathNavigator>Belge düzeninde belirtilen öğeye gider.</span><span class="sxs-lookup"><span data-stu-id="7f778-116">Moves the <xref:System.Xml.XPath.XPathNavigator> to the specified element in document order.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|<span data-ttu-id="7f778-117">' Öğesini, <xref:System.Xml.XPath.XPathNavigator> `ID` belirtilen ile eşleşen bir değeri olan bir özniteliğine sahip düğüme taşımıştır <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="7f778-117">Moves the <xref:System.Xml.XPath.XPathNavigator> to the node that has an attribute of type `ID` with a value that matches the given <xref:System.String>.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<span data-ttu-id="7f778-118"><xref:System.Xml.XPath.XPathNavigator>Geçerli düğümün sonraki eşdüzey düğümüne gider.</span><span class="sxs-lookup"><span data-stu-id="7f778-118">Moves the <xref:System.Xml.XPath.XPathNavigator> to the next sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|<span data-ttu-id="7f778-119">Öğesini <xref:System.Xml.XPath.XPathNavigator> geçerli düğümün üst düğümüne kaydırır.</span><span class="sxs-lookup"><span data-stu-id="7f778-119">Moves the <xref:System.Xml.XPath.XPathNavigator> to the parent node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<span data-ttu-id="7f778-120"><xref:System.Xml.XPath.XPathNavigator>Geçerli düğümün önceki eşdüzey düğümüne gider.</span><span class="sxs-lookup"><span data-stu-id="7f778-120">Moves the <xref:System.Xml.XPath.XPathNavigator> to the previous sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|<span data-ttu-id="7f778-121">Öğesini <xref:System.Xml.XPath.XPathNavigator> XML belgesinin kök düğümüne gider.</span><span class="sxs-lookup"><span data-stu-id="7f778-121">Moves the <xref:System.Xml.XPath.XPathNavigator> to the root node of the XML document.</span></span>|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a><span data-ttu-id="7f778-122">Açıklamalar ve Işleme yönergesi düğüm gezintisi</span><span class="sxs-lookup"><span data-stu-id="7f778-122">Comments and Processing Instruction Node Navigation</span></span>  
 <span data-ttu-id="7f778-123">Aşağıdaki <xref:System.Xml.XPath.XPathNavigator> sınıf yöntemleri, BIR XML belgesindeki diğer düğümlerden açıklamalara veya işleme talimatlarına geçmek için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7f778-123">The following <xref:System.Xml.XPath.XPathNavigator> class methods are valid for moving to comments or processing instructions from other nodes in an XML document.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a><span data-ttu-id="7f778-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f778-124">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="7f778-125">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="7f778-125">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="7f778-126">XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme</span><span class="sxs-lookup"><span data-stu-id="7f778-126">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="7f778-127">XPathNavigator Kullanarak XML Verilerini Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7f778-127">Extract XML Data Using XPathNavigator</span></span>](extract-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="7f778-128">XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="7f778-128">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
