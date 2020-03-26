---
title: 'Nasıl Yapılır: Bir Özniteliğin Değerini Alın (LINQ- XML)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 6593639dcdc234ddda808cfdb5e85ebe1a771b62
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248953"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="50bc5-102">Nasıl Yapılır: Bir Özniteliğin Değerini (LINQ'dan XML'e) (Visual Basic) alın</span><span class="sxs-lookup"><span data-stu-id="50bc5-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="50bc5-103">Bu konu, özniteliklerin değerini nasıl elde edilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="50bc5-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="50bc5-104">İki ana yolu vardır: İstediğiniz türe bir <xref:System.Xml.Linq.XAttribute> döküm yapabilirsiniz; açık dönüştürme işleci daha sonra öğenin içeriğini veya belirtilen türe atnitelik dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="50bc5-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="50bc5-105">Alternatif olarak, <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50bc5-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="50bc5-106">Ancak, döküm genellikle daha iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="50bc5-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="50bc5-107">Özniteliği boşkullanılabilir bir değer türüne atarsanız, var olabilir veya olmayabilir bir öznitelik değerini alırken kod yazmak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="50bc5-107">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="50bc5-108">Bu teknik örnekleri için [bkz: Bir Öğenin Değerini (LINQ-XML) (Visual Basic) alın.](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="50bc5-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50bc5-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="50bc5-109">Example</span></span>  
 <span data-ttu-id="50bc5-110">Visual Basic'te, bir özniteliğin değerini almak için tümleşik öznitelik özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50bc5-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="50bc5-111">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="50bc5-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="50bc5-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="50bc5-112">Example</span></span>  
 <span data-ttu-id="50bc5-113">Visual Basic'te, bir özniteliğin değerini ayarlamak için tümleşik öznitelik özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50bc5-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="50bc5-114">Ayrıca, var olmayan bir öznitelik değerini ayarlamak için tümleşik öznitelik özelliğini kullanırsanız, öznitelik oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="50bc5-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="50bc5-115">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="50bc5-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="50bc5-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="50bc5-116">Example</span></span>  
 <span data-ttu-id="50bc5-117">Aşağıdaki örnek, özniteliğin ad alanında olduğu bir özniteliğin değerini nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="50bc5-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="50bc5-118">Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="50bc5-118">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="50bc5-119">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="50bc5-119">This example produces the following output:</span></span>  
  
```console  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="50bc5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50bc5-120">See also</span></span>

- [<span data-ttu-id="50bc5-121">LINQ - XML Eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50bc5-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
