---
title: (C# üzerinde LINQ) bileşik anahtarlar kullanarak birleştirme
description: LINQ to bileşik anahtarlar kullanarak birleştirme hakkında bilgi edinin.
ms.date: 12/01/2016
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: 460a52da7e0c0a47b77d4c64e76641bae9da7cd6
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857521"
---
# <a name="join-by-using-composite-keys"></a><span data-ttu-id="80b95-103">Bileşik anahtarlar kullanarak birleştirme</span><span class="sxs-lookup"><span data-stu-id="80b95-103">Join by using composite keys</span></span>

<span data-ttu-id="80b95-104">Bu örnek, birden fazla anahtar bir eşleşme tanımlamak için kullanmak istediğiniz birleştirme işlemleri gerçekleştirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="80b95-104">This example shows how to perform join operations in which you want to use more than one key to define a match.</span></span> <span data-ttu-id="80b95-105">Bu, bir bileşik anahtarı kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="80b95-105">This is accomplished by using a composite key.</span></span> <span data-ttu-id="80b95-106">Bir bileşik anahtarı anonim bir tür olarak veya adlandırılmış karşılaştırmak istediğiniz değerlerle yazılı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="80b95-106">You create a composite key as an anonymous type or named typed with the values that you want to compare.</span></span> <span data-ttu-id="80b95-107">Sorgu değişkeni yöntemi sınırlarında geçirilir, geçersiz kılmalar adlandırılmış bir tür kullanın. <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> anahtarı.</span><span class="sxs-lookup"><span data-stu-id="80b95-107">If the query variable will be passed across method boundaries, use a named type that overrides <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> for the key.</span></span> <span data-ttu-id="80b95-108">Özellikler ve, bunlar, sırayla adları içindeki her anahtarın aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="80b95-108">The names of the properties, and the order in which they occur, must be identical in each key.</span></span>

## <a name="example"></a><span data-ttu-id="80b95-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="80b95-109">Example</span></span>

<span data-ttu-id="80b95-110">Aşağıdaki örnek, üç tablolardaki verileri birleştirmek için bir bileşik anahtarı kullanacak şekilde gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="80b95-110">The following example demonstrates how to use a composite key to join data from three tables:</span></span>

```csharp
var query = from o in db.Orders
    from p in db.Products
    join d in db.OrderDetails
        on new {o.OrderID, p.ProductID} equals new {d.OrderID, d.ProductID} into details
        from d in details
        select new {o.OrderID, p.ProductID, d.UnitPrice};
```

<span data-ttu-id="80b95-111">Anahtarlar ve, bunlar sırayla özelliklerinde adlarını bileşik anahtarlar tür çıkarımı bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="80b95-111">Type inference on composite keys depends on the names of the properties in the keys, and the order in which they occur.</span></span> <span data-ttu-id="80b95-112">Kaynak dizileri özelliklerinde aynı ada sahip değilseniz, yeni anahtarları adlarında atamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="80b95-112">If the properties in the source sequences don't have the same names, you must assign new names in the keys.</span></span> <span data-ttu-id="80b95-113">Örneğin, varsa `Orders` tablo ve `OrderDetails` her tabloda kullanılan kendilerine ait sütunların için farklı adlar, anonim türde aynı ada atayarak bileşik anahtarlar oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="80b95-113">For example, if the `Orders` table and `OrderDetails` table each used different names for their columns, you could create composite keys by assigning identical names in the anonymous types:</span></span>

```csharp
join...on new {Name = o.CustomerName, ID = o.CustID} equals
    new {Name = d.CustName, ID = d.CustID }
```

<span data-ttu-id="80b95-114">Bileşik anahtarlar da kullanılabilir bir `group` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="80b95-114">Composite keys can be also used in a `group` clause.</span></span>

## <a name="see-also"></a><span data-ttu-id="80b95-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80b95-115">See also</span></span>

- [<span data-ttu-id="80b95-116">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="80b95-116">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="80b95-117">join yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="80b95-117">join clause</span></span>](../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="80b95-118">group yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="80b95-118">group clause</span></span>](../language-reference/keywords/group-clause.md)
