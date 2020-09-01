---
description: WHERE yan tümcesi-C# başvurusu
title: WHERE yan tümcesi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 58a8dc226bb2720b6a8251f028712a80f74e893c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141692"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="8d932-103">where tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8d932-103">where clause (C# Reference)</span></span>

<span data-ttu-id="8d932-104">`where`Yan tümcesi, sorgu ifadesinde veri kaynağından hangi öğelerin döndürüleceğini belirtmek için bir sorgu ifadesinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8d932-104">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="8d932-105">Her kaynak öğesine (Aralık değişkeni tarafından başvurulan) bir Boolean koşulu (*koşul*) uygular ve belirtilen koşulun doğru olduğu öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d932-105">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="8d932-106">Tek bir sorgu ifadesinde birden çok `where` yan tümce bulunabilir ve tek bir yan tümce birden çok koşul alt ifadesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8d932-106">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>

## <a name="example"></a><span data-ttu-id="8d932-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d932-107">Example</span></span>

<span data-ttu-id="8d932-108">Aşağıdaki örnekte `where` yan tümce, beş ' dan az olanlar hariç tüm sayıları filtreler.</span><span class="sxs-lookup"><span data-stu-id="8d932-108">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="8d932-109">`where`Yan tümcesini kaldırırsanız, veri kaynağındaki tüm sayılar döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8d932-109">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="8d932-110">İfade, `num < 5` her bir öğeye uygulanan belirtedir.</span><span class="sxs-lookup"><span data-stu-id="8d932-110">The expression `num < 5` is the predicate that is applied to each element.</span></span>

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a><span data-ttu-id="8d932-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d932-111">Example</span></span>

<span data-ttu-id="8d932-112">Tek bir `where` yan tümce içinde, [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) ve [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) işleçlerini kullanarak gereken sayıda koşulu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d932-112">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) and [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="8d932-113">Aşağıdaki örnekte sorgu, yalnızca beş ' dan küçük olan sayıları seçmek için iki koşul belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d932-113">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a><span data-ttu-id="8d932-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d932-114">Example</span></span>

<span data-ttu-id="8d932-115">Bir `where` yan tümce, Boolean değer döndüren bir veya daha fazla yöntem içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8d932-115">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="8d932-116">Aşağıdaki örnekte `where` yan tümce, Aralık değişkeninin geçerli değerinin çift mi yoksa tek mi olduğunu anlamak için bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="8d932-116">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a><span data-ttu-id="8d932-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d932-117">Remarks</span></span>

<span data-ttu-id="8d932-118">`where`Yan tümce bir filtreleme mekanizmasıdır.</span><span class="sxs-lookup"><span data-stu-id="8d932-118">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="8d932-119">Bir sorgu ifadesinde neredeyse her yerde konumlandırılmış olabilir, ancak ilk veya son yan tümce olamaz.</span><span class="sxs-lookup"><span data-stu-id="8d932-119">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="8d932-120">Bir `where` yan tümce, kaynak öğeleri gruplandırılmadan önce veya sonra filtrelemeniz gerekip gerekmediğini bağlı olarak, bir [Grup](group-clause.md) yan tümcesinden önce veya sonra görünebilir.</span><span class="sxs-lookup"><span data-stu-id="8d932-120">A `where` clause may appear either before or after a [group](group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>

<span data-ttu-id="8d932-121">Belirtilen koşul veri kaynağındaki öğeler için geçerli değilse, bir derleme zamanı hatası ortaya kalır.</span><span class="sxs-lookup"><span data-stu-id="8d932-121">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="8d932-122">Bu, LINQ tarafından sunulan güçlü tür denetiminin bir avantajıdır.</span><span class="sxs-lookup"><span data-stu-id="8d932-122">This is one benefit of the strong type-checking provided by LINQ.</span></span>

<span data-ttu-id="8d932-123">Derleme zamanında `where` anahtar sözcüğü <xref:System.Linq.Enumerable.Where%2A> Standart sorgu işleci yöntemine yapılan bir çağrıya dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="8d932-123">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d932-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d932-124">See also</span></span>

- [<span data-ttu-id="8d932-125">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="8d932-125">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="8d932-126">from tümcesi</span><span class="sxs-lookup"><span data-stu-id="8d932-126">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="8d932-127">select tümcesi</span><span class="sxs-lookup"><span data-stu-id="8d932-127">select clause</span></span>](select-clause.md)
- [<span data-ttu-id="8d932-128">Verileri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="8d932-128">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)
- [<span data-ttu-id="8d932-129">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="8d932-129">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="8d932-130">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="8d932-130">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
