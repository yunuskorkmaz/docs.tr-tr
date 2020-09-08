---
title: Eksen yöntemi çağrılarını zincirle-LINQ to XML
description: Ağaçtaki belirli bir derinlikte belirtilen bir adın tüm öğelerini bulmak için XContainer. Elements ve Extensions. Elements yöntemlerini nasıl kullanacağınızı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 23d3b5a3dacbc56a570a92178cb8e28482907ca1
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553494"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml"></a>Zincir eksen yöntem çağrıları (LINQ to XML)

Kodunuzda kullanacağınız ortak bir model, bir eksen yöntemi çağırmak ve sonra uzantı yöntemi eksenlerinden birini çağırmalıdır.

Adında `Elements` bir öğe koleksiyonu döndüren iki eksen vardır: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> yöntemi ve <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> yöntemi. Ağaçta verilen bir derinlikte belirtilen bir adın tüm öğelerini bulmak için bu iki ekseni birleştirebilirsiniz.

## <a name="example-retrieve-all-name-elements"></a>Örnek: tüm ad öğelerini Al

Bu örnek, tüm öğelerinde tüm öğelerin tüm öğelerini <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> almak için ve kullanır `Name` `Address` `PurchaseOrder` .

Bu örnek, XML belgesi [örnek xml dosyasını kullanır: birden fazla satın alma siparişi](sample-xml-file-multiple-purchase-orders.md).

```csharp
XElement purchaseOrders = XElement.Load("PurchaseOrders.xml");
IEnumerable<XElement> names =
    from el in purchaseOrders
        .Elements("PurchaseOrder")
        .Elements("Address")
        .Elements("Name")
    select el;
foreach (XElement e in names)
    Console.WriteLine(e);
```

```vb
Dim purchaseOrders As XElement = XElement.Load("PurchaseOrders.xml")
Dim names As IEnumerable(Of XElement) = _
    From el In purchaseOrders.<PurchaseOrder>.<Address>.<Name> _
    Select el
For Each e As XElement In names
    Console.WriteLine(e)
Next
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Name>Ellen Adams</Name>
<Name>Tai Yee</Name>
<Name>Cristian Osorio</Name>
<Name>Cristian Osorio</Name>
<Name>Jessica Arnold</Name>
<Name>Jessica Arnold</Name>
```

Bu, eksenin uygulamalarından biri `Elements` üzerinde bir genişletme yöntemi olduğu için geçerlidir <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XContainer> . <xref:System.Xml.Linq.XElement> ' dan türetilir <xref:System.Xml.Linq.XContainer> , bu sayede yöntemine yapılan <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> çağrının sonuçlarında yöntemi çağırabilirsiniz <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> .

## <a name="example-retrieve-all-elements-at-a-particular-depth"></a>Örnek: tüm öğeleri belirli bir derinlikte al

Bazı durumlarda, aradaki üst öğeler olmadığında, belirli bir öğe derinliğinde tüm öğeleri almak istersiniz. Örneğin, aşağıdaki belgede, öğesinin alt öğesi olan tüm öğeleri almak isteyebilirsiniz `ConfigParameter` `Customer` , ancak `ConfigParameter` öğenin bir alt öğesi olamaz `Root` .

```xml
<Root>
  <ConfigParameter>RootConfigParameter</ConfigParameter>
  <Customer>
    <Name>Frank</Name>
    <Config>
      <ConfigParameter>FirstConfigParameter</ConfigParameter>
    </Config>
  </Customer>
  <Customer>
    <Name>Bob</Name>
    <!--This customer doesn't have a Config element-->
  </Customer>
  <Customer>
    <Name>Bill</Name>
    <Config>
      <ConfigParameter>SecondConfigParameter</ConfigParameter>
    </Config>
  </Customer>
</Root>
```

 Bunu yapmak için, <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> aşağıdaki gibi, eksenini kullanabilirsiniz:

```csharp
XElement root = XElement.Load("Irregular.xml");
IEnumerable<XElement> configParameters =
    root.Elements("Customer").Elements("Config").
    Elements("ConfigParameter");
foreach (XElement cp in configParameters)
    Console.WriteLine(cp);
```

```vb
Dim root As XElement = XElement.Load("Irregular.xml")
Dim configParameters As IEnumerable(Of XElement) = _
    root.<Customer>.<Config>.<ConfigParameter>
For Each cp As XElement In configParameters
    Console.WriteLine(cp)
Next
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<ConfigParameter>FirstConfigParameter</ConfigParameter>
<ConfigParameter>SecondConfigParameter</ConfigParameter>
```

## <a name="example-retrieve-elements-for-xml-thats-in-a-namespace"></a>Örnek: bir ad alanında bulunan XML için öğeleri alma

Aşağıdaki örnek, bir ad alanında bulunan XML için aynı tekniği gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).

Bu örnek, XML belgesi [örnek xml dosyası kullanır: bir ad alanında birden fazla satın alma siparişi](sample-xml-file-multiple-purchase-orders-namespace.md).

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement purchaseOrders = XElement.Load("PurchaseOrdersInNamespace.xml");
IEnumerable<XElement> names =
    from el in purchaseOrders
        .Elements(aw + "PurchaseOrder")
        .Elements(aw + "Address")
        .Elements(aw + "Name")
    select el;
foreach (XElement e in names)
    Console.WriteLine(e);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim purchaseOrders As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")
        Dim names As IEnumerable(Of XElement) = _
            From el In purchaseOrders.<aw:PurchaseOrder>.<aw:Address>.<aw:Name> _
            Select el
        For Each e As XElement In names
            Console.WriteLine(e)
        Next
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>
```

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenlerine genel bakış](linq-xml-axes-overview.md)
