---
title: XPath Veri Modelini Kullanarak XML Verilerini İşleme
ms.date: 03/30/2017
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
ms.openlocfilehash: 840fb40cc650d8f65af533d4102f18132bce3f53
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686962"
---
# <a name="process-xml-data-using-the-xpath-data-model"></a><span data-ttu-id="cf5fc-102">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="cf5fc-102">Process XML Data Using the XPath Data Model</span></span>

<span data-ttu-id="cf5fc-103"><xref:System.Xml?displayProperty=nameWithType>Ad alanı, veya sınıfları kullanarak XML belgelerinin, parçaların, düğümlerin veya düğüm kümesinin bellek içinde programlı bir gösterimini sağlar <xref:System.Xml.XmlDocument> <xref:System.Xml.XPath.XPathDocument> .</span><span class="sxs-lookup"><span data-stu-id="cf5fc-103">The <xref:System.Xml?displayProperty=nameWithType> namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets in-memory, using the <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> classes.</span></span>  
  
 <span data-ttu-id="cf5fc-104"><xref:System.Xml.XPath.XPathDocument>Sınıfı, XPath veri modelini kullanarak BIR XML belgesinin hızlı, Salt okunabilir ve bellek içi gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf5fc-104">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="cf5fc-105"><xref:System.Xml.XmlDocument>Sınıfı, W3C belge nesne modeli (DOM) düzey 1 Core ve çekırdek DOM düzeyi 2 uygulayan BIR XML belgesinin düzenlenebilir bellek içi gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf5fc-105">The <xref:System.Xml.XmlDocument> class provides an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="cf5fc-106">Her iki sınıf de <xref:System.Xml.XPath.IXPathNavigable> arabirimini uygular ve <xref:System.Xml.XPath.XPathNavigator> seçim yapmak, değerlendirmek, gezinmek ve bazı durumlarda, temel alınan XML verilerini düzenlemek için kullanılan bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="cf5fc-106">Both classes implement the <xref:System.Xml.XPath.IXPathNavigable> interface and return an <xref:System.Xml.XPath.XPathNavigator> object used to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="cf5fc-107">Aşağıdaki bölümlerde, <xref:System.Xml.XPath.XPathNavigator> döndüren sınıfına göre sınıfının işlevleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="cf5fc-107">The following sections describe the functionality of the <xref:System.Xml.XPath.XPathNavigator> class based on the class that returns it.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf5fc-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cf5fc-108">In This Section</span></span>  

 [<span data-ttu-id="cf5fc-109">XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma</span><span class="sxs-lookup"><span data-stu-id="cf5fc-109">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 <span data-ttu-id="cf5fc-110">Bir <xref:System.Xml.XPath.XPathDocument> XML belgesini okumak ve <xref:System.Xml.XmlDocument> bir XML belgesini okumak ve düzenlemek için bir salt okunurdur ve düzenlenebilir sınıf nesnesi oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf5fc-110">Describes how to create a read-only <xref:System.Xml.XPath.XPathDocument> class object to read an XML document and how to create an editable <xref:System.Xml.XmlDocument> class object to read and edit an XML document.</span></span> <span data-ttu-id="cf5fc-111">Bu konu ayrıca <xref:System.Xml.XPath.XPathNavigator> BIR XML belgesini gezinmek ve düzenlemek için her sınıftan bir nesne döndürme işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf5fc-111">This topic also describes how return an <xref:System.Xml.XPath.XPathNavigator> object from each class to navigate and edit an XML document.</span></span>  
  
 [<span data-ttu-id="cf5fc-112">XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="cf5fc-112">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="cf5fc-113">Bir <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> XPath sorgusu kullanarak bir veya nesnesindeki düğümleri seçmek, bir XPath ifadesinin sonuçlarını değerlendirmek ve INCELEMEK ve bir XML belgesindeki bir düğümün belirli bir XPath ifadesiyle eşleşip eşleşmediğini belirlemek için kullanılan sınıfının yöntemlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf5fc-113">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an XML document matches a given XPath expression.</span></span>  
  
 [<span data-ttu-id="cf5fc-114">XPathNavigator Kullanarak XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="cf5fc-114">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="cf5fc-115"><xref:System.Xml.XPath.XPathNavigator>Düğümlerde gezinmek, XML verilerini ayıklamak ve bir veya nesnesinde kesin olarak BELIRLENMIŞ XML verilerine erişmek için kullanılan sınıfının yöntemlerini açıklar <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="cf5fc-115">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to navigate nodes, extract XML data and access strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="cf5fc-116">XPathNavigator Kullanarak XML Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="cf5fc-116">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="cf5fc-117"><xref:System.Xml.XPath.XPathNavigator>Bir nesne içindeki BIR XML belgesinden düğümleri ve değerleri eklemek, değiştirmek ve kaldırmak için kullanılan sınıfının yöntemlerini açıklar <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="cf5fc-117">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to insert, modify and remove nodes and values from an XML document contained in an <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="cf5fc-118">XPathNavigator Kullanarak Şema Doğrulama</span><span class="sxs-lookup"><span data-stu-id="cf5fc-118">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="cf5fc-119">Bir veya nesnesinde bulunan XML içeriğini doğrulamaya yönelik yolları açıklar <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="cf5fc-119">Describes the ways to validate the XML content contained in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf5fc-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf5fc-120">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="cf5fc-121">DOM Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="cf5fc-121">Process XML Data Using the DOM Model</span></span>](process-xml-data-using-the-dom-model.md)
