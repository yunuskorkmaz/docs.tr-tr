---
title: 'Nasıl yapılır: Zincir eksen yöntem çağrıları (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 39113c1b96ea7376d61c606aaa5f79715dbe3cab
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485928"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a>Nasıl yapılır: Zincir eksen yöntem çağrıları (LINQ to XML) (C#)
Kodunuzda kullanacağınız yaygın bir eksen yöntemi çağrısı, ardından çağrı genişletme yöntemini eksenleri birini modelidir.  
  
 İki eksenli bir adı vardır `Elements` öğelerinin bir koleksiyonunu döndürür: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> yöntemi ve <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> yöntemi. Belirtilen adın tüm öğeleri belirli bir derinliğinde ağacında bulmak için bu iki eksen birleştirebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> ve <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> bulmak için `Name` tüm öğeleri `Address` tüm öğeleri `PurchaseOrder` öğeleri.  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Birden fazla satın alma siparişi (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 Bunun çalışmasının nedeni uygulamalarından `Elements` eksen üzerinde bir genişletme yöntemi olan <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XContainer>. <xref:System.Xml.Linq.XElement> öğesinden türetilen <xref:System.Xml.Linq.XContainer>, çağırabilirsiniz <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> yöntemine bir çağrı sonuçlarını <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="example"></a>Örnek  
 Bazen belirli bir öğenin derinliği tüm öğeleri almak istediğiniz zaman var olabilir ya da ilgili üst öğelerinden olmayabilir. Örneğin, aşağıdaki belgede, tüm almak isteyebileceğiniz `ConfigParameter` alt öğeleri `Customer` öğesi, ama `ConfigParameter` diğer bir deyişle bir alt öğesi `Root` öğesi.  
  
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
  
 Bunu yapmak için kullanabileceğiniz <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> aşağıdaki gibi bir eksen:  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =   
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ad alanındaki XML için aynı tekniği gösterir. Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Bir Namespace, birden fazla satın alma siparişi](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
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

- [LINQ to XML eksenleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
