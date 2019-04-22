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
ms.openlocfilehash: 1c84a4cdb4a149154d459ca4d9c290ed360d1772
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835017"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="b81f0-102">Order By Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b81f0-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="b81f0-103">Sorgu sonucu için sıralama düzenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b81f0-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b81f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b81f0-104">Syntax</span></span>  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="b81f0-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="b81f0-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="b81f0-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b81f0-106">Required.</span></span> <span data-ttu-id="b81f0-107">Döndürülen değerlerin nasıl tanımlayan bir veya daha fazla alanlardan geçerli sorgu sonucu.</span><span class="sxs-lookup"><span data-stu-id="b81f0-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="b81f0-108">Alan adlarını, virgül (,) ile ayrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b81f0-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="b81f0-109">Her bir alan olarak kullanarak azalan veya artan düzende sıralanmış olarak tanımlayabilirsiniz `Ascending` veya `Descending` anahtar sözcükleri.</span><span class="sxs-lookup"><span data-stu-id="b81f0-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="b81f0-110">Hayır ise `Ascending` veya `Descending` anahtar sözcüğü belirtilmediğinde, varsayılan sıralama artan düzendedir.</span><span class="sxs-lookup"><span data-stu-id="b81f0-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="b81f0-111">Sıralama düzeni alanlarını öncelik soldan sağa atanır.</span><span class="sxs-lookup"><span data-stu-id="b81f0-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b81f0-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b81f0-112">Remarks</span></span>  
 <span data-ttu-id="b81f0-113">Kullanabileceğiniz `Order By` bir sorgunun sonuçlarını sıralamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="b81f0-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="b81f0-114">`Order By` Yan tümcesinin aralık değişkeni geçerli kapsam için temel bir sonuç yalnızca sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b81f0-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="b81f0-115">Örneğin, `Select` yan tümcesi bir sorgu ifadesinde yeni yineleme değişkenleri ile ilgili kapsam için yeni bir kapsam tanıtır.</span><span class="sxs-lookup"><span data-stu-id="b81f0-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="b81f0-116">Aralık önce tanımlanan değişkenler bir `Select` sorgu yan tümcesinde kullanılamaz sonra `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="b81f0-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="b81f0-117">Bu nedenle, sonuçlarınızı kullanılamaz bir alana göre sıralamak isterseniz `Select` yan tümcesi gerekir put `Order By` yan tümcesi önce `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="b81f0-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="b81f0-118">Bir örneği olduğunda bunu yapmak gerekir, sorgu sonucu bir parçası olarak döndürülmez alanlara göre sıralamak istediğinizi olduğunda.</span><span class="sxs-lookup"><span data-stu-id="b81f0-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="b81f0-119">Artan ve azalan bir alan uygulaması tarafından belirlenir <xref:System.IComparable> alanın veri türü için arabirim.</span><span class="sxs-lookup"><span data-stu-id="b81f0-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="b81f0-120">Veri türü uygulamazsa <xref:System.IComparable> arabirimi, sıralama düzeni göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="b81f0-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b81f0-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="b81f0-121">Example</span></span>  
 <span data-ttu-id="b81f0-122">Aşağıdaki sorgu ifadesi kullanan bir `From` yan tümcesinin aralık değişkenini bildirmek için `book` için `books` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="b81f0-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="b81f0-123">`Order By` Yan tümce sorgu sonucuna göre artan düzende (varsayılan) fiyatı sıralar.</span><span class="sxs-lookup"><span data-stu-id="b81f0-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="b81f0-124">Kitapları ile aynı fiyat üzerinden, artan düzende başlığa göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="b81f0-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="b81f0-125">`Select` Yan tümcesi seçer `Title` ve `Price` sorgu tarafından döndürülen değer olarak özellikleri.</span><span class="sxs-lookup"><span data-stu-id="b81f0-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="b81f0-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="b81f0-126">Example</span></span>  
 <span data-ttu-id="b81f0-127">Aşağıdaki sorgu ifadesi kullanan `Order By` sorgu sonucuna göre azalan düzende fiyatı sıralamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="b81f0-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="b81f0-128">Kitapları ile aynı fiyat üzerinden, artan düzende başlığa göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="b81f0-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="b81f0-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="b81f0-129">Example</span></span>  
 <span data-ttu-id="b81f0-130">Aşağıdaki sorgu ifadesi kullanan bir `Select` yan kitap başlığını seçin, fiyat, yayımlama tarihi ve yazar.</span><span class="sxs-lookup"><span data-stu-id="b81f0-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="b81f0-131">Ardından doldurur `Title`, `Price`, `PublishDate`, ve `Author` yeni kapsam için Aralık değişkeninin alanları.</span><span class="sxs-lookup"><span data-stu-id="b81f0-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="b81f0-132">`Order By` Yan tümcesi yeni aralık değişkeni yazar adı, kitap başlığı ve fiyat göre sıralar.</span><span class="sxs-lookup"><span data-stu-id="b81f0-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="b81f0-133">Her sütun (artan) varsayılan sıraya göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="b81f0-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="b81f0-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b81f0-134">See also</span></span>

- [<span data-ttu-id="b81f0-135">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="b81f0-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="b81f0-136">Sorgular</span><span class="sxs-lookup"><span data-stu-id="b81f0-136">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="b81f0-137">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="b81f0-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="b81f0-138">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="b81f0-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
