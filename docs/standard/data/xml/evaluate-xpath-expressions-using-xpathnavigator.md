---
title: XPathNavigator Kullanarak XPath İfadelerini Değerlendirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
ms.openlocfilehash: 19e3287a990bbfd793bce892b14f08f31c53faa2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687209"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="4d6d6-102">XPathNavigator Kullanarak XPath İfadelerini Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="4d6d6-102">Evaluate XPath Expressions using XPathNavigator</span></span>

<span data-ttu-id="4d6d6-103"><xref:System.Xml.XPath.XPathNavigator>Sınıfı, <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> bir XPath ifadesini değerlendirmek için yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d6d6-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="4d6d6-104"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Yöntemi bir XPath ifadesi alır, değerlendirir ve XPath ifadesinin sonucuna göre Boole, sayı, dize veya düğüm KÜMESININ W3C XPath türünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="4d6d6-104">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="4d6d6-105">Değerlendir yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d6d6-105">The Evaluate Method</span></span>  

 <span data-ttu-id="4d6d6-106"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Yöntemi bir XPath ifadesi alır, bunu değerlendirir ve Boole ( <xref:System.Boolean> ), sayı ( <xref:System.Double> ), dize () <xref:System.String> veya düğüm kümesi ( <xref:System.Xml.XPath.XPathNodeIterator> ) ile yazılmış bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="4d6d6-106">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="4d6d6-107">Örneğin, <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi matematiksel bir yöntemde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4d6d6-107">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="4d6d6-108">Aşağıdaki örnek kod, dosyadaki tüm kitapların toplam fiyatını hesaplar `books.xml` .</span><span class="sxs-lookup"><span data-stu-id="4d6d6-108">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="4d6d6-109">Örnek, `books.xml` dosyayı giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="4d6d6-109">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="4d6d6-110">konum ve son Işlevler</span><span class="sxs-lookup"><span data-stu-id="4d6d6-110">position and last Functions</span></span>  

 <span data-ttu-id="4d6d6-111"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Yöntemi aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="4d6d6-111">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="4d6d6-112">Yöntemlerden biri bir <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> <xref:System.Xml.XPath.XPathNodeIterator> nesneyi parametre olarak alır.</span><span class="sxs-lookup"><span data-stu-id="4d6d6-112">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="4d6d6-113">Bu belirli <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Yöntem, <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yalnızca bir nesneyi parametre olarak alan ve bir <xref:System.Xml.XPath.XPathExpression> düğüm kümesi bağımsız değişkeninin üzerinde değerlendirmeyi gerçekleştirmek için geçerli bağlamı belirtmesini olanaklı hale getirecağından, bu yöntem ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="4d6d6-113">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="4d6d6-114">Bu bağlam, XPath `position()` ve `last()` işlevler için geçerli bağlam düğümü göreli oldukları için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4d6d6-114">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="4d6d6-115">Bir konum adımında koşul olarak kullanılmadığı sürece `position()` ve `last()` işlevleri, aksi takdirde değerlendirilmek üzere bir düğüm kümesine başvuru gerektirir, `position` ve `last` işlevleri döndürülür `0` .</span><span class="sxs-lookup"><span data-stu-id="4d6d6-115">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d6d6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d6d6-116">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="4d6d6-117">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="4d6d6-117">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="4d6d6-118">XPathNavigator Kullanarak XML Verileri Seçme</span><span class="sxs-lookup"><span data-stu-id="4d6d6-118">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="4d6d6-119">XPathNavigator Kullanarak Düğümleri Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="4d6d6-119">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="4d6d6-120">XPath Sorguları ile Tanınan Düğüm Türleri</span><span class="sxs-lookup"><span data-stu-id="4d6d6-120">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="4d6d6-121">XPath Sorguları ve Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="4d6d6-121">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="4d6d6-122">Derlenmiş XPath İfadeleri</span><span class="sxs-lookup"><span data-stu-id="4d6d6-122">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
