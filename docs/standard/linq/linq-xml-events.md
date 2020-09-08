---
title: LINQ to XML olayları-LINQ to XML
description: XML ağacındaki değişiklikleri izlemek için XML olaylarını nasıl kullanacağınızı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 755aa1a449e873a2c4f5b17d4df3eee7ecfa9969
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553341"
---
# <a name="linq-to-xml-events-linq-to-xml"></a>LINQ to XML olayları (LINQ to XML)

LINQ to XML olaylar, bir XML ağacı değiştiğinde size bildirim gönderilmesini sağlar.

Herhangi bir örneğine olay ekleyebilirsiniz <xref:System.Xml.Linq.XObject> . Olay işleyicisi daha sonra bu <xref:System.Xml.Linq.XObject> ve alt öğelerinden herhangi birine değişiklikler için olaylar alır. Örneğin, ağacın köküne bir olay işleyicisi ekleyebilir ve ağaçtaki tüm değişiklikleri bu olay işleyicisinden işleyebilirsiniz.

LINQ to XML olayları örnekleri için bkz <xref:System.Xml.Linq.XObject.Changing> <xref:System.Xml.Linq.XObject.Changed> . ve.

## <a name="types-and-events"></a>Türler ve olaylar

Olaylarla çalışırken aşağıdaki türleri kullanın:

|Tür|Description|
|----------|-----------------|
|<xref:System.Xml.Linq.XObjectChange>|Bir olay oluşturulduğunda olay türünü belirtir <xref:System.Xml.Linq.XObject> .|
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Ve olayları için veri <xref:System.Xml.Linq.XObject.Changing> sağlar <xref:System.Xml.Linq.XObject.Changed> .|

Bir XML ağacını değiştirirken aşağıdaki olaylar oluşturulur:

|Olay|Description|
|-----------|-----------------|
|<xref:System.Xml.Linq.XObject.Changing>|Bu <xref:System.Xml.Linq.XObject> veya alt öğelerinden herhangi birinin değişmesinden hemen önce gerçekleşir.|
|<xref:System.Xml.Linq.XObject.Changed>|Bir değiştiğinde <xref:System.Xml.Linq.XObject> veya alt öğelerinden herhangi biri değiştiğinde gerçekleşir.|

## <a name="example-use-events-to-maintain-a-proper-total-when-items-are-changed"></a>Örnek: öğeler değiştirildiğinde doğru bir toplamı sürdürmek için olayları kullanın

Olaylar, bir XML ağacındaki bazı toplu bilgileri korumak istediğinizde faydalıdır. Örneğin, faturanın satır öğelerinin toplamı olan bir fatura toplamı sağlamak isteyebilirsiniz. Bu örnek, karmaşık öğe altındaki tüm alt öğelerinin toplamını korumak için olayları kullanır `Items` .

```csharp
XElement root = new XElement("Root",
    new XElement("Total", "0"),
    new XElement("Items")
);
XElement total = root.Element("Total");
XElement items = root.Element("Items");
items.Changed += (object sender, XObjectChangeEventArgs cea) =>
{
    switch (cea.ObjectChange)
    {
        case XObjectChange.Add:
            if (sender is XElement)
                total.Value = ((int)total + (int)(XElement)sender).ToString();
            if (sender is XText)
                total.Value = ((int)total + (int)((XText)sender).Parent).ToString();
            break;
        case XObjectChange.Remove:
            if (sender is XElement)
                total.Value = ((int)total - (int)(XElement)sender).ToString();
            if (sender is XText)
                total.Value = ((int)total - Int32.Parse(((XText)sender).Value)).ToString();
            break;
    }
    Console.WriteLine("Changed {0} {1}",
      sender.GetType().ToString(), cea.ObjectChange.ToString());
};
items.SetElementValue("Item1", 25);
items.SetElementValue("Item2", 50);
items.SetElementValue("Item2", 75);
items.SetElementValue("Item3", 133);
items.SetElementValue("Item1", null);
items.SetElementValue("Item4", 100);
Console.WriteLine("Total:{0}", (int)total);
Console.WriteLine(root);
```

```vb
Module Module1
    Dim WithEvents items As XElement = Nothing
    Dim total As XElement = Nothing
    Dim root As XElement = _
            <Root>
                <Total>0</Total>
                <Items></Items>
            </Root>

    Private Sub XObjectChanged( _
            ByVal sender As Object, _
            ByVal cea As XObjectChangeEventArgs) _
            Handles items.Changed
        Select Case cea.ObjectChange
            Case XObjectChange.Add
                If sender.GetType() Is GetType(XElement) Then
                    total.Value = CStr(CInt(total.Value) + _
                            CInt((DirectCast(sender, XElement)).Value))
                End If
                If sender.GetType() Is GetType(XText) Then
                    total.Value = CStr(CInt(total.Value) + _
                            CInt((DirectCast(sender, XText)).Value))
                End If
            Case XObjectChange.Remove
                If sender.GetType() Is GetType(XElement) Then
                    total.Value = CStr(CInt(total.Value) - _
                            CInt((DirectCast(sender, XElement)).Value))
                End If
                If sender.GetType() Is GetType(XText) Then
                    total.Value = CStr(CInt(total.Value) - _
                            CInt((DirectCast(sender, XText)).Value))
                End If
        End Select
        Console.WriteLine("Changed {0} {1}", _
                            sender.GetType().ToString(), _
                            cea.ObjectChange.ToString())
    End Sub

    Sub Main()
        total = root.<Total>(0)
        items = root.<Items>(0)
        items.SetElementValue("Item1", 25)
        items.SetElementValue("Item2", 50)
        items.SetElementValue("Item2", 75)
        items.SetElementValue("Item3", 133)
        items.SetElementValue("Item1", Nothing)
        items.SetElementValue("Item4", 100)
        Console.WriteLine("Total:{0}", CInt(total))
        Console.WriteLine(root)
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
Changed System.Xml.Linq.XElement Add
Changed System.Xml.Linq.XElement Add
Changed System.Xml.Linq.XText Remove
Changed System.Xml.Linq.XText Add
Changed System.Xml.Linq.XElement Add
Changed System.Xml.Linq.XElement Remove
Changed System.Xml.Linq.XElement Add
Total:308
<Root>
  <Total>308</Total>
  <Items>
    <Item2>75</Item2>
    <Item3>133</Item3>
    <Item4>100</Item4>
  </Items>
</Root>
```
