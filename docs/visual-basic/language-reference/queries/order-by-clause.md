---
title: "Order By Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21ee21942b966668a67b14aba72b8f9fc5ee903c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="c1201-102">Order By Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1201-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="c1201-103">Sorgu sonucu için sıralama düzenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1201-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1201-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1201-104">Syntax</span></span>  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="c1201-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c1201-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="c1201-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c1201-106">Required.</span></span> <span data-ttu-id="c1201-107">Döndürülen değerlerini sıralamak nasıl tanımlayan bir veya daha fazla alanlarından geçerli sorgu sonucu.</span><span class="sxs-lookup"><span data-stu-id="c1201-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="c1201-108">Alan adları (,) virgülle ayrılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1201-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="c1201-109">Her bir alan olarak kullanarak azalan veya artan düzende sıralanmış olarak tanımlayabilirsiniz `Ascending` veya `Descending` anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="c1201-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="c1201-110">Öyle değilse `Ascending` veya `Descending` anahtar sözcüğü belirtilmediyse, varsayılan sıralama düzeni artan.</span><span class="sxs-lookup"><span data-stu-id="c1201-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="c1201-111">Sıralama sipariş alanlar soldan sağa öncelik verilir.</span><span class="sxs-lookup"><span data-stu-id="c1201-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1201-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1201-112">Remarks</span></span>  
 <span data-ttu-id="c1201-113">Kullanabileceğiniz `Order By` bir sorgunun sonuçlarını sıralamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="c1201-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="c1201-114">`Order By` Yan tümcesi yalnızca geçerli kapsam için aralık değişkeni dayalı bir sonuç sıralayın.</span><span class="sxs-lookup"><span data-stu-id="c1201-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="c1201-115">Örneğin, `Select` yan tümcesi bu kapsam için bir sorgu ifadesinde yeni yineleme değişkenleri ile yeni bir kapsam tanıtır.</span><span class="sxs-lookup"><span data-stu-id="c1201-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="c1201-116">Aralık önce tanımlanan değişkenler bir `Select` bir sorgu yan tümcesinde kullanılamaz sonra `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="c1201-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="c1201-117">Bu nedenle, sonuçlarınızı kullanılamaz bir alana göre sıralamak istiyorsanız `Select` yan tümcesi olmalıdır yerleştirme `Order By` önce yan tümcesi `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="c1201-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="c1201-118">Bir zaman bunu yapmak olurdu örneğidir sorgunuzu sonucu bir parçası olarak döndürülmez alanlara göre sıralamak istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="c1201-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="c1201-119">Artan veya azalan bir alan uygulaması tarafından belirlenir için <xref:System.IComparable> alanın veri türü için arabirim.</span><span class="sxs-lookup"><span data-stu-id="c1201-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="c1201-120">Veri türü uygulamazsa <xref:System.IComparable> arabirimi, sıralama düzeni göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="c1201-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1201-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1201-121">Example</span></span>  
 <span data-ttu-id="c1201-122">Aşağıdaki sorgu ifade kullanan bir `From` yan tümcesinin aralık değişkeni bildirmek için `book` için `books` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c1201-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="c1201-123">`Order By` Yan tümcesi göre artan sırada (varsayılan) fiyatı sorgu sonucu sıralar.</span><span class="sxs-lookup"><span data-stu-id="c1201-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="c1201-124">Aynı fiyatla Books artan düzende başlığa göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="c1201-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="c1201-125">`Select` Yan tümcesi seçer `Title` ve `Price` sorgu tarafından döndürülen değer olarak özellikleri.</span><span class="sxs-lookup"><span data-stu-id="c1201-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="c1201-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1201-126">Example</span></span>  
 <span data-ttu-id="c1201-127">Aşağıdaki sorgu ifadesi kullanır `Order By` göre azalan sırada fiyatı sorgu sonucu sıralamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="c1201-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="c1201-128">Aynı fiyatla Books artan düzende başlığa göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="c1201-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="c1201-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1201-129">Example</span></span>  
 <span data-ttu-id="c1201-130">Aşağıdaki sorgu ifade kullanan bir `Select` yan tümcesini defteri başlığı seçin, fiyat, yayımlama tarihi ve yazar.</span><span class="sxs-lookup"><span data-stu-id="c1201-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="c1201-131">Ardından doldurur `Title`, `Price`, `PublishDate`, ve `Author` yeni kapsam için Aralık değişkeninin alanları.</span><span class="sxs-lookup"><span data-stu-id="c1201-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="c1201-132">`Order By` Yan tümcesi siparişleri yazar adı, kitap başlığı ve ardından fiyat yeni aralık değişkeni.</span><span class="sxs-lookup"><span data-stu-id="c1201-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="c1201-133">Her sütunun (artan) varsayılan sıraya göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="c1201-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c1201-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1201-134">See Also</span></span>  
 [<span data-ttu-id="c1201-135">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="c1201-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="c1201-136">Sorguları</span><span class="sxs-lookup"><span data-stu-id="c1201-136">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="c1201-137">Select tümcesi</span><span class="sxs-lookup"><span data-stu-id="c1201-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="c1201-138">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="c1201-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
