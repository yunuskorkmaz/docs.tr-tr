---
title: Belirli bir alt öğeye sahip bir öğe bulma-LINQ to XML
description: Alt öğesi belirli bir değere sahip olan bir öğe bulun
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 947983ea1ea9d50528a9cb0beaa9c86b545e5ea6
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552866"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-linq-to-xml"></a><span data-ttu-id="575b6-103">Belirli bir alt öğeye sahip bir öğe bulma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="575b6-103">How to find an element with a specific child element (LINQ to XML)</span></span>

<span data-ttu-id="575b6-104">Bu makalede, alt öğesi belirli bir değere sahip olan bir öğenin nasıl bulunacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="575b6-104">This article shows how to find an element whose child element has a specific value.</span></span>

## <a name="example-find-an-element-whose-child-element-has-a-specific-value"></a><span data-ttu-id="575b6-105">Örnek: alt öğesi belirli bir değere sahip olan bir öğe bul</span><span class="sxs-lookup"><span data-stu-id="575b6-105">Example: Find an element whose child element has a specific value</span></span>

<span data-ttu-id="575b6-106">Örnek, `Test` `CommandLine` alt öğesi "Examp2.EXE" değerine sahip olan öğeyi bulur.</span><span class="sxs-lookup"><span data-stu-id="575b6-106">The example finds the `Test` element whose `CommandLine` child element has a value of "Examp2.EXE".</span></span> <span data-ttu-id="575b6-107">Örnek, XML belgesi [örnek xml dosyası kullanır: test yapılandırması](sample-xml-file-test-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="575b6-107">The example uses XML document [Sample XML file: Test configuration](sample-xml-file-test-configuration.md).</span></span>

```csharp
XElement root = XElement.Load("TestConfig.xml");
IEnumerable<XElement> tests =
    from el in root.Elements("Test")
    where (string)el.Element("CommandLine") == "Examp2.EXE"
    select el;
foreach (XElement el in tests)
    Console.WriteLine((string)el.Attribute("TestId"));
```

```vb
Dim root As XElement = XElement.Load("TestConfig.xml")
Dim tests As IEnumerable(Of XElement) = _
    From el In root.<Test> _
    Where el.<CommandLine>.Value = "Examp2.EXE" _
    Select el
For Each el as XElement In tests
    Console.WriteLine(el.@TestId)
Next
```

<span data-ttu-id="575b6-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="575b6-108">This example produces the following output:</span></span>

```output
0002
0006
```

<span data-ttu-id="575b6-109">Kodun Visual Basic sürümünün [XML alt eksen özelliğini](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), [XML özniteliği eksen özelliğini](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)ve [XML değeri özelliğini](../../visual-basic/language-reference/xml-axis/xml-value-property.md)kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="575b6-109">Note that the Visual Basic version of the code uses the [XML Child axis property](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), the [XML Attribute axis property](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md), and the [XML Value property](../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>

## <a name="example-find-when-the-xml-is-in-a-namespace"></a><span data-ttu-id="575b6-110">Örnek: XML 'in bir ad alanında olduğunu bul</span><span class="sxs-lookup"><span data-stu-id="575b6-110">Example: Find when the XML is in a namespace</span></span>

<span data-ttu-id="575b6-111">Aşağıdaki örnek, öncekiyle aynı şekilde, ancak bir ad alanında olan XML için de aynıdır.</span><span class="sxs-lookup"><span data-stu-id="575b6-111">The following example does the same as the previous one, but for XML that's in a namespace.</span></span> <span data-ttu-id="575b6-112">Örnek, XML belgesi [örnek xml dosyası kullanır: bir ad alanında test yapılandırması](sample-xml-file-test-configuration-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="575b6-112">The example uses XML document [Sample XML file: Test configuration in a namespace](sample-xml-file-test-configuration-namespace.md).</span></span>

<span data-ttu-id="575b6-113">Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="575b6-113">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Load("TestConfigInNamespace.xml");
XNamespace ad = "http://www.adatum.com";
IEnumerable<XElement> tests =
    from el in root.Elements(ad + "Test")
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"
    select el;
foreach (XElement el in tests)
    Console.WriteLine((string)el.Attribute("TestId"));
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("TestConfigInNamespace.xml")
        Dim tests As IEnumerable(Of XElement) = _
            From el In root.<Test> _
            Where el.<CommandLine>.Value = "Examp2.EXE" _
            Select el
        For Each el As XElement In tests
            Console.WriteLine(el.@TestId)
        Next
    End Sub
End Module
```

<span data-ttu-id="575b6-114">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="575b6-114">This example produces the following output:</span></span>

```output
0002
0006
```

## <a name="see-also"></a><span data-ttu-id="575b6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="575b6-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="575b6-116">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="575b6-116">Standard Query Operators Overview (C#)</span></span>](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="575b6-117">Projeksiyon Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="575b6-117">Projection Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="575b6-118">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="575b6-118">Standard Query Operators Overview (Visual Basic)</span></span>](/../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
