---
title: Bileşik anahtarlar kullanarak birleştirme
description: Bileşik anahtarlar kullanarak birleştirme yapma.
ms.date: 12/1/2016
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: e40f4d147886c07913c761bb5df83ee34d23eaba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271220"
---
# <a name="join-by-using-composite-keys"></a>Bileşik anahtarlar kullanarak birleştirme

Bu örnek, birden fazla anahtar bir eşleşme tanımlamak için kullanmak istediğiniz birleştirme işlemleri gerçekleştirme gösterilmektedir. Bu, bir bileşik anahtarı kullanılarak gerçekleştirilir. Bileşik anahtar anonim bir tür olarak veya adlandırılmış karşılaştırmak istediğiniz değerleri ile yazılan oluşturduğunuz. Sorgu değişkeni yöntemi sınırlarında geçirilir, geçersiz kılan bir adlandırılmış türü kullanın. <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> anahtar. Özellikleri ve, bunlar, sırayla adları her anahtarında aynı olmalıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, üç tablolardaki verileri katılmak için bileşik bir anahtar kullanımı gösterilmiştir:  
  
```csharp  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,        d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 Tür çıkarımı bileşik anahtarlar anahtarları ve içinde gerçekleşme sipariş özelliklerinde adlarını bağlıdır. Kaynak sıraları özelliklerinde aynı adı yoksa, yeni adları anahtarlarında atamanız gerekir. Örneğin, varsa `Orders` tablo ve `OrderDetails` tablo her kullanılan kendi sütunlar için farklı adlar, anonim türler aynı adlarında atayarak bileşik anahtarlar oluşturabilirsiniz:  
  
```csharp  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 Bileşik anahtarlar da kullanılabilir bir `group` yan tümcesi.  

## <a name="see-also"></a>Ayrıca bkz.  
 [LINQ Sorgu ifadeleri](index.md)  
 [join yan tümcesi](../language-reference/keywords/join-clause.md)  
 [group yan tümcesi](../language-reference/keywords/group-clause.md)
