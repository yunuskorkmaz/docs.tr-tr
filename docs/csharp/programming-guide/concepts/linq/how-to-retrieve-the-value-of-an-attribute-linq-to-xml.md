---
title: Bir özniteliğin değerini alma (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: d5b8bb3b5857b82a61367953b8e1cd63bea90beb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347429"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="4ea9a-102">Bir özniteliğin değerini alma (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4ea9a-102">How to retrieve the value of an attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="4ea9a-103">Bu konu, özniteliklerin değerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ea9a-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="4ea9a-104">İki ana yol vardır: <xref:System.Xml.Linq.XAttribute> istenen türe çevirebilirsiniz; Açık dönüştürme işleci daha sonra öğe veya özniteliğin içeriğini belirtilen türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="4ea9a-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="4ea9a-105">Alternatif olarak, <xref:System.Xml.Linq.XAttribute.Value%2A> özelliğini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ea9a-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="4ea9a-106">Ancak, atama genellikle daha iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="4ea9a-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="4ea9a-107">Özniteliğini null yapılabilir bir türe çevirebilirsiniz, bu, var olabilen veya varolmayan bir özniteliğin değeri alınırken yazmak daha basittir.</span><span class="sxs-lookup"><span data-stu-id="4ea9a-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="4ea9a-108">Bu tekniğin örnekleri için bkz. [bir öğenin değerini alma (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4ea9a-108">For examples of this technique, see [How to retrieve the value of an element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ea9a-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ea9a-109">Example</span></span>  
 <span data-ttu-id="4ea9a-110">Bir özniteliğin değerini almak için <xref:System.Xml.Linq.XAttribute> nesnesini istediğiniz türe atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="4ea9a-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="4ea9a-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4ea9a-111">This example produces the following output:</span></span>  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="4ea9a-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ea9a-112">Example</span></span>  
 <span data-ttu-id="4ea9a-113">Aşağıdaki örnek, özniteliğinin bir ad alanında olduğu bir özniteliğin değerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ea9a-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="4ea9a-114">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4ea9a-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="4ea9a-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4ea9a-115">This example produces the following output:</span></span>  
  
```output  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ea9a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ea9a-116">See also</span></span>

- [<span data-ttu-id="4ea9a-117">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="4ea9a-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
