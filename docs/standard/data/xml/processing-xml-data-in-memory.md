---
title: XML Verilerini Bellek İçinde İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f1a4587838180896b52bb79d447ed7ede3e22d1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770428"
---
# <a name="processing-xml-data-in-memory"></a><span data-ttu-id="aaeb9-102">XML Verilerini Bellek İçinde İşleme</span><span class="sxs-lookup"><span data-stu-id="aaeb9-102">Processing XML Data In-Memory</span></span>
<span data-ttu-id="aaeb9-103">Microsoft .NET Framework XML verilerini işlemek için üç model içerir: <xref:System.Xml.XmlDocument> sınıfı <xref:System.Xml.XPath.XPathDocument> sınıfı ve [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="aaeb9-103">The Microsoft .NET Framework includes three models for processing XML data: the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.XPath.XPathDocument> class, and [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="aaeb9-104"><xref:System.Xml.XmlDocument> Sınıfı W3C belge nesne modeli (DOM) Düzey 1 çekirdek uygular ve çekirdek DOM Düzey 2 öneriler.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-104">The <xref:System.Xml.XmlDocument> class implements the W3C document object model (DOM) level 1 core and the core DOM level 2 recommendations.</span></span> <span data-ttu-id="aaeb9-105">DOM bir bellek içi (önbellek) olan bir XML belgesi gösterimini ağaç.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-105">The DOM is an in-memory (cache) tree representation of an XML document.</span></span> <span data-ttu-id="aaeb9-106">İle <xref:System.Xml.XmlDocument> ve ilişkili sınıflarının, XML belgeleri oluşturmak, yüklemek ve verilere erişir, verileri değiştirme ve değişiklikleri kaydedilsin.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-106">With the <xref:System.Xml.XmlDocument> and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
 <span data-ttu-id="aaeb9-107"><xref:System.Xml.XPath.XPathDocument> XPath veri modelini temel alan bir salt okunur, bellek içi veri deposuna bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-107">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory data store that is based on the XPath data model.</span></span> <span data-ttu-id="aaeb9-108"><xref:System.Xml.XPath.XPathNavigator> Sınıfı sunar birkaç düzenleme seçeneklerini ve gezinti özellikleri salt okunur bulunan XML belgeleri üzerinde bir imleç modeli kullanarak <xref:System.Xml.XPath.XPathDocument> sınıfı yanı sıra <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-108">The <xref:System.Xml.XPath.XPathNavigator> class offers several editing options and navigation capabilities using a cursor model over XML documents contained in the read-only <xref:System.Xml.XPath.XPathDocument> class as well as the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="aaeb9-109">[LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) .NET Framework sürüm 3.5 XML verilerini işlemek için sunulan bir modeli.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-109">[LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) is a model introduced in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="aaeb9-110">Bunu yararlanan bir bellek içi modelidir [dil ile tümleşik sorgu (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="aaeb9-110">It's an in-memory model that leverages [Language-Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).</span></span> <span data-ttu-id="aaeb9-111">LINQ genişletir dili sözdizimi C# ve Visual Basic yeni sorgu işlevleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-111">LINQ extends the language syntax of C# and Visual Basic to provide new query capabilities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aaeb9-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="aaeb9-112">In This Section</span></span>  
 [<span data-ttu-id="aaeb9-113">DOM Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="aaeb9-113">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 <span data-ttu-id="aaeb9-114">Kullanımını açıklar <xref:System.Xml.XmlDocument>ve ilişkili sınıflarının XML verilerini işleme.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-114">Discusses using the <xref:System.Xml.XmlDocument>, and its related classes to process XML data.</span></span>  
  
 [<span data-ttu-id="aaeb9-115">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="aaeb9-115">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="aaeb9-116">Kullanımını açıklar <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, ve <xref:System.Xml.XPath.XPathNavigator> XML verilerini işleme sınıfları.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-116">Discusses using the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, and <xref:System.Xml.XPath.XPathNavigator> classes to process XML data.</span></span>  
  
 [<span data-ttu-id="aaeb9-117">LINQ to XML Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="aaeb9-117">Process XML Data Using LINQ to XML</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 <span data-ttu-id="aaeb9-118">XML için LINQ kısa bir genel bakış sağlar ve LINQ to XML belgeleri için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-118">Provides a brief overview of LINQ to XML and provides links to the LINQ to XML documentation.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aaeb9-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="aaeb9-119">Related Sections</span></span>  
 [<span data-ttu-id="aaeb9-120">XML Belgeleri ve Verileri</span><span class="sxs-lookup"><span data-stu-id="aaeb9-120">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
