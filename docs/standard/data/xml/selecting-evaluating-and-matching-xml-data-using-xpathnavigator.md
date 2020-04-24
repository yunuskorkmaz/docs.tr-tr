---
title: XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 46e059f8-4dc8-4185-9236-784be95228ed
ms.openlocfilehash: 1a76edf22483c0df8871badcb5e162dd3e66001f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710147"
---
# <a name="selecting-evaluating-and-matching-xml-data-using-xpathnavigator"></a><span data-ttu-id="28542-102">XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="28542-102">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>
<span data-ttu-id="28542-103"><xref:System.Xml.XPath.XPathNavigator> Sınıfı, bir XPath sorgusu kullanarak <xref:System.Xml.XPath.XPathDocument> bir veya <xref:System.Xml.XmlDocument> nesnesindeki düğümleri seçmek, bir XPath ifadesinin sonuçlarını değerlendirmek ve incelemek ve bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesindeki bir düğümün belirli bir XPath ifadesiyle eşleşip eşleşmediğini belirlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="28542-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object matches a given XPath expression.</span></span> <span data-ttu-id="28542-104">Bu ve bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesindeki düğümleri seçme, değerlendirme ve eşleştirme ile ilgili diğer kavramlar aşağıdaki konularda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="28542-104">These and other concepts that relate to selecting, evaluating and matching nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object are described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="28542-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="28542-105">In This Section</span></span>  
 [<span data-ttu-id="28542-106">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="28542-106">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="28542-107">Bir XPath ifadesi kullanarak <xref:System.Xml.XPath.XPathNavigator> bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesindeki düğüm kümesi seçmek için kullanılan sınıf yöntemleri kümesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="28542-107">Describes the set of <xref:System.Xml.XPath.XPathNavigator> class methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span>  
  
 [<span data-ttu-id="28542-108">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="28542-108">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 <span data-ttu-id="28542-109">Bir XPath <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> ifadesini değerlendirmek için <xref:System.Xml.XPath.XPathNavigator> kullanılan sınıfının metodunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="28542-109">Describes the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to evaluate an XPath expression.</span></span>  
  
 [<span data-ttu-id="28542-110">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="28542-110">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 <span data-ttu-id="28542-111">Bir düğümün <xref:System.Xml.XPath.XPathNavigator.Matches%2A> bir XPath ifadesiyle <xref:System.Xml.XPath.XPathNavigator> eşleşip eşleşmediğini anlamak için kullanılan sınıfının yöntemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="28542-111">Describes the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to determine if a node matches an XPath expression.</span></span>  
  
 [<span data-ttu-id="28542-112">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="28542-112">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 <span data-ttu-id="28542-113">Bir XPath sorgusunda tanınan düğümlerin türlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="28542-113">Describes the types of nodes recognized in an XPath query.</span></span>  
  
 [<span data-ttu-id="28542-114">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="28542-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 <span data-ttu-id="28542-115">Bir XPath sorgusunda ad alanlarının kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="28542-115">Describes the use of namespaces in an XPath query.</span></span>  
  
 [<span data-ttu-id="28542-116">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="28542-116">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)  
 <span data-ttu-id="28542-117">Derlenmiş bir <xref:System.Xml.XPath.XPathExpression> XPath sorgusunu temsil eden sınıfı açıklar.</span><span class="sxs-lookup"><span data-stu-id="28542-117">Describes the <xref:System.Xml.XPath.XPathExpression> class that represents a compiled XPath query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28542-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28542-118">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="28542-119">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="28542-119">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="28542-120">XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma</span><span class="sxs-lookup"><span data-stu-id="28542-120">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="28542-121">XPathNavigator Kullanarak XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="28542-121">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="28542-122">XPathNavigator Kullanarak XML Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="28542-122">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="28542-123">XPathNavigator Kullanarak Şema Doğrulama</span><span class="sxs-lookup"><span data-stu-id="28542-123">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
