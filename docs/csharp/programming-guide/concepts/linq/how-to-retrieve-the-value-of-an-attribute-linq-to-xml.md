---
title: "Nasıl yapılır: bir öznitelik (LINQ-XML) değerini almak (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 12720ca8bd1937d37f8d30400e0b25afa22a40cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="dab3b-102">Nasıl yapılır: bir öznitelik (LINQ-XML) değerini almak (C#)</span><span class="sxs-lookup"><span data-stu-id="dab3b-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="dab3b-103">Bu konu özniteliklerin değeri elde etme gösterir.</span><span class="sxs-lookup"><span data-stu-id="dab3b-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="dab3b-104">Başlıca iki yolu vardır: dönüştürmek bir <xref:System.Xml.Linq.XAttribute> istenen türe; açık dönüşüm işleci sonra içeriği öğesi veya özniteliği belirtilen türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="dab3b-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="dab3b-105">Alternatif olarak, kullanabileceğiniz <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="dab3b-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="dab3b-106">Ancak, atama genellikle daha iyi yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="dab3b-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="dab3b-107">Boş değer atanabilir bir tür için öznitelik atama, kodu olabilir ya da var olmayabilir bir özniteliğin değeri alınırken yazma daha basittir.</span><span class="sxs-lookup"><span data-stu-id="dab3b-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="dab3b-108">Bu teknik örnekleri için bkz: [nasıl yapılır: bir öğenin (LINQ-XML) değerini alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="dab3b-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dab3b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="dab3b-109">Example</span></span>  
 <span data-ttu-id="dab3b-110">Özniteliğin değerini almak için yalnızca cast <xref:System.Xml.Linq.XAttribute> nesne, istenen türü.</span><span class="sxs-lookup"><span data-stu-id="dab3b-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="dab3b-111">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="dab3b-111">This example produces the following output:</span></span>  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="dab3b-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="dab3b-112">Example</span></span>  
 <span data-ttu-id="dab3b-113">Aşağıdaki örnekte bir öznitelik değerini almak öznitelik bir ad alanındaki olduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dab3b-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="dab3b-114">Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="dab3b-114">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="dab3b-115">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="dab3b-115">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="dab3b-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dab3b-116">See Also</span></span>  
 [<span data-ttu-id="dab3b-117">LINQ-XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="dab3b-117">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
