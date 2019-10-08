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
ms.openlocfilehash: f8ee46b12e84f99629c3a92057fc3a7bb8a3c2e8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004947"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="64ec5-102">Order By Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64ec5-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="64ec5-103">Bir sorgu sonucu için sıralama düzenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="64ec5-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64ec5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64ec5-104">Syntax</span></span>  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="64ec5-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="64ec5-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="64ec5-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="64ec5-106">Required.</span></span> <span data-ttu-id="64ec5-107">Geçerli sorgu sonucundan döndürülen değerlerin nasıl sıraya alınacağını belirleyen bir veya daha fazla alan.</span><span class="sxs-lookup"><span data-stu-id="64ec5-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="64ec5-108">Alan adları virgüller (,) ile ayrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="64ec5-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="64ec5-109">@No__t-0 veya `Descending` anahtar sözcüklerini kullanarak her bir alanı artan veya azalan düzende sıralanmış olarak belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64ec5-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="64ec5-110">@No__t-0 veya `Descending` anahtar sözcüğü belirtilmemişse, varsayılan sıralama düzeni artan olur.</span><span class="sxs-lookup"><span data-stu-id="64ec5-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="64ec5-111">Sıralama düzeni alanlarına soldan sağa öncelik verilir.</span><span class="sxs-lookup"><span data-stu-id="64ec5-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64ec5-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64ec5-112">Remarks</span></span>  
 <span data-ttu-id="64ec5-113">Bir sorgunun sonuçlarını sıralamak için `Order By` yan tümcesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64ec5-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="64ec5-114">@No__t-0 yan tümcesi yalnızca geçerli kapsamın Aralık değişkenine göre bir sonuç sıralayabilir.</span><span class="sxs-lookup"><span data-stu-id="64ec5-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="64ec5-115">Örneğin, `Select` yan tümcesi, bu kapsam için yeni yineleme değişkenleriyle bir sorgu ifadesinde yeni bir kapsam sunar.</span><span class="sxs-lookup"><span data-stu-id="64ec5-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="64ec5-116">Sorgudaki `Select` yan tümcesinden önce tanımlanan Aralık değişkenleri `Select` yan tümcesinden sonra kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="64ec5-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="64ec5-117">Bu nedenle, sonuçlarınızı `Select` yan tümcesinde kullanılamayan bir alana göre sıralamak isterseniz, `Select` yan tümcesinin önüne `Order By` yan tümcesini koymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="64ec5-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="64ec5-118">Bunu yapmanız gereken bir örnek, sorgunuzu sonucun bir parçası olarak döndürülmüyor alanlara göre sıralamak isteeceklerdir.</span><span class="sxs-lookup"><span data-stu-id="64ec5-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="64ec5-119">Bir alan için artan ve azalan sıralama, alanın veri türü için <xref:System.IComparable> arabiriminin uygulamasına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="64ec5-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="64ec5-120">Veri türü <xref:System.IComparable> arabirimini uygulamadığı takdirde sıralama düzeni yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="64ec5-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64ec5-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="64ec5-121">Example</span></span>  
 <span data-ttu-id="64ec5-122">Aşağıdaki sorgu ifadesi bir `From` yan tümcesini kullanarak `books` koleksiyonu için-1 @no__t bir Aralık değişkeni bildirir.</span><span class="sxs-lookup"><span data-stu-id="64ec5-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="64ec5-123">@No__t-0 yan tümcesi, sorgu sonucunu fiyata göre artan sırada sıralar (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="64ec5-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="64ec5-124">Aynı fiyata sahip olan kitaplar başlığa göre artan sırada sıralanır.</span><span class="sxs-lookup"><span data-stu-id="64ec5-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="64ec5-125">@No__t-0 yan tümcesi, sorgu tarafından döndürülen değerler olarak `Title` ve `Price` özelliklerini seçer.</span><span class="sxs-lookup"><span data-stu-id="64ec5-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="64ec5-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="64ec5-126">Example</span></span>  
 <span data-ttu-id="64ec5-127">Aşağıdaki sorgu ifadesi, sorgu sonucunu fiyata göre azalan sırada sıralamak için `Order By` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="64ec5-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="64ec5-128">Aynı fiyata sahip olan kitaplar başlığa göre artan sırada sıralanır.</span><span class="sxs-lookup"><span data-stu-id="64ec5-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="64ec5-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="64ec5-129">Example</span></span>  
 <span data-ttu-id="64ec5-130">Aşağıdaki sorgu ifadesi, kitap başlığı, Fiyat, yayımlama tarihi ve yazar seçmek için bir `Select` yan tümcesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="64ec5-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="64ec5-131">Ardından, yeni kapsamın aralık değişkeninin `Title`, `Price`, `PublishDate` ve `Author` alanlarını doldurur.</span><span class="sxs-lookup"><span data-stu-id="64ec5-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="64ec5-132">@No__t-0 yan tümcesi, yeni Aralık değişkenini yazar adına, kitap başlığına ve ardından fiyata göre sıralar.</span><span class="sxs-lookup"><span data-stu-id="64ec5-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="64ec5-133">Her sütun varsayılan sırada sıralanır (artan).</span><span class="sxs-lookup"><span data-stu-id="64ec5-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="64ec5-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64ec5-134">See also</span></span>

- [<span data-ttu-id="64ec5-135">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="64ec5-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="64ec5-136">Sorgular</span><span class="sxs-lookup"><span data-stu-id="64ec5-136">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="64ec5-137">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="64ec5-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="64ec5-138">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="64ec5-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
