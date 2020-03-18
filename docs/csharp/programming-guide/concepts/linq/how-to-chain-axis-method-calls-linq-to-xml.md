---
title: Eksen yöntemi çağrıları (LINQ- XML) (C#) nasıl zincirilir?
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 56fa5c9e8358883d838b68e99664240aa97f347f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169473"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a>Eksen yöntemi çağrıları (LINQ- XML) (C#) nasıl zincirilir?
Kodunuzda kullanacağınız yaygın bir desen, eksen yöntemini çağırmak, ardından uzantı yöntemi eksenlerinden birini çağırmaktır.  
  
 Bu döndürme öğeleri bir `Elements` koleksiyon adı ile iki <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> eksen <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> vardır: yöntem ve yöntem. Ağaçta belirli bir derinlikte belirli bir adın tüm öğelerini bulmak için bu iki ekseni birleştirebilirsiniz.  
  
## <a name="example"></a>Örnek  
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> Bu örnek, <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> tüm `Name` `Address` `PurchaseOrder` öğelerdeki tüm öğelerdeki tüm öğeleri kullanır.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Birden Çok SatınAlma Siparişi (LINQ-XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 `Elements` Eksenin uygulamalarından biri üzerinde <xref:System.Collections.Generic.IEnumerable%601> bir uzantı yöntemi olarak olduğu için bu <xref:System.Xml.Linq.XContainer>çalışır. <xref:System.Xml.Linq.XElement><xref:System.Xml.Linq.XContainer>türetilmiştir, böylece <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> yönteme yapılan bir çağrının sonuçlarında metodu arayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bazen, müdahale eden atalar olabilir veya olmayabilir belirli bir öğe derinliğinde tüm öğeleri almak istiyorum. Örneğin, aşağıdaki `ConfigParameter` belgede, `Customer` öğenin alt öğeleri olan tüm öğeleri almak isteyebilirsiniz, `ConfigParameter` ancak `Root` öğenin bir alt değil.  
  
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
  
 Bunu yapmak için ekseni <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> aşağıdaki gibi kullanabilirsiniz:  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, xml için bir ad alanında olan aynı tekniği gösterir. Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Ad alanında birden çok Satınalma Siparişi.](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md)  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - XML Eksenleri (C#)](linq-to-xml-axes-overview.md)
