---
title: XML belge nesne modeli (DOM) hiyerarşisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef2b5b200f95cdfac9b08a33c328c1dfb797e59e
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537780"
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="a45be-102">XML belge nesne modeli (DOM) hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="a45be-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="a45be-103">Sınıf hiyerarşisi için XML belge nesne modeli (DOM), aşağıdaki çizimde, ilgili olduğu sınıf adıyla birlikte parantez içinde World Wide Web Consortium (W3C) adı.</span><span class="sxs-lookup"><span data-stu-id="a45be-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="a45be-104">![XML belge nesne modeli &#40;DOM&#41; hiyerarşi](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="a45be-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="a45be-105">XML belge nesne modeli (DOM) hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="a45be-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="a45be-106">Aşağıdaki sınıflar seçeneğinden devralmamanızı **XmlNode**:</span><span class="sxs-lookup"><span data-stu-id="a45be-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
-   <span data-ttu-id="a45be-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="a45be-107">**XmlImplementation**</span></span>  
  
-   <span data-ttu-id="a45be-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="a45be-108">**XmlNamedNodeMap**</span></span>  
  
-   <span data-ttu-id="a45be-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="a45be-109">**XmlNodeList**</span></span>  
  
-   <span data-ttu-id="a45be-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="a45be-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="a45be-111">**XmlImplementation** sınıfı, bir XML belgesi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a45be-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="a45be-112">Daha fazla bilgi için [XML belgesi oluşturma](../../../../docs/standard/data/xml/xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="a45be-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="a45be-113">**XmlNamedNodeMap** sınıfı sırasız bir dizi düğümü işler.</span><span class="sxs-lookup"><span data-stu-id="a45be-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="a45be-114">Daha fazla bilgi için [ada veya dizine göre sırasız düğüm alma](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="a45be-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="a45be-115">**XmlNodeList** sınıfı işleme düğümleri sıralı bir listesi.</span><span class="sxs-lookup"><span data-stu-id="a45be-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="a45be-116">Daha fazla bilgi için [dizine göre sıralı düğüm alma](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="a45be-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="a45be-117">**XmlNodeChangedEventArgs** sınıfı işleme kayıtlı olay işleyicilerinin **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="a45be-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="a45be-118">Daha fazla bilgi için [XML belgesinde XmlNodeChangedEventArgs kullanarak olay işleme](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="a45be-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="a45be-119">**XmlLinkedNode** sınıfının devraldığı **XmlNode**.</span><span class="sxs-lookup"><span data-stu-id="a45be-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="a45be-120">İki yöntemleri geçersiz kılmak için amacı olan **XmlNode**: **PreviousSibling** ve **NextSibling** yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="a45be-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="a45be-121">Bu geçersiz kılınan yöntemler ardından devralınan ve tarafından kullanılan **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, ve **XmlProcessingInstruction**, önceki ve sonraki eşdüzey öğesi olan sınıfları şunlardır.</span><span class="sxs-lookup"><span data-stu-id="a45be-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a45be-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a45be-122">See also</span></span>

- [<span data-ttu-id="a45be-123">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="a45be-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
