---
title: 'Nasıl yapılır: (Visual Basic) ad alanlarında XML üzerinde sorgu yazma'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: 4efa1de254a0264752514c5ae6e601a66fa56f95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614836"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a><span data-ttu-id="5cefe-102">Nasıl yapılır: (Visual Basic) ad alanlarında XML üzerinde sorgu yazma</span><span class="sxs-lookup"><span data-stu-id="5cefe-102">How to: Write Queries on XML in Namespaces (Visual Basic)</span></span>
<span data-ttu-id="5cefe-103">Bir ad alanındaki XML üzerinde sorgu yazmak için kullanmalısınız <xref:System.Xml.Linq.XName> doğru ad alanı olan nesne.</span><span class="sxs-lookup"><span data-stu-id="5cefe-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="5cefe-104">Visual Basic'te, en yaygın bir genel ad alanı tanımlayın ve ardından XML sabit değerleri ve XML özellikleri, genel ad kullanmak yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="5cefe-104">In Visual Basic, the most common approach is to define a global namespace, and then use XML literals and XML properties that use the global namespace.</span></span> <span data-ttu-id="5cefe-105">XML değişmez değerlerinde bir öğe ad varsayılan olarak, bu durumda olacaktır, bir genel varsayılan ad alanı tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cefe-105">You can define a global default namespace, in which case elements in the XML literals will be in the namespace by default.</span></span> <span data-ttu-id="5cefe-106">Alternatif olarak, genel bir ad alanı öneki ile tanımlayabilir ve ardından XML sabit değerleri ve XML özellikleri gerektiği gibi ön ekini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cefe-106">Alternatively, you can define a global namespace with a prefix, and then use the prefix as required in the XML literals, and in XML properties.</span></span> <span data-ttu-id="5cefe-107">Formlarla diğer XML olarak, öznitelikleri her zaman varsayılan olarak hiçbir ad alanı olur.</span><span class="sxs-lookup"><span data-stu-id="5cefe-107">As with other forms of XML, attributes are always in no namespace by default.</span></span>  
  
 <span data-ttu-id="5cefe-108">Bu konudaki örnekler ilk kümesi, varsayılan ad alanında bir XML ağacı oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5cefe-108">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="5cefe-109">İkinci küme, önekli ad alanında bir XML ağacı oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5cefe-109">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cefe-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="5cefe-110">Example</span></span>  
 <span data-ttu-id="5cefe-111">Aşağıdaki örnek, bir varsayılan ad alanı içinde bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5cefe-111">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="5cefe-112">Ardından, öğelerinin bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="5cefe-112">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="5cefe-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="5cefe-113">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="5cefe-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="5cefe-114">Example</span></span>  
 <span data-ttu-id="5cefe-115">Visual Basic'te, ancak bir ad alanı öneki ile kullanan bir XML ağacının üzerinde sorgu yazma bir XML ağacı varsayılan ad alanı içinde sorgulamaktan oldukça farklıdır.</span><span class="sxs-lookup"><span data-stu-id="5cefe-115">In Visual Basic, however, writing queries on an XML tree that uses a namespace with a prefix is quite different from querying an XML tree in a default namespace.</span></span> <span data-ttu-id="5cefe-116">Tipik olarak kullandığınız `Imports` ad alanı öneki ile içeri aktarma deyimi.</span><span class="sxs-lookup"><span data-stu-id="5cefe-116">Typically you use the `Imports` statement to import the namespace with a prefix.</span></span> <span data-ttu-id="5cefe-117">XML ağacı oluştururken öğe ve öznitelik adları önekini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cefe-117">You then use the prefix in the element and attribute names when you construct the XML tree.</span></span> <span data-ttu-id="5cefe-118">XML özelliklerini kullanarak bir XML ağacı sorgulanırken de ön ekini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cefe-118">You also use the prefix when querying an XML tree using XML properties.</span></span>  
  
 <span data-ttu-id="5cefe-119">Aşağıdaki örnek, bir ad alanı öneki olan bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5cefe-119">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="5cefe-120">Ardından, öğelerinin bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="5cefe-120">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="5cefe-121">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="5cefe-121">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="5cefe-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cefe-122">See also</span></span>

- [<span data-ttu-id="5cefe-123">XML ad alanları (Visual Basic) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="5cefe-123">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
