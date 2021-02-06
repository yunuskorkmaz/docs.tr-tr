---
description: 'Daha fazla bilgi edinin: Select tümcesi (Visual Basic)'
title: Select Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: 029778ce8262a93eee9a69843579523e8434eb01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653582"
---
# <a name="select-clause-visual-basic"></a><span data-ttu-id="59683-103">Select Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59683-103">Select Clause (Visual Basic)</span></span>

<span data-ttu-id="59683-104">Bir sorgunun sonucunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="59683-104">Defines the result of a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59683-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="59683-105">Syntax</span></span>  
  
```vb  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="59683-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="59683-106">Parts</span></span>  

 `var1`  
 <span data-ttu-id="59683-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="59683-107">Optional.</span></span> <span data-ttu-id="59683-108">Sütun ifadesinin sonuçlarına başvurmak için kullanılabilecek bir diğer ad.</span><span class="sxs-lookup"><span data-stu-id="59683-108">An alias that can be used to reference the results of the column expression.</span></span>  
  
 `fieldName1`  
 <span data-ttu-id="59683-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="59683-109">Required.</span></span> <span data-ttu-id="59683-110">Sorgu sonucuna döndürülecek alanın adı.</span><span class="sxs-lookup"><span data-stu-id="59683-110">The name of the field to return in the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59683-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59683-111">Remarks</span></span>  

 <span data-ttu-id="59683-112">`Select`Bir sorgudan döndürülecek sonuçları tanımlamak için yan tümcesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59683-112">You can use the `Select` clause to define the results to return from a query.</span></span> <span data-ttu-id="59683-113">Bu, bir sorgu tarafından oluşturulan yeni bir anonim türün üyelerini tanımlamanızı ya da bir sorgu tarafından döndürülen adlandırılmış türün üyelerini hedeflemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="59683-113">This enables you to either define the members of a new anonymous type that is created by a query, or to target the members of a named type that is returned by a query.</span></span> <span data-ttu-id="59683-114">`Select`Bir sorgu için yan tümce gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="59683-114">The `Select` clause is not required for a query.</span></span> <span data-ttu-id="59683-115">Hiçbir `Select` yan tümce belirtilmemişse, sorgu geçerli kapsam için tanımlanan Aralık değişkenlerinin tüm üyelerini temel alan bir tür döndürür.</span><span class="sxs-lookup"><span data-stu-id="59683-115">If no `Select` clause is specified, the query will return a type based on all members of the range variables identified for the current scope.</span></span> <span data-ttu-id="59683-116">Daha fazla bilgi için bkz. [anonim türler](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="59683-116">For more information, see [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span> <span data-ttu-id="59683-117">Bir sorgu adlandırılmış bir tür oluşturduğunda, oluşturulduğu tür bir sonuç döndürür <xref:System.Collections.Generic.IEnumerable%601> `T` .</span><span class="sxs-lookup"><span data-stu-id="59683-117">When a query creates a named type, it will return a result of type <xref:System.Collections.Generic.IEnumerable%601> where `T` is the created type.</span></span>  
  
 <span data-ttu-id="59683-118">`Select`Yan tümce geçerli kapsamdaki değişkenlere başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="59683-118">The `Select` clause can reference any variables in the current scope.</span></span> <span data-ttu-id="59683-119">Bu, `From` yan tümcesinde (veya `From` yan tümcelerde) tanımlanan Aralık değişkenlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="59683-119">This includes range variables identified in the `From` clause (or `From` clauses).</span></span> <span data-ttu-id="59683-120">Ayrıca,,, veya yan tümceleri tarafından oluşturulan yeni değişkenler `Aggregate` `Let` `Group By` `Group Join` veya `Select` sorgu ifadesinde Previous yan tümcesinin değişkenleri de içerir.</span><span class="sxs-lookup"><span data-stu-id="59683-120">It also includes any new variables created with an alias by the `Aggregate`, `Let`, `Group By`, or `Group Join` clauses, or variables from a previous `Select` clause in the query expression.</span></span> <span data-ttu-id="59683-121">`Select`Yan tümce statik değerler de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="59683-121">The `Select` clause can also include static values.</span></span> <span data-ttu-id="59683-122">Örneğin, aşağıdaki kod örneği, `Select` yan tümcesinin sorgu sonucunu dört üyeli yeni bir anonim tür olarak tanımladığı bir sorgu ifadesi gösterir: `ProductName` , `Price` , `Discount` ve `DiscountedPrice` .</span><span class="sxs-lookup"><span data-stu-id="59683-122">For example, the following code example shows a query expression in which the `Select` clause defines the query result as a new anonymous type with four members: `ProductName`, `Price`, `Discount`, and `DiscountedPrice`.</span></span> <span data-ttu-id="59683-123">`ProductName`Ve `Price` üye değerleri, yan tümcesinde tanımlanan ürün aralığı değişkeninden alınır `From` .</span><span class="sxs-lookup"><span data-stu-id="59683-123">The `ProductName` and `Price` member values are taken from the product range variable that is defined in the `From` clause.</span></span> <span data-ttu-id="59683-124">`DiscountedPrice`Üye değeri `Let` yan tümcesinde hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="59683-124">The `DiscountedPrice` member value is calculated in the `Let` clause.</span></span> <span data-ttu-id="59683-125">`Discount`Üye statik bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="59683-125">The `Discount` member is a static value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 <span data-ttu-id="59683-126">`Select`Yan tümcesi, sonraki sorgu yan tümceleri için yeni bir Aralık değişkenleri kümesi tanıtır ve önceki Aralık değişkenleri artık kapsamda değildir.</span><span class="sxs-lookup"><span data-stu-id="59683-126">The `Select` clause introduces a new set of range variables for subsequent query clauses, and previous range variables are no longer in scope.</span></span> <span data-ttu-id="59683-127">`Select`Sorgu ifadesindeki son yan tümce sorgunun dönüş değerini belirler.</span><span class="sxs-lookup"><span data-stu-id="59683-127">The last `Select` clause in a query expression determines the return value of the query.</span></span> <span data-ttu-id="59683-128">Örneğin, aşağıdaki sorgu toplam 500 ' ı aşan her müşteri siparişi için şirket adı ve sipariş KIMLIĞINI döndürür.</span><span class="sxs-lookup"><span data-stu-id="59683-128">For example, the following query returns the company name and order ID for every customer order for which the total exceeds 500.</span></span> <span data-ttu-id="59683-129">İlk `Select` yan tümce, `Where` yan tümce ve ikinci yan tümce için Aralık değişkenlerini tanımlar `Select` .</span><span class="sxs-lookup"><span data-stu-id="59683-129">The first `Select` clause identifies the range variables for the `Where` clause and the second `Select` clause.</span></span> <span data-ttu-id="59683-130">İkinci `Select` yan tümce, yeni bir anonim tür olarak sorgu tarafından döndürülen değerleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="59683-130">The second `Select` clause identifies the values returned by the query as a new anonymous type.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 <span data-ttu-id="59683-131">`Select`Yan tümcesi döndürülecek tek bir öğeyi tanımlarsa, sorgu ifadesi bu tek öğe türünün bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="59683-131">If the `Select` clause identifies a single item to return, the query expression returns a collection of the type of that single item.</span></span> <span data-ttu-id="59683-132">`Select`Yan tümcesi döndürülecek birden çok öğeyi tanımlarsa, sorgu ifadesi seçili öğelere göre yeni bir anonim türün koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="59683-132">If the `Select` clause identifies multiple items to return, the query expression returns a collection of a new anonymous type, based on the selected items.</span></span> <span data-ttu-id="59683-133">Örneğin, aşağıdaki iki sorgu yan tümcesini temel alan iki farklı türdeki koleksiyonları döndürür `Select` .</span><span class="sxs-lookup"><span data-stu-id="59683-133">For example, the following two queries return collections of two different types based on the `Select` clause.</span></span> <span data-ttu-id="59683-134">İlk sorgu, bir şirket adları koleksiyonunu dize olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="59683-134">The first query returns a collection of company names as strings.</span></span> <span data-ttu-id="59683-135">İkinci sorgu, `Customer` Şirket adları ve adres bilgileriyle doldurulmuş bir nesne koleksiyonu döndürür.</span><span class="sxs-lookup"><span data-stu-id="59683-135">The second query returns a collection of `Customer` objects populated with the company names and address information.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="59683-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="59683-136">Example</span></span>  

 <span data-ttu-id="59683-137">Aşağıdaki sorgu ifadesi, `From` koleksiyon için bir Aralık değişkeni bildirmek üzere bir yan tümce kullanır `cust` `customers` .</span><span class="sxs-lookup"><span data-stu-id="59683-137">The following query expression uses a `From` clause to declare a range variable `cust` for the `customers` collection.</span></span> <span data-ttu-id="59683-138">`Select`Yan tümce, müşteri adı ve kimlik değerini seçer ve `CompanyName` `CustomerID` Yeni Aralık değişkeninin ve sütunlarını doldurur.</span><span class="sxs-lookup"><span data-stu-id="59683-138">The `Select` clause selects the customer name and ID value and populates the `CompanyName` and `CustomerID` columns of the new range variable.</span></span> <span data-ttu-id="59683-139">`For Each`İfade döndürülen her nesnenin üzerinde döngü alır ve her bir `CompanyName` `CustomerID` kayıt için ve sütunlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="59683-139">The `For Each` statement loops over each returned object and displays the `CompanyName` and `CustomerID` columns for each record.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="59683-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59683-140">See also</span></span>

- [<span data-ttu-id="59683-141">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="59683-141">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="59683-142">Sorgular</span><span class="sxs-lookup"><span data-stu-id="59683-142">Queries</span></span>](index.md)
- [<span data-ttu-id="59683-143">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="59683-143">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="59683-144">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="59683-144">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="59683-145">Order by yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="59683-145">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="59683-146">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="59683-146">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
