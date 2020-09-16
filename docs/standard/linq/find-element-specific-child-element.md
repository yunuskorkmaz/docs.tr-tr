---
title: Belirli bir alt öğeye sahip bir öğe bulma-LINQ to XML
description: Alt öğesi belirli bir değere sahip olan bir öğe bulun
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 2f97f920ce09222858a0a51eb52ffe0d58dba960
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678640"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-linq-to-xml"></a>Belirli bir alt öğeye sahip bir öğe bulma (LINQ to XML)

Bu makalede, alt öğesi belirli bir değere sahip olan bir öğenin nasıl bulunacağı gösterilmektedir.

## <a name="example-find-an-element-whose-child-element-has-a-specific-value"></a>Örnek: alt öğesi belirli bir değere sahip olan bir öğe bul

Örnek, `Test` `CommandLine` alt öğesi "Examp2.EXE" değerine sahip olan öğeyi bulur. Örnek, XML belgesi [örnek xml dosyası kullanır: test yapılandırması](sample-xml-file-test-configuration.md).

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

Bu örnek aşağıdaki çıktıyı üretir:

```output
0002
0006
```

Kodun Visual Basic sürümünün [XML alt eksen özelliğini](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), [XML özniteliği eksen özelliğini](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)ve [XML değeri özelliğini](../../visual-basic/language-reference/xml-axis/xml-value-property.md)kullandığını unutmayın.

## <a name="example-find-when-the-xml-is-in-a-namespace"></a>Örnek: XML 'in bir ad alanında olduğunu bul

Aşağıdaki örnek, öncekiyle aynı şekilde, ancak bir ad alanında olan XML için de aynıdır. Örnek, XML belgesi [örnek xml dosyası kullanır: bir ad alanında test yapılandırması](sample-xml-file-test-configuration-namespace.md).

Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).

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

Bu örnek aşağıdaki çıktıyı üretir:

```output
0002
0006
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Standart Sorgu İşleçlerine Genel Bakış](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Projeksiyon İşlemleri](../../csharp/programming-guide/concepts/linq/projection-operations.md)
