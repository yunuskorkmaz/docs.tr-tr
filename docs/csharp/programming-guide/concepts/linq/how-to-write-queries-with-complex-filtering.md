---
title: 'Nasıl yapılır: Karmaşık filtreleme ile sorgu yazma (C#)'
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 7a90a754036008463646321a3e9b9b7d83a3be33
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484587"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a>Nasıl yapılır: Karmaşık filtreleme ile sorgu yazma (C#)
Bazen karmaşık filtrelerle XML sorgularında LINQ yazmak istersiniz. Örneğin, bir özel ad ve değer olan bir alt öğesi olan tüm öğeleri Bul gerekebilir. Bu konu, karmaşık filtreleme ile sorgu yazma örneği sağlar.  
  
## <a name="example"></a>Örnek  
 Bu örnekte tüm bulmayı gösteren `PurchaseOrder` alt olan öğeler `Address` sahip öğe bir `Type` özniteliği "Gönderim" hem de bir alt gruba eşit `State` öğesi "NY için" eşit. İç içe bir sorgu kullanan `Where` yan tümcesi ve `Any` işleci döndürür `true` koleksiyonu herhangi bir öğe varsa. Metot tabanlı sorgu söz dizimi hakkında daha fazla bilgi için bkz: [sorgu sözdizimi ve yöntem sözdizimi LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Birden fazla satın alma siparişi (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
 Hakkında daha fazla bilgi için `Any` işleci bkz [Niceleyici işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).  
  
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
 Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir. Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Bir Namespace, birden fazla satın alma siparişi](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
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
- [Projeksiyon işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [Niceleyici işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
