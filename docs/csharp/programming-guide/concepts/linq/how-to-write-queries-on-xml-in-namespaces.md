---
title: Ad alanlarında XML üzerinde sorgu yazma (C#)
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: a8b8d55daaad1ae00e43fed897080ed7a62fafab
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337369"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a><span data-ttu-id="ab798-102">Ad alanlarında XML üzerinde sorgu yazma (C#)</span><span class="sxs-lookup"><span data-stu-id="ab798-102">How to write queries on XML in namespaces (C#)</span></span>
<span data-ttu-id="ab798-103">Bir ad alanında olan XML üzerinde bir sorgu yazmak için, doğru ad alanına sahip <xref:System.Xml.Linq.XName> nesneleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab798-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="ab798-104">İçin C#en yaygın YAKLAŞıM, URI 'yi içeren bir dize kullanarak bir <xref:System.Xml.Linq.XNamespace> başlatmaktır ve sonra ad alanını yerel adla birleştirmek için ek işleç aşırı yüklemesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="ab798-104">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>  
  
 <span data-ttu-id="ab798-105">Bu konudaki ilk örnek kümesi, varsayılan bir ad alanında bir XML ağacının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab798-105">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="ab798-106">İkinci küme, öneki olan bir ad alanında bir XML ağacının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab798-106">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab798-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab798-107">Example</span></span>  
 <span data-ttu-id="ab798-108">Aşağıdaki örnek, varsayılan bir ad alanında bulunan bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ab798-108">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="ab798-109">Daha sonra bir öğe koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="ab798-109">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="ab798-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ab798-110">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="ab798-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab798-111">Example</span></span>  
 <span data-ttu-id="ab798-112">' C#De, ön ek içeren bir ad alanı kullanan bir XML ağacına veya varsayılan bir ad alanına sahıp bir XML ağacına sorgu yazarken aynı şekilde sorgular yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="ab798-112">In C#, you write queries in the same way regardless of whether you are writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>  
  
 <span data-ttu-id="ab798-113">Aşağıdaki örnek, öneki olan bir ad alanında olan bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ab798-113">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="ab798-114">Daha sonra bir öğe koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="ab798-114">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="ab798-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ab798-115">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab798-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab798-116">See also</span></span>

- [<span data-ttu-id="ab798-117">Ad alanlarına genel bakış (LINQ to XMLC#) ()</span><span class="sxs-lookup"><span data-stu-id="ab798-117">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
