---
title: 'Nasıl yapılır: karmaşık (C#) filtreleme ile sorgu yazma'
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 2f8eef2f75e45212b3493aa1b6f813c52beb7665
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508839"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a>Nasıl yapılır: karmaşık (C#) filtreleme ile sorgu yazma
Bazen karmaşık filtrelerle XML sorgularında LINQ yazmak istersiniz. Örneğin, bir özel ad ve değer olan bir alt öğesi olan tüm öğeleri Bul gerekebilir. Bu konu, karmaşık filtreleme ile sorgu yazma örneği sağlar.  
  
## <a name="example"></a>Örnek  
 Bu örnekte tüm bulmayı gösteren `PurchaseOrder` alt olan öğeler `Address` sahip öğe bir `Type` özniteliği "Gönderim" hem de bir alt gruba eşit `State` öğesi "NY için" eşit. İç içe bir sorgu kullanan `Where` yan tümcesi ve `Any` işleci döndürür `true` koleksiyonu herhangi bir öğe varsa. Metot tabanlı sorgu söz dizimi hakkında daha fazla bilgi için bkz: [sorgu sözdizimi ve yöntem sözdizimi LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
 Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: birden fazla satın alma siparişi (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
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
 Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir. Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: bir Namespace, birden fazla satın alma siparişi](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Xml.Linq.XElement.Attribute%2A>  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
- [Temel sorgular (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
- [Projeksiyon işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
- [Niceleyici işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
