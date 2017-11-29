---
title: "XPath veri modelini kullanarak işlem XML verileri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3d2c8db03d494be13a93df06a359e4e4294c22a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="process-xml-data-using-the-xpath-data-model"></a><span data-ttu-id="fa91e-102">XPath veri modelini kullanarak işlem XML verileri</span><span class="sxs-lookup"><span data-stu-id="fa91e-102">Process XML Data Using the XPath Data Model</span></span>
<span data-ttu-id="fa91e-103"><xref:System.Xml?displayProperty=nameWithType> Ad alanı sağlar XML belgeleri, parçaları, düğüm veya düğüm kümeleri bellek içi, programlı bir gösterimini kullanarak <xref:System.Xml.XmlDocument> veya <xref:System.Xml.XPath.XPathDocument> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="fa91e-103">The <xref:System.Xml?displayProperty=nameWithType> namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets in-memory, using the <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> classes.</span></span>  
  
 <span data-ttu-id="fa91e-104"><xref:System.Xml.XPath.XPathDocument> Sınıfı XPath veri modelini kullanarak bir XML belgesi hızlı, salt okunur, bellek içi bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa91e-104">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="fa91e-105"><xref:System.Xml.XmlDocument> Sınıfı W3C belge nesne modeli (DOM) Düzey 1 çekirdek ve çekirdek DOM Düzey 2 uygulayan bir XML belgesi düzenlenebilir bir bellek içi gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa91e-105">The <xref:System.Xml.XmlDocument> class provides an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="fa91e-106">Her iki sınıfları uygulamak <xref:System.Xml.XPath.IXPathNavigable> arabirim ve dönüş bir <xref:System.Xml.XPath.XPathNavigator> seçmek, değerlendirmek, gidin ve bazı durumlarda, temel alınan XML verileri düzenlemek için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="fa91e-106">Both classes implement the <xref:System.Xml.XPath.IXPathNavigable> interface and return an <xref:System.Xml.XPath.XPathNavigator> object used to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="fa91e-107">Aşağıdaki bölümlerde işlevselliğini <xref:System.Xml.XPath.XPathNavigator> sınıf tabanlı döndürdüğü sınıf.</span><span class="sxs-lookup"><span data-stu-id="fa91e-107">The following sections describe the functionality of the <xref:System.Xml.XPath.XPathNavigator> class based on the class that returns it.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa91e-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fa91e-108">In This Section</span></span>  
 [<span data-ttu-id="fa91e-109">XPathDocument ve XmlDocument kullanarak XML verilerini okuma</span><span class="sxs-lookup"><span data-stu-id="fa91e-109">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 <span data-ttu-id="fa91e-110">Salt okunur oluşturmayı açıklar <xref:System.Xml.XPath.XPathDocument> bir XML belgesi ve bir düzenlenebilir oluşturma okumak için sınıf nesnesi <xref:System.Xml.XmlDocument> okuyun ve bir XML belgesi düzenlemek için sınıf nesnesi.</span><span class="sxs-lookup"><span data-stu-id="fa91e-110">Describes how to create a read-only <xref:System.Xml.XPath.XPathDocument> class object to read an XML document and how to create an editable <xref:System.Xml.XmlDocument> class object to read and edit an XML document.</span></span> <span data-ttu-id="fa91e-111">Bu konu ayrıca açıklar nasıl dönüş bir <xref:System.Xml.XPath.XPathNavigator> gidin ve bir XML belgesi düzenlemek için her sınıftan nesne.</span><span class="sxs-lookup"><span data-stu-id="fa91e-111">This topic also describes how return an <xref:System.Xml.XPath.XPathNavigator> object from each class to navigate and edit an XML document.</span></span>  
  
 [<span data-ttu-id="fa91e-112">Seçildiğinde, Evaluating ve XML XPathNavigator kullanarak veri eşleştirme</span><span class="sxs-lookup"><span data-stu-id="fa91e-112">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="fa91e-113">Yöntemleri açıklar <xref:System.Xml.XPath.XPathNavigator> düğümler seçmek için kullanılan sınıf bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> bir XPath sorgusu kullanılarak nesne, değerlendirmek ve bir XPath ifadesi sonuçlarını inceleyin ve bir XML belgesi düğümünde verilen XPath eşleşip eşleşmediğini belirlemek ifade.</span><span class="sxs-lookup"><span data-stu-id="fa91e-113">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an XML document matches a given XPath expression.</span></span>  
  
 [<span data-ttu-id="fa91e-114">XML XPathNavigator kullanarak verilerine erişme</span><span class="sxs-lookup"><span data-stu-id="fa91e-114">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="fa91e-115">Yöntemleri açıklar <xref:System.Xml.XPath.XPathNavigator> düğümleri gidin, XML verileri ayıklamak ve kesin türü belirtilmiş XML verilerine erişmek için kullanılan sınıf bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="fa91e-115">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to navigate nodes, extract XML data and access strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="fa91e-116">XML XPathNavigator kullanarak verileri düzenleme</span><span class="sxs-lookup"><span data-stu-id="fa91e-116">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="fa91e-117">Yöntemleri açıklar <xref:System.Xml.XPath.XPathNavigator> eklemek, değiştirmek ve içinde yer alan bir XML belgesi düğümleri ve değerleri kaldırmak için kullanılan sınıf bir <xref:System.Xml.XmlDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="fa91e-117">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to insert, modify and remove nodes and values from an XML document contained in an <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="fa91e-118">XPathNavigator kullanarak şema doğrulaması</span><span class="sxs-lookup"><span data-stu-id="fa91e-118">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="fa91e-119">Bulunan XML içeriği doğrulamak yolları açıklanmaktadır bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="fa91e-119">Describes the ways to validate the XML content contained in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa91e-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa91e-120">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="fa91e-121">DOM modelini kullanarak işlem XML verileri</span><span class="sxs-lookup"><span data-stu-id="fa91e-121">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
