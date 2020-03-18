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
# <a name="join-by-using-composite-keys"></a><span data-ttu-id="0aab8-103">Bileşik anahtarlar kullanarak birleştirme</span><span class="sxs-lookup"><span data-stu-id="0aab8-103">Join by using composite keys</span></span>

<span data-ttu-id="0aab8-104">Bu örnek, bir eşleşmetanımlamak için birden fazla anahtar kullanmak istediğiniz birleştirme işlemlerini nasıl gerçekleştireceklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0aab8-104">This example shows how to perform join operations in which you want to use more than one key to define a match.</span></span> <span data-ttu-id="0aab8-105">Bu, bileşik anahtar kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0aab8-105">This is accomplished by using a composite key.</span></span> <span data-ttu-id="0aab8-106">Karşılaştırmak istediğiniz değerlerle anonim bir tür olarak bileşik bir anahtar oluşturursunuz veya adlandırılmış bir anahtar oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="0aab8-106">You create a composite key as an anonymous type or named typed with the values that you want to compare.</span></span> <span data-ttu-id="0aab8-107">Sorgu değişkeni yöntem sınırları nın ötesine geçilecekse, <xref:System.Object.Equals%2A> <xref:System.Object.GetHashCode%2A> geçersiz kılan ve anahtar için adlandırılmış bir tür kullanın.</span><span class="sxs-lookup"><span data-stu-id="0aab8-107">If the query variable will be passed across method boundaries, use a named type that overrides <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> for the key.</span></span> <span data-ttu-id="0aab8-108">Özelliklerin adları ve bunların oluştuğu sıra, her anahtarda aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0aab8-108">The names of the properties, and the order in which they occur, must be identical in each key.</span></span>

## <a name="example"></a><span data-ttu-id="0aab8-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0aab8-109">Example</span></span>

<span data-ttu-id="0aab8-110">Aşağıdaki örnek, üç tablodaki verileri birleştirmek için bileşik anahtarın nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="0aab8-110">The following example demonstrates how to use a composite key to join data from three tables:</span></span>

```csharp
var query = from o in db.Orders
    from p in db.Products
    join d in db.OrderDetails
        on new {o.OrderID, p.ProductID} equals new {d.OrderID, d.ProductID} into details
        from d in details
        select new {o.OrderID, p.ProductID, d.UnitPrice};
```

<span data-ttu-id="0aab8-111">Bileşik anahtarlara yazı çıkarımı, anahtarlarda bulunan özelliklerin adlarına ve bunların oluşma sırasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0aab8-111">Type inference on composite keys depends on the names of the properties in the keys, and the order in which they occur.</span></span> <span data-ttu-id="0aab8-112">Kaynak dizideki özellikler aynı adlara sahip değilse, anahtarlara yeni adlar atamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0aab8-112">If the properties in the source sequences don't have the same names, you must assign new names in the keys.</span></span> <span data-ttu-id="0aab8-113">Örneğin, `Orders` tablo ve `OrderDetails` tablo nun her biri sütunları için farklı adlar kullanılıyorsa, anonim türlere aynı adlar atayarak bileşik anahtarlar oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0aab8-113">For example, if the `Orders` table and `OrderDetails` table each used different names for their columns, you could create composite keys by assigning identical names in the anonymous types:</span></span>

```csharp
join...on new {Name = o.CustomerName, ID = o.CustID} equals
    new {Name = d.CustName, ID = d.CustID }
```

<span data-ttu-id="0aab8-114">Bileşik tuşlar bir `group` yan tümcede de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0aab8-114">Composite keys can be also used in a `group` clause.</span></span>

## <a name="see-also"></a><span data-ttu-id="0aab8-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0aab8-115">See also</span></span>

- [<span data-ttu-id="0aab8-116">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="0aab8-116">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="0aab8-117">birleştirme yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="0aab8-117">join clause</span></span>](../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="0aab8-118">group yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="0aab8-118">group clause</span></span>](../language-reference/keywords/group-clause.md)
