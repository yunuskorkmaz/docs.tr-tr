---
title: XML Belge Nesne Modeli (DOM) Hiyerarşisi
ms.date: 03/30/2017
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
ms.openlocfilehash: 24ef51a18392fe3034e64bd585d879941fca4b95
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718364"
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="de781-102">XML Belge Nesne Modeli (DOM) Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="de781-102">XML Document Object Model (DOM) Hierarchy</span></span>

<span data-ttu-id="de781-103">Aşağıdaki çizim, parantez içinde World Wide Web Konsorsiyumu (W3C) adı olan XML Belge Nesne Modeli (DOM) için sınıf hiyerarşisini ve ilgili olduğu sınıf adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="de781-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="de781-104">![XML Belge Nesne Modeli &#40;DOM&#41; hiyerarşisi](media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="de781-104">![XML Document Object Model &#40;DOM&#41; hierarchy](media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="de781-105">XML Belge Nesne Modeli (DOM) hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="de781-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="de781-106">Aşağıdaki sınıflar **XMLNode**'dan aktarılmaz:</span><span class="sxs-lookup"><span data-stu-id="de781-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
- <span data-ttu-id="de781-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="de781-107">**XmlImplementation**</span></span>  
  
- <span data-ttu-id="de781-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="de781-108">**XmlNamedNodeMap**</span></span>  
  
- <span data-ttu-id="de781-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="de781-109">**XmlNodeList**</span></span>  
  
- <span data-ttu-id="de781-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="de781-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="de781-111">**XmlImplementation** sınıfı bir XML belgesi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="de781-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="de781-112">Daha fazla bilgi için bkz. [XML belgesi oluşturma](xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="de781-112">For more information, see [XML Document Creation](xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="de781-113">**XmlNamedNodeMap** sınıfı, sıralanmamış bir düğüm kümesini işler.</span><span class="sxs-lookup"><span data-stu-id="de781-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="de781-114">Daha fazla bilgi için bkz. [ada veya dizine göre sıralanmamış düğüm alma](unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="de781-114">For more information, see [Unordered Node Retrieval by Name or Index](unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="de781-115">**XmlNodeList** sınıfı, sıralı bir düğüm listesini işler.</span><span class="sxs-lookup"><span data-stu-id="de781-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="de781-116">Daha fazla bilgi için bkz. [dizine göre sıralı düğüm alma](ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="de781-116">For more information, see [Ordered Node Retrieval by Index](ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="de781-117">**XmlNodeChangedEventArgs** sınıfı, **XmlDocument** üzerinde kayıtlı olay işleyicilerini işler.</span><span class="sxs-lookup"><span data-stu-id="de781-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="de781-118">Daha fazla bilgi için bkz. [XML belgesinde XmlNodeChangedEventArgs kullanılarak olay işleme](event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="de781-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="de781-119">**XmlLinkedNode** sınıfı **XMLNode**'dan devralır.</span><span class="sxs-lookup"><span data-stu-id="de781-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="de781-120">Amacı **XMLNode**'dan iki yöntemi geçersiz kılmalıdır: **Previouseşdüzey** ve **nexteşdüzey** yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="de781-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="de781-121">Bu geçersiz kılınan Yöntemler daha sonra devralınan ve **Xmlkarakterverisi**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference** ve **xmlprocessinginstruction** tarafından, önceki ve sonraki eşdüzey olan sınıflar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="de781-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de781-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de781-122">See also</span></span>

- [<span data-ttu-id="de781-123">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="de781-123">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
