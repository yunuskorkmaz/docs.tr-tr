---
title: DOM Modelini Kullanarak XML Verilerini İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 56b6e9c7-ed82-4a65-a647-7be32c83bcc8
ms.openlocfilehash: 01ef4bef57b8a2e3e13f28a98adb21b111f3f4ed
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710459"
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="f114c-102">DOM Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="f114c-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="f114c-103">XML Belge Nesne Modeli (DOM), XML verilerini standart bir nesne kümesi olarak değerlendirir ve XML verilerini bellekte işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f114c-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="f114c-104">`System.Xml` Ad alanı, XML belgelerinin, parçaların, düğümlerin veya düğüm kümelerinin programlı bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f114c-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="f114c-105">World Wide Web Konsorsiyumu (W3C) DOM düzeyi 1 çekirdeğini ve DOM düzey 2 temel önerilerini temel alır.</span><span class="sxs-lookup"><span data-stu-id="f114c-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="f114c-106"><xref:System.Xml.XmlDocument> Sınıfı bir XML belgesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f114c-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="f114c-107">Diğer tüm XML nesnelerini alma ve oluşturma üyelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f114c-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="f114c-108"><xref:System.Xml.XmlDocument>Ve ilişkili SıNıFLARıNı kullanarak XML belgeleri oluşturabilir, verileri yükleyebilir ve erişebilir, verileri değiştirebilir ve değişiklikleri kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f114c-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f114c-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f114c-109">In This Section</span></span>  
  
- [<span data-ttu-id="f114c-110">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="f114c-110">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)  
  
- [<span data-ttu-id="f114c-111">XML Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="f114c-111">Types of XML Nodes</span></span>](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
  
- [<span data-ttu-id="f114c-112">XML Belge Nesne Modeli (DOM) Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="f114c-112">XML Document Object Model (DOM) Hierarchy</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md)  
  
- [<span data-ttu-id="f114c-113">XML Verilerine Nesne Hiyerarşisi Eşleme</span><span class="sxs-lookup"><span data-stu-id="f114c-113">Mapping the Object Hierarchy to XML Data</span></span>](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)  
  
- [<span data-ttu-id="f114c-114">XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f114c-114">XML Document Creation</span></span>](../../../../docs/standard/data/xml/xml-document-creation.md)  
  
- [<span data-ttu-id="f114c-115">DOM’da XML Belgesi Okuma</span><span class="sxs-lookup"><span data-stu-id="f114c-115">Reading an XML Document into the DOM</span></span>](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)  
  
- [<span data-ttu-id="f114c-116">XML Belgesine Düğüm Ekleme</span><span class="sxs-lookup"><span data-stu-id="f114c-116">Inserting Nodes into an XML Document</span></span>](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md)  
  
- [<span data-ttu-id="f114c-117">Bir XML Belgesinden Düğümleri, İçeriği ve Değerleri Kaldırma</span><span class="sxs-lookup"><span data-stu-id="f114c-117">Removing Nodes, Content, and Values from an XML Document</span></span>](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md)  
  
- [<span data-ttu-id="f114c-118">Bir XML Belgesindeki Düğüm, İçerik ve Değerleri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="f114c-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)  
  
- [<span data-ttu-id="f114c-119">DOM’da XML Belgesi Doğrulama</span><span class="sxs-lookup"><span data-stu-id="f114c-119">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
  
- [<span data-ttu-id="f114c-120">Belge Kaydetme ve Yazma</span><span class="sxs-lookup"><span data-stu-id="f114c-120">Saving and Writing a Document</span></span>](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)  
  
- [<span data-ttu-id="f114c-121">XPath Gezintisi Kullanarak Düğüm Seçme</span><span class="sxs-lookup"><span data-stu-id="f114c-121">Select Nodes Using XPath Navigation</span></span>](../../../../docs/standard/data/xml/select-nodes-using-xpath-navigation.md)  
  
- [<span data-ttu-id="f114c-122">Dış Kaynakları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="f114c-122">Resolving External Resources</span></span>](../../../../docs/standard/data/xml/resolving-external-resources.md)  
  
- [<span data-ttu-id="f114c-123">XmlNameTable Kullanarak Nesne Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="f114c-123">Object Comparison Using XmlNameTable</span></span>](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)  
  
- [<span data-ttu-id="f114c-124">NamedNodeMaps ve NodeLists İçindeki Düğüm Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="f114c-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md)  
  
- [<span data-ttu-id="f114c-125">NodeLists ve NamedNodeMaps Dinamik Güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="f114c-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](../../../../docs/standard/data/xml/dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
- [<span data-ttu-id="f114c-126">DOM Ad Alanı Desteği</span><span class="sxs-lookup"><span data-stu-id="f114c-126">Namespace Support in the DOM</span></span>](../../../../docs/standard/data/xml/namespace-support-in-the-dom.md)  
  
- [<span data-ttu-id="f114c-127">Bir XML Belgesinde XmlNodeChangedEventArgs Kullanarak Olay İşleme</span><span class="sxs-lookup"><span data-stu-id="f114c-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
- [<span data-ttu-id="f114c-128">DOM Genişletme</span><span class="sxs-lookup"><span data-stu-id="f114c-128">Extending the DOM</span></span>](../../../../docs/standard/data/xml/extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="f114c-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f114c-129">Related Sections</span></span>  
 [<span data-ttu-id="f114c-130">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="f114c-130">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="f114c-131"><xref:System.Xml.XPath.XPathNavigator> SıNıFıNı kullanarak XML işlemesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f114c-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
