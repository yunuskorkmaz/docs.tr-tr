---
title: Bir özniteliğin değerini alma-LINQ to XML
description: Bir özniteliğin değerini alır. Bir XAttribute 'u istenen türe çevirebilirsiniz veya XAttribute. Value özelliğini kullanabilirsiniz.
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 7af3616c9808cad5dfb52f53c74b21a59da5c954
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553875"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml"></a><span data-ttu-id="8fa72-104">Öznitelik değerini alma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="8fa72-104">How to retrieve the value of an attribute (LINQ to XML)</span></span>

<span data-ttu-id="8fa72-105">Bu makale, özniteliklerin değerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8fa72-105">This article shows how to obtain the value of attributes.</span></span> <span data-ttu-id="8fa72-106">İki ana yol vardır: bir <xref:System.Xml.Linq.XAttribute> türü istenen türe çevirebilirsiniz; açık dönüştürme işleci, öğe veya özniteliğin içeriğini belirtilen türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8fa72-106">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="8fa72-107">Alternatif olarak, özelliğini de kullanabilirsiniz <xref:System.Xml.Linq.XAttribute.Value%2A> .</span><span class="sxs-lookup"><span data-stu-id="8fa72-107">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="8fa72-108">Ancak, atama genellikle daha iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="8fa72-108">However, casting is generally the better approach.</span></span> <span data-ttu-id="8fa72-109">Özniteliğini null yapılabilir bir değer türüne ayarlarsanız, kod, var olabilen veya var olabilen bir özniteliğin değeri alınırken yazmak daha basittir.</span><span class="sxs-lookup"><span data-stu-id="8fa72-109">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="8fa72-110">Bu tekniğin örnekleri için bkz. [bir öğenin değerini alma](retrieve-value-element.md).</span><span class="sxs-lookup"><span data-stu-id="8fa72-110">For examples of this technique, see [How to retrieve the value of an element](retrieve-value-element.md).</span></span>

## <a name="example-use-a-cast-to-retrieve-the-value-of-an-attribute"></a><span data-ttu-id="8fa72-111">Örnek: bir özniteliğin değerini almak için bir atama kullanın</span><span class="sxs-lookup"><span data-stu-id="8fa72-111">Example: Use a cast to retrieve the value of an attribute</span></span>

<span data-ttu-id="8fa72-112">C# içindeki bir özniteliğin değerini almak için, <xref:System.Xml.Linq.XAttribute> nesneyi istediğiniz türe atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="8fa72-112">To retrieve the value of an attribute in C#, you cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span> <span data-ttu-id="8fa72-113">Visual Basic, değeri almak için tümleşik öznitelik özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fa72-113">In Visual Basic, you can use the integrated attribute property to retrieve the value.</span></span>

```csharp
XElement root = new XElement("Root",
                    new XAttribute("Attr", "abcde")
                );
Console.WriteLine(root);
string str = (string)root.Attribute("Attr");
Console.WriteLine(str);
```

```vb
Dim root As XElement = <Root Attr="abcde"/>
Console.WriteLine(root)
Dim str As String = root.@Attr
Console.WriteLine(str)
```

<span data-ttu-id="8fa72-114">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="8fa72-114">This example produces the following output:</span></span>

```output
<Root Attr="abcde" />
abcde
```

## <a name="example-use-a-cast-to-retrieve-from-xml-thats-in-a-namespace"></a><span data-ttu-id="8fa72-115">Örnek: bir ad alanında olan XML 'den almak için bir tür dönüştürme kullanın</span><span class="sxs-lookup"><span data-stu-id="8fa72-115">Example: Use a cast to retrieve from XML that's in a namespace</span></span>

<span data-ttu-id="8fa72-116">Aşağıdaki örnek, özniteliği bir ad alanında ise bir özniteliğin değerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8fa72-116">The following example shows how to retrieve the value of an attribute if the attribute is in a namespace.</span></span> <span data-ttu-id="8fa72-117">Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8fa72-117">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
                    new XAttribute(aw + "Attr", "abcde")
                );
string str = (string)root.Attribute(aw + "Attr");
Console.WriteLine(str);
```

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

<span data-ttu-id="8fa72-118">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="8fa72-118">This example produces the following output:</span></span>

```output
abcde
```

## <a name="see-also"></a><span data-ttu-id="8fa72-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fa72-119">See also</span></span>

- [<span data-ttu-id="8fa72-120">LINQ to XML eksenlerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="8fa72-120">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
