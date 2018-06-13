---
title: XML belge nesne modeli (DOM) hiyerarşisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5b4ca249928200ddfc9dcd133ac673261046fb2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570178"
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="326d0-102">XML belge nesne modeli (DOM) hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="326d0-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="326d0-103">Sınıf hiyerarşisi için XML belge nesne modeli (DOM), aşağıdaki çizimde gösterilmektedir World Wide Web Konsorsiyumu (W3C) ile ilgili olduğu sınıf adı ile birlikte parantez içinde adı.</span><span class="sxs-lookup"><span data-stu-id="326d0-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="326d0-104">![XML belge nesnesi modeli &#40;DOM&#41; hiyerarşi](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="326d0-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="326d0-105">XML belge nesne modeli (DOM) hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="326d0-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="326d0-106">Aşağıdaki sınıflar devralınmalıdır değil **XmlNode**:</span><span class="sxs-lookup"><span data-stu-id="326d0-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
-   <span data-ttu-id="326d0-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="326d0-107">**XmlImplementation**</span></span>  
  
-   <span data-ttu-id="326d0-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="326d0-108">**XmlNamedNodeMap**</span></span>  
  
-   <span data-ttu-id="326d0-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="326d0-109">**XmlNodeList**</span></span>  
  
-   <span data-ttu-id="326d0-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="326d0-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="326d0-111">**XmlImplementation** sınıfı, bir XML belgesi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="326d0-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="326d0-112">Daha fazla bilgi için bkz: [XML belgesi oluşturma](../../../../docs/standard/data/xml/xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="326d0-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="326d0-113">**XmlNamedNodeMap** sınıfı düğümler sırasız bir kümesini işler.</span><span class="sxs-lookup"><span data-stu-id="326d0-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="326d0-114">Daha fazla bilgi için bkz: [adı veya dizin tarafından sırasız düğümü alma](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="326d0-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="326d0-115">**XmlNodeList** sınıfı işler düğümleri sıralı bir listesi.</span><span class="sxs-lookup"><span data-stu-id="326d0-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="326d0-116">Daha fazla bilgi için bkz: [dizine göre sıralı düğüm alma](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="326d0-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="326d0-117">**XmlNodeChangedEventArgs** sınıfı işler kayıtlı olay işleyicileri **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="326d0-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="326d0-118">Daha fazla bilgi için bkz: [olay işleme XmlNodeChangedEventArgs kullanarak bir XML belgesi](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="326d0-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="326d0-119">**XmlLinkedNode** sınıfının devraldığı **XmlNode**.</span><span class="sxs-lookup"><span data-stu-id="326d0-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="326d0-120">İki yöntemleri geçersiz kılmak için amacı olan **XmlNode**: **PreviousSibling** ve **NextSibling** yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="326d0-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="326d0-121">Geçersiz kılınan bu yöntemleri sonra devralınan ve tarafından kullanılan **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, ve **XmlProcessingInstruction**, önceki ve sonraki eşdüzey öğesi sınıfları olduğu.</span><span class="sxs-lookup"><span data-stu-id="326d0-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="326d0-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="326d0-122">See Also</span></span>  
 [<span data-ttu-id="326d0-123">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="326d0-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
