---
title: Bir özniteliğin değerini alma (LINQ to XML) (C#)
description: Bir özniteliğin değerini alma hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 5ee6995a54829b6d992e2982e6a6effcabf76470
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301560"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="02efb-104">Bir özniteliğin değerini alma (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="02efb-104">How to retrieve the value of an attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="02efb-105">Bu konu, özniteliklerin değerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="02efb-105">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="02efb-106">İki ana yol vardır: bir <xref:System.Xml.Linq.XAttribute> türü istenen türe çevirebilirsiniz; açık dönüştürme işleci, öğe veya özniteliğin içeriğini belirtilen türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="02efb-106">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="02efb-107">Alternatif olarak, özelliğini de kullanabilirsiniz <xref:System.Xml.Linq.XAttribute.Value%2A> .</span><span class="sxs-lookup"><span data-stu-id="02efb-107">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="02efb-108">Ancak, atama genellikle daha iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="02efb-108">However, casting is generally the better approach.</span></span> <span data-ttu-id="02efb-109">Özniteliğini null yapılabilir bir değer türüne ayarlarsanız, kod, var olabilen veya var olabilen bir özniteliğin değeri alınırken yazmak daha basittir.</span><span class="sxs-lookup"><span data-stu-id="02efb-109">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="02efb-110">Bu tekniğin örnekleri için bkz. [bir öğenin değerini alma (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="02efb-110">For examples of this technique, see [How to retrieve the value of an element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="02efb-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="02efb-111">Example</span></span>  
 <span data-ttu-id="02efb-112">Bir özniteliğin değerini almak için, <xref:System.Xml.Linq.XAttribute> nesneyi istediğiniz türe atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="02efb-112">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="02efb-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="02efb-113">This example produces the following output:</span></span>  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="02efb-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="02efb-114">Example</span></span>  
 <span data-ttu-id="02efb-115">Aşağıdaki örnek, özniteliğinin bir ad alanında olduğu bir özniteliğin değerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="02efb-115">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="02efb-116">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="02efb-116">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="02efb-117">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="02efb-117">This example produces the following output:</span></span>  
  
```output  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="02efb-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02efb-118">See also</span></span>

- [<span data-ttu-id="02efb-119">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="02efb-119">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
