---
title: (C# üzerinde LINQ) sorgu ifadelerinde boş değerler işleme
description: C# LINQ Sorgu ifadelerinde boş değerler işleme hakkında bilgi edinin.
ms.date: 12/1/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 2c477ef371dbb424c72fb9d34948760b7e3f5609
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43561385"
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="be3cd-103">Sorgu ifadelerinde boş değerler işleme</span><span class="sxs-lookup"><span data-stu-id="be3cd-103">Handle null values in query expressions</span></span>

<span data-ttu-id="be3cd-104">Bu örnek, kaynak koleksiyonları olası null değerlerin nasıl ele alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="be3cd-104">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="be3cd-105">Bir nesne koleksiyonu gibi bir <xref:System.Collections.Generic.IEnumerable%601> değeri öğeleri içerebilir [null](../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="be3cd-105">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="be3cd-106">Bir kaynak koleksiyonu null veya değeri null olan bir öğe içeriyor ve sorgunuzu null değerler işlemez bir <xref:System.NullReferenceException> sorgu yürütülürken oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="be3cd-106">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>

## <a name="example"></a><span data-ttu-id="be3cd-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="be3cd-107">Example</span></span>

<span data-ttu-id="be3cd-108">Aşağıdaki örnekte gösterildiği gibi bir null başvurusu özel durumu önlemek için biçimde geliştirmelisiniz kod yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="be3cd-108">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

<span data-ttu-id="be3cd-109">Önceki örnekte, `where` yan tümcesi filtreler kategoriler dizisi null tüm öğeler kullanıma.</span><span class="sxs-lookup"><span data-stu-id="be3cd-109">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="be3cd-110">Bu teknik, null denetimi JOIN yan tümcesi içinde bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="be3cd-110">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="be3cd-111">Bu örnekte null koşullu ifadeyle çalışır çünkü `Products.CategoryID` türünde `int?` için Toplu özellik olduğu `Nullable<int>`.</span><span class="sxs-lookup"><span data-stu-id="be3cd-111">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>

## <a name="example"></a><span data-ttu-id="be3cd-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="be3cd-112">Example</span></span>

<span data-ttu-id="be3cd-113">Karşılaştırma anahtarlarından birini bir boş değer atanabilir değer türü olduğundan, yalnızca bir JOIN yan tümcesinde, boş değer atanabilir bir tür diğer sorgu ifadesinde çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be3cd-113">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable type in the query expression.</span></span> <span data-ttu-id="be3cd-114">Aşağıdaki örnekte, varsayımında `EmployeeID` türü değerleri içeren bir sütun `int?`:</span><span class="sxs-lookup"><span data-stu-id="be3cd-114">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="be3cd-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be3cd-115">See also</span></span>

- <xref:System.Nullable%601>  
- [<span data-ttu-id="be3cd-116">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="be3cd-116">Language Integrated Query (LINQ)</span></span>](index.md)  
- [<span data-ttu-id="be3cd-117">Boş değer atanabilir türler</span><span class="sxs-lookup"><span data-stu-id="be3cd-117">Nullable types</span></span>](../programming-guide/nullable-types/index.md)  
