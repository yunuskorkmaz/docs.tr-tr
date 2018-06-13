---
title: Ön Atomization XName nesnelerin (LINQ-XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: 141aa5e19e75e4a09b2d7aa04d83e8a24d2a27f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645726"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="c5973-102">Ön Atomization XName nesnelerin (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5973-102">Pre-Atomization of XName Objects (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="c5973-103">LINQ-XML performansını artırmak için bir yoldur önceden küçük parçalara ayrılamıyor için <xref:System.Xml.Linq.XName> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c5973-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="c5973-104">Ön atomization anlamına gelir dizeye atadığınız bir <xref:System.Xml.Linq.XName> , oluşturucuları kullanarak XML ağaç oluşturmadan önce nesne <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="c5973-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="c5973-105">Ardından, oluşturucuya bir dizeye geçiliyor yerine, kullandığınız örtük bir dönüştürme için <xref:System.Xml.Linq.XName>, başlatılmış geçirdiğiniz <xref:System.Xml.Linq.XName> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c5973-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="c5973-106">Belirli adları yinelenen büyük bir XML ağacı oluştururken bu performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="c5973-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="c5973-107">Bunu yapmak için bildirme ve başlatma <xref:System.Xml.Linq.XName> XML ağacını oluşturmak ve ardından kullanmaya başlamadan önce nesneleri <xref:System.Xml.Linq.XName> öğe ve öznitelik adları için dizelerini belirtme yerine nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c5973-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="c5973-108">Çok sayıda öğe (ve özniteliklerin) oluşturuyorsanız, bu teknik aynı ada sahip önemli ölçüde performans artışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5973-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="c5973-109">Bunu kullanmalısınız varsa karar vermek için senaryonuzun öncesi atomization test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5973-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5973-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5973-110">Example</span></span>  
 <span data-ttu-id="c5973-111">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5973-111">The following example demonstrates this.</span></span>  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 <span data-ttu-id="c5973-112">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="c5973-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="c5973-113">Aşağıdaki örnek, XML belgesi bir ad alanındaki olduğu aynı tekniği gösterir:</span><span class="sxs-lookup"><span data-stu-id="c5973-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 <span data-ttu-id="c5973-114">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="c5973-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="c5973-115">Aşağıdaki örnek, ne, büyük olasılıkla gerçek dünyada karşınıza çıkacak için daha benzer.</span><span class="sxs-lookup"><span data-stu-id="c5973-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="c5973-116">Bu örnekte, öğenin içeriğinin bir sorgu tarafından sağlanır:</span><span class="sxs-lookup"><span data-stu-id="c5973-116">In this example, the content of the element is supplied by a query:</span></span>  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 <span data-ttu-id="c5973-117">Önceki örnekte, adları değil önceden atomized aşağıdaki örnek, daha iyi gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="c5973-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5973-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5973-118">See Also</span></span>  
 [<span data-ttu-id="c5973-119">Performans (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5973-119">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)  
 [<span data-ttu-id="c5973-120">Atomized XName ve XNamespace nesneleri (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5973-120">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
