---
title: DOM modelini kullanarak işlem XML verileri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 56b6e9c7-ed82-4a65-a647-7be32c83bcc8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c59d84148aae35794410f5f7237cef96ab5b7560
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570370"
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="49238-102">DOM modelini kullanarak işlem XML verileri</span><span class="sxs-lookup"><span data-stu-id="49238-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="49238-103">XML belge nesne modeli (DOM) XML verileri standart bir nesneler kümesini değerlendirir ve işlem bellek XML verileri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="49238-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="49238-104">`System.Xml` Ad alanı XML belgeleri, parçaları, düğüm veya düğüm kümeleri programlı bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="49238-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="49238-105">World Wide Web Konsorsiyumu (W3C) DOM düzey 1 çekirdek ve DOM Düzey 2 Çekirdek önerileri dayanır.</span><span class="sxs-lookup"><span data-stu-id="49238-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="49238-106"><xref:System.Xml.XmlDocument> Sınıfı, bir XML belgesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="49238-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="49238-107">Diğer tüm XML nesneleri oluşturma ve alma için üye içeriyor.</span><span class="sxs-lookup"><span data-stu-id="49238-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="49238-108">Kullanarak <xref:System.Xml.XmlDocument>ve kendi ilgili sınıflar, XML belgeleri oluşturmak, yükleme ve erişim verilerini, verileri değiştirme ve değişiklikleri kaydedilsin.</span><span class="sxs-lookup"><span data-stu-id="49238-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="49238-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="49238-109">In This Section</span></span>  
  
-   [<span data-ttu-id="49238-110">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="49238-110">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)  
  
-   [<span data-ttu-id="49238-111">XML Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="49238-111">Types of XML Nodes</span></span>](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
  
-   [<span data-ttu-id="49238-112">XML Belge Nesne Modeli (DOM) Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="49238-112">XML Document Object Model (DOM) Hierarchy</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md)  
  
-   [<span data-ttu-id="49238-113">XML Verilerine Nesne Hiyerarşisi Eşleme</span><span class="sxs-lookup"><span data-stu-id="49238-113">Mapping the Object Hierarchy to XML Data</span></span>](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)  
  
-   [<span data-ttu-id="49238-114">XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="49238-114">XML Document Creation</span></span>](../../../../docs/standard/data/xml/xml-document-creation.md)  
  
-   [<span data-ttu-id="49238-115">DOM’da XML Belgesi Okuma</span><span class="sxs-lookup"><span data-stu-id="49238-115">Reading an XML Document into the DOM</span></span>](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)  
  
-   [<span data-ttu-id="49238-116">XML Belgesine Düğüm Ekleme</span><span class="sxs-lookup"><span data-stu-id="49238-116">Inserting Nodes into an XML Document</span></span>](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md)  
  
-   [<span data-ttu-id="49238-117">Bir XML Belgesinden Düğümleri, İçeriği ve Değerleri Kaldırma</span><span class="sxs-lookup"><span data-stu-id="49238-117">Removing Nodes, Content, and Values from an XML Document</span></span>](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md)  
  
-   [<span data-ttu-id="49238-118">Bir XML Belgesindeki Düğüm, İçerik ve Değerleri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="49238-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)  
  
-   [<span data-ttu-id="49238-119">DOM’da XML Belgesi Doğrulama</span><span class="sxs-lookup"><span data-stu-id="49238-119">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
  
-   [<span data-ttu-id="49238-120">Belge Kaydetme ve Yazma</span><span class="sxs-lookup"><span data-stu-id="49238-120">Saving and Writing a Document</span></span>](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)  
  
-   [<span data-ttu-id="49238-121">XPath Gezintisi Kullanarak Düğüm Seçme</span><span class="sxs-lookup"><span data-stu-id="49238-121">Select Nodes Using XPath Navigation</span></span>](../../../../docs/standard/data/xml/select-nodes-using-xpath-navigation.md)  
  
-   [<span data-ttu-id="49238-122">Dış Kaynakları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="49238-122">Resolving External Resources</span></span>](../../../../docs/standard/data/xml/resolving-external-resources.md)  
  
-   [<span data-ttu-id="49238-123">XmlNameTable Kullanarak Nesne Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="49238-123">Object Comparison Using XmlNameTable</span></span>](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)  
  
-   [<span data-ttu-id="49238-124">NamedNodeMaps ve NodeLists İçindeki Düğüm Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="49238-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md)  
  
-   [<span data-ttu-id="49238-125">NodeLists ve NamedNodeMaps Dinamik Güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="49238-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](../../../../docs/standard/data/xml/dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
-   [<span data-ttu-id="49238-126">DOM Ad Alanı Desteği</span><span class="sxs-lookup"><span data-stu-id="49238-126">Namespace Support in the DOM</span></span>](../../../../docs/standard/data/xml/namespace-support-in-the-dom.md)  
  
-   [<span data-ttu-id="49238-127">Bir XML Belgesinde XmlNodeChangedEventArgs Kullanarak Olay İşleme</span><span class="sxs-lookup"><span data-stu-id="49238-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
-   [<span data-ttu-id="49238-128">DOM Genişletme</span><span class="sxs-lookup"><span data-stu-id="49238-128">Extending the DOM</span></span>](../../../../docs/standard/data/xml/extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="49238-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="49238-129">Related Sections</span></span>  
 [<span data-ttu-id="49238-130">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="49238-130">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="49238-131">XML işleme kullanan anlatılmaktadır <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="49238-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
