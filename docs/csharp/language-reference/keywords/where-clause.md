---
title: where tümcesi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 8607c79a8b1e9a9fd999e4f5b77ecfac786161b3
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43003157"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="4d39c-102">where tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4d39c-102">where clause (C# Reference)</span></span>
<span data-ttu-id="4d39c-103">`where` Yan tümcesi bir sorgu ifadesinde sorgu ifadesi içinde veri kaynağından hangi öğelerin döndürülmesi belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4d39c-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="4d39c-104">Bir Boolean koşulu uygular (*koşul*) için her kaynak öğesi (aralık değişkeni tarafından başvurulan) ve bunlar için belirtilen koşulun true döndürür.</span><span class="sxs-lookup"><span data-stu-id="4d39c-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="4d39c-105">Tek bir sorgu ifadesi birden çok içerebilir `where` yan tümceleri ve tek bir yan tümce birden çok koşul alt ifadeler içeriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="4d39c-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d39c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d39c-106">Example</span></span>  
 <span data-ttu-id="4d39c-107">Aşağıdaki örnekte, `where` yan tümcesi filtreler en az beş olanlar dışındaki tüm sayılar uğradı.</span><span class="sxs-lookup"><span data-stu-id="4d39c-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="4d39c-108">Kaldırırsanız `where` yan tümcesi, veri kaynağından tüm sayılar döndürülen.</span><span class="sxs-lookup"><span data-stu-id="4d39c-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="4d39c-109">İfade `num < 5` her öğeye uygulanan koşuldur.</span><span class="sxs-lookup"><span data-stu-id="4d39c-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="4d39c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d39c-110">Example</span></span>  
 <span data-ttu-id="4d39c-111">Tek bir `where` yan tümcesini kullanarak, çok doğrulamaları gerektiği gibi belirtebilirsiniz [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) ve [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="4d39c-111">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) operators.</span></span> <span data-ttu-id="4d39c-112">Aşağıdaki örnekte, yalnızca en az beş olan çift sayıları seçmek için iki doğrulamaları sorguyu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d39c-112">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="4d39c-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d39c-113">Example</span></span>  
 <span data-ttu-id="4d39c-114">A `where` yan tümcesi, Boole değerleri döndüren bir veya daha fazla yöntemler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4d39c-114">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="4d39c-115">Aşağıdaki örnekte, `where` yan tümcesinin Aralık değişkeninin geçerli değerini çift veya tek sayı olup olmadığını belirlemek için bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="4d39c-115">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="4d39c-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d39c-116">Remarks</span></span>  
 <span data-ttu-id="4d39c-117">`where` Yan tümcesi ise bir filtreleme mekanizması.</span><span class="sxs-lookup"><span data-stu-id="4d39c-117">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="4d39c-118">İlk veya son yan tümcesi olamaz dışında bir sorgu ifadesinde, neredeyse her yerden konumlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4d39c-118">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="4d39c-119">A `where` yan tümcesi, önce veya sonra görünebilir bir [grubu](../../../csharp/language-reference/keywords/group-clause.md) önce veya sonra gruplanmış olan kaynak öğeleri filtrelemek olmasına bağlı olarak yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4d39c-119">A `where` clause may appear either before or after a [group](../../../csharp/language-reference/keywords/group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>  
  
 <span data-ttu-id="4d39c-120">Belirtilen bir koşulu veri kaynağındaki öğeleri için geçerli değilse, bir derleme zamanı hatası neden olur.</span><span class="sxs-lookup"><span data-stu-id="4d39c-120">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="4d39c-121">Bu güçlü tür tarafından sağlanan denetimi bir yararı, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4d39c-121">This is one benefit of the strong type-checking provided by [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span></span>  
  
 <span data-ttu-id="4d39c-122">Derleme zamanında `where` anahtar sözcüğü, bir çağrı biçimine dönüştürülür <xref:System.Linq.Enumerable.Where%2A> standart sorgu işleci yöntem.</span><span class="sxs-lookup"><span data-stu-id="4d39c-122">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d39c-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d39c-123">See Also</span></span>

- [<span data-ttu-id="4d39c-124">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="4d39c-124">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
- [<span data-ttu-id="4d39c-125">from yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="4d39c-125">from clause</span></span>](../../../csharp/language-reference/keywords/from-clause.md)  
- [<span data-ttu-id="4d39c-126">select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="4d39c-126">select clause</span></span>](../../../csharp/language-reference/keywords/select-clause.md)  
- [<span data-ttu-id="4d39c-127">Verileri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="4d39c-127">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)  
- [<span data-ttu-id="4d39c-128">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="4d39c-128">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [<span data-ttu-id="4d39c-129">C#'de LINQ Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="4d39c-129">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
