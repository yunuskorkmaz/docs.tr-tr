---
title: "DOM modelini kullanarak işlem XML verileri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56b6e9c7-ed82-4a65-a647-7be32c83bcc8
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 06c8b2e130dbecaca4c08684d030c8dcef1cd5a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="8bbaa-102">DOM modelini kullanarak işlem XML verileri</span><span class="sxs-lookup"><span data-stu-id="8bbaa-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="8bbaa-103">XML belge nesne modeli (DOM) XML verileri standart bir nesneler kümesini değerlendirir ve işlem bellek XML verileri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8bbaa-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="8bbaa-104">`System.Xml` Ad alanı XML belgeleri, parçaları, düğüm veya düğüm kümeleri programlı bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8bbaa-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="8bbaa-105">World Wide Web Konsorsiyumu (W3C) DOM düzey 1 çekirdek ve DOM Düzey 2 Çekirdek önerileri dayanır.</span><span class="sxs-lookup"><span data-stu-id="8bbaa-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="8bbaa-106"><xref:System.Xml.XmlDocument> Sınıfı, bir XML belgesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8bbaa-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="8bbaa-107">Diğer tüm XML nesneleri oluşturma ve alma için üye içeriyor.</span><span class="sxs-lookup"><span data-stu-id="8bbaa-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="8bbaa-108">Kullanarak <xref:System.Xml.XmlDocument>ve kendi ilgili sınıflar, XML belgeleri oluşturmak, yükleme ve erişim verilerini, verileri değiştirme ve değişiklikleri kaydedilsin.</span><span class="sxs-lookup"><span data-stu-id="8bbaa-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8bbaa-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8bbaa-109">In This Section</span></span>  
  
-   [<span data-ttu-id="8bbaa-110">XML belge nesne modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="8bbaa-110">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)  
  
-   [<span data-ttu-id="8bbaa-111">XML düğüm türleri</span><span class="sxs-lookup"><span data-stu-id="8bbaa-111">Types of XML Nodes</span></span>](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
  
-   [<span data-ttu-id="8bbaa-112">XML belge nesne modeli (DOM) hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="8bbaa-112">XML Document Object Model (DOM) Hierarchy</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md)  
  
-   [<span data-ttu-id="8bbaa-113">XML verilerine nesne hiyerarşisi eşleme</span><span class="sxs-lookup"><span data-stu-id="8bbaa-113">Mapping the Object Hierarchy to XML Data</span></span>](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)  
  
-   [<span data-ttu-id="8bbaa-114">XML belgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="8bbaa-114">XML Document Creation</span></span>](../../../../docs/standard/data/xml/xml-document-creation.md)  
  
-   [<span data-ttu-id="8bbaa-115">Bir XML belgesi DOM okuma</span><span class="sxs-lookup"><span data-stu-id="8bbaa-115">Reading an XML Document into the DOM</span></span>](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)  
  
-   [<span data-ttu-id="8bbaa-116">Bir XML belgeye düğümleri ekleniyor</span><span class="sxs-lookup"><span data-stu-id="8bbaa-116">Inserting Nodes into an XML Document</span></span>](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md)  
  
-   [<span data-ttu-id="8bbaa-117">Bir XML belgesinden düğümleri, içerik ve değerleri kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="8bbaa-117">Removing Nodes, Content, and Values from an XML Document</span></span>](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md)  
  
-   [<span data-ttu-id="8bbaa-118">Düğümler, içerik ve bir XML belgesi değerlerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="8bbaa-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)  
  
-   [<span data-ttu-id="8bbaa-119">XML belgesi DOM içinde doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="8bbaa-119">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
  
-   [<span data-ttu-id="8bbaa-120">Kaydetme ve bir belgeyi yazma</span><span class="sxs-lookup"><span data-stu-id="8bbaa-120">Saving and Writing a Document</span></span>](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)  
  
-   [<span data-ttu-id="8bbaa-121">XPath Gezinti kullanarak düğümleri seçin</span><span class="sxs-lookup"><span data-stu-id="8bbaa-121">Select Nodes Using XPath Navigation</span></span>](../../../../docs/standard/data/xml/select-nodes-using-xpath-navigation.md)  
  
-   [<span data-ttu-id="8bbaa-122">Dış kaynaklara çözme</span><span class="sxs-lookup"><span data-stu-id="8bbaa-122">Resolving External Resources</span></span>](../../../../docs/standard/data/xml/resolving-external-resources.md)  
  
-   [<span data-ttu-id="8bbaa-123">Nesne karşılaştırma kullanarak XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="8bbaa-123">Object Comparison Using XmlNameTable</span></span>](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)  
  
-   [<span data-ttu-id="8bbaa-124">Düğüm koleksiyonlarda NamedNodeMaps ve NodeLists</span><span class="sxs-lookup"><span data-stu-id="8bbaa-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md)  
  
-   [<span data-ttu-id="8bbaa-125">Dinamik güncelleştirmeleri NodeLists ve NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="8bbaa-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](../../../../docs/standard/data/xml/dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
-   [<span data-ttu-id="8bbaa-126">DOM Namespace desteği</span><span class="sxs-lookup"><span data-stu-id="8bbaa-126">Namespace Support in the DOM</span></span>](../../../../docs/standard/data/xml/namespace-support-in-the-dom.md)  
  
-   [<span data-ttu-id="8bbaa-127">Olay XmlNodeChangedEventArgs kullanarak bir XML belgesi işleme</span><span class="sxs-lookup"><span data-stu-id="8bbaa-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
-   [<span data-ttu-id="8bbaa-128">DOM genişletme</span><span class="sxs-lookup"><span data-stu-id="8bbaa-128">Extending the DOM</span></span>](../../../../docs/standard/data/xml/extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="8bbaa-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8bbaa-129">Related Sections</span></span>  
 [<span data-ttu-id="8bbaa-130">XPath veri modelini kullanarak işlem XML verileri</span><span class="sxs-lookup"><span data-stu-id="8bbaa-130">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="8bbaa-131">XML işleme kullanan anlatılmaktadır <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8bbaa-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
