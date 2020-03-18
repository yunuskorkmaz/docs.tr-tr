---
title: XName Nesnelerinin Ön Atomizasyonu (LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 2fd754a352bd2988e52ec9c67a9915a8e587b107
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591499"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a><span data-ttu-id="647e9-102">XName Nesnelerinin Ön Atomizasyonu (LINQ - XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="647e9-102">Pre-Atomization of XName Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="647e9-103">LINQ'daki performansı XML'e yükseltmenin bir yolu <xref:System.Xml.Linq.XName> nesneleri önceden atomize etmektir.</span><span class="sxs-lookup"><span data-stu-id="647e9-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="647e9-104">Ön atomize, <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> xml ağacını oluşturmadan önce bir nesneye bir dize atadığınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="647e9-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="647e9-105">Daha sonra, dizeden örtülü dönüştürmeyi string'e <xref:System.Xml.Linq.XName>doğru kullanan bir dizeyi <xref:System.Xml.Linq.XName> oluşturucuya geçirmek yerine, başharfe çevrilmiş nesneyi geçersiniz.</span><span class="sxs-lookup"><span data-stu-id="647e9-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="647e9-106">Bu, belirli adların yinelendiği büyük bir XML ağacı oluşturduğunuzda performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="647e9-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="647e9-107">Bunu yapmak için, XML <xref:System.Xml.Linq.XName> ağacını oluşturmadan önce nesneleri bildirir ve <xref:System.Xml.Linq.XName> baş harflerine başharfe çevirirsiniz ve ardından öğe ve öznitelik adları için dizeleri belirtmek yerine nesneleri kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="647e9-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="647e9-108">Bu teknik, aynı ada sahip çok sayıda öğe (veya öznitelik) oluşturuyorsanız önemli performans kazançları sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="647e9-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="647e9-109">Kullanıp kullanmadığınıza karar vermek için ön atomizeasyonu senaryonuzla test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="647e9-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="647e9-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="647e9-110">Example</span></span>  
 <span data-ttu-id="647e9-111">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="647e9-111">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="647e9-112">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="647e9-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="647e9-113">Aşağıdaki örnek, XML belgesinin bir ad alanında olduğu aynı tekniği gösterir:</span><span class="sxs-lookup"><span data-stu-id="647e9-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
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
  
 <span data-ttu-id="647e9-114">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="647e9-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="647e9-115">Aşağıdaki örnek, gerçek dünyada karşılaşacağınız şeye daha çok benzer.</span><span class="sxs-lookup"><span data-stu-id="647e9-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="647e9-116">Bu örnekte, öğenin içeriği bir sorgu tarafından sağlanır:</span><span class="sxs-lookup"><span data-stu-id="647e9-116">In this example, the content of the element is supplied by a query:</span></span>  
  
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
  
 <span data-ttu-id="647e9-117">Önceki örnek, adların önceden atomlaştırılmayan aşağıdaki örnekten daha iyi performans gösterir:</span><span class="sxs-lookup"><span data-stu-id="647e9-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="647e9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="647e9-118">See also</span></span>

- [<span data-ttu-id="647e9-119">Atomize XName ve XNamespace Nesneler (LINQ xml için) (C#)</span><span class="sxs-lookup"><span data-stu-id="647e9-119">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>](./atomized-xname-and-xnamespace-objects-linq-to-xml.md)
