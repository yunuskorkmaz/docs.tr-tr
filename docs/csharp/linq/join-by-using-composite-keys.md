---
title: Bileşik tuşları kullanarak katılın (C#'da LINQ)
description: LINQ'da bileşik tuşları kullanarak nasıl katılacağınızı öğrenin.
ms.date: 12/01/2016
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: 460a52da7e0c0a47b77d4c64e76641bae9da7cd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659884"
---
# <a name="join-by-using-composite-keys"></a>Bileşik anahtarlar kullanarak birleştirme

Bu örnek, bir eşleşmetanımlamak için birden fazla anahtar kullanmak istediğiniz birleştirme işlemlerini nasıl gerçekleştireceklerini gösterir. Bu, bileşik anahtar kullanılarak gerçekleştirilir. Karşılaştırmak istediğiniz değerlerle anonim bir tür olarak bileşik bir anahtar oluşturursunuz veya adlandırılmış bir anahtar oluşturursunuz. Sorgu değişkeni yöntem sınırları nın ötesine geçilecekse, <xref:System.Object.Equals%2A> <xref:System.Object.GetHashCode%2A> geçersiz kılan ve anahtar için adlandırılmış bir tür kullanın. Özelliklerin adları ve bunların oluştuğu sıra, her anahtarda aynı olmalıdır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, üç tablodaki verileri birleştirmek için bileşik anahtarın nasıl kullanılacağını gösterir:

```csharp
var query = from o in db.Orders
    from p in db.Products
    join d in db.OrderDetails
        on new {o.OrderID, p.ProductID} equals new {d.OrderID, d.ProductID} into details
        from d in details
        select new {o.OrderID, p.ProductID, d.UnitPrice};
```

Bileşik anahtarlara yazı çıkarımı, anahtarlarda bulunan özelliklerin adlarına ve bunların oluşma sırasına bağlıdır. Kaynak dizideki özellikler aynı adlara sahip değilse, anahtarlara yeni adlar atamanız gerekir. Örneğin, `Orders` tablo ve `OrderDetails` tablo nun her biri sütunları için farklı adlar kullanılıyorsa, anonim türlere aynı adlar atayarak bileşik anahtarlar oluşturabilirsiniz:

```csharp
join...on new {Name = o.CustomerName, ID = o.CustID} equals
    new {Name = d.CustName, ID = d.CustID }
```

Bileşik tuşlar bir `group` yan tümcede de kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
- [birleştirme yan tümcesi](../language-reference/keywords/join-clause.md)
- [group yan tümcesi](../language-reference/keywords/group-clause.md)
