---
title: "XPath XPathNavigator kullanarak ifadeler değerlendir"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3d513f48155a582a5158cccdd682f5b8485caefd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="6fd2d-102">XPath XPathNavigator kullanarak ifadeler değerlendir</span><span class="sxs-lookup"><span data-stu-id="6fd2d-102">Evaluate XPath Expressions using XPathNavigator</span></span>
<span data-ttu-id="6fd2d-103"><xref:System.Xml.XPath.XPathNavigator> SAX <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> bir XPath ifadesi değerlendirmek için bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="6fd2d-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="6fd2d-104"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Yöntemi bir XPath ifadesi alır, bu hesaplar ve mantıksal değer, sayı, dize W3C XPath türünü döndürür veya düğüm kümesi XPath ifadesi sonucuna bağlı.</span><span class="sxs-lookup"><span data-stu-id="6fd2d-104">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="6fd2d-105">Yöntemini değerlendirin</span><span class="sxs-lookup"><span data-stu-id="6fd2d-105">The Evaluate Method</span></span>  
 <span data-ttu-id="6fd2d-106"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Yöntemi bir XPath ifadesi alır, bu değerlendirir ve Boolean yazılan sonucunu döndürür (<xref:System.Boolean>), sayı (<xref:System.Double>), dize (<xref:System.String>), veya düğüm kümesi (<xref:System.Xml.XPath.XPathNodeIterator>).</span><span class="sxs-lookup"><span data-stu-id="6fd2d-106">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="6fd2d-107">Örneğin, <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi matematiksel yönteminde kullanılan.</span><span class="sxs-lookup"><span data-stu-id="6fd2d-107">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="6fd2d-108">Aşağıdaki kod örneği tüm books toplam fiyatını hesaplar `books.xml` dosya.</span><span class="sxs-lookup"><span data-stu-id="6fd2d-108">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Dim query As XPathExpression = navigator.Compile("sum(//price/text())")  
Dim total As Double = CType(navigator.Evaluate(query), Double)  
Console.WriteLine(total)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
XPathExpression query = navigator.Compile("sum(//price/text())");  
Double total = (Double)navigator.Evaluate(query);  
Console.WriteLine(total);  
```  
  
 <span data-ttu-id="6fd2d-109">Örnek alır `books.xml` dosya giriş olarak.</span><span class="sxs-lookup"><span data-stu-id="6fd2d-109">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="6fd2d-110">konum ve son işlevleri</span><span class="sxs-lookup"><span data-stu-id="6fd2d-110">position and last Functions</span></span>  
 <span data-ttu-id="6fd2d-111"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Yöntemi aşırı yüklü.</span><span class="sxs-lookup"><span data-stu-id="6fd2d-111">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="6fd2d-112">Aşağıdakilerden birini <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemleri alır bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesini parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="6fd2d-112">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="6fd2d-113">Bu belirli <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi ile aynıdır <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yönteminin yalnızca alan bir <xref:System.Xml.XPath.XPathExpression> bir düğüm kümesi değerlendirme yapmak için geçerli bağlamı belirtmek için bağımsız değişken sağlar ancak bu nesne bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="6fd2d-113">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="6fd2d-114">Bu bağlam için XPath gereklidir `position()` ve `last()` göre geçerli bağlam düğümünün oldukları gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="6fd2d-114">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="6fd2d-115">Konum adımda, bir koşul olarak kullanılmadığı sürece `position()` ve `last()` işlevleri düğüm Aksi halde, değerlendirilebilmesi için kümesi başvurusu gerektiren `position` ve `last` işlevleri return `0`.</span><span class="sxs-lookup"><span data-stu-id="6fd2d-115">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fd2d-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6fd2d-116">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="6fd2d-117">XPath veri modelini kullanarak işlem XML verileri</span><span class="sxs-lookup"><span data-stu-id="6fd2d-117">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="6fd2d-118">XML verileri XPathNavigator kullanarak seçin</span><span class="sxs-lookup"><span data-stu-id="6fd2d-118">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="6fd2d-119">Eşleşen düğümleri XPathNavigator kullanma</span><span class="sxs-lookup"><span data-stu-id="6fd2d-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="6fd2d-120">XPath sorguları tanınan düğüm türleri</span><span class="sxs-lookup"><span data-stu-id="6fd2d-120">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="6fd2d-121">XPath sorguları ve ad alanları</span><span class="sxs-lookup"><span data-stu-id="6fd2d-121">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="6fd2d-122">Derlenmiş XPath ifadeleri</span><span class="sxs-lookup"><span data-stu-id="6fd2d-122">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
