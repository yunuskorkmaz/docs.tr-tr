---
title: XML Belge Nesne Modeli (DOM) Hiyerarşisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 79078b16f0d56c40a3dcfeabaaed9b5cbb7753a0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64589836"
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="218ad-102">XML Belge Nesne Modeli (DOM) Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="218ad-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="218ad-103">Sınıf hiyerarşisi için XML belge nesne modeli (DOM), aşağıdaki çizimde, ilgili olduğu sınıf adıyla birlikte parantez içinde World Wide Web Consortium (W3C) adı.</span><span class="sxs-lookup"><span data-stu-id="218ad-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="218ad-104">![XML belge nesne modeli &#40;DOM&#41; hiyerarşi](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="218ad-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="218ad-105">XML belge nesne modeli (DOM) hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="218ad-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="218ad-106">Aşağıdaki sınıflar seçeneğinden devralmamanızı **XmlNode**:</span><span class="sxs-lookup"><span data-stu-id="218ad-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
- <span data-ttu-id="218ad-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="218ad-107">**XmlImplementation**</span></span>  
  
- <span data-ttu-id="218ad-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="218ad-108">**XmlNamedNodeMap**</span></span>  
  
- <span data-ttu-id="218ad-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="218ad-109">**XmlNodeList**</span></span>  
  
- <span data-ttu-id="218ad-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="218ad-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="218ad-111">**XmlImplementation** sınıfı, bir XML belgesi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="218ad-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="218ad-112">Daha fazla bilgi için [XML belgesi oluşturma](../../../../docs/standard/data/xml/xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="218ad-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="218ad-113">**XmlNamedNodeMap** sınıfı sırasız bir dizi düğümü işler.</span><span class="sxs-lookup"><span data-stu-id="218ad-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="218ad-114">Daha fazla bilgi için [ada veya dizine göre sırasız düğüm alma](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="218ad-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="218ad-115">**XmlNodeList** sınıfı işleme düğümleri sıralı bir listesi.</span><span class="sxs-lookup"><span data-stu-id="218ad-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="218ad-116">Daha fazla bilgi için [dizine göre sıralı düğüm alma](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="218ad-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="218ad-117">**XmlNodeChangedEventArgs** sınıfı işleme kayıtlı olay işleyicilerinin **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="218ad-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="218ad-118">Daha fazla bilgi için [XML belgesinde XmlNodeChangedEventArgs kullanarak olay işleme](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="218ad-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="218ad-119">**XmlLinkedNode** sınıfının devraldığı **XmlNode**.</span><span class="sxs-lookup"><span data-stu-id="218ad-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="218ad-120">İki yöntemleri geçersiz kılmak için amacı olan **XmlNode**: **PreviousSibling** ve **NextSibling** yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="218ad-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="218ad-121">Bu geçersiz kılınan yöntemler ardından devralınan ve tarafından kullanılan **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, ve **XmlProcessingInstruction**, önceki ve sonraki eşdüzey öğesi olan sınıfları şunlardır.</span><span class="sxs-lookup"><span data-stu-id="218ad-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="218ad-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="218ad-122">See also</span></span>

- [<span data-ttu-id="218ad-123">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="218ad-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
