---
title: Seçme, değerlendirme ve eşleştirme XPathNavigator kullanarak XML verileri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 46e059f8-4dc8-4185-9236-784be95228ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2544070bb7ea891a804edd559a5d58e08b071771
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252518"
---
# <a name="selecting-evaluating-and-matching-xml-data-using-xpathnavigator"></a><span data-ttu-id="00aff-102">Seçme, değerlendirme ve eşleştirme XPathNavigator kullanarak XML verileri</span><span class="sxs-lookup"><span data-stu-id="00aff-102">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>
<span data-ttu-id="00aff-103"><xref:System.Xml.XPath.XPathNavigator> Sınıfı düğümleri seçmek için yöntemler sağlar bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> XPath sorgusunu kullanarak, değerlendirin ve bir XPath ifadesi sonuçları inceleyin ve bir düğüm olup bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesne eşleşen bir belirli bir XPath ifadesi.</span><span class="sxs-lookup"><span data-stu-id="00aff-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object matches a given XPath expression.</span></span> <span data-ttu-id="00aff-104">Bunlar ve seçme, değerlendirme ve eşleşen düğümleri ile ilgili diğer kavramlara bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesne, aşağıdaki konularda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="00aff-104">These and other concepts that relate to selecting, evaluating and matching nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object are described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00aff-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="00aff-105">In This Section</span></span>  
 [<span data-ttu-id="00aff-106">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="00aff-106">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="00aff-107">Kümesini anlatan <xref:System.Xml.XPath.XPathNavigator> sınıf kümesi düğümleri seçmek için kullanılan yöntemleri bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> bir XPath ifadesi kullanarak nesne.</span><span class="sxs-lookup"><span data-stu-id="00aff-107">Describes the set of <xref:System.Xml.XPath.XPathNavigator> class methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span>  
  
 [<span data-ttu-id="00aff-108">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="00aff-108">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 <span data-ttu-id="00aff-109">Açıklar <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi <xref:System.Xml.XPath.XPathNavigator> bir XPath ifadesini değerlendirme için kullanılan sınıf.</span><span class="sxs-lookup"><span data-stu-id="00aff-109">Describes the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to evaluate an XPath expression.</span></span>  
  
 [<span data-ttu-id="00aff-110">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="00aff-110">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 <span data-ttu-id="00aff-111">Açıklar <xref:System.Xml.XPath.XPathNavigator.Matches%2A> yöntemi <xref:System.Xml.XPath.XPathNavigator> bir düğüm bir XPath ifadesi eşleşip eşleşmediğini belirlemek için kullanılan sınıf.</span><span class="sxs-lookup"><span data-stu-id="00aff-111">Describes the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to determine if a node matches an XPath expression.</span></span>  
  
 [<span data-ttu-id="00aff-112">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="00aff-112">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 <span data-ttu-id="00aff-113">Bir XPath sorgusu tanınan düğüm türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="00aff-113">Describes the types of nodes recognized in an XPath query.</span></span>  
  
 [<span data-ttu-id="00aff-114">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="00aff-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 <span data-ttu-id="00aff-115">Bir XPath sorgusu ad alanları kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="00aff-115">Describes the use of namespaces in an XPath query.</span></span>  
  
 [<span data-ttu-id="00aff-116">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="00aff-116">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)  
 <span data-ttu-id="00aff-117">Açıklar <xref:System.Xml.XPath.XPathExpression> derlenmiş bir XPath sorgusu temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="00aff-117">Describes the <xref:System.Xml.XPath.XPathExpression> class that represents a compiled XPath query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00aff-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00aff-118">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="00aff-119">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="00aff-119">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="00aff-120">XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma</span><span class="sxs-lookup"><span data-stu-id="00aff-120">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
- [<span data-ttu-id="00aff-121">XPathNavigator Kullanarak XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="00aff-121">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="00aff-122">XPathNavigator Kullanarak XML Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="00aff-122">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="00aff-123">XPathNavigator Kullanarak Şema Doğrulama</span><span class="sxs-lookup"><span data-stu-id="00aff-123">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
