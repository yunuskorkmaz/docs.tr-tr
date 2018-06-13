---
title: 'Nasıl yapılır: zincir eksen yöntem çağrıları (LINQ-XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 36160a9dd4cc26b0b1d54e6e8b91d2880dd23abf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333784"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a>Nasıl yapılır: zincir eksen yöntem çağrıları (LINQ-XML) (C#)
Kodunuzda kullanacağınız genel bir desen bir eksen yöntemini çağırın, ardından çağrısı uzantısı yöntemi eksenleri birini ' dir.  
  
 İki eksen adı vardır `Elements` öğe koleksiyonunu döndürür: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> yöntemi ve <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> yöntemi. Belirtilen adın tüm öğeleri verilen derinliğinde ağacında bulmak için bu iki eksenler birleştirebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> ve <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> tüm bulmak için `Name` tüm öğeleri `Address` tüm öğeleri `PurchaseOrder` öğeleri.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: birden çok satınalma siparişi (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 Bu çalışır çünkü uygulamaları birini `Elements` ekseni üzerinde bir genişletme yöntemi değil <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XContainer>. <xref:System.Xml.Linq.XElement> türetilen <xref:System.Xml.Linq.XContainer>, çağırabilirsiniz <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> yöntemine yapılan bir çağrı sonuçları <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="example"></a>Örnek  
 Bazen belirli öğesinin derinliği tüm öğeler almak istediğiniz zaman var olabilir veya araya giren üst öğelerinden olmayabilir. Örneğin, aşağıdaki belgede, tüm almak isteyebilirsiniz `ConfigParameter` , alt öğelerini `Customer` öğesi, ama `ConfigParameter` olan bir alt `Root` öğesi.  
  
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
  
 Bunu yapmak için kullanabileceğiniz <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> şekilde eksen:  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =   
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ad alanı içinde XML için aynı yöntemleri gösterir. Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: bir Namespace içinde birden çok satınalma siparişi](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML eksenleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
