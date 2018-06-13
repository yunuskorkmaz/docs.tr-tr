---
title: 'Nasıl yapılır: XML ad alanları (C#) içinde sorguları yazma'
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: a5de5ffdafc2dd191a35860150e48a86a3603f3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320336"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a><span data-ttu-id="b1416-102">Nasıl yapılır: XML ad alanları (C#) içinde sorguları yazma</span><span class="sxs-lookup"><span data-stu-id="b1416-102">How to: Write Queries on XML in Namespaces (C#)</span></span>
<span data-ttu-id="b1416-103">İçinde bir ad alanı XML bir sorgu yazmak için kullanmanız gerekir <xref:System.Xml.Linq.XName> doğru ad alanına sahip nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b1416-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="b1416-104">C# ' ta en yaygın başlatmak için yaklaşımdır bir <xref:System.Xml.Linq.XNamespace> URI içeren bir dize sonra kullanımı Toplama işleci aşırı ad alanı yerel ad ile birleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="b1416-104">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>  
  
 <span data-ttu-id="b1416-105">Bu konudaki örnekler ilk kümesi varsayılan ad alanında bir XML ağacı oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1416-105">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="b1416-106">İkinci küme öneki bir ad alanındaki bir XML ağacı oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1416-106">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1416-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1416-107">Example</span></span>  
 <span data-ttu-id="b1416-108">Aşağıdaki örnek, bir varsayılan ad alanı içinde bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1416-108">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="b1416-109">Ardından, öğe koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="b1416-109">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="b1416-110">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="b1416-110">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="b1416-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1416-111">Example</span></span>  
 <span data-ttu-id="b1416-112">C# ' ta, sorguları olup bir ad alanı öneki ile kullanan bir XML ağaç veya varsayılan ad alanını içeren bir XML ağacı sorguları yazıyorsanız bağımsız olarak aynı şekilde yazın.</span><span class="sxs-lookup"><span data-stu-id="b1416-112">In C#, you write queries in the same way regardless of whether you are writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>  
  
 <span data-ttu-id="b1416-113">Aşağıdaki örnek, bir ad alanı öneki bulunduğu bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1416-113">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="b1416-114">Ardından, öğe koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="b1416-114">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="b1416-115">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="b1416-115">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1416-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1416-116">See Also</span></span>  
 [<span data-ttu-id="b1416-117">XML ad alanları (C#) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="b1416-117">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
