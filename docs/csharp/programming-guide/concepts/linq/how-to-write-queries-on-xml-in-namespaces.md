---
title: 'Nasıl yapılır: XML ad alanları (C#) üzerinde sorgu yazma'
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 29c4b01bfce75ce71d5214fef0cc55cd82c4e776
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525649"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a><span data-ttu-id="3d091-102">Nasıl yapılır: XML ad alanları (C#) üzerinde sorgu yazma</span><span class="sxs-lookup"><span data-stu-id="3d091-102">How to: Write Queries on XML in Namespaces (C#)</span></span>
<span data-ttu-id="3d091-103">Bir ad alanındaki XML üzerinde sorgu yazmak için kullanmalısınız <xref:System.Xml.Linq.XName> doğru ad alanı olan nesne.</span><span class="sxs-lookup"><span data-stu-id="3d091-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="3d091-104">C# ' ta başlatmak için en yaygın bir yaklaşım olan bir <xref:System.Xml.Linq.XNamespace> URI içeren bir dize ardından kullanarak toplama işleci aşırı yükleme yerel adı ad alanı birleştirin.</span><span class="sxs-lookup"><span data-stu-id="3d091-104">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>  
  
 <span data-ttu-id="3d091-105">Bu konudaki örnekler ilk kümesi, varsayılan ad alanında bir XML ağacı oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3d091-105">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="3d091-106">İkinci küme, önekli ad alanında bir XML ağacı oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3d091-106">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d091-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d091-107">Example</span></span>  
 <span data-ttu-id="3d091-108">Aşağıdaki örnek, bir varsayılan ad alanı içinde bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3d091-108">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="3d091-109">Ardından, öğelerinin bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="3d091-109">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="3d091-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3d091-110">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="3d091-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d091-111">Example</span></span>  
 <span data-ttu-id="3d091-112">C# ' ta, sorguları olup bir ad alanı öneki ile kullanan bir XML ağacı veya varsayılan bir ad alanı ile XML ağacı sorguları yazıyorsanız bağımsız olarak aynı şekilde yazın.</span><span class="sxs-lookup"><span data-stu-id="3d091-112">In C#, you write queries in the same way regardless of whether you are writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>  
  
 <span data-ttu-id="3d091-113">Aşağıdaki örnek, bir ad alanı öneki olan bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3d091-113">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="3d091-114">Ardından, öğelerinin bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="3d091-114">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="3d091-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3d091-115">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d091-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d091-116">See Also</span></span>

- [<span data-ttu-id="3d091-117">XML ad alanları (C#) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="3d091-117">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
