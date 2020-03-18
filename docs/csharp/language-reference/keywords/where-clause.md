---
title: where yan tümcesi - C# Referans
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 33616e4eacb484b9c6eda3862cd86fdd1e6df165
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173490"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="60703-102">where tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="60703-102">where clause (C# Reference)</span></span>

<span data-ttu-id="60703-103">Yan `where` tümce, sorgu ifadesinde veri kaynağından hangi öğelerin döndürüleceğini belirtmek için bir sorgu ifadesinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="60703-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="60703-104">Her kaynak öğe öğesine (aralık değişkeni tarafından başvurulan) boolean koşulu *(yüklem)* uygular ve belirtilen koşulun doğru olduğu durumu döndürür.</span><span class="sxs-lookup"><span data-stu-id="60703-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="60703-105">Tek bir sorgu ifadesi `where` birden çok yan tümce içerebilir ve tek bir yan tümce birden çok yüklem alt ifadesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="60703-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>

## <a name="example"></a><span data-ttu-id="60703-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="60703-106">Example</span></span>

<span data-ttu-id="60703-107">Aşağıdaki örnekte, `where` yan tümce beşten küçük olanlar dışındaki tüm sayıları filtreler.</span><span class="sxs-lookup"><span data-stu-id="60703-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="60703-108">Yan tümceyi `where` kaldırırsanız, veri kaynağından tüm sayılar döndürülür.</span><span class="sxs-lookup"><span data-stu-id="60703-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="60703-109">İfade, `num < 5` her öğeye uygulanan yüklemdir.</span><span class="sxs-lookup"><span data-stu-id="60703-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a><span data-ttu-id="60703-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="60703-110">Example</span></span>

<span data-ttu-id="60703-111">Tek `where` bir yan tümce içinde, ve [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) işleçleri [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) kullanarak gerektiği kadar yüklem belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60703-111">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) and [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="60703-112">Aşağıdaki örnekte, sorgu yalnızca beşten küçük olan çift sayıları seçmek için iki yüklem belirtir.</span><span class="sxs-lookup"><span data-stu-id="60703-112">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a><span data-ttu-id="60703-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="60703-113">Example</span></span>

<span data-ttu-id="60703-114">Bir `where` yan tümce Boolean değerlerini döndüren bir veya daha fazla yöntem içerebilir.</span><span class="sxs-lookup"><span data-stu-id="60703-114">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="60703-115">Aşağıdaki örnekte, `where` yan tümce, aralık değişkeninin geçerli değerinin çift veya tek olup olmadığını belirlemek için bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="60703-115">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a><span data-ttu-id="60703-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60703-116">Remarks</span></span>

<span data-ttu-id="60703-117">Yan `where` tümce bir filtreleme mekanizmasıdır.</span><span class="sxs-lookup"><span data-stu-id="60703-117">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="60703-118">İlk veya son tümce olamaz dışında, sorgu ifadesinde hemen hemen her yerde konumlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="60703-118">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="60703-119">Bir `where` yan tümce, gruplandırılmadan önce veya sonra kaynak öğeleri filtrelemeniz gerekip gerekmediğine bağlı olarak [bir grup](group-clause.md) yan tümcesinden önce veya sonra görünebilir.</span><span class="sxs-lookup"><span data-stu-id="60703-119">A `where` clause may appear either before or after a [group](group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>

<span data-ttu-id="60703-120">Veri kaynağındaki öğeler için belirli bir yüklem geçerli değilse, derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="60703-120">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="60703-121">Bu, LINQ tarafından sağlanan güçlü tür denetiminin bir avantajıdır.</span><span class="sxs-lookup"><span data-stu-id="60703-121">This is one benefit of the strong type-checking provided by LINQ.</span></span>

<span data-ttu-id="60703-122">Derleme zamanında `where` anahtar <xref:System.Linq.Enumerable.Where%2A> kelime, Standart Sorgu Operatörü yöntemine çağrıya dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="60703-122">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>

## <a name="see-also"></a><span data-ttu-id="60703-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60703-123">See also</span></span>

- [<span data-ttu-id="60703-124">Sorgu Anahtar Kelimeleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="60703-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="60703-125">fıkradan</span><span class="sxs-lookup"><span data-stu-id="60703-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="60703-126">yan tümceyi seçin</span><span class="sxs-lookup"><span data-stu-id="60703-126">select clause</span></span>](select-clause.md)
- [<span data-ttu-id="60703-127">Verileri filtreleme</span><span class="sxs-lookup"><span data-stu-id="60703-127">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)
- [<span data-ttu-id="60703-128">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="60703-128">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="60703-129">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="60703-129">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
