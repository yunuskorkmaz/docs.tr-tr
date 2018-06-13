---
title: 'Nasıl yapılır: XML ad alanları (Visual Basic) içinde sorguları yazma'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: f4e895e560d0fb11c128248e4f42d1d5124bc124
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645570"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a><span data-ttu-id="87b4f-102">Nasıl yapılır: XML ad alanları (Visual Basic) içinde sorguları yazma</span><span class="sxs-lookup"><span data-stu-id="87b4f-102">How to: Write Queries on XML in Namespaces (Visual Basic)</span></span>
<span data-ttu-id="87b4f-103">İçinde bir ad alanı XML bir sorgu yazmak için kullanmanız gerekir <xref:System.Xml.Linq.XName> doğru ad alanına sahip nesneleri.</span><span class="sxs-lookup"><span data-stu-id="87b4f-103">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="87b4f-104">Visual Basic'te en yaygın genel ad alanı tanımlamak ve XML değişmez değerleri ve genel ad alanı kullanmak XML özellikleri kullanmak için bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="87b4f-104">In Visual Basic, the most common approach is to define a global namespace, and then use XML literals and XML properties that use the global namespace.</span></span> <span data-ttu-id="87b4f-105">Genel varsayılan ad alanı, varsayılan olarak ad alanında XML değişmez değerleri öğelerinde; Bu durumda olacaktır tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87b4f-105">You can define a global default namespace, in which case elements in the XML literals will be in the namespace by default.</span></span> <span data-ttu-id="87b4f-106">Alternatif olarak, genel ad alanı öneki tanımlamak ve XML değişmez değerleri ve XML özellikleri gerektiği gibi ön ekini kullanın.</span><span class="sxs-lookup"><span data-stu-id="87b4f-106">Alternatively, you can define a global namespace with a prefix, and then use the prefix as required in the XML literals, and in XML properties.</span></span> <span data-ttu-id="87b4f-107">Formlarla diğer XML gibi her zaman varsayılan olarak hiçbir ad alanındaki öznitelikleridir.</span><span class="sxs-lookup"><span data-stu-id="87b4f-107">As with other forms of XML, attributes are always in no namespace by default.</span></span>  
  
 <span data-ttu-id="87b4f-108">Bu konudaki örnekler ilk kümesi varsayılan ad alanında bir XML ağacı oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="87b4f-108">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="87b4f-109">İkinci küme öneki bir ad alanındaki bir XML ağacı oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="87b4f-109">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87b4f-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="87b4f-110">Example</span></span>  
 <span data-ttu-id="87b4f-111">Aşağıdaki örnek, bir varsayılan ad alanı içinde bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87b4f-111">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="87b4f-112">Ardından, öğe koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="87b4f-112">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="87b4f-113">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="87b4f-113">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="87b4f-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="87b4f-114">Example</span></span>  
 <span data-ttu-id="87b4f-115">Visual Basic'te, ancak, bir ad alanı öneki ile kullanan bir XML ağaç sorguları yazma bir varsayılan ad alanı XML ağacında sorgulama oldukça farklıdır.</span><span class="sxs-lookup"><span data-stu-id="87b4f-115">In Visual Basic, however, writing queries on an XML tree that uses a namespace with a prefix is quite different from querying an XML tree in a default namespace.</span></span> <span data-ttu-id="87b4f-116">Tipik olarak kullandığınız `Imports` ad alanı öneki almak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="87b4f-116">Typically you use the `Imports` statement to import the namespace with a prefix.</span></span> <span data-ttu-id="87b4f-117">XML ağaç yapısı oluştururken öğe ve öznitelik adları ön ekini kullanın.</span><span class="sxs-lookup"><span data-stu-id="87b4f-117">You then use the prefix in the element and attribute names when you construct the XML tree.</span></span> <span data-ttu-id="87b4f-118">XML özellikleri kullanılarak bir XML ağacı sorgulanırken de ön ekini kullanın.</span><span class="sxs-lookup"><span data-stu-id="87b4f-118">You also use the prefix when querying an XML tree using XML properties.</span></span>  
  
 <span data-ttu-id="87b4f-119">Aşağıdaki örnek, bir ad alanı öneki bulunduğu bir XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87b4f-119">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="87b4f-120">Ardından, öğe koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="87b4f-120">It then retrieves a collection of elements.</span></span>  
  
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
  
 <span data-ttu-id="87b4f-121">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="87b4f-121">This example produces the following output:</span></span>  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="87b4f-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87b4f-122">See Also</span></span>  
 [<span data-ttu-id="87b4f-123">XML ad alanları (Visual Basic) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="87b4f-123">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
