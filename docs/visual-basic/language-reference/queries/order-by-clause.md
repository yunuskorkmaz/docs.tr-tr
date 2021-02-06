---
description: 'Daha fazla bilgi edinin: order by tümcesi (Visual Basic)'
title: Order By Yan Tümcesi
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
ms.openlocfilehash: b5e7cc93b11393ef2f256e90e402975fbf6633a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653621"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="80ef6-103">Order By Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80ef6-103">Order By Clause (Visual Basic)</span></span>

<span data-ttu-id="80ef6-104">Bir sorgu sonucu için sıralama düzenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="80ef6-104">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80ef6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="80ef6-105">Syntax</span></span>  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="80ef6-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="80ef6-106">Parts</span></span>  

 `orderExp1`  
 <span data-ttu-id="80ef6-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="80ef6-107">Required.</span></span> <span data-ttu-id="80ef6-108">Geçerli sorgu sonucundan döndürülen değerlerin nasıl sıraya alınacağını belirleyen bir veya daha fazla alan.</span><span class="sxs-lookup"><span data-stu-id="80ef6-108">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="80ef6-109">Alan adları virgüller (,) ile ayrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="80ef6-109">The field names must be separated by commas (,).</span></span> <span data-ttu-id="80ef6-110">`Ascending`Veya anahtar sözcüklerini kullanarak her bir alanı artan veya azalan düzende sıralanmış olarak belirleyebilirsiniz `Descending` .</span><span class="sxs-lookup"><span data-stu-id="80ef6-110">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="80ef6-111">Hayır `Ascending` veya `Descending` anahtar sözcüğü belirtilmemişse, varsayılan sıralama düzeni artan olur.</span><span class="sxs-lookup"><span data-stu-id="80ef6-111">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="80ef6-112">Sıralama düzeni alanlarına soldan sağa öncelik verilir.</span><span class="sxs-lookup"><span data-stu-id="80ef6-112">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80ef6-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80ef6-113">Remarks</span></span>  

 <span data-ttu-id="80ef6-114">`Order By`Bir sorgunun sonuçlarını sıralamak için yan tümcesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80ef6-114">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="80ef6-115">`Order By`Yan tümce yalnızca geçerli kapsamın Aralık değişkenine göre bir sonuç sıralayabilir.</span><span class="sxs-lookup"><span data-stu-id="80ef6-115">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="80ef6-116">Örneğin `Select` yan tümcesi, bir sorgu ifadesinde bu kapsam için yeni yineleme değişkenleriyle yeni bir kapsam sağlar.</span><span class="sxs-lookup"><span data-stu-id="80ef6-116">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="80ef6-117">Sorgudaki bir yan tümce öncesinde tanımlanan Aralık değişkenleri `Select` , `Select` yan tümcesinden sonra kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="80ef6-117">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="80ef6-118">Bu nedenle, sonuçlarınızı yan tümcesinde kullanılamayan bir alana göre sıralamak isterseniz, yan tümcesini `Select` yan tümce önüne koymanız gerekir `Order By` `Select` .</span><span class="sxs-lookup"><span data-stu-id="80ef6-118">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="80ef6-119">Bunu yapmanız gereken bir örnek, sorgunuzu sonucun bir parçası olarak döndürülmüyor alanlara göre sıralamak isteeceklerdir.</span><span class="sxs-lookup"><span data-stu-id="80ef6-119">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="80ef6-120">Bir alan için artan ve azalan sıralama, <xref:System.IComparable> alanın veri türü için arabirim uygulamasına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="80ef6-120">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="80ef6-121">Veri türü arabirimi uygulamadığı takdirde <xref:System.IComparable> sıralama düzeni yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="80ef6-121">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80ef6-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="80ef6-122">Example</span></span>  

 <span data-ttu-id="80ef6-123">Aşağıdaki sorgu ifadesi, `From` koleksiyon için bir Aralık değişkeni bildirmek üzere bir yan tümce kullanır `book` `books` .</span><span class="sxs-lookup"><span data-stu-id="80ef6-123">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="80ef6-124">`Order By`Yan tümcesi, sorgu sonucunu fiyata göre artan sırada sıralar (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="80ef6-124">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="80ef6-125">Aynı fiyata sahip olan kitaplar başlığa göre artan sırada sıralanır.</span><span class="sxs-lookup"><span data-stu-id="80ef6-125">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="80ef6-126">`Select`Yan tümcesi, `Title` ve `Price` özelliklerini sorgu tarafından döndürülen değerler olarak seçer.</span><span class="sxs-lookup"><span data-stu-id="80ef6-126">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="80ef6-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="80ef6-127">Example</span></span>  

 <span data-ttu-id="80ef6-128">Aşağıdaki sorgu ifadesi, `Order By` sorgu sonucunu fiyata göre azalan sırada sıralamak için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="80ef6-128">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="80ef6-129">Aynı fiyata sahip olan kitaplar başlığa göre artan sırada sıralanır.</span><span class="sxs-lookup"><span data-stu-id="80ef6-129">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="80ef6-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="80ef6-130">Example</span></span>  

 <span data-ttu-id="80ef6-131">Aşağıdaki sorgu ifadesi, `Select` kitap başlığı, Fiyat, yayımlama tarihi ve yazar seçmek için bir yan tümce kullanır.</span><span class="sxs-lookup"><span data-stu-id="80ef6-131">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="80ef6-132">Ardından, `Title` `Price` `PublishDate` `Author` Yeni kapsamın aralık değişkeninin,, ve alanlarını doldurur.</span><span class="sxs-lookup"><span data-stu-id="80ef6-132">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="80ef6-133">`Order By`Yan tümcesi, yeni Aralık değişkenini yazar adı, kitap başlığı ve sonra fiyat olarak sıralar.</span><span class="sxs-lookup"><span data-stu-id="80ef6-133">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="80ef6-134">Her sütun varsayılan sırada sıralanır (artan).</span><span class="sxs-lookup"><span data-stu-id="80ef6-134">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="80ef6-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80ef6-135">See also</span></span>

- [<span data-ttu-id="80ef6-136">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="80ef6-136">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="80ef6-137">Sorgular</span><span class="sxs-lookup"><span data-stu-id="80ef6-137">Queries</span></span>](index.md)
- [<span data-ttu-id="80ef6-138">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="80ef6-138">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="80ef6-139">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="80ef6-139">From Clause</span></span>](from-clause.md)
