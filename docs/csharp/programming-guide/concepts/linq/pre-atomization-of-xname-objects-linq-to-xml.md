---
title: Parçalara ayırma öncesi XName nesneleri (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 6a1f3ea5e0b53fe488c13ebd273cce436d7c685b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516222"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a><span data-ttu-id="8162d-102">Parçalara ayırma öncesi XName nesneleri (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8162d-102">Pre-Atomization of XName Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="8162d-103">LINQ to XML performansını artırmak için bir yolu önceden küçük parçalara etmektir <xref:System.Xml.Linq.XName> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="8162d-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="8162d-104">Parçalara ayırma öncesi anlamına gelir, bir dizeye atadığınız bir <xref:System.Xml.Linq.XName> oluşturucuları kullanarak XML ağacı oluşturmadan önce nesne <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="8162d-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="8162d-105">Ardından, oluşturucuya bir dizeyi geçirmek yerine, kullandığınız dizesine örtük dönüştürme <xref:System.Xml.Linq.XName>, başlatılmış geçirdiğiniz <xref:System.Xml.Linq.XName> nesne.</span><span class="sxs-lookup"><span data-stu-id="8162d-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="8162d-106">Bu, belirli adları yinelenen büyük bir XML ağacı oluştururken performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="8162d-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="8162d-107">Bunu yapmak için bildirmek ve başlatmak <xref:System.Xml.Linq.XName> XML ağacı oluşturmak ve ardından kullanmadan önce nesneleri <xref:System.Xml.Linq.XName> öğe ve öznitelik adları için dizeleri belirtmek yerine, nesneleri.</span><span class="sxs-lookup"><span data-stu-id="8162d-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="8162d-108">Çok sayıda öğe (veya öznitelikleri) oluşturuyorsanız bu teknik, aynı ada sahip önemli ölçüde performans kazanımı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="8162d-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="8162d-109">Parçalara ayırma öncesi kendi senaryonuza kullanılması gerektiği, karar vermek için test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8162d-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8162d-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="8162d-110">Example</span></span>  
 <span data-ttu-id="8162d-111">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8162d-111">The following example demonstrates this.</span></span>  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="8162d-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="8162d-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="8162d-113">Aşağıdaki örnek, XML belgesi bir ad alanında olduğu aynı tekniği gösterir:</span><span class="sxs-lookup"><span data-stu-id="8162d-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XName Root = aw + "Root";  
XName Data = aw + "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XAttribute(XNamespace.Xmlns + "aw", aw),  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="8162d-114">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="8162d-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="8162d-115">Aşağıdaki örnek, ne, büyük olasılıkla gerçek dünyada karşınıza çıkacak için daha benzer.</span><span class="sxs-lookup"><span data-stu-id="8162d-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="8162d-116">Bu örnekte, öğenin içeriğini bir sorgu tarafından sağlanır:</span><span class="sxs-lookup"><span data-stu-id="8162d-116">In this example, the content of the element is supplied by a query:</span></span>  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
DateTime t1 = DateTime.Now;  
XElement root = new XElement(Root,  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement(Data,  
        new XAttribute(ID, i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
 <span data-ttu-id="8162d-117">Önceki örnekte, adları değil önceden parçalara ayrılmış aşağıdaki örnek, daha iyi gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="8162d-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
```csharp  
DateTime t1 = DateTime.Now;  
XElement root = new XElement("Root",  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement("Data",  
        new XAttribute("ID", i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="8162d-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8162d-118">See Also</span></span>

- [<span data-ttu-id="8162d-119">Performans (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8162d-119">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)  
- [<span data-ttu-id="8162d-120">Parçalara ayrılmış XName ve XNamespace nesneleri (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8162d-120">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
