---
title: Bir öznitelik (LINQ xml) (C#) değerini almak için nasıl
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 212ad3bb3097e7e2c76da8f165011b181f329d4c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249200"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="b1e51-102">Bir öznitelik (LINQ xml) (C#) değerini almak için nasıl</span><span class="sxs-lookup"><span data-stu-id="b1e51-102">How to retrieve the value of an attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="b1e51-103">Bu konu, özniteliklerin değerini nasıl elde edilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1e51-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="b1e51-104">İki ana yolu vardır: İstediğiniz türe bir <xref:System.Xml.Linq.XAttribute> döküm yapabilirsiniz; açık dönüştürme işleci daha sonra öğenin içeriğini veya belirtilen türe atnitelik dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="b1e51-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="b1e51-105">Alternatif olarak, <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1e51-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="b1e51-106">Ancak, döküm genellikle daha iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="b1e51-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="b1e51-107">Özniteliği boşkullanılabilir bir değer türüne atarsanız, var olabilir veya olmayabilir bir öznitelik değerini alırken kod yazmak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="b1e51-107">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="b1e51-108">Bu teknik örnekleri için, [bir öğenin (LINQ- XML) (C#) değerini nasıl alabildiğini](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md)görün.</span><span class="sxs-lookup"><span data-stu-id="b1e51-108">For examples of this technique, see [How to retrieve the value of an element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1e51-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1e51-109">Example</span></span>  
 <span data-ttu-id="b1e51-110">Bir özniteliğin değerini almak için nesneyi <xref:System.Xml.Linq.XAttribute> istediğiniz türe atmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="b1e51-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="b1e51-111">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b1e51-111">This example produces the following output:</span></span>  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="b1e51-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1e51-112">Example</span></span>  
 <span data-ttu-id="b1e51-113">Aşağıdaki örnek, özniteliğin ad alanında olduğu bir özniteliğin değerini nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1e51-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="b1e51-114">Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b1e51-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="b1e51-115">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b1e51-115">This example produces the following output:</span></span>  
  
```output  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1e51-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1e51-116">See also</span></span>

- [<span data-ttu-id="b1e51-117">LINQ - XML Eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b1e51-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
