---
title: 'Nasıl yapılır: bir öznitelik (LINQ-XML) değerini almak (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 96d5e5a0c7ee294b140385c93b13ee56f3f92491
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642960"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="0b429-102">Nasıl yapılır: bir öznitelik (LINQ-XML) değerini almak (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b429-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="0b429-103">Bu konu özniteliklerin değeri elde etme gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b429-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="0b429-104">Başlıca iki yolu vardır: dönüştürmek bir <xref:System.Xml.Linq.XAttribute> istenen türe; açık dönüşüm işleci sonra içeriği öğesi veya özniteliği belirtilen türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0b429-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="0b429-105">Alternatif olarak, kullanabileceğiniz <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="0b429-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="0b429-106">Ancak, atama genellikle daha iyi yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="0b429-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="0b429-107">Boş değer atanabilir bir tür için öznitelik atama, kodu olabilir ya da var olmayabilir bir özniteliğin değeri alınırken yazma daha basittir.</span><span class="sxs-lookup"><span data-stu-id="0b429-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="0b429-108">Bu teknik örnekleri için bkz: [nasıl yapılır: bir öğenin (LINQ-XML) değerini alma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0b429-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b429-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b429-109">Example</span></span>  
 <span data-ttu-id="0b429-110">Visual Basic'te bir öznitelik değerini almak için tümleşik özniteliği özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b429-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="0b429-111">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="0b429-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="0b429-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b429-112">Example</span></span>  
 <span data-ttu-id="0b429-113">Visual Basic'te bir öznitelik değerini ayarlamak için tümleşik öznitelik özelliği'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b429-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="0b429-114">Ayrıca, var olmayan bir öznitelik değerini ayarlamak için tümleşik özniteliği özelliğini kullanırsanız, öznitelik oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0b429-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="0b429-115">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="0b429-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="0b429-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b429-116">Example</span></span>  
 <span data-ttu-id="0b429-117">Aşağıdaki örnekte bir öznitelik değerini almak öznitelik bir ad alanındaki olduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b429-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="0b429-118">Daha fazla bilgi için bkz: [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="0b429-118">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="0b429-119">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="0b429-119">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b429-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b429-120">See Also</span></span>  
 [<span data-ttu-id="0b429-121">LINQ-XML eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b429-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
