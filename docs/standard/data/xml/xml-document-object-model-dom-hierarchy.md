---
title: XML Belge Nesne Modeli (DOM) Hiyerarşisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
ms.openlocfilehash: 1193d7631816fe9fbf7aa1984d79ef8e61d5da80
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709978"
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="c4fef-102">XML Belge Nesne Modeli (DOM) Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="c4fef-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="c4fef-103">Aşağıdaki çizim, parantez içinde World Wide Web Konsorsiyumu (W3C) adı olan XML Belge Nesne Modeli (DOM) için sınıf hiyerarşisini ve ilgili olduğu sınıf adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4fef-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="c4fef-104">![XML Belge Nesne Modeli &#40;Dom&#41; hiyerarşisi](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="c4fef-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="c4fef-105">XML Belge Nesne Modeli (DOM) hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="c4fef-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="c4fef-106">Aşağıdaki sınıflar **XMLNode**'dan aktarılmaz:</span><span class="sxs-lookup"><span data-stu-id="c4fef-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
- <span data-ttu-id="c4fef-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="c4fef-107">**XmlImplementation**</span></span>  
  
- <span data-ttu-id="c4fef-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="c4fef-108">**XmlNamedNodeMap**</span></span>  
  
- <span data-ttu-id="c4fef-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="c4fef-109">**XmlNodeList**</span></span>  
  
- <span data-ttu-id="c4fef-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="c4fef-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="c4fef-111">**XmlImplementation** sınıfı bir XML belgesi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c4fef-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="c4fef-112">Daha fazla bilgi için bkz. [XML belgesi oluşturma](../../../../docs/standard/data/xml/xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="c4fef-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="c4fef-113">**XmlNamedNodeMap** sınıfı, sıralanmamış bir düğüm kümesini işler.</span><span class="sxs-lookup"><span data-stu-id="c4fef-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="c4fef-114">Daha fazla bilgi için bkz. [ada veya dizine göre sıralanmamış düğüm alma](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="c4fef-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="c4fef-115">**XmlNodeList** sınıfı, sıralı bir düğüm listesini işler.</span><span class="sxs-lookup"><span data-stu-id="c4fef-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="c4fef-116">Daha fazla bilgi için bkz. [dizine göre sıralı düğüm alma](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="c4fef-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="c4fef-117">**XmlNodeChangedEventArgs** sınıfı, **XmlDocument**üzerinde kayıtlı olay işleyicilerini işler.</span><span class="sxs-lookup"><span data-stu-id="c4fef-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="c4fef-118">Daha fazla bilgi için bkz. [XML belgesinde XmlNodeChangedEventArgs kullanılarak olay işleme](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="c4fef-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="c4fef-119">**XmlLinkedNode** sınıfı **XMLNode**'dan devralır.</span><span class="sxs-lookup"><span data-stu-id="c4fef-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="c4fef-120">Amacı **XMLNode**'dan iki yöntemi geçersiz kılmalıdır: **Previouseşdüzey** ve **nexteşdüzey** yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="c4fef-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="c4fef-121">Bu geçersiz kılınan Yöntemler daha sonra devralınan ve **Xmlkarakterverisi**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**ve **xmlprocessinginstruction**tarafından, önceki ve sonraki eşdüzey olan sınıflar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c4fef-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4fef-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4fef-122">See also</span></span>

- [<span data-ttu-id="c4fef-123">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="c4fef-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
