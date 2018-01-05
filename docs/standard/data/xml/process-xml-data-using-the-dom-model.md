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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: de7ca0ff08ae7183f92fd7caa1bfe977e01e616d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="44d50-102">DOM modelini kullanarak işlem XML verileri</span><span class="sxs-lookup"><span data-stu-id="44d50-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="44d50-103">XML belge nesne modeli (DOM) XML verileri standart bir nesneler kümesini değerlendirir ve işlem bellek XML verileri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="44d50-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="44d50-104">`System.Xml` Ad alanı XML belgeleri, parçaları, düğüm veya düğüm kümeleri programlı bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="44d50-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="44d50-105">World Wide Web Konsorsiyumu (W3C) DOM düzey 1 çekirdek ve DOM Düzey 2 Çekirdek önerileri dayanır.</span><span class="sxs-lookup"><span data-stu-id="44d50-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="44d50-106"><xref:System.Xml.XmlDocument> Sınıfı, bir XML belgesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="44d50-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="44d50-107">Diğer tüm XML nesneleri oluşturma ve alma için üye içeriyor.</span><span class="sxs-lookup"><span data-stu-id="44d50-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="44d50-108">Kullanarak <xref:System.Xml.XmlDocument>ve kendi ilgili sınıflar, XML belgeleri oluşturmak, yükleme ve erişim verilerini, verileri değiştirme ve değişiklikleri kaydedilsin.</span><span class="sxs-lookup"><span data-stu-id="44d50-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44d50-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="44d50-109">In This Section</span></span>  
  
-   [<span data-ttu-id="44d50-110">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="44d50-110">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)  
  
-   [<span data-ttu-id="44d50-111">XML Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="44d50-111">Types of XML Nodes</span></span>](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
  
-   [<span data-ttu-id="44d50-112">XML Belge Nesne Modeli (DOM) Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="44d50-112">XML Document Object Model (DOM) Hierarchy</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md)  
  
-   [<span data-ttu-id="44d50-113">XML Verilerine Nesne Hiyerarşisi Eşleme</span><span class="sxs-lookup"><span data-stu-id="44d50-113">Mapping the Object Hierarchy to XML Data</span></span>](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)  
  
-   [<span data-ttu-id="44d50-114">XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="44d50-114">XML Document Creation</span></span>](../../../../docs/standard/data/xml/xml-document-creation.md)  
  
-   [<span data-ttu-id="44d50-115">DOM’da XML Belgesi Okuma</span><span class="sxs-lookup"><span data-stu-id="44d50-115">Reading an XML Document into the DOM</span></span>](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)  
  
-   [<span data-ttu-id="44d50-116">XML Belgesine Düğüm Ekleme</span><span class="sxs-lookup"><span data-stu-id="44d50-116">Inserting Nodes into an XML Document</span></span>](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md)  
  
-   [<span data-ttu-id="44d50-117">Bir XML Belgesinden Düğümleri, İçeriği ve Değerleri Kaldırma</span><span class="sxs-lookup"><span data-stu-id="44d50-117">Removing Nodes, Content, and Values from an XML Document</span></span>](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md)  
  
-   [<span data-ttu-id="44d50-118">Bir XML Belgesindeki Düğüm, İçerik ve Değerleri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="44d50-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)  
  
-   [<span data-ttu-id="44d50-119">DOM’da XML Belgesi Doğrulama</span><span class="sxs-lookup"><span data-stu-id="44d50-119">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
  
-   [<span data-ttu-id="44d50-120">Belge Kaydetme ve Yazma</span><span class="sxs-lookup"><span data-stu-id="44d50-120">Saving and Writing a Document</span></span>](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)  
  
-   [<span data-ttu-id="44d50-121">XPath Gezintisi Kullanarak Düğüm Seçme</span><span class="sxs-lookup"><span data-stu-id="44d50-121">Select Nodes Using XPath Navigation</span></span>](../../../../docs/standard/data/xml/select-nodes-using-xpath-navigation.md)  
  
-   [<span data-ttu-id="44d50-122">Dış Kaynakları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="44d50-122">Resolving External Resources</span></span>](../../../../docs/standard/data/xml/resolving-external-resources.md)  
  
-   [<span data-ttu-id="44d50-123">XmlNameTable Kullanarak Nesne Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="44d50-123">Object Comparison Using XmlNameTable</span></span>](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)  
  
-   [<span data-ttu-id="44d50-124">NamedNodeMaps ve NodeLists İçindeki Düğüm Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="44d50-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md)  
  
-   [<span data-ttu-id="44d50-125">NodeLists ve NamedNodeMaps Dinamik Güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="44d50-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](../../../../docs/standard/data/xml/dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
-   [<span data-ttu-id="44d50-126">DOM Ad Alanı Desteği</span><span class="sxs-lookup"><span data-stu-id="44d50-126">Namespace Support in the DOM</span></span>](../../../../docs/standard/data/xml/namespace-support-in-the-dom.md)  
  
-   [<span data-ttu-id="44d50-127">Bir XML Belgesinde XmlNodeChangedEventArgs Kullanarak Olay İşleme</span><span class="sxs-lookup"><span data-stu-id="44d50-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
-   [<span data-ttu-id="44d50-128">DOM Genişletme</span><span class="sxs-lookup"><span data-stu-id="44d50-128">Extending the DOM</span></span>](../../../../docs/standard/data/xml/extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="44d50-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="44d50-129">Related Sections</span></span>  
 [<span data-ttu-id="44d50-130">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="44d50-130">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="44d50-131">XML işleme kullanan anlatılmaktadır <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="44d50-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
