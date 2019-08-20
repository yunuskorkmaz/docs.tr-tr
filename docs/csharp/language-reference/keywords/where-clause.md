---
title: WHERE yan tümcesi C# -başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: aceda6cfd33a53388a5afb046359c4dcfddfd1f8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602026"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="fa380-102">where tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fa380-102">where clause (C# Reference)</span></span>

<span data-ttu-id="fa380-103">`where` Yan tümcesi, sorgu ifadesinde veri kaynağından hangi öğelerin döndürüleceğini belirtmek için bir sorgu ifadesinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa380-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="fa380-104">Her kaynak öğesine (Aralık değişkeni tarafından başvurulan) bir Boolean koşulu (*koşul*) uygular ve belirtilen koşulun doğru olduğu öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa380-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="fa380-105">Tek bir sorgu ifadesinde birden çok `where` yan tümce bulunabilir ve tek bir yan tümce birden çok koşul alt ifadesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fa380-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>

## <a name="example"></a><span data-ttu-id="fa380-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa380-106">Example</span></span>

<span data-ttu-id="fa380-107">Aşağıdaki örnekte `where` yan tümce, beş ' dan az olanlar hariç tüm sayıları filtreler.</span><span class="sxs-lookup"><span data-stu-id="fa380-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="fa380-108">`where` Yan tümcesini kaldırırsanız, veri kaynağındaki tüm sayılar döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fa380-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="fa380-109">İfade `num < 5` , her bir öğeye uygulanan belirtedir.</span><span class="sxs-lookup"><span data-stu-id="fa380-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a><span data-ttu-id="fa380-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa380-110">Example</span></span>

<span data-ttu-id="fa380-111">Tek `where` bir yan tümce içinde, [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) ve [ &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) işleçlerini kullanarak gereken sayıda koşulu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa380-111">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) and [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="fa380-112">Aşağıdaki örnekte sorgu, yalnızca beş ' dan küçük olan sayıları seçmek için iki koşul belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa380-112">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a><span data-ttu-id="fa380-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa380-113">Example</span></span>

<span data-ttu-id="fa380-114">Bir `where` yan tümce, Boolean değer döndüren bir veya daha fazla yöntem içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fa380-114">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="fa380-115">Aşağıdaki örnekte `where` yan tümce, Aralık değişkeninin geçerli değerinin çift mi yoksa tek mi olduğunu anlamak için bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="fa380-115">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a><span data-ttu-id="fa380-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa380-116">Remarks</span></span>

<span data-ttu-id="fa380-117">`where` Yan tümce bir filtreleme mekanizmasıdır.</span><span class="sxs-lookup"><span data-stu-id="fa380-117">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="fa380-118">Bir sorgu ifadesinde neredeyse her yerde konumlandırılmış olabilir, ancak ilk veya son yan tümce olamaz.</span><span class="sxs-lookup"><span data-stu-id="fa380-118">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="fa380-119">Bir `where` yan tümce, kaynak öğeleri gruplandırılmadan önce veya sonra filtrelemeniz gerekip gerekmediğini bağlı olarak, bir [Grup](group-clause.md) yan tümcesinden önce veya sonra görünebilir.</span><span class="sxs-lookup"><span data-stu-id="fa380-119">A `where` clause may appear either before or after a [group](group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>

<span data-ttu-id="fa380-120">Belirtilen koşul veri kaynağındaki öğeler için geçerli değilse, bir derleme zamanı hatası ortaya kalır.</span><span class="sxs-lookup"><span data-stu-id="fa380-120">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="fa380-121">Bu, tarafından [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]sunulan güçlü tür denetiminin bir avantajıdır.</span><span class="sxs-lookup"><span data-stu-id="fa380-121">This is one benefit of the strong type-checking provided by [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span></span>

<span data-ttu-id="fa380-122">Derleme zamanında `where` anahtar sözcüğü <xref:System.Linq.Enumerable.Where%2A> standart sorgu işleci yöntemine yapılan bir çağrıya dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="fa380-122">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa380-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa380-123">See also</span></span>

- [<span data-ttu-id="fa380-124">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="fa380-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="fa380-125">from yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="fa380-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="fa380-126">select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="fa380-126">select clause</span></span>](select-clause.md)
- [<span data-ttu-id="fa380-127">Verileri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="fa380-127">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)
- [<span data-ttu-id="fa380-128">LINQ sorgu Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="fa380-128">LINQ Query Expressions</span></span>](../../programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="fa380-129">C#'de LINQ Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="fa380-129">Getting Started with LINQ in C#</span></span>](../../programming-guide/concepts/linq/getting-started-with-linq.md)
