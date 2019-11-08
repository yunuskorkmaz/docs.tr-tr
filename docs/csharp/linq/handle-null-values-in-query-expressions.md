---
title: Sorgu ifadelerinde null değerleri işle (LINQ ın C#)
description: İçindeki C#LINQ sorgu ifadelerinde null değerleri nasıl işleyeceğinizi öğrenin.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: c9a3aaec05fa029a8db66826bdcb4a1d106176e3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736862"
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="4f015-103">Sorgu ifadelerinde boş değerler işleme</span><span class="sxs-lookup"><span data-stu-id="4f015-103">Handle null values in query expressions</span></span>

<span data-ttu-id="4f015-104">Bu örnek, kaynak koleksiyonlarında olası null değerlerin nasıl işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f015-104">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="4f015-105"><xref:System.Collections.Generic.IEnumerable%601> gibi bir nesne koleksiyonu, değeri [null](../language-reference/keywords/null.md)olan öğeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4f015-105">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="4f015-106">Bir kaynak koleksiyon null ise veya değeri null olan bir öğe içeriyorsa ve sorgunuz null değerleri işlemezse, sorguyu yürüttüğünüzde bir <xref:System.NullReferenceException> atılır.</span><span class="sxs-lookup"><span data-stu-id="4f015-106">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>

## <a name="example"></a><span data-ttu-id="4f015-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f015-107">Example</span></span>

<span data-ttu-id="4f015-108">Aşağıdaki örnekte gösterildiği gibi, bir null başvurusu özel durumunun önüne geçmek için savunmaya büyük bir kod oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4f015-108">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

<span data-ttu-id="4f015-109">Önceki örnekte, `where` yan tümcesi Kategoriler dizisindeki tüm null öğeleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="4f015-109">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="4f015-110">Bu teknik, JOIN yan tümcesindeki null denetiminden bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="4f015-110">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="4f015-111">Bu örnekte null değeri olan koşullu ifade, `Products.CategoryID` `Nullable<int>`için toplu olan `int?` türünde olduğundan işe yarar.</span><span class="sxs-lookup"><span data-stu-id="4f015-111">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>

## <a name="example"></a><span data-ttu-id="4f015-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f015-112">Example</span></span>

<span data-ttu-id="4f015-113">JOIN yan tümcesinde, karşılaştırma anahtarlarından yalnızca biri null yapılabilir bir değer türü ise, diğerini sorgu ifadesinde null yapılabilen bir türe çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f015-113">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable type in the query expression.</span></span> <span data-ttu-id="4f015-114">Aşağıdaki örnekte, `EmployeeID` `int?`türünde değerler içeren bir sütun olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="4f015-114">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="4f015-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f015-115">See also</span></span>

- <xref:System.Nullable%601>
- [<span data-ttu-id="4f015-116">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="4f015-116">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="4f015-117">Null yapılabilir değer türleri</span><span class="sxs-lookup"><span data-stu-id="4f015-117">Nullable value types</span></span>](../language-reference/builtin-types/nullable-value-types.md)
