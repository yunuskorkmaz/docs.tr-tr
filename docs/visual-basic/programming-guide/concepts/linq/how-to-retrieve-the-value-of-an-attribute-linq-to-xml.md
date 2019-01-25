---
title: 'Nasıl yapılır: Bir öznitelik (LINQ to XML) değerini alma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: ab14072317bf963e87534b743e3c5a6c39ee39c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690728"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="b1e6d-102">Nasıl yapılır: Bir öznitelik (LINQ to XML) değerini alma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1e6d-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="b1e6d-103">Bu konuda, öznitelik değerini elde etme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b1e6d-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="b1e6d-104">Başlıca iki yolu vardır: Edebilirsiniz bir <xref:System.Xml.Linq.XAttribute> istenen türe; açık dönüştürme operatörü sonra içeriği öğe veya öznitelik belirtilen türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="b1e6d-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="b1e6d-105">Alternatif olarak, <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b1e6d-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="b1e6d-106">Ancak, atama, genellikle daha iyi bir yaklaşım değildir.</span><span class="sxs-lookup"><span data-stu-id="b1e6d-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="b1e6d-107">Öznitelik boş değer atanabilir bir tür için tür dönüştürme, kod var olmayabilir veya bir özniteliğin değeri alınırken yazmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="b1e6d-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="b1e6d-108">Bu tekniğe ilişkin örnekler için bkz [nasıl yapılır: Bir öğe (LINQ to XML) değerini alma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b1e6d-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1e6d-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1e6d-109">Example</span></span>  
 <span data-ttu-id="b1e6d-110">Visual Basic'te, tümleşik öznitelik özelliği bir özniteliğin değerini almak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1e6d-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="b1e6d-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b1e6d-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="b1e6d-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1e6d-112">Example</span></span>  
 <span data-ttu-id="b1e6d-113">Visual Basic'te, tümleşik öznitelik özelliği bir özniteliğin değerini ayarlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1e6d-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="b1e6d-114">Ayrıca, mevcut olmayan bir öznitelik değerini ayarlamak için tümleşik öznitelik özelliği kullanırsanız, öznitelik oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b1e6d-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="b1e6d-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b1e6d-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="b1e6d-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1e6d-116">Example</span></span>  
 <span data-ttu-id="b1e6d-117">Aşağıdaki örnekte, öznitelik bir ad alanında olduğu bir özniteliğin değerini almak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1e6d-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="b1e6d-118">Daha fazla bilgi için [(Visual Basic) XML ad alanları ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="b1e6d-118">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>  
        Dim str As String = root.@aw:Attr  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="b1e6d-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b1e6d-119">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1e6d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1e6d-120">See also</span></span>
- [<span data-ttu-id="b1e6d-121">LINQ to XML eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1e6d-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
