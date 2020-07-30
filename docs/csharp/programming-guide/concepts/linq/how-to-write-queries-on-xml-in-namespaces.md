---
title: Ad alanlarında XML üzerinde sorgu yazma (C#)
description: Ad alanlarında XML üzerinde sorgu yazmayı öğrenin. Bu sorgular için, doğru ad alanına sahip XName nesnelerini kullanmanız gerekir.
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 64eb9df1cde3b434a11e2e5410aab96993dc0fa1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303185"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a><span data-ttu-id="14d56-104">Ad alanlarında XML üzerinde sorgu yazma (C#)</span><span class="sxs-lookup"><span data-stu-id="14d56-104">How to write queries on XML in namespaces (C#)</span></span>
<span data-ttu-id="14d56-105">Bir ad alanında olan XML üzerinde bir sorgu yazmak için, <xref:System.Xml.Linq.XName> doğru ad alanına sahip nesneleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="14d56-105">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="14d56-106">C# için en yaygın yaklaşım, <xref:System.Xml.Linq.XNamespace> URI 'yi içeren bir dize kullanarak başlatmak, ardından ad alanını yerel adla birleştirmek için ek işleç aşırı yüklemesi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="14d56-106">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>  
  
 <span data-ttu-id="14d56-107">Bu konudaki ilk örnek kümesi, varsayılan bir ad alanında bir XML ağacının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="14d56-107">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="14d56-108">İkinci küme, öneki olan bir ad alanında bir XML ağacının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="14d56-108">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14d56-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="14d56-109">Example</span></span>  
 <span data-ttu-id="14d56-110">Aşağıdaki örnek, varsayılan bir ad alanında bulunan bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="14d56-110">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="14d56-111">Daha sonra bir öğe koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="14d56-111">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="14d56-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="14d56-112">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="14d56-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="14d56-113">Example</span></span>  
 <span data-ttu-id="14d56-114">C# ' ta, ön ek içeren bir ad alanı kullanan bir XML ağacına veya varsayılan bir ad alanı olan bir XML ağacına sorgu yazarken aynı şekilde sorgular yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="14d56-114">In C#, you write queries in the same way regardless of whether you are writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>  
  
 <span data-ttu-id="14d56-115">Aşağıdaki örnek, öneki olan bir ad alanında olan bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="14d56-115">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="14d56-116">Daha sonra bir öğe koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="14d56-116">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="14d56-117">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="14d56-117">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="14d56-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14d56-118">See also</span></span>

- [<span data-ttu-id="14d56-119">Ad alanlarına genel bakış (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="14d56-119">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
