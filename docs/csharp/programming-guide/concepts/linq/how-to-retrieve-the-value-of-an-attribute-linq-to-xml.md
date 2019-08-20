---
title: 'Nasıl yapılır: Bir özniteliğin değerini alma (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 54ea4b532669ed2c615fcde02011fdd1228705a3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592475"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="0477c-102">Nasıl yapılır: Bir özniteliğin değerini alma (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0477c-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="0477c-103">Bu konu, özniteliklerin değerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0477c-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="0477c-104">İki ana yol vardır: İstediğiniz türe çevirebilirsiniz <xref:System.Xml.Linq.XAttribute> ; açık dönüştürme işleci daha sonra öğenin veya özniteliğin içeriğini belirtilen türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0477c-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="0477c-105">Alternatif olarak, <xref:System.Xml.Linq.XAttribute.Value%2A> özelliğini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0477c-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="0477c-106">Ancak, atama genellikle daha iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="0477c-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="0477c-107">Özniteliğini null yapılabilir bir türe çevirebilirsiniz, bu, var olabilen veya varolmayan bir özniteliğin değeri alınırken yazmak daha basittir.</span><span class="sxs-lookup"><span data-stu-id="0477c-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="0477c-108">Bu tekniğin örnekleri için bkz [. nasıl yapılır: Bir öğenin değerini Al (LINQ to XML) (C#).](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="0477c-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0477c-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0477c-109">Example</span></span>  
 <span data-ttu-id="0477c-110">Bir özniteliğin değerini almak için, <xref:System.Xml.Linq.XAttribute> nesneyi istediğiniz türe atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="0477c-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="0477c-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0477c-111">This example produces the following output:</span></span>  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="0477c-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="0477c-112">Example</span></span>  
 <span data-ttu-id="0477c-113">Aşağıdaki örnek, özniteliğinin bir ad alanında olduğu bir özniteliğin değerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0477c-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="0477c-114">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0477c-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="0477c-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0477c-115">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="0477c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0477c-116">See also</span></span>

- [<span data-ttu-id="0477c-117">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="0477c-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
