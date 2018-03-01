---
title: "where tümcesi (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0324346ee5e214bf467fcb522ef781c91fa1b76f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="a1f62-102">where tümcesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a1f62-102">where clause (C# Reference)</span></span>
<span data-ttu-id="a1f62-103">`where` Yan tümcesi, veri kaynağından hangi öğelerin sorgu ifadesinde döndürülecek belirtmek için bir sorgu ifadesinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1f62-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="a1f62-104">Bir Boole koşulu geçerlidir (*koşulu*) (aralık değişkeni tarafından başvurulan) her kaynak öğesine ve bunlar belirtilen koşulu olduğu true döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1f62-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="a1f62-105">Tek bir sorgu ifade birden çok içerebilir `where` yan tümceleri ve tek bir yan tümce birden çok koşul alt ifadelerin içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a1f62-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1f62-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a1f62-106">Example</span></span>  
 <span data-ttu-id="a1f62-107">Aşağıdaki örnekte, `where` en az beş olanlar dışındaki tüm sayılar filtreleyen yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="a1f62-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="a1f62-108">Kaldırırsanız `where` yan tümcesi, veri kaynağından gelen tüm sayıları döndürülen.</span><span class="sxs-lookup"><span data-stu-id="a1f62-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="a1f62-109">İfade `num < 5` her öğeye uygulanan koşul.</span><span class="sxs-lookup"><span data-stu-id="a1f62-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="a1f62-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="a1f62-110">Example</span></span>  
 <span data-ttu-id="a1f62-111">Tek bir `where` yan tümcesi sayıda koşulları gerektiği gibi kullanarak belirleyebileceğiniz [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) ve [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) işleçler.</span><span class="sxs-lookup"><span data-stu-id="a1f62-111">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) operators.</span></span> <span data-ttu-id="a1f62-112">Aşağıdaki örnekte, sorgunun yalnızca en az beş olan çift sayı seçmek için iki koşulları belirtir.</span><span class="sxs-lookup"><span data-stu-id="a1f62-112">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="a1f62-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="a1f62-113">Example</span></span>  
 <span data-ttu-id="a1f62-114">A `where` yan tümcesi, Boole değerleri döndüren bir veya daha fazla yöntemleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a1f62-114">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="a1f62-115">Aşağıdaki örnekte, `where` yan tümcesinin aralık değişkeni geçerli değeri çift veya tek olup olmadığını belirlemek için bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="a1f62-115">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="a1f62-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1f62-116">Remarks</span></span>  
 <span data-ttu-id="a1f62-117">`where` Yan tümcesi olan bir filtreleme mekanizması.</span><span class="sxs-lookup"><span data-stu-id="a1f62-117">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="a1f62-118">İlk veya son yan tümcesi olamaz dışında neredeyse her yerden sorgu ifadesinde yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a1f62-118">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="a1f62-119">A `where` yan tümcesi önce veya sonra görünebilir bir [grup](../../../csharp/language-reference/keywords/group-clause.md) önce veya sonra bunlar gruplandırılır kaynağı öğeleri filtrelemek sahip bağlı olarak yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="a1f62-119">A `where` clause may appear either before or after a [group](../../../csharp/language-reference/keywords/group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>  
  
 <span data-ttu-id="a1f62-120">Belirtilen önerme veri kaynağındaki öğeler için geçerli değilse, derleme zamanı hata neden olur.</span><span class="sxs-lookup"><span data-stu-id="a1f62-120">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="a1f62-121">Tanımlayıcı türü tarafından sağlanan denetimi bir yararı budur [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a1f62-121">This is one benefit of the strong type-checking provided by [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span></span>  
  
 <span data-ttu-id="a1f62-122">Derleme zamanında `where` anahtar sözcüğü bir çağrı biçimine dönüştürülür <xref:System.Linq.Enumerable.Where%2A> standart sorgu işleci yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a1f62-122">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f62-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a1f62-123">See Also</span></span>  
 [<span data-ttu-id="a1f62-124">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="a1f62-124">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="a1f62-125">from yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="a1f62-125">from clause</span></span>](../../../csharp/language-reference/keywords/from-clause.md)  
 [<span data-ttu-id="a1f62-126">select tümcesi</span><span class="sxs-lookup"><span data-stu-id="a1f62-126">select clause</span></span>](../../../csharp/language-reference/keywords/select-clause.md)  
 [<span data-ttu-id="a1f62-127">Verileri filtreleme</span><span class="sxs-lookup"><span data-stu-id="a1f62-127">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)  
 [<span data-ttu-id="a1f62-128">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="a1f62-128">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="a1f62-129">C# üzerinde LINQ ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="a1f62-129">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
