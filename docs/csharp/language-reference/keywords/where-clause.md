---
title: Burada yan tümcesi - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: fc259f0e0a83d2f55bf2d50fa336c9201b8b5bef
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633215"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="c36bf-102">where tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c36bf-102">where clause (C# Reference)</span></span>

<span data-ttu-id="c36bf-103">`where` Yan tümcesi bir sorgu ifadesinde sorgu ifadesi içinde veri kaynağından hangi öğelerin döndürülmesi belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c36bf-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="c36bf-104">Bir Boolean koşulu uygular (*koşul*) için her kaynak öğesi (aralık değişkeni tarafından başvurulan) ve bunlar için belirtilen koşulun true döndürür.</span><span class="sxs-lookup"><span data-stu-id="c36bf-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="c36bf-105">Tek bir sorgu ifadesi birden çok içerebilir `where` yan tümceleri ve tek bir yan tümce birden çok koşul alt ifadeler içeriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="c36bf-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>

## <a name="example"></a><span data-ttu-id="c36bf-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="c36bf-106">Example</span></span>

<span data-ttu-id="c36bf-107">Aşağıdaki örnekte, `where` yan tümcesi filtreler en az beş olanlar dışındaki tüm sayılar uğradı.</span><span class="sxs-lookup"><span data-stu-id="c36bf-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="c36bf-108">Kaldırırsanız `where` yan tümcesi, veri kaynağından tüm sayılar döndürülen.</span><span class="sxs-lookup"><span data-stu-id="c36bf-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="c36bf-109">İfade `num < 5` her öğeye uygulanan koşuldur.</span><span class="sxs-lookup"><span data-stu-id="c36bf-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a><span data-ttu-id="c36bf-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="c36bf-110">Example</span></span>

<span data-ttu-id="c36bf-111">Tek bir `where` yan tümcesini kullanarak, çok doğrulamaları gerektiği gibi belirtebilirsiniz [ && ](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) ve [ &#124; &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="c36bf-111">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) and [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="c36bf-112">Aşağıdaki örnekte, yalnızca en az beş olan çift sayıları seçmek için iki doğrulamaları sorguyu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c36bf-112">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a><span data-ttu-id="c36bf-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="c36bf-113">Example</span></span>

<span data-ttu-id="c36bf-114">A `where` yan tümcesi, Boole değerleri döndüren bir veya daha fazla yöntemler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c36bf-114">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="c36bf-115">Aşağıdaki örnekte, `where` yan tümcesinin Aralık değişkeninin geçerli değerini çift veya tek sayı olup olmadığını belirlemek için bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="c36bf-115">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a><span data-ttu-id="c36bf-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c36bf-116">Remarks</span></span>

<span data-ttu-id="c36bf-117">`where` Yan tümcesi ise bir filtreleme mekanizması.</span><span class="sxs-lookup"><span data-stu-id="c36bf-117">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="c36bf-118">İlk veya son yan tümcesi olamaz dışında bir sorgu ifadesinde, neredeyse her yerden konumlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c36bf-118">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="c36bf-119">A `where` yan tümcesi, önce veya sonra görünebilir bir [grubu](group-clause.md) önce veya sonra gruplanmış olan kaynak öğeleri filtrelemek olmasına bağlı olarak yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="c36bf-119">A `where` clause may appear either before or after a [group](group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>

<span data-ttu-id="c36bf-120">Belirtilen bir koşulu veri kaynağındaki öğeleri için geçerli değilse, bir derleme zamanı hatası neden olur.</span><span class="sxs-lookup"><span data-stu-id="c36bf-120">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="c36bf-121">Bu güçlü tür tarafından sağlanan denetimi bir yararı, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c36bf-121">This is one benefit of the strong type-checking provided by [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span></span>

<span data-ttu-id="c36bf-122">Derleme zamanında `where` anahtar sözcüğü, bir çağrı biçimine dönüştürülür <xref:System.Linq.Enumerable.Where%2A> standart sorgu işleci yöntem.</span><span class="sxs-lookup"><span data-stu-id="c36bf-122">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>

## <a name="see-also"></a><span data-ttu-id="c36bf-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c36bf-123">See also</span></span>

- [<span data-ttu-id="c36bf-124">Query Keywords (LINQ)</span><span class="sxs-lookup"><span data-stu-id="c36bf-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="c36bf-125">from yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="c36bf-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="c36bf-126">select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="c36bf-126">select clause</span></span>](select-clause.md)
- [<span data-ttu-id="c36bf-127">Verileri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="c36bf-127">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)
- [<span data-ttu-id="c36bf-128">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="c36bf-128">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="c36bf-129">C#'de LINQ Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="c36bf-129">Getting Started with LINQ in C#</span></span>](../../programming-guide/concepts/linq/getting-started-with-linq.md)
