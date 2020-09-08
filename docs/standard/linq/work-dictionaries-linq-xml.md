---
title: LINQ to XML LINQ to XML kullanarak sözlüklerle çalışma
description: Birçok türdeki veri yapısını XML 'e dönüştürebilirsiniz ve XML 'yi yapılara dönüştürebilirsiniz. Bir genel. sözlüğü XML 'e ve geri dönüştüren bir örnek aşağıda verilmiştir.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: ea61a79549488765526f45852dae7a4df7cacb64
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553214"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml"></a>LINQ to XML kullanarak sözlüklerle çalışma

Çeşitli türlerdeki veri yapılarını XML 'e ve ardından XML 'den diğer veri yapılarına dönüştürmek genellikle yararlıdır. Bu makalede bir <xref:System.Collections.Generic.Dictionary%602> XML ve Back öğesine dönüştürme gösterilmektedir.

## <a name="example-create-a-dictionary-and-convert-its-contents-to-xml"></a>Örnek: bir sözlük oluşturun ve içeriğini XML 'e dönüştürün

Bu ilk örnek bir oluşturur <xref:System.Collections.Generic.Dictionary%602> ve sonra XML 'ye dönüştürür.

Örneğin bu C# sürümü, bir sorgu projesinin yeni <xref:System.Xml.Linq.XElement> nesneler ve elde edilen koleksiyonun bir bağımsız değişken olarak kök nesnenin oluşturucusuna geçirildiği işlevsel oluşturma formunu kullanır <xref:System.Xml.Linq.XElement> .

Visual Basic sürümü, katıştırılmış ifadede XML değişmez değerlerini ve bir sorguyu kullanır. Sorgu yeni nesneler, <xref:System.Xml.Linq.XElement> daha sonra nesne için yeni içerik haline gelir `Root` <xref:System.Xml.Linq.XElement> .

```csharp
Dictionary<string, string> dict = new Dictionary<string, string>();
dict.Add("Child1", "Value1");
dict.Add("Child2", "Value2");
dict.Add("Child3", "Value3");
dict.Add("Child4", "Value4");
XElement root = new XElement("Root",
    from keyValue in dict
    select new XElement(keyValue.Key, keyValue.Value)
);
Console.WriteLine(root);
```

```vb
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()
dict.Add("Child1", "Value1")
dict.Add("Child2", "Value2")
dict.Add("Child3", "Value3")
dict.Add("Child4", "Value4")
Dim root As XElement = _
    <Root>
        <%= From keyValue In dict _
            Select New XElement(keyValue.Key, keyValue.Value) %>
    </Root>
Console.WriteLine(root)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root>
  <Child1>Value1</Child1>
  <Child2>Value2</Child2>
  <Child3>Value3</Child3>
  <Child4>Value4</Child4>
</Root>
```

## <a name="example-create-a-dictionary-and-load-it-from-xml-data"></a>Örnek: sözlük oluşturma ve XML verilerinden yükleme

Bir sonraki örnek, bir sözlük yüklerini XML verilerinden yükler.

```csharp
XElement root = new XElement("Root",
    new XElement("Child1", "Value1"),
    new XElement("Child2", "Value2"),
    new XElement("Child3", "Value3"),
    new XElement("Child4", "Value4")
);

Dictionary<string, string> dict = new Dictionary<string, string>();
foreach (XElement el in root.Elements())
    dict.Add(el.Name.LocalName, el.Value);
foreach (string str in dict.Keys)
    Console.WriteLine("{0}:{1}", str, dict[str]);
```

```vb
Dim root As XElement = _
        <Root>
            <Child1>Value1</Child1>
            <Child2>Value2</Child2>
            <Child3>Value3</Child3>
            <Child4>Value4</Child4>
        </Root>

Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)
For Each el As XElement In root.Elements
    dict.Add(el.Name.LocalName, el.Value)
Next
For Each str As String In dict.Keys
    Console.WriteLine("{0}:{1}", str, dict(str))
Next
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
Child1:Value1
Child2:Value2
Child3:Value3
Child4:Value4
```

## <a name="see-also"></a>Ayrıca bkz.

- [Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
