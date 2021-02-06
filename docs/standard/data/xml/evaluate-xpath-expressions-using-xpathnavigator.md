---
description: 'Hakkında daha fazla bilgi edinin: XPathNavigator kullanarak XPath deyimlerini değerlendirme'
title: XPathNavigator Kullanarak XPath İfadelerini Değerlendirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
ms.openlocfilehash: 847f83eb9a41cdd28763c5b1516bee89c04517fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99629623"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="f4ced-103">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="f4ced-103">Evaluate XPath Expressions using XPathNavigator</span></span>

<span data-ttu-id="f4ced-104"><xref:System.Xml.XPath.XPathNavigator>Sınıfı, <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> bir XPath ifadesini değerlendirmek için yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4ced-104">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="f4ced-105"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Yöntemi bir XPath ifadesi alır, değerlendirir ve XPath ifadesinin sonucuna göre Boole, sayı, dize veya düğüm KÜMESININ W3C XPath türünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4ced-105">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="f4ced-106">Değerlendir yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4ced-106">The Evaluate Method</span></span>  

 <span data-ttu-id="f4ced-107"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Yöntemi bir XPath ifadesi alır, bunu değerlendirir ve Boole ( <xref:System.Boolean> ), sayı ( <xref:System.Double> ), dize () <xref:System.String> veya düğüm kümesi ( <xref:System.Xml.XPath.XPathNodeIterator> ) ile yazılmış bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4ced-107">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="f4ced-108">Örneğin, <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi matematiksel bir yöntemde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f4ced-108">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="f4ced-109">Aşağıdaki örnek kod, dosyadaki tüm kitapların toplam fiyatını hesaplar `books.xml` .</span><span class="sxs-lookup"><span data-stu-id="f4ced-109">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="f4ced-110">Örnek, `books.xml` dosyayı giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="f4ced-110">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="f4ced-111">konum ve son Işlevler</span><span class="sxs-lookup"><span data-stu-id="f4ced-111">position and last Functions</span></span>  

 <span data-ttu-id="f4ced-112"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Yöntemi aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="f4ced-112">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="f4ced-113">Yöntemlerden biri bir <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> <xref:System.Xml.XPath.XPathNodeIterator> nesneyi parametre olarak alır.</span><span class="sxs-lookup"><span data-stu-id="f4ced-113">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="f4ced-114">Bu belirli <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Yöntem, <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yalnızca bir nesneyi parametre olarak alan ve bir <xref:System.Xml.XPath.XPathExpression> düğüm kümesi bağımsız değişkeninin üzerinde değerlendirmeyi gerçekleştirmek için geçerli bağlamı belirtmesini olanaklı hale getirecağından, bu yöntem ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f4ced-114">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="f4ced-115">Bu bağlam, XPath `position()` ve `last()` işlevler için geçerli bağlam düğümü göreli oldukları için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f4ced-115">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="f4ced-116">Bir konum adımında koşul olarak kullanılmadığı sürece `position()` ve `last()` işlevleri, aksi takdirde değerlendirilmek üzere bir düğüm kümesine başvuru gerektirir, `position` ve `last` işlevleri döndürülür `0` .</span><span class="sxs-lookup"><span data-stu-id="f4ced-116">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4ced-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4ced-117">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="f4ced-118">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="f4ced-118">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="f4ced-119">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="f4ced-119">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="f4ced-120">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="f4ced-120">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="f4ced-121">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="f4ced-121">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="f4ced-122">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="f4ced-122">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="f4ced-123">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="f4ced-123">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
