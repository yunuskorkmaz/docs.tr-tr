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
# <a name="join-by-using-composite-keys"></a><span data-ttu-id="3c127-104">Bileşik anahtarlar kullanarak birleştirme</span><span class="sxs-lookup"><span data-stu-id="3c127-104">Join by using composite keys</span></span>

<span data-ttu-id="3c127-105">Bu örnek, birden fazla anahtar bir eşleşme tanımlamak için kullanmak istediğiniz birleştirme işlemleri gerçekleştirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3c127-105">This example shows how to perform join operations in which you want to use more than one key to define a match.</span></span> <span data-ttu-id="3c127-106">Bu, bir bileşik anahtarı kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3c127-106">This is accomplished by using a composite key.</span></span> <span data-ttu-id="3c127-107">Bileşik anahtar anonim bir tür olarak veya adlandırılmış karşılaştırmak istediğiniz değerleri ile yazılan oluşturduğunuz.</span><span class="sxs-lookup"><span data-stu-id="3c127-107">You create a composite key as an anonymous type or named typed with the values that you want to compare.</span></span> <span data-ttu-id="3c127-108">Sorgu değişkeni yöntemi sınırlarında geçirilir, geçersiz kılan bir adlandırılmış türü kullanın. <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> anahtar.</span><span class="sxs-lookup"><span data-stu-id="3c127-108">If the query variable will be passed across method boundaries, use a named type that overrides <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> for the key.</span></span> <span data-ttu-id="3c127-109">Özellikleri ve, bunlar, sırayla adları her anahtarında aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3c127-109">The names of the properties, and the order in which they occur, must be identical in each key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c127-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c127-110">Example</span></span>  
 <span data-ttu-id="3c127-111">Aşağıdaki örnekte, üç tablolardaki verileri katılmak için bileşik bir anahtar kullanımı gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3c127-111">The following example demonstrates how to use a composite key to join data from three tables:</span></span>  
  
```csharp  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,        d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 <span data-ttu-id="3c127-112">Tür çıkarımı bileşik anahtarlar anahtarları ve içinde gerçekleşme sipariş özelliklerinde adlarını bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3c127-112">Type inference on composite keys depends on the names of the properties in the keys, and the order in which they occur.</span></span> <span data-ttu-id="3c127-113">Kaynak sıraları özelliklerinde aynı adı yoksa, yeni adları anahtarlarında atamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c127-113">If the properties in the source sequences do not have the same names, you must assign new names in the keys.</span></span> <span data-ttu-id="3c127-114">Örneğin, varsa `Orders` tablo ve `OrderDetails` tablo her kullanılan kendi sütunlar için farklı adlar, anonim türler aynı adlarında atayarak bileşik anahtarlar oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3c127-114">For example, if the `Orders` table and `OrderDetails` table each used different names for their columns, you could create composite keys by assigning identical names in the anonymous types:</span></span>  
  
```csharp  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 <span data-ttu-id="3c127-115">Bileşik anahtarlar da kullanılabilir bir `group` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="3c127-115">Composite keys can be also used in a `group` clause.</span></span>  

## <a name="see-also"></a><span data-ttu-id="3c127-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c127-116">See also</span></span>  
 [<span data-ttu-id="3c127-117">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="3c127-117">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="3c127-118">Join tümcesi</span><span class="sxs-lookup"><span data-stu-id="3c127-118">join clause</span></span>](../language-reference/keywords/join-clause.md)  
 [<span data-ttu-id="3c127-119">Group tümcesi</span><span class="sxs-lookup"><span data-stu-id="3c127-119">group clause</span></span>](../language-reference/keywords/group-clause.md)
