---
title: "Bileşik anahtarlar kullanarak birleştirme"
description: "Bileşik anahtarlar kullanarak birleştirme yapma."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: c285e768d64d1da7e428e29fc67838e87575500c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Join tümcesi](../language-reference/keywords/join-clause.md)  
 [Group tümcesi](../language-reference/keywords/group-clause.md)
