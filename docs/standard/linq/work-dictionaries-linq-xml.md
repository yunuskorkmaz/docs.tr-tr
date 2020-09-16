---
title: LINQ to XML LINQ to XML kullanarak sözlüklerle çalışma
description: Birçok türdeki veri yapısını XML 'e dönüştürebilirsiniz ve XML 'yi yapılara dönüştürebilirsiniz. Bir genel. sözlüğü XML 'e ve geri dönüştüren bir örnek aşağıda verilmiştir.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: 9f6304dde828b3269f1cf369c3a6f14368676a48
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554488"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml"></a><span data-ttu-id="bcd08-104">LINQ to XML kullanarak sözlüklerle çalışma</span><span class="sxs-lookup"><span data-stu-id="bcd08-104">How to work with dictionaries using LINQ to XML</span></span>

<span data-ttu-id="bcd08-105">Çeşitli türlerdeki veri yapılarını XML 'e ve ardından XML 'den diğer veri yapılarına dönüştürmek genellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="bcd08-105">It's often convenient to convert data structures of various kinds to XML, and then from XML to other data structures.</span></span> <span data-ttu-id="bcd08-106">Bu makalede bir <xref:System.Collections.Generic.Dictionary%602> XML ve Back öğesine dönüştürme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bcd08-106">This article shows a conversion of a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>

## <a name="example-create-a-dictionary-and-convert-its-contents-to-xml"></a><span data-ttu-id="bcd08-107">Örnek: bir sözlük oluşturun ve içeriğini XML 'e dönüştürün</span><span class="sxs-lookup"><span data-stu-id="bcd08-107">Example: Create a Dictionary and convert its contents to XML</span></span>

<span data-ttu-id="bcd08-108">Bu ilk örnek bir oluşturur <xref:System.Collections.Generic.Dictionary%602> ve sonra XML 'ye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="bcd08-108">This first example creates a <xref:System.Collections.Generic.Dictionary%602>, and then converts it to XML.</span></span>

<span data-ttu-id="bcd08-109">Örneğin bu C# sürümü, bir sorgu projesinin yeni <xref:System.Xml.Linq.XElement> nesneler ve elde edilen koleksiyonun bir bağımsız değişken olarak kök nesnenin oluşturucusuna geçirildiği işlevsel oluşturma formunu kullanır <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="bcd08-109">This C# version of the example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>

<span data-ttu-id="bcd08-110">Visual Basic sürümü, katıştırılmış ifadede XML değişmez değerlerini ve bir sorguyu kullanır.</span><span class="sxs-lookup"><span data-stu-id="bcd08-110">The Visual Basic version uses XML literals and a query in an embedded expression.</span></span> <span data-ttu-id="bcd08-111">Sorgu yeni nesneler, <xref:System.Xml.Linq.XElement> daha sonra nesne için yeni içerik haline gelir `Root` <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="bcd08-111">The query projects new <xref:System.Xml.Linq.XElement> objects which then become the new content for the `Root` <xref:System.Xml.Linq.XElement> object.</span></span>

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

<span data-ttu-id="bcd08-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bcd08-112">This example produces the following output:</span></span>

```xml
<Root>
  <Child1>Value1</Child1>
  <Child2>Value2</Child2>
  <Child3>Value3</Child3>
  <Child4>Value4</Child4>
</Root>
```

## <a name="example-create-a-dictionary-and-load-it-from-xml-data"></a><span data-ttu-id="bcd08-113">Örnek: sözlük oluşturma ve XML verilerinden yükleme</span><span class="sxs-lookup"><span data-stu-id="bcd08-113">Example: Create a dictionary and load it from XML data</span></span>

<span data-ttu-id="bcd08-114">Bir sonraki örnek, bir sözlük yüklerini XML verilerinden yükler.</span><span class="sxs-lookup"><span data-stu-id="bcd08-114">The next example creates a dictionary loads loads it from XML data.</span></span>

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

<span data-ttu-id="bcd08-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bcd08-115">This example produces the following output:</span></span>

```output
Child1:Value1
Child2:Value2
Child3:Value3
Child4:Value4
```

## <a name="see-also"></a><span data-ttu-id="bcd08-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcd08-116">See also</span></span>

- [<span data-ttu-id="bcd08-117">Projeksiyon Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcd08-117">Projection Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
