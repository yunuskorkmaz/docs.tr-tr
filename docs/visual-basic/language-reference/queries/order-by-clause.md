---
title: Order By Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: 7c60156ee81618530b42d5f61dbcac6f59c4f675
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604126"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="331e8-102">Order By Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="331e8-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="331e8-103">Sorgu sonucu için sıralama düzenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="331e8-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="331e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="331e8-104">Syntax</span></span>  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="331e8-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="331e8-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="331e8-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="331e8-106">Required.</span></span> <span data-ttu-id="331e8-107">Döndürülen değerlerini sıralamak nasıl tanımlayan bir veya daha fazla alanlarından geçerli sorgu sonucu.</span><span class="sxs-lookup"><span data-stu-id="331e8-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="331e8-108">Alan adları (,) virgülle ayrılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="331e8-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="331e8-109">Her bir alan olarak kullanarak azalan veya artan düzende sıralanmış olarak tanımlayabilirsiniz `Ascending` veya `Descending` anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="331e8-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="331e8-110">Öyle değilse `Ascending` veya `Descending` anahtar sözcüğü belirtilmediyse, varsayılan sıralama düzeni artan.</span><span class="sxs-lookup"><span data-stu-id="331e8-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="331e8-111">Sıralama sipariş alanlar soldan sağa öncelik verilir.</span><span class="sxs-lookup"><span data-stu-id="331e8-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="331e8-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="331e8-112">Remarks</span></span>  
 <span data-ttu-id="331e8-113">Kullanabileceğiniz `Order By` bir sorgunun sonuçlarını sıralamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="331e8-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="331e8-114">`Order By` Yan tümcesi yalnızca geçerli kapsam için aralık değişkeni dayalı bir sonuç sıralayın.</span><span class="sxs-lookup"><span data-stu-id="331e8-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="331e8-115">Örneğin, `Select` yan tümcesi bu kapsam için bir sorgu ifadesinde yeni yineleme değişkenleri ile yeni bir kapsam tanıtır.</span><span class="sxs-lookup"><span data-stu-id="331e8-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="331e8-116">Aralık önce tanımlanan değişkenler bir `Select` bir sorgu yan tümcesinde kullanılamaz sonra `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="331e8-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="331e8-117">Bu nedenle, sonuçlarınızı kullanılamaz bir alana göre sıralamak istiyorsanız `Select` yan tümcesi olmalıdır yerleştirme `Order By` önce yan tümcesi `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="331e8-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="331e8-118">Bir zaman bunu yapmak olurdu örneğidir sorgunuzu sonucu bir parçası olarak döndürülmez alanlara göre sıralamak istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="331e8-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="331e8-119">Artan veya azalan bir alan uygulaması tarafından belirlenir için <xref:System.IComparable> alanın veri türü için arabirim.</span><span class="sxs-lookup"><span data-stu-id="331e8-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="331e8-120">Veri türü uygulamazsa <xref:System.IComparable> arabirimi, sıralama düzeni göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="331e8-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="331e8-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="331e8-121">Example</span></span>  
 <span data-ttu-id="331e8-122">Aşağıdaki sorgu ifade kullanan bir `From` yan tümcesinin aralık değişkeni bildirmek için `book` için `books` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="331e8-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="331e8-123">`Order By` Yan tümcesi göre artan sırada (varsayılan) fiyatı sorgu sonucu sıralar.</span><span class="sxs-lookup"><span data-stu-id="331e8-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="331e8-124">Aynı fiyatla Books artan düzende başlığa göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="331e8-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="331e8-125">`Select` Yan tümcesi seçer `Title` ve `Price` sorgu tarafından döndürülen değer olarak özellikleri.</span><span class="sxs-lookup"><span data-stu-id="331e8-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="331e8-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="331e8-126">Example</span></span>  
 <span data-ttu-id="331e8-127">Aşağıdaki sorgu ifadesi kullanır `Order By` göre azalan sırada fiyatı sorgu sonucu sıralamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="331e8-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="331e8-128">Aynı fiyatla Books artan düzende başlığa göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="331e8-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="331e8-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="331e8-129">Example</span></span>  
 <span data-ttu-id="331e8-130">Aşağıdaki sorgu ifade kullanan bir `Select` yan tümcesini defteri başlığı seçin, fiyat, yayımlama tarihi ve yazar.</span><span class="sxs-lookup"><span data-stu-id="331e8-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="331e8-131">Ardından doldurur `Title`, `Price`, `PublishDate`, ve `Author` yeni kapsam için Aralık değişkeninin alanları.</span><span class="sxs-lookup"><span data-stu-id="331e8-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="331e8-132">`Order By` Yan tümcesi siparişleri yazar adı, kitap başlığı ve ardından fiyat yeni aralık değişkeni.</span><span class="sxs-lookup"><span data-stu-id="331e8-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="331e8-133">Her sütunun (artan) varsayılan sıraya göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="331e8-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="331e8-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="331e8-134">See Also</span></span>  
 [<span data-ttu-id="331e8-135">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="331e8-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="331e8-136">Sorgular</span><span class="sxs-lookup"><span data-stu-id="331e8-136">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="331e8-137">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="331e8-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="331e8-138">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="331e8-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
