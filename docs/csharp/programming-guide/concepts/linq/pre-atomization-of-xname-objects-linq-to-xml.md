---
title: XName nesnelerinin (LINQ to XML) (C#) ön atomonu
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 2fd754a352bd2988e52ec9c67a9915a8e587b107
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591499"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a><span data-ttu-id="4ce10-102">XName nesnelerinin (LINQ to XML) (C#) ön atomonu</span><span class="sxs-lookup"><span data-stu-id="4ce10-102">Pre-Atomization of XName Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="4ce10-103">LINQ to XML performansını artırmanın bir yolu, önceden ayrılamaz <xref:System.Xml.Linq.XName> nesneleri kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="4ce10-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="4ce10-104">Ön cekleştirme, <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> sınıflarının oluşturucularını kullanarak xml ağacını oluşturmadan önce bir nesneye bir dize atadığınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4ce10-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="4ce10-105">Ardından, dizeden öğesine <xref:System.Xml.Linq.XName>örtük dönüştürmeyi kullanan oluşturucuya bir dize geçirmek yerine, başlatılan <xref:System.Xml.Linq.XName> nesneyi geçirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ce10-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="4ce10-106">Bu, belirli adların tekrarlandığı büyük bir XML ağacı oluşturduğunuzda performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="4ce10-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="4ce10-107">Bunu yapmak için, xml ağacını oluşturmadan önce <xref:System.Xml.Linq.XName> nesneleri bildirir ve başlatır ve sonra öğe ve öznitelik adları için dizeleri <xref:System.Xml.Linq.XName> belirtmek yerine nesneleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ce10-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="4ce10-108">Aynı ada sahip çok sayıda öğe (veya öznitelik) oluşturuyorsanız bu teknik önemli performans artışı elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="4ce10-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="4ce10-109">Kullanmanız gerekip gerekmediğini belirlemek için senaryolarınız ile önceden atomleştirme testi yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ce10-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ce10-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ce10-110">Example</span></span>  
 <span data-ttu-id="4ce10-111">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ce10-111">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="4ce10-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4ce10-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="4ce10-113">Aşağıdaki örnek, XML belgesinin bir ad alanında bulunduğu tekniği gösterir:</span><span class="sxs-lookup"><span data-stu-id="4ce10-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
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
  
 <span data-ttu-id="4ce10-114">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4ce10-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="4ce10-115">Aşağıdaki örnek, gerçek dünyada büyük olasılıkla karşılaşacağınız şekilde daha benzerdir.</span><span class="sxs-lookup"><span data-stu-id="4ce10-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="4ce10-116">Bu örnekte, öğesinin içeriği bir sorgu tarafından sağlanır:</span><span class="sxs-lookup"><span data-stu-id="4ce10-116">In this example, the content of the element is supplied by a query:</span></span>  
  
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
  
 <span data-ttu-id="4ce10-117">Önceki örnek, şu örnekteki adların ön cede olmadığı bir daha iyi şekilde çalışır:</span><span class="sxs-lookup"><span data-stu-id="4ce10-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ce10-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ce10-118">See also</span></span>

- [<span data-ttu-id="4ce10-119">Atomlanmış XName ve XNamespace nesneleri (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4ce10-119">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>](./atomized-xname-and-xnamespace-objects-linq-to-xml.md)
