---
title: 'Nasıl yapılır: Tek Bir Öznitelik Alma (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: 34c390fbffc1aea68a2fd8ae64b17d2637a1f4f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397862"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="3c36f-102">Nasıl yapılır: tek bir öznitelik alma (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c36f-102">How to: Retrieve a Single Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="3c36f-103">Bu konu, öznitelik adı verilen bir öğenin tek bir özniteliğinin nasıl alınacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="3c36f-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="3c36f-104">Bu, belirli bir özniteliğe sahip bir öğeyi bulmak istediğiniz sorgu ifadeleri yazmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3c36f-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="3c36f-105"><xref:System.Xml.Linq.XElement.Attribute%2A> <xref:System.Xml.Linq.XElement> Sınıfının yöntemi, <xref:System.Xml.Linq.XAttribute> belirtilen ada sahip öğesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="3c36f-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c36f-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c36f-106">Example</span></span>  
 <span data-ttu-id="3c36f-107">Aşağıdaki örnek <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3c36f-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="3c36f-108">Bu örnek adlı ağaçtaki tüm alt öğeleri bulur `Phone` ve sonra adlı özniteliği bulur `type` .</span><span class="sxs-lookup"><span data-stu-id="3c36f-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="3c36f-109">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3c36f-109">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="3c36f-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c36f-110">Example</span></span>  
 <span data-ttu-id="3c36f-111">Özniteliğin değerini almak istiyorsanız, nesneleri ile yaptığınız gibi, bu özniteliği de çevirebilirsiniz <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="3c36f-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="3c36f-112">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c36f-112">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="3c36f-113">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3c36f-113">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="3c36f-114">,,,,,,,,,,,,,, <xref:System.Xml.Linq.XAttribute> `string` `bool` `bool?` `int` `int?` ,, `uint` `uint?` `long` `long?` `ulong` `ulong?` `float` `float?` `double` `double?` `decimal` `decimal?` , `DateTime` , `DateTime?` `TimeSpan` `TimeSpan?` `GUID` `GUID?` ,,,,,,,,,,,,,,,,,, ve için</span><span class="sxs-lookup"><span data-stu-id="3c36f-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c36f-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c36f-115">Example</span></span>  
 <span data-ttu-id="3c36f-116">Aşağıdaki örnek, bir ad alanında olan bir özniteliği için aynı kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c36f-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="3c36f-117">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3c36f-117">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="3c36f-118">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3c36f-118">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c36f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c36f-119">See also</span></span>

- [<span data-ttu-id="3c36f-120">LINQ to XML eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c36f-120">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
