---
title: XML Belge Nesne Modeli (DOM) Hiyerarşisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef2b5b200f95cdfac9b08a33c328c1dfb797e59e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959217"
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="0f1fd-102">XML Belge Nesne Modeli (DOM) Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="0f1fd-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="0f1fd-103">Sınıf hiyerarşisi için XML belge nesne modeli (DOM), aşağıdaki çizimde, ilgili olduğu sınıf adıyla birlikte parantez içinde World Wide Web Consortium (W3C) adı.</span><span class="sxs-lookup"><span data-stu-id="0f1fd-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="0f1fd-104">![XML belge nesne modeli &#40;DOM&#41; hiyerarşi](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="0f1fd-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="0f1fd-105">XML belge nesne modeli (DOM) hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="0f1fd-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="0f1fd-106">Aşağıdaki sınıflar seçeneğinden devralmamanızı **XmlNode**:</span><span class="sxs-lookup"><span data-stu-id="0f1fd-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
- <span data-ttu-id="0f1fd-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="0f1fd-107">**XmlImplementation**</span></span>  
  
- <span data-ttu-id="0f1fd-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="0f1fd-108">**XmlNamedNodeMap**</span></span>  
  
- <span data-ttu-id="0f1fd-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="0f1fd-109">**XmlNodeList**</span></span>  
  
- <span data-ttu-id="0f1fd-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="0f1fd-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="0f1fd-111">**XmlImplementation** sınıfı, bir XML belgesi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f1fd-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="0f1fd-112">Daha fazla bilgi için [XML belgesi oluşturma](../../../../docs/standard/data/xml/xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="0f1fd-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="0f1fd-113">**XmlNamedNodeMap** sınıfı sırasız bir dizi düğümü işler.</span><span class="sxs-lookup"><span data-stu-id="0f1fd-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="0f1fd-114">Daha fazla bilgi için [ada veya dizine göre sırasız düğüm alma](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="0f1fd-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="0f1fd-115">**XmlNodeList** sınıfı işleme düğümleri sıralı bir listesi.</span><span class="sxs-lookup"><span data-stu-id="0f1fd-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="0f1fd-116">Daha fazla bilgi için [dizine göre sıralı düğüm alma](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="0f1fd-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="0f1fd-117">**XmlNodeChangedEventArgs** sınıfı işleme kayıtlı olay işleyicilerinin **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="0f1fd-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="0f1fd-118">Daha fazla bilgi için [XML belgesinde XmlNodeChangedEventArgs kullanarak olay işleme](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="0f1fd-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="0f1fd-119">**XmlLinkedNode** sınıfının devraldığı **XmlNode**.</span><span class="sxs-lookup"><span data-stu-id="0f1fd-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="0f1fd-120">İki yöntemleri geçersiz kılmak için amacı olan **XmlNode**: **PreviousSibling** ve **NextSibling** yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="0f1fd-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="0f1fd-121">Bu geçersiz kılınan yöntemler ardından devralınan ve tarafından kullanılan **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, ve **XmlProcessingInstruction**, önceki ve sonraki eşdüzey öğesi olan sınıfları şunlardır.</span><span class="sxs-lookup"><span data-stu-id="0f1fd-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f1fd-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f1fd-122">See also</span></span>

- [<span data-ttu-id="0f1fd-123">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="0f1fd-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
