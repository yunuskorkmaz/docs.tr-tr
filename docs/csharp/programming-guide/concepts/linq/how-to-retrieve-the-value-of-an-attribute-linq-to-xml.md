---
title: Bir öznitelik (LINQ xml) (C#) değerini almak için nasıl
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: d5b8bb3b5857b82a61367953b8e1cd63bea90beb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347429"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="9aa7f-102">Bir öznitelik (LINQ xml) (C#) değerini almak için nasıl</span><span class="sxs-lookup"><span data-stu-id="9aa7f-102">How to retrieve the value of an attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="9aa7f-103">Bu konu, özniteliklerin değerini nasıl elde edilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9aa7f-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="9aa7f-104">İki ana yolu vardır: İstediğiniz türe bir <xref:System.Xml.Linq.XAttribute> döküm yapabilirsiniz; açık dönüştürme işleci daha sonra öğenin içeriğini veya belirtilen türe atnitelik dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="9aa7f-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="9aa7f-105">Alternatif olarak, <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aa7f-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="9aa7f-106">Ancak, döküm genellikle daha iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="9aa7f-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="9aa7f-107">Özniteliği boşta bir türe atarsanız, var olabilir veya olmayabilir bir öznitelik değerini alırken kod yazmak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="9aa7f-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="9aa7f-108">Bu teknik örnekleri için, [bir öğenin (LINQ- XML) (C#) değerini nasıl alabildiğini](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md)görün.</span><span class="sxs-lookup"><span data-stu-id="9aa7f-108">For examples of this technique, see [How to retrieve the value of an element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9aa7f-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="9aa7f-109">Example</span></span>  
 <span data-ttu-id="9aa7f-110">Bir özniteliğin değerini almak için nesneyi <xref:System.Xml.Linq.XAttribute> istediğiniz türe atmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="9aa7f-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="9aa7f-111">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="9aa7f-111">This example produces the following output:</span></span>  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="9aa7f-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="9aa7f-112">Example</span></span>  
 <span data-ttu-id="9aa7f-113">Aşağıdaki örnek, özniteliğin ad alanında olduğu bir özniteliğin değerini nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9aa7f-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="9aa7f-114">Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9aa7f-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="9aa7f-115">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="9aa7f-115">This example produces the following output:</span></span>  
  
```output  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="9aa7f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9aa7f-116">See also</span></span>

- [<span data-ttu-id="9aa7f-117">LINQ - XML Eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="9aa7f-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
