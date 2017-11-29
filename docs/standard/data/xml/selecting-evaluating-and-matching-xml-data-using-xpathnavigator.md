---
title: "Seçildiğinde, Evaluating ve XML XPathNavigator kullanarak veri eşleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46e059f8-4dc8-4185-9236-784be95228ed
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7a86fb36d367342ea0c5bc4968bdd5744bd0524e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="selecting-evaluating-and-matching-xml-data-using-xpathnavigator"></a><span data-ttu-id="5231e-102">Seçildiğinde, Evaluating ve XML XPathNavigator kullanarak veri eşleştirme</span><span class="sxs-lookup"><span data-stu-id="5231e-102">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>
<span data-ttu-id="5231e-103"><xref:System.Xml.XPath.XPathNavigator> Sınıfı düğümler seçmek için yöntemler sağlar bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> bir XPath sorgusu kullanılarak nesne, değerlendirmek ve bir XPath ifadesi sonuçlarını inceleyin ve bir düğüm olup bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesne eşleşen bir verilen XPath ifadesi.</span><span class="sxs-lookup"><span data-stu-id="5231e-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object matches a given XPath expression.</span></span> <span data-ttu-id="5231e-104">Bunlar ve seçerek, değerlendirme ve eşleşen düğümler ile ilgili diğer kavramlara bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesne aşağıdaki konularda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5231e-104">These and other concepts that relate to selecting, evaluating and matching nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object are described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5231e-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5231e-105">In This Section</span></span>  
 [<span data-ttu-id="5231e-106">XML verileri XPathNavigator kullanarak seçin</span><span class="sxs-lookup"><span data-stu-id="5231e-106">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="5231e-107">Açıklar <xref:System.Xml.XPath.XPathNavigator> sınıfı yöntemlerinin düğümler kümesi seçmek için kullanılan bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> bir XPath ifadesi kullanarak nesne.</span><span class="sxs-lookup"><span data-stu-id="5231e-107">Describes the set of <xref:System.Xml.XPath.XPathNavigator> class methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span>  
  
 [<span data-ttu-id="5231e-108">XPath XPathNavigator kullanarak ifadeler değerlendir</span><span class="sxs-lookup"><span data-stu-id="5231e-108">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 <span data-ttu-id="5231e-109">Açıklar <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi <xref:System.Xml.XPath.XPathNavigator> bir XPath ifadesi değerlendirmek için kullanılan bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="5231e-109">Describes the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to evaluate an XPath expression.</span></span>  
  
 [<span data-ttu-id="5231e-110">Eşleşen düğümleri XPathNavigator kullanma</span><span class="sxs-lookup"><span data-stu-id="5231e-110">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 <span data-ttu-id="5231e-111">Açıklar <xref:System.Xml.XPath.XPathNavigator.Matches%2A> yöntemi <xref:System.Xml.XPath.XPathNavigator> bir düğümün bir XPath ifadesi eşleşip eşleşmediğini belirlemek için kullanılan bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="5231e-111">Describes the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to determine if a node matches an XPath expression.</span></span>  
  
 [<span data-ttu-id="5231e-112">XPath sorguları tanınan düğüm türleri</span><span class="sxs-lookup"><span data-stu-id="5231e-112">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 <span data-ttu-id="5231e-113">Bir XPath sorgusu tanınan düğüm türlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="5231e-113">Describes the types of nodes recognized in an XPath query.</span></span>  
  
 [<span data-ttu-id="5231e-114">XPath sorguları ve ad alanları</span><span class="sxs-lookup"><span data-stu-id="5231e-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 <span data-ttu-id="5231e-115">Bir XPath sorgusu ad alanları kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="5231e-115">Describes the use of namespaces in an XPath query.</span></span>  
  
 [<span data-ttu-id="5231e-116">Derlenmiş XPath ifadeleri</span><span class="sxs-lookup"><span data-stu-id="5231e-116">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)  
 <span data-ttu-id="5231e-117">Açıklar <xref:System.Xml.XPath.XPathExpression> derlenmiş bir XPath sorgusu temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="5231e-117">Describes the <xref:System.Xml.XPath.XPathExpression> class that represents a compiled XPath query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5231e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5231e-118">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="5231e-119">XPath veri modelini kullanarak işlem XML verileri</span><span class="sxs-lookup"><span data-stu-id="5231e-119">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="5231e-120">XPathDocument ve XmlDocument kullanarak XML verilerini okuma</span><span class="sxs-lookup"><span data-stu-id="5231e-120">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [<span data-ttu-id="5231e-121">XML XPathNavigator kullanarak verilerine erişme</span><span class="sxs-lookup"><span data-stu-id="5231e-121">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="5231e-122">XML XPathNavigator kullanarak verileri düzenleme</span><span class="sxs-lookup"><span data-stu-id="5231e-122">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="5231e-123">XPathNavigator kullanarak şema doğrulaması</span><span class="sxs-lookup"><span data-stu-id="5231e-123">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
