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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4d4515b8ebea338a153319dfd02eab8d389b843b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="e977d-102">XPath XPathNavigator kullanarak ifadeler değerlendir</span><span class="sxs-lookup"><span data-stu-id="e977d-102">Evaluate XPath Expressions using XPathNavigator</span></span>
<span data-ttu-id="e977d-103"><xref:System.Xml.XPath.XPathNavigator> SAX <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> bir XPath ifadesi değerlendirmek için bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="e977d-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="e977d-104"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Yöntemi bir XPath ifadesi alır, bu hesaplar ve mantıksal değer, sayı, dize W3C XPath türünü döndürür veya düğüm kümesi XPath ifadesi sonucuna bağlı.</span><span class="sxs-lookup"><span data-stu-id="e977d-104">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="e977d-105">Yöntemini değerlendirin</span><span class="sxs-lookup"><span data-stu-id="e977d-105">The Evaluate Method</span></span>  
 <span data-ttu-id="e977d-106"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Yöntemi bir XPath ifadesi alır, bu değerlendirir ve Boolean yazılan sonucunu döndürür (<xref:System.Boolean>), sayı (<xref:System.Double>), dize (<xref:System.String>), veya düğüm kümesi (<xref:System.Xml.XPath.XPathNodeIterator>).</span><span class="sxs-lookup"><span data-stu-id="e977d-106">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="e977d-107">Örneğin, <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi matematiksel yönteminde kullanılan.</span><span class="sxs-lookup"><span data-stu-id="e977d-107">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="e977d-108">Aşağıdaki kod örneği tüm books toplam fiyatını hesaplar `books.xml` dosya.</span><span class="sxs-lookup"><span data-stu-id="e977d-108">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="e977d-109">Örnek alır `books.xml` dosya giriş olarak.</span><span class="sxs-lookup"><span data-stu-id="e977d-109">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="e977d-110">konum ve son işlevleri</span><span class="sxs-lookup"><span data-stu-id="e977d-110">position and last Functions</span></span>  
 <span data-ttu-id="e977d-111"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Yöntemi aşırı yüklü.</span><span class="sxs-lookup"><span data-stu-id="e977d-111">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="e977d-112">Aşağıdakilerden birini <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemleri alır bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesini parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="e977d-112">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="e977d-113">Bu belirli <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi ile aynıdır <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yönteminin yalnızca alan bir <xref:System.Xml.XPath.XPathExpression> bir düğüm kümesi değerlendirme yapmak için geçerli bağlamı belirtmek için bağımsız değişken sağlar ancak bu nesne bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="e977d-113">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="e977d-114">Bu bağlam için XPath gereklidir `position()` ve `last()` göre geçerli bağlam düğümünün oldukları gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="e977d-114">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="e977d-115">Konum adımda, bir koşul olarak kullanılmadığı sürece `position()` ve `last()` işlevleri düğüm Aksi halde, değerlendirilebilmesi için kümesi başvurusu gerektiren `position` ve `last` işlevleri return `0`.</span><span class="sxs-lookup"><span data-stu-id="e977d-115">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e977d-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e977d-116">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="e977d-117">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="e977d-117">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="e977d-118">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="e977d-118">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="e977d-119">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="e977d-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="e977d-120">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="e977d-120">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="e977d-121">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="e977d-121">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="e977d-122">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="e977d-122">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
