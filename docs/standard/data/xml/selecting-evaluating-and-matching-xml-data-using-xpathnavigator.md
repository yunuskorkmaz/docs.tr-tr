---
title: XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme
ms.date: 03/30/2017
ms.assetid: 46e059f8-4dc8-4185-9236-784be95228ed
ms.openlocfilehash: 3096582055dc17d5724cebd79e74d2aa24154bcb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734679"
---
# <a name="selecting-evaluating-and-matching-xml-data-using-xpathnavigator"></a><span data-ttu-id="f32c0-102">XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="f32c0-102">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>

<span data-ttu-id="f32c0-103">Sınıfı, bir <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> XPath sorgusu kullanarak bir veya nesnesindeki düğümleri seçmek, bir XPath ifadesinin sonuçlarını değerlendirmek ve incelemek ve bir <xref:System.Xml.XPath.XPathDocument> veya nesnesindeki bir düğümün <xref:System.Xml.XmlDocument> belirli bir XPath ifadesiyle eşleşip eşleşmediğini belirlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f32c0-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object matches a given XPath expression.</span></span> <span data-ttu-id="f32c0-104">Bu ve bir veya nesnesindeki düğümleri seçme, değerlendirme ve eşleştirme ile ilgili diğer kavramlar <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> aşağıdaki konularda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f32c0-104">These and other concepts that relate to selecting, evaluating and matching nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object are described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f32c0-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f32c0-105">In This Section</span></span>  

 [<span data-ttu-id="f32c0-106">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="f32c0-106">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="f32c0-107">Bir <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathDocument> XPath ifadesi kullanarak bir veya nesnesindeki düğüm kümesi seçmek için kullanılan sınıf yöntemleri kümesini açıklar <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="f32c0-107">Describes the set of <xref:System.Xml.XPath.XPathNavigator> class methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span>  
  
 [<span data-ttu-id="f32c0-108">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="f32c0-108">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)  
 <span data-ttu-id="f32c0-109"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> <xref:System.Xml.XPath.XPathNavigator> Bir XPath ifadesini değerlendirmek için kullanılan sınıfının metodunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="f32c0-109">Describes the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to evaluate an XPath expression.</span></span>  
  
 [<span data-ttu-id="f32c0-110">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="f32c0-110">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)  
 <span data-ttu-id="f32c0-111"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> <xref:System.Xml.XPath.XPathNavigator> Bir düğümün bir XPath ifadesiyle eşleşip eşleşmediğini anlamak için kullanılan sınıfının yöntemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f32c0-111">Describes the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to determine if a node matches an XPath expression.</span></span>  
  
 [<span data-ttu-id="f32c0-112">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="f32c0-112">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)  
 <span data-ttu-id="f32c0-113">Bir XPath sorgusunda tanınan düğümlerin türlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f32c0-113">Describes the types of nodes recognized in an XPath query.</span></span>  
  
 [<span data-ttu-id="f32c0-114">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="f32c0-114">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)  
 <span data-ttu-id="f32c0-115">Bir XPath sorgusunda ad alanlarının kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f32c0-115">Describes the use of namespaces in an XPath query.</span></span>  
  
 [<span data-ttu-id="f32c0-116">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="f32c0-116">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)  
 <span data-ttu-id="f32c0-117"><xref:System.Xml.XPath.XPathExpression>Derlenmiş bir XPath sorgusunu temsil eden sınıfı açıklar.</span><span class="sxs-lookup"><span data-stu-id="f32c0-117">Describes the <xref:System.Xml.XPath.XPathExpression> class that represents a compiled XPath query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f32c0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f32c0-118">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="f32c0-119">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="f32c0-119">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="f32c0-120">XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma</span><span class="sxs-lookup"><span data-stu-id="f32c0-120">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="f32c0-121">XPathNavigator Kullanarak XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="f32c0-121">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="f32c0-122">XPathNavigator Kullanarak XML Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="f32c0-122">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="f32c0-123">XPathNavigator Kullanarak Şema Doğrulama</span><span class="sxs-lookup"><span data-stu-id="f32c0-123">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)
