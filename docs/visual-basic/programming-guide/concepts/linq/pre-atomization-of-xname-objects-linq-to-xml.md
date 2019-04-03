---
title: Parçalara ayırma öncesi XName nesneleri (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: 250b7aa8060c8196c28725fded090e2a63a0ee54
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819300"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="498a7-102">Parçalara ayırma öncesi XName nesneleri (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="498a7-102">Pre-Atomization of XName Objects (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="498a7-103">LINQ to XML performansını artırmak için bir yolu önceden küçük parçalara etmektir <xref:System.Xml.Linq.XName> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="498a7-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="498a7-104">Parçalara ayırma öncesi anlamına gelir, bir dizeye atadığınız bir <xref:System.Xml.Linq.XName> oluşturucuları kullanarak XML ağacı oluşturmadan önce nesne <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="498a7-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="498a7-105">Ardından, oluşturucuya bir dizeyi geçirmek yerine, kullandığınız dizesine örtük dönüştürme <xref:System.Xml.Linq.XName>, başlatılmış geçirdiğiniz <xref:System.Xml.Linq.XName> nesne.</span><span class="sxs-lookup"><span data-stu-id="498a7-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="498a7-106">Bu, belirli adları yinelenen büyük bir XML ağacı oluştururken performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="498a7-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="498a7-107">Bunu yapmak için bildirmek ve başlatmak <xref:System.Xml.Linq.XName> XML ağacı oluşturmak ve ardından kullanmadan önce nesneleri <xref:System.Xml.Linq.XName> öğe ve öznitelik adları için dizeleri belirtmek yerine, nesneleri.</span><span class="sxs-lookup"><span data-stu-id="498a7-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="498a7-108">Çok sayıda öğe (veya öznitelikleri) oluşturuyorsanız bu teknik, aynı ada sahip önemli ölçüde performans kazanımı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="498a7-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="498a7-109">Parçalara ayırma öncesi kendi senaryonuza kullanılması gerektiği, karar vermek için test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="498a7-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="498a7-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="498a7-110">Example</span></span>  
 <span data-ttu-id="498a7-111">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="498a7-111">The following example demonstrates this.</span></span>  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 <span data-ttu-id="498a7-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="498a7-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="498a7-113">Aşağıdaki örnek, XML belgesi bir ad alanında olduğu aynı tekniği gösterir:</span><span class="sxs-lookup"><span data-stu-id="498a7-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 <span data-ttu-id="498a7-114">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="498a7-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="498a7-115">Aşağıdaki örnek, ne, büyük olasılıkla gerçek dünyada karşınıza çıkacak için daha benzer.</span><span class="sxs-lookup"><span data-stu-id="498a7-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="498a7-116">Bu örnekte, öğenin içeriğini bir sorgu tarafından sağlanır:</span><span class="sxs-lookup"><span data-stu-id="498a7-116">In this example, the content of the element is supplied by a query:</span></span>  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 <span data-ttu-id="498a7-117">Önceki örnekte, adları değil önceden parçalara ayrılmış aşağıdaki örnek, daha iyi gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="498a7-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a><span data-ttu-id="498a7-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="498a7-118">See also</span></span>

- [<span data-ttu-id="498a7-119">Performans (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="498a7-119">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
- [<span data-ttu-id="498a7-120">Parçalara ayrılmış XName ve XNamespace nesneleri (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="498a7-120">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
