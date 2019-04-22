---
title: 'Nasıl yapılır: (LINQ to XML) tek bir öznitelik alma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: f56bdf86e4b63bc952c1d139aac9ee619b5a5f6c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837149"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="0f6e9-102">Nasıl yapılır: (LINQ to XML) tek bir öznitelik alma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f6e9-102">How to: Retrieve a Single Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="0f6e9-103">Bu konu nasıl tek bir öznitelik, bir öğenin özniteliği adı verilir alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0f6e9-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="0f6e9-104">Bu, belirli bir özniteliği olan bir öğeyi bulmak istediğiniz sorgu ifadeleri yazmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0f6e9-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="0f6e9-105"><xref:System.Xml.Linq.XElement.Attribute%2A> Yöntemi <xref:System.Xml.Linq.XElement> sınıfı döndürür <xref:System.Xml.Linq.XAttribute> belirtilen ada sahip.</span><span class="sxs-lookup"><span data-stu-id="0f6e9-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f6e9-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f6e9-106">Example</span></span>  
 <span data-ttu-id="0f6e9-107">Aşağıdaki örnekte <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0f6e9-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList = From el In cust...<Phone>  
For Each e As XElement In elList  
    Console.WriteLine(e.@type)  
Next  
```  
  
 <span data-ttu-id="0f6e9-108">Bu örnek adlı ağacında tüm alt öğeleri bulan `Phone`ve ardından adlı özniteliği bulduğunda `type`.</span><span class="sxs-lookup"><span data-stu-id="0f6e9-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="0f6e9-109">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0f6e9-109">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="0f6e9-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f6e9-110">Example</span></span>  
 <span data-ttu-id="0f6e9-111">Özniteliğin değerini almak istiyorsanız, yalnızca yaptığınız, çevirebilirsiniz <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0f6e9-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="0f6e9-112">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f6e9-112">The following example demonstrates this.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList As IEnumerable(Of XElement) = _  
    From el In cust...<Phone> _  
    Select el  
For Each el As XElement In elList  
    Console.WriteLine(el.@type)  
Next  
```  
  
 <span data-ttu-id="0f6e9-113">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0f6e9-113">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="0f6e9-114">açık tür dönüştürme işleçleri sağlar <xref:System.Xml.Linq.XAttribute> sınıfının `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`ve `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="0f6e9-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f6e9-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f6e9-115">Example</span></span>  
 <span data-ttu-id="0f6e9-116">Aşağıdaki örnek, bir ad alanında bir öznitelik için aynı kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f6e9-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="0f6e9-117">Daha fazla bilgi için [(Visual Basic) XML ad alanları ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="0f6e9-117">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cust As XElement = _  
            <aw:PhoneNumbers>  
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>  
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>  
            </aw:PhoneNumbers>  
        Dim elList As IEnumerable(Of XElement) = _  
            From el In cust...<aw:Phone> _  
            Select el  
        For Each el As XElement In elList  
            Console.WriteLine(el.@aw:type)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="0f6e9-118">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0f6e9-118">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f6e9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f6e9-119">See also</span></span>

- [<span data-ttu-id="0f6e9-120">LINQ to XML eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f6e9-120">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
