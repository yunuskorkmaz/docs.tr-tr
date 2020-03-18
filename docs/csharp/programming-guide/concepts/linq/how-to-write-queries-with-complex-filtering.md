---
title: Karmaşık filtreleme (C#) ile sorgu yazma
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: bc85d7f1e5c5305407ad22f3ada908523313d964
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168524"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a>Karmaşık filtreleme (C#) ile sorgu yazma
Bazen karmaşık filtrelerle XML sorgularına LINQ yazmak istersiniz. Örneğin, belirli bir ada ve değere sahip bir alt öğeye sahip tüm öğeleri bulmanız gerekebilir. Bu konu karmaşık filtreleme ile bir sorgu yazma bir örnek verir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, "Gönderim" ile `PurchaseOrder` `Address` eşit bir `Type` özniteliği olan bir alt öğeye `State` sahip tüm öğeleri ve "NY" ile eşit bir alt öğeyi nasıl bulabileceğinizi gösterir. Yan tümcede iç içe bir `Any` sorgu kullanır ve koleksiyonda herhangi bir öğe varsa işleç döndürür. `true` `Where` Yöntem tabanlı sorgu sözdizimini kullanma hakkında bilgi [için, LINQ'da Sorgu Sözdizimi ve Yöntem Sözdizimi'ne](./query-syntax-and-method-syntax-in-linq.md)bakın.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Birden Çok SatınAlma Siparişi (LINQ-XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
 `Any` Operatör hakkında daha fazla bilgi için [Quantifier Operations (C#)](./quantifier-operations.md)bakın.  
  
```csharp  
XElement root = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements("PurchaseOrder")  
    where
        (from add in el.Elements("Address")  
        where  
            (string)add.Attribute("Type") == "Shipping" &&  
            (string)add.Element("State") == "NY"  
        select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```output  
99505  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ad alanında olan XML için aynı sorguyu gösterir. Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Ad alanında birden çok Satınalma Siparişi.](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md)  
  
```csharp  
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements(aw + "PurchaseOrder")  
    where  
        (from add in el.Elements(aw + "Address")  
         where  
             (string)add.Attribute(aw + "Type") == "Shipping" &&  
             (string)add.Element(aw + "State") == "NY"  
         select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```output  
99505  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Projeksiyon İşlemleri (C#)](./projection-operations.md)
- [Niceleyici İşlemleri (C#)](./quantifier-operations.md)
