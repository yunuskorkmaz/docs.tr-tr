---
title: XPathNavigator Kullanarak Düğüm Kümesinde Gezinme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
ms.openlocfilehash: 91115af03b635d7660721fac5ce8bd749953e4ff
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710576"
---
# <a name="node-set-navigation-using-xpathnavigator"></a><span data-ttu-id="939e9-102">XPathNavigator Kullanarak Düğüm Kümesinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="939e9-102">Node Set Navigation Using XPathNavigator</span></span>
<span data-ttu-id="939e9-103">Sınıfın düğüm kümesi gezinti yöntemlerini kullanarak bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesindeki düğümlerin üzerinde gezinebilirsiniz. <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="939e9-103">You can navigate over nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="939e9-104"><xref:System.Xml.XPath.XPathNavigator> Sınıfın seçim yöntemlerinden biri tarafından döndürülen tüm düğümlerin veya seçili düğüm kümesinin üzerinde gezinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="939e9-104">You can navigate over all the nodes or over a selected set of nodes returned by one of the selection methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="element-node-set-navigation"></a><span data-ttu-id="939e9-105">Öğe düğümü kümesi gezintisi</span><span class="sxs-lookup"><span data-stu-id="939e9-105">Element Node Set Navigation</span></span>  
 <span data-ttu-id="939e9-106">Sınıfı <xref:System.Xml.XPath.XPathNavigator> , öğe düğümlerinde gezinmek için kullanılan birkaç yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="939e9-106">The <xref:System.Xml.XPath.XPathNavigator> class provides several methods used to navigate element nodes.</span></span> <span data-ttu-id="939e9-107">Aşağıdaki tabloda kullanılabilir gezinti yöntemleri ve bunların nasıl taşındıklarından bir açıklama gösterilmektedir; Bu, öznitelik ve ad alanı düğümlerinde gezinmek için kullanılan yöntemleri içermez.</span><span class="sxs-lookup"><span data-stu-id="939e9-107">The following table shows the navigation methods available and a description of how they move; this does not include methods used to navigate attribute and namespace nodes.</span></span>  
  
 <span data-ttu-id="939e9-108">Bir <xref:System.Xml.XPath.XPathNavigator> nesnedeki düğümleri seçme hakkında daha fazla bilgi için bkz. [XPathNavigator kullanarak XML verilerini seçme, değerlendirme ve eşleştirme](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="939e9-108">For more information about selecting nodes in an <xref:System.Xml.XPath.XPathNavigator> object, see [Selecting, Evaluating and Matching XML Data using XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span></span> <span data-ttu-id="939e9-109">Öznitelik ve ad alanı düğümlerine gitme hakkında daha fazla bilgi için bkz. [XPathNavigator kullanarak öznitelik ve ad alanı düğümü gezintisi](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="939e9-109">For more information about navigating attribute and namespace nodes, see [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span></span>  
  
|<span data-ttu-id="939e9-110">Yöntem</span><span class="sxs-lookup"><span data-stu-id="939e9-110">Method</span></span>|<span data-ttu-id="939e9-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="939e9-111">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|<span data-ttu-id="939e9-112"><xref:System.Xml.XPath.XPathNavigator> ' İ <xref:System.Xml.XPath.XPathNavigator> belirtilen konumuna gider.</span><span class="sxs-lookup"><span data-stu-id="939e9-112">Moves the <xref:System.Xml.XPath.XPathNavigator> to the same position of the <xref:System.Xml.XPath.XPathNavigator> specified.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|<span data-ttu-id="939e9-113"><xref:System.Xml.XPath.XPathNavigator> Öğesini geçerli düğümün alt düğümüne gider.</span><span class="sxs-lookup"><span data-stu-id="939e9-113">Moves the <xref:System.Xml.XPath.XPathNavigator> to a child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<span data-ttu-id="939e9-114"><xref:System.Xml.XPath.XPathNavigator> Geçerli düğümün ilk eşdüzey düğümüne gider.</span><span class="sxs-lookup"><span data-stu-id="939e9-114">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<span data-ttu-id="939e9-115"><xref:System.Xml.XPath.XPathNavigator> Geçerli düğümün ilk alt düğümüne gider.</span><span class="sxs-lookup"><span data-stu-id="939e9-115">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<span data-ttu-id="939e9-116"><xref:System.Xml.XPath.XPathNavigator> Belge düzeninde belirtilen öğeye gider.</span><span class="sxs-lookup"><span data-stu-id="939e9-116">Moves the <xref:System.Xml.XPath.XPathNavigator> to the specified element in document order.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|<span data-ttu-id="939e9-117">' Öğesini <xref:System.Xml.XPath.XPathNavigator> , belirtilen `ID` <xref:System.String>ile eşleşen bir değeri olan bir özniteliğine sahip düğüme taşımıştır.</span><span class="sxs-lookup"><span data-stu-id="939e9-117">Moves the <xref:System.Xml.XPath.XPathNavigator> to the node that has an attribute of type `ID` with a value that matches the given <xref:System.String>.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<span data-ttu-id="939e9-118"><xref:System.Xml.XPath.XPathNavigator> Geçerli düğümün sonraki eşdüzey düğümüne gider.</span><span class="sxs-lookup"><span data-stu-id="939e9-118">Moves the <xref:System.Xml.XPath.XPathNavigator> to the next sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|<span data-ttu-id="939e9-119"><xref:System.Xml.XPath.XPathNavigator> Öğesini geçerli düğümün üst düğümüne kaydırır.</span><span class="sxs-lookup"><span data-stu-id="939e9-119">Moves the <xref:System.Xml.XPath.XPathNavigator> to the parent node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<span data-ttu-id="939e9-120"><xref:System.Xml.XPath.XPathNavigator> Geçerli düğümün önceki eşdüzey düğümüne gider.</span><span class="sxs-lookup"><span data-stu-id="939e9-120">Moves the <xref:System.Xml.XPath.XPathNavigator> to the previous sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|<span data-ttu-id="939e9-121"><xref:System.Xml.XPath.XPathNavigator> Öğesini XML belgesinin kök düğümüne gider.</span><span class="sxs-lookup"><span data-stu-id="939e9-121">Moves the <xref:System.Xml.XPath.XPathNavigator> to the root node of the XML document.</span></span>|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a><span data-ttu-id="939e9-122">Açıklamalar ve Işleme yönergesi düğüm gezintisi</span><span class="sxs-lookup"><span data-stu-id="939e9-122">Comments and Processing Instruction Node Navigation</span></span>  
 <span data-ttu-id="939e9-123">Aşağıdaki <xref:System.Xml.XPath.XPathNavigator> sınıf yöntemleri, bir XML belgesindeki diğer düğümlerden açıklamalara veya işleme talimatlarına geçmek için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="939e9-123">The following <xref:System.Xml.XPath.XPathNavigator> class methods are valid for moving to comments or processing instructions from other nodes in an XML document.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a><span data-ttu-id="939e9-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="939e9-124">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="939e9-125">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="939e9-125">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="939e9-126">XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme</span><span class="sxs-lookup"><span data-stu-id="939e9-126">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="939e9-127">XPathNavigator Kullanarak XML Verilerini Ayıklama</span><span class="sxs-lookup"><span data-stu-id="939e9-127">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="939e9-128">XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="939e9-128">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
