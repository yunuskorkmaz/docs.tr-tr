---
title: 'Nasıl yapılır: Karmaşık filtrelemeye (C#) sahip sorguları yazma'
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 3fe62b4a3c78c61de28311adf3feec1a613ff167
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592175"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a>Nasıl yapılır: Karmaşık filtrelemeye (C#) sahip sorguları yazma
Bazen karmaşık filtrelerle LINQ to XML sorguları yazmak isteyebilirsiniz. Örneğin, belirli bir ada ve değere sahip bir alt öğesi olan tüm öğeleri bulmanız gerekebilir. Bu konu, karmaşık filtrelemeye sahip sorgu yazma örneği sağlar.  
  
## <a name="example"></a>Örnek  
 Bu `PurchaseOrder` örnek, `Address` `State` bir özniteliği "Shipping" ve alt öğesi "NY" değerine eşit olan bir alt öğesi olan tüm öğelerin nasıl bulunacağını gösterir. `Type` `Where` Yan tümcesinde iç içe geçmiş bir sorgu kullanır `Any` ve koleksiyonda herhangi bir öğe `true` varsa işleç döndürülür. Yöntem tabanlı sorgu söz dizimini kullanma hakkında daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi](./query-syntax-and-method-syntax-in-linq.md).  
  
 Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Birden çok satın alma siparişi (](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)LINQ to XML).  
  
 `Any` İşleci hakkında daha fazla bilgi için bkz. [nicelik belirteci işlemleriC#()](./quantifier-operations.md).  
  
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
  
```  
99505  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).  
  
 Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Bir ad alanında](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md)birden fazla satın alma siparişi.  
  
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
  
```  
99505  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Projeksiyon Işlemleri (C#)](./projection-operations.md)
- [Nicelik belirteci IşlemleriC#()](./quantifier-operations.md)
