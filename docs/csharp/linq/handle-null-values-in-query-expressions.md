---
title: Sorgu ifadelerinde null değerlerini işleme (C#'da LINQ)
description: C#'daki LINQ sorgu ifadelerinde null değerleri nasıl işleyeceğinizi öğrenin.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 3da490b72bd518df7be8c14b34655af8c6f84929
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249311"
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="8f41f-103">Sorgu ifadelerinde boş değerler işleme</span><span class="sxs-lookup"><span data-stu-id="8f41f-103">Handle null values in query expressions</span></span>

<span data-ttu-id="8f41f-104">Bu örnek, kaynak koleksiyonlarındaki olası null değerlerin nasıl işleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f41f-104">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="8f41f-105">Bir nesne koleksiyonu <xref:System.Collections.Generic.IEnumerable%601> gibi değeri [null](../language-reference/keywords/null.md)olan öğeler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8f41f-105">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="8f41f-106">Kaynak koleksiyonu null ise veya değeri null olan bir öğe içeriyorsa ve <xref:System.NullReferenceException> sorgunuz null değerleri işlemiyorsa, sorguyu yürüttüğünüzde bir öğe atılır.</span><span class="sxs-lookup"><span data-stu-id="8f41f-106">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>

## <a name="example"></a><span data-ttu-id="8f41f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f41f-107">Example</span></span>

<span data-ttu-id="8f41f-108">Aşağıdaki örnekte gösterildiği gibi geçersiz bir başvuru özel durum önlemek için savunma kodlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8f41f-108">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

<span data-ttu-id="8f41f-109">Önceki örnekte, `where` yan tümce, kategoriler dizisindeki tüm null öğeleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="8f41f-109">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="8f41f-110">Bu teknik, birleştirme yan tümcesindeki null denetiminden bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="8f41f-110">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="8f41f-111">Bu örnekte null olan koşullu `Products.CategoryID` ifade `int?` çalışır, çünkü `Nullable<int>`stenobun kısaltmasi.</span><span class="sxs-lookup"><span data-stu-id="8f41f-111">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>

## <a name="example"></a><span data-ttu-id="8f41f-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f41f-112">Example</span></span>

<span data-ttu-id="8f41f-113">Birleştirme yan tümcesinde, karşılaştırma anahtarlarından yalnızca biri geçersiz bir değer türüyse, diğerini sorgu ifadesinde boşdeğer türüne atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f41f-113">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable value type in the query expression.</span></span> <span data-ttu-id="8f41f-114">Aşağıdaki örnekte, tür `EmployeeID` `int?`değerlerini içeren bir sütun olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="8f41f-114">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="8f41f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f41f-115">See also</span></span>

- <xref:System.Nullable%601>
- [<span data-ttu-id="8f41f-116">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="8f41f-116">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="8f41f-117">Nullable değer türleri</span><span class="sxs-lookup"><span data-stu-id="8f41f-117">Nullable value types</span></span>](../language-reference/builtin-types/nullable-value-types.md)
