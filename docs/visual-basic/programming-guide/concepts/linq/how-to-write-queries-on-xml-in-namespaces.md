---
title: 'Nasıl yapılır: ad alanlarında XML üzerinde sorgu yazma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: 71e66791b41e26ea13f828ef6239a8db9a9365b0
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835000"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a><span data-ttu-id="c26f9-102">Nasıl yapılır: ad alanlarında XML üzerinde sorgu yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c26f9-102">How to: Write Queries on XML in Namespaces (Visual Basic)</span></span>
<span data-ttu-id="c26f9-103">Bir ad alanında olan XML üzerinde bir sorgu yazmak için, doğru ad alanına sahip <xref:System.Xml.Linq.XName> nesnelerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c26f9-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="c26f9-104">Visual Basic, en yaygın yaklaşım genel bir ad alanı tanımlamaktır ve sonra genel ad alanını kullanan XML değişmez değerlerini ve XML özelliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c26f9-104">In Visual Basic, the most common approach is to define a global namespace, and then use XML literals and XML properties that use the global namespace.</span></span> <span data-ttu-id="c26f9-105">Genel bir varsayılan ad alanı tanımlayabilirsiniz. Bu durumda, XML sabit değerlerinde bulunan öğeler varsayılan olarak ad alanında yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="c26f9-105">You can define a global default namespace, in which case elements in the XML literals will be in the namespace by default.</span></span> <span data-ttu-id="c26f9-106">Alternatif olarak, ön ek içeren bir genel ad alanı tanımlayabilir ve sonra öneki XML sabit değerlerinde ve XML özelliklerinde gereken şekilde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c26f9-106">Alternatively, you can define a global namespace with a prefix, and then use the prefix as required in the XML literals, and in XML properties.</span></span> <span data-ttu-id="c26f9-107">Diğer XML formlarında olduğu gibi, özniteliklerin her zaman varsayılan olarak ad alanı yoktur.</span><span class="sxs-lookup"><span data-stu-id="c26f9-107">As with other forms of XML, attributes are always in no namespace by default.</span></span>  
  
 <span data-ttu-id="c26f9-108">Bu konudaki ilk örnek kümesi, varsayılan bir ad alanında bir XML ağacının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c26f9-108">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="c26f9-109">İkinci küme, öneki olan bir ad alanında bir XML ağacının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c26f9-109">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c26f9-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="c26f9-110">Example</span></span>  
 <span data-ttu-id="c26f9-111">Aşağıdaki örnek, varsayılan bir ad alanında bulunan bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c26f9-111">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="c26f9-112">Daha sonra bir öğe koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="c26f9-112">It then retrieves a collection of elements.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="c26f9-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c26f9-113">This example produces the following output:</span></span>  
  
```console  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="c26f9-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="c26f9-114">Example</span></span>  
 <span data-ttu-id="c26f9-115">Ancak Visual Basic ' de, ön ek içeren bir ad alanı kullanan bir XML ağacına sorgu yazmak, varsayılan bir ad alanında bir XML ağacını sorgulamadan oldukça farklıdır.</span><span class="sxs-lookup"><span data-stu-id="c26f9-115">In Visual Basic, however, writing queries on an XML tree that uses a namespace with a prefix is quite different from querying an XML tree in a default namespace.</span></span> <span data-ttu-id="c26f9-116">Genellikle `Imports` ifadesini kullanarak ad alanını önekiyle içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c26f9-116">Typically you use the `Imports` statement to import the namespace with a prefix.</span></span> <span data-ttu-id="c26f9-117">Ardından, XML ağacını oluştururken öğesi ve öznitelik adlarında öneki kullanın.</span><span class="sxs-lookup"><span data-stu-id="c26f9-117">You then use the prefix in the element and attribute names when you construct the XML tree.</span></span> <span data-ttu-id="c26f9-118">Xml özelliklerini kullanarak bir XML ağacını sorgularken de ön eki kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c26f9-118">You also use the prefix when querying an XML tree using XML properties.</span></span>  
  
 <span data-ttu-id="c26f9-119">Aşağıdaki örnek, öneki olan bir ad alanında olan bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c26f9-119">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="c26f9-120">Daha sonra bir öğe koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="c26f9-120">It then retrieves a collection of elements.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>1</aw:Child>  
                <aw:Child>2</aw:Child>  
                <aw:Child>3</aw:Child>  
                <aw:AnotherChild>4</aw:AnotherChild>  
                <aw:AnotherChild>5</aw:AnotherChild>  
                <aw:AnotherChild>6</aw:AnotherChild>  
            </aw:Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<aw:Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="c26f9-121">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c26f9-121">This example produces the following output:</span></span>  
  
```console  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="c26f9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c26f9-122">See also</span></span>

- [<span data-ttu-id="c26f9-123">Ad alanlarına genel bakış (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c26f9-123">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
