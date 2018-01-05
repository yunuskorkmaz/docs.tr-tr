---
title: "XML verilerini işlemek bellek içi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9fc2f9e7a9ba232c062b12e8c1aeb72eece760e2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="processing-xml-data-in-memory"></a><span data-ttu-id="2188b-102">XML verilerini işlemek bellek içi</span><span class="sxs-lookup"><span data-stu-id="2188b-102">Processing XML Data In-Memory</span></span>
<span data-ttu-id="2188b-103">Microsoft .NET Framework XML verilerini işlemek için üç modeli içerir: <xref:System.Xml.XmlDocument> sınıfı, <xref:System.Xml.XPath.XPathDocument> sınıfı ve [LINQ-XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span><span class="sxs-lookup"><span data-stu-id="2188b-103">The Microsoft .NET Framework includes three models for processing XML data: the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.XPath.XPathDocument> class, and [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span>  
  
 <span data-ttu-id="2188b-104"><xref:System.Xml.XmlDocument> Sınıfı W3C belge nesne modeli (DOM) Düzey 1 çekirdeğini uygular ve çekirdek DOM Düzey 2 öneriler.</span><span class="sxs-lookup"><span data-stu-id="2188b-104">The <xref:System.Xml.XmlDocument> class implements the W3C document object model (DOM) level 1 core and the core DOM level 2 recommendations.</span></span> <span data-ttu-id="2188b-105">DOM bir bellek içi (önbellek) olan bir XML belgesi gösterimini ağacı.</span><span class="sxs-lookup"><span data-stu-id="2188b-105">The DOM is an in-memory (cache) tree representation of an XML document.</span></span> <span data-ttu-id="2188b-106">İle <xref:System.Xml.XmlDocument> ve kendi ilgili sınıflar, XML belgeleri oluşturmak, yükleme ve erişim verilerini, verileri değiştirme ve değişiklikleri kaydedilsin.</span><span class="sxs-lookup"><span data-stu-id="2188b-106">With the <xref:System.Xml.XmlDocument> and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
 <span data-ttu-id="2188b-107"><xref:System.Xml.XPath.XPathDocument> XPath veri modelini temel alan bir salt okunur, bellek içi veri deposu bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="2188b-107">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory data store that is based on the XPath data model.</span></span> <span data-ttu-id="2188b-108"><xref:System.Xml.XPath.XPathNavigator> Sınıfı sunar birkaç düzenleme seçenekleri ve gezinti özellikleri salt okunur bulunan XML belgelerini üzerinden bir imleç modeli kullanılarak <xref:System.Xml.XPath.XPathDocument> sınıfı yanı sıra <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2188b-108">The <xref:System.Xml.XPath.XPathNavigator> class offers several editing options and navigation capabilities using a cursor model over XML documents contained in the read-only <xref:System.Xml.XPath.XPathDocument> class as well as the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="2188b-109">[LINQ-XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) .NET Framework sürüm 3.5 XML verilerini işlemek için yeni modelidir.</span><span class="sxs-lookup"><span data-stu-id="2188b-109">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="2188b-110">Yararlanır bir bellek içi modelini olan [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span><span class="sxs-lookup"><span data-stu-id="2188b-110">It is an in-memory model that leverages [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span></span> <span data-ttu-id="2188b-111">LINQ C# ve Visual Basic yeni sorgu özellikleri sağlamak üzere dili sözdizimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="2188b-111">LINQ extends the language syntax of C# and Visual Basic to provide new query capabilities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2188b-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2188b-112">In This Section</span></span>  
 [<span data-ttu-id="2188b-113">DOM Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="2188b-113">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 <span data-ttu-id="2188b-114">Kullanarak anlatılmaktadır <xref:System.Xml.XmlDocument>ve ilişkili sınıfları XML verileri işleyemedi.</span><span class="sxs-lookup"><span data-stu-id="2188b-114">Discusses using the <xref:System.Xml.XmlDocument>, and its related classes to process XML data.</span></span>  
  
 [<span data-ttu-id="2188b-115">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="2188b-115">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="2188b-116">Kullanarak anlatılmaktadır <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, ve <xref:System.Xml.XPath.XPathNavigator> sınıfları XML veri işleyecek.</span><span class="sxs-lookup"><span data-stu-id="2188b-116">Discusses using the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, and <xref:System.Xml.XPath.XPathNavigator> classes to process XML data.</span></span>  
  
 [<span data-ttu-id="2188b-117">LINQ to XML Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="2188b-117">Process XML Data Using LINQ to XML</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 <span data-ttu-id="2188b-118">XML LINQ kısa bir genel bakış sağlar ve LINQ-XML belgeleri için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="2188b-118">Provides a brief overview of LINQ to XML and provides links to the LINQ to XML documentation.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2188b-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="2188b-119">Related Sections</span></span>  
 [<span data-ttu-id="2188b-120">XML Belgeleri ve Verileri</span><span class="sxs-lookup"><span data-stu-id="2188b-120">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
