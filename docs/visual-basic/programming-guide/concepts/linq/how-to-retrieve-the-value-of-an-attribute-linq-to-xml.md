---
title: 'Nasıl yapılır: Bir özniteliğin değerini alma (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: d03b2b146ad2f6b796ba6589cf99d06aa429535d
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710504"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="95b20-102">Nasıl yapılır: Bir özniteliğin değerini alma (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95b20-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="95b20-103">Bu konu, özniteliklerin değerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="95b20-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="95b20-104">İki ana yol vardır: İstediğiniz türe çevirebilirsiniz <xref:System.Xml.Linq.XAttribute> ; açık dönüştürme işleci daha sonra öğenin veya özniteliğin içeriğini belirtilen türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="95b20-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="95b20-105">Alternatif olarak, <xref:System.Xml.Linq.XAttribute.Value%2A> özelliğini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95b20-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="95b20-106">Ancak, atama genellikle daha iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="95b20-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="95b20-107">Özniteliğini null yapılabilir bir türe çevirebilirsiniz, bu, var olabilen veya varolmayan bir özniteliğin değeri alınırken yazmak daha basittir.</span><span class="sxs-lookup"><span data-stu-id="95b20-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="95b20-108">Bu tekniğin örnekleri için bkz [. nasıl yapılır: Bir öğenin değerini alın (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="95b20-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="95b20-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="95b20-109">Example</span></span>  
 <span data-ttu-id="95b20-110">Visual Basic, bir özniteliğin değerini almak için tümleşik öznitelik özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95b20-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="95b20-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="95b20-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="95b20-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="95b20-112">Example</span></span>  
 <span data-ttu-id="95b20-113">Visual Basic, bir özniteliğin değerini ayarlamak için tümleşik öznitelik özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95b20-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="95b20-114">Ayrıca, var olmayan bir özniteliğin değerini ayarlamak için tümleşik öznitelik özelliğini kullanırsanız, öznitelik oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="95b20-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="95b20-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="95b20-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="95b20-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="95b20-116">Example</span></span>  
 <span data-ttu-id="95b20-117">Aşağıdaki örnek, özniteliğinin bir ad alanında olduğu bir özniteliğin değerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="95b20-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="95b20-118">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="95b20-118">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="95b20-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="95b20-119">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="95b20-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95b20-120">See also</span></span>

- [<span data-ttu-id="95b20-121">LINQ to XML eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95b20-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
