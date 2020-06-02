---
title: DOM Modelini Kullanarak XML Verilerini İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 56b6e9c7-ed82-4a65-a647-7be32c83bcc8
ms.openlocfilehash: 242554cc948ef16972ffd26d5464dae2727ed339
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290843"
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="2d1ff-102">DOM Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="2d1ff-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="2d1ff-103">XML Belge Nesne Modeli (DOM), XML verilerini standart bir nesne kümesi olarak değerlendirir ve XML verilerini bellekte işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2d1ff-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="2d1ff-104">`System.Xml`Ad alanı, XML belgelerinin, parçaların, düğümlerin veya düğüm kümelerinin programlı bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d1ff-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="2d1ff-105">World Wide Web Konsorsiyumu (W3C) DOM düzeyi 1 çekirdeğini ve DOM düzey 2 temel önerilerini temel alır.</span><span class="sxs-lookup"><span data-stu-id="2d1ff-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="2d1ff-106"><xref:System.Xml.XmlDocument>Sınıfı BIR XML belgesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2d1ff-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="2d1ff-107">Diğer tüm XML nesnelerini alma ve oluşturma üyelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="2d1ff-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="2d1ff-108"><xref:System.Xml.XmlDocument>Ve ilişkili sınıflarını kullanarak XML belgeleri oluşturabilir, verileri yükleyebilir ve erişebilir, verileri değiştirebilir ve değişiklikleri kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d1ff-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d1ff-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2d1ff-109">In This Section</span></span>  
  
- [<span data-ttu-id="2d1ff-110">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="2d1ff-110">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)  
  
- [<span data-ttu-id="2d1ff-111">XML Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="2d1ff-111">Types of XML Nodes</span></span>](types-of-xml-nodes.md)  
  
- [<span data-ttu-id="2d1ff-112">XML Belge Nesne Modeli (DOM) Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="2d1ff-112">XML Document Object Model (DOM) Hierarchy</span></span>](xml-document-object-model-dom-hierarchy.md)  
  
- [<span data-ttu-id="2d1ff-113">XML Verilerine Nesne Hiyerarşisi Eşleme</span><span class="sxs-lookup"><span data-stu-id="2d1ff-113">Mapping the Object Hierarchy to XML Data</span></span>](mapping-the-object-hierarchy-to-xml-data.md)  
  
- [<span data-ttu-id="2d1ff-114">XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2d1ff-114">XML Document Creation</span></span>](xml-document-creation.md)  
  
- [<span data-ttu-id="2d1ff-115">DOM’da XML Belgesi Okuma</span><span class="sxs-lookup"><span data-stu-id="2d1ff-115">Reading an XML Document into the DOM</span></span>](reading-an-xml-document-into-the-dom.md)  
  
- [<span data-ttu-id="2d1ff-116">XML Belgesine Düğüm Ekleme</span><span class="sxs-lookup"><span data-stu-id="2d1ff-116">Inserting Nodes into an XML Document</span></span>](inserting-nodes-into-an-xml-document.md)  
  
- [<span data-ttu-id="2d1ff-117">Bir XML Belgesinden Düğümleri, İçeriği ve Değerleri Kaldırma</span><span class="sxs-lookup"><span data-stu-id="2d1ff-117">Removing Nodes, Content, and Values from an XML Document</span></span>](removing-nodes-content-and-values-from-an-xml-document.md)  
  
- [<span data-ttu-id="2d1ff-118">Bir XML Belgesindeki Düğüm, İçerik ve Değerleri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="2d1ff-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](modifying-nodes-content-and-values-in-an-xml-document.md)  
  
- [<span data-ttu-id="2d1ff-119">DOM’da XML Belgesi Doğrulama</span><span class="sxs-lookup"><span data-stu-id="2d1ff-119">Validating an XML Document in the DOM</span></span>](validating-an-xml-document-in-the-dom.md)  
  
- [<span data-ttu-id="2d1ff-120">Belge Kaydetme ve Yazma</span><span class="sxs-lookup"><span data-stu-id="2d1ff-120">Saving and Writing a Document</span></span>](saving-and-writing-a-document.md)  
  
- [<span data-ttu-id="2d1ff-121">XPath Gezintisi Kullanarak Düğüm Seçme</span><span class="sxs-lookup"><span data-stu-id="2d1ff-121">Select Nodes Using XPath Navigation</span></span>](select-nodes-using-xpath-navigation.md)  
  
- [<span data-ttu-id="2d1ff-122">Dış Kaynakları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="2d1ff-122">Resolving External Resources</span></span>](resolving-external-resources.md)  
  
- [<span data-ttu-id="2d1ff-123">XmlNameTable Kullanarak Nesne Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="2d1ff-123">Object Comparison Using XmlNameTable</span></span>](object-comparison-using-xmlnametable.md)  
  
- [<span data-ttu-id="2d1ff-124">NamedNodeMaps ve NodeLists İçindeki Düğüm Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="2d1ff-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](node-collections-in-namednodemaps-and-nodelists.md)  
  
- [<span data-ttu-id="2d1ff-125">NodeLists ve NamedNodeMaps Dinamik Güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="2d1ff-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
- [<span data-ttu-id="2d1ff-126">DOM Ad Alanı Desteği</span><span class="sxs-lookup"><span data-stu-id="2d1ff-126">Namespace Support in the DOM</span></span>](namespace-support-in-the-dom.md)  
  
- [<span data-ttu-id="2d1ff-127">Bir XML Belgesinde XmlNodeChangedEventArgs Kullanarak Olay İşleme</span><span class="sxs-lookup"><span data-stu-id="2d1ff-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
- [<span data-ttu-id="2d1ff-128">DOM Genişletme</span><span class="sxs-lookup"><span data-stu-id="2d1ff-128">Extending the DOM</span></span>](extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="2d1ff-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="2d1ff-129">Related Sections</span></span>  
 [<span data-ttu-id="2d1ff-130">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="2d1ff-130">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="2d1ff-131">Sınıfını kullanarak XML işlemesini açıklar <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="2d1ff-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
