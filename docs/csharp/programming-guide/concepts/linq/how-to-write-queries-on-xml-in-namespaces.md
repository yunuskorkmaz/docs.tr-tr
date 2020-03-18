---
title: Ad alanlarında XML'de sorgu yazma (C#)
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: a8b8d55daaad1ae00e43fed897080ed7a62fafab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75337369"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a><span data-ttu-id="d21f9-102">Ad alanlarında XML'de sorgu yazma (C#)</span><span class="sxs-lookup"><span data-stu-id="d21f9-102">How to write queries on XML in namespaces (C#)</span></span>
<span data-ttu-id="d21f9-103">XML'de ad alanında bir sorgu yazmak için <xref:System.Xml.Linq.XName> doğru ad alanına sahip nesneleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d21f9-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="d21f9-104">C# için en yaygın yaklaşım, URI <xref:System.Xml.Linq.XNamespace> içeren bir dize kullanarak bir başlangıç yapmak, ardından ad alanını yerel adla birleştirmek için ek işleci aşırı yüklenmesini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="d21f9-104">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>  
  
 <span data-ttu-id="d21f9-105">Bu konudaki ilk örnek kümesi, varsayılan ad alanında bir XML ağacının nasıl oluşturultur olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d21f9-105">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="d21f9-106">İkinci küme, bir ad alanında önek içeren bir XML ağacının nasıl oluşturultur olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d21f9-106">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d21f9-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d21f9-107">Example</span></span>  
 <span data-ttu-id="d21f9-108">Aşağıdaki örnekte varsayılan ad alanında bir XML ağacı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d21f9-108">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="d21f9-109">Daha sonra bir öğe koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="d21f9-109">It then retrieves a collection of elements.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 <span data-ttu-id="d21f9-110">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d21f9-110">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="d21f9-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d21f9-111">Example</span></span>  
 <span data-ttu-id="d21f9-112">C#'da, önklü bir ad alanı kullanan bir XML ağacında veya varsayılan ad alanına sahip bir XML ağacında sorgu lar yazıp yazmadığınıza bakılmaksızın sorguları aynı şekilde yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="d21f9-112">In C#, you write queries in the same way regardless of whether you are writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>  
  
 <span data-ttu-id="d21f9-113">Aşağıdaki örnek, önek içeren bir ad alanında olan bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d21f9-113">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="d21f9-114">Daha sonra bir öğe koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="d21f9-114">It then retrieves a collection of elements.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
    <aw:Child>1</aw:Child>  
    <aw:Child>2</aw:Child>  
    <aw:Child>3</aw:Child>  
    <aw:AnotherChild>4</aw:AnotherChild>  
    <aw:AnotherChild>5</aw:AnotherChild>  
    <aw:AnotherChild>6</aw:AnotherChild>  
</aw:Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 <span data-ttu-id="d21f9-115">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d21f9-115">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="d21f9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d21f9-116">See also</span></span>

- [<span data-ttu-id="d21f9-117">İsim Alanlarına Genel Bakış (LINQ - XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d21f9-117">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
