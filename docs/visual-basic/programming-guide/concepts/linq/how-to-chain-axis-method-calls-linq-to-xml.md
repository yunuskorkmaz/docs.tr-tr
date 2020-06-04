---
title: 'Nasıl yapılır: Zincir Eksen Yöntem Çağrıları (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: e4e22942-39bd-460f-b3c0-9f09e53d3aa9
ms.openlocfilehash: 51396c9aaffb43badf405600251ed5cb06198dc3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375141"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-visual-basic"></a>Nasıl yapılır: eksen yöntemi çağrıları zinciri (LINQ to XML) (Visual Basic)
Kodunuzda kullanacağınız ortak bir model, bir eksen yöntemi çağırmak ve sonra uzantı yöntemi eksenlerinden birini çağırmalıdır.  
  
 Adında `Elements` bir öğe koleksiyonu döndüren iki eksen vardır: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> yöntemi ve <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> yöntemi. Ağaçta verilen bir derinlikte belirtilen bir adın tüm öğelerini bulmak için bu iki ekseni birleştirebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek, tüm öğelerinde tüm öğelerdeki tüm <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> öğeleri bulmak için ve kullanır `Name` `Address` `PurchaseOrder` .  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: birden fazla satın alma siparişi (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
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
  
 Bu, eksenin uygulamalarından biri `Elements` üzerinde bir genişletme yöntemi olduğu için geçerlidir <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XContainer> . <xref:System.Xml.Linq.XElement>' dan türetilir <xref:System.Xml.Linq.XContainer> , bu sayede yöntemine yapılan <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> çağrının sonuçlarında yöntemi çağırabilirsiniz <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> .  
  
## <a name="example"></a>Örnek  
 Bazı durumlarda, üst öğelerinden oluşan veya aradaki bir işlem olduğunda, belirli bir öğe derinliğinde tüm öğeleri almak istersiniz. Örneğin, aşağıdaki belgede, öğesinin alt öğesi olan tüm öğeleri almak isteyebilirsiniz `ConfigParameter` `Customer` , ancak `ConfigParameter` öğesinin bir alt öğesidir `Root` .  
  
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
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ad alanında bulunan XML için aynı tekniği gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında birden fazla satın alma siparişi](sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
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

- [LINQ to XML eksenleri (Visual Basic)](linq-to-xml-axes.md)
