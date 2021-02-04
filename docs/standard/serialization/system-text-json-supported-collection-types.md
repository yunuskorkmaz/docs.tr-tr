---
title: İçinde desteklenen koleksiyon türleri System.Text.Json
description: Ad alanındaki API 'Ler tarafından serileştirme için hangi koleksiyon türlerinin desteklendiğini öğrenin System.Text.Json .
ms.date: 02/01/2021
no-loc:
- System.Text.Json
ms.topic: reference
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 5a5016c70e86124510a4778aafb9fb14b1890add
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99547661"
---
# <a name="supported-collection-types-in-systemtextjson"></a><span data-ttu-id="8e808-103">İçinde desteklenen koleksiyon türleri System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="8e808-103">Supported collection types in System.Text.Json</span></span>

<span data-ttu-id="8e808-104">Bu makale serileştirme ve seri durumundan çıkarma için hangi koleksiyonların desteklendiği hakkında genel bakış sunar.</span><span class="sxs-lookup"><span data-stu-id="8e808-104">This article gives an overview of which collections are supported for serialization and deserialization.</span></span> <span data-ttu-id="8e808-105"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> , serileştirme için bir koleksiyon türünü destekler:</span><span class="sxs-lookup"><span data-stu-id="8e808-105"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> supports a collection type for serialization if it:</span></span>

* <span data-ttu-id="8e808-106">Türetiliyor <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="8e808-106">Derives from <xref:System.Collections.IEnumerable>.</span></span>
* <span data-ttu-id="8e808-107">Seri hale getirilebilir öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="8e808-107">Contains elements that are serializable.</span></span>

<span data-ttu-id="8e808-108">Seri hale getirici <xref:System.Collections.IEnumerable.GetEnumerator> yöntemini çağırır ve öğeleri yazar.</span><span class="sxs-lookup"><span data-stu-id="8e808-108">The serializer calls the <xref:System.Collections.IEnumerable.GetEnumerator> method, and writes the elements.</span></span>

<span data-ttu-id="8e808-109">Seri durumdan çıkarma daha karmaşıktır ve bazı koleksiyon türleri için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="8e808-109">Deserialization is more complicated and is not supported for some collection types.</span></span>

<span data-ttu-id="8e808-110">Aşağıdaki bölümler ad alanına göre düzenlenmiştir ve serileştirme ve seri durumdan çıkarma için hangi türlerin desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8e808-110">The following sections are organized by namespace and show which types are supported for serialization and deserialization.</span></span>

## <a name="systemarray-namespace"></a><span data-ttu-id="8e808-111">System. Array ad alanı</span><span class="sxs-lookup"><span data-stu-id="8e808-111">System.Array namespace</span></span>

| <span data-ttu-id="8e808-112">Tür</span><span class="sxs-lookup"><span data-stu-id="8e808-112">Type</span></span>                                                                                            | <span data-ttu-id="8e808-113">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8e808-113">Serialization</span></span> | <span data-ttu-id="8e808-114">Seri</span><span class="sxs-lookup"><span data-stu-id="8e808-114">Deserialization</span></span> |
|-------------------------------------------------------------------------------------------------|---------------|-----------------|
| [<span data-ttu-id="8e808-115">Tek boyutlu diziler</span><span class="sxs-lookup"><span data-stu-id="8e808-115">Single-dimensional arrays</span></span>](../../csharp/programming-guide/arrays/single-dimensional-arrays.md) | <span data-ttu-id="8e808-116">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-116">✔️</span></span>           | <span data-ttu-id="8e808-117">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-117">✔️</span></span>              |
| [<span data-ttu-id="8e808-118">Çok boyutlu diziler</span><span class="sxs-lookup"><span data-stu-id="8e808-118">Multi-dimensional arrays</span></span>](../../csharp/programming-guide/arrays/multidimensional-arrays.md)    | ❌           | ❌              |
| [<span data-ttu-id="8e808-119">Sivri diziler</span><span class="sxs-lookup"><span data-stu-id="8e808-119">Jagged arrays</span></span>](../../csharp/programming-guide/arrays/jagged-arrays.md)                         | <span data-ttu-id="8e808-120">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-120">✔️</span></span>           | <span data-ttu-id="8e808-121">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-121">✔️</span></span>              |

## <a name="systemcollections-namespace"></a><span data-ttu-id="8e808-122">System. Collections ad alanı</span><span class="sxs-lookup"><span data-stu-id="8e808-122">System.Collections namespace</span></span>

| <span data-ttu-id="8e808-123">Tür</span><span class="sxs-lookup"><span data-stu-id="8e808-123">Type</span></span>                                      | <span data-ttu-id="8e808-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8e808-124">Serialization</span></span> | <span data-ttu-id="8e808-125">Seri</span><span class="sxs-lookup"><span data-stu-id="8e808-125">Deserialization</span></span> |
|-------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ArrayList>       | <span data-ttu-id="8e808-126">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-126">✔️</span></span>           | <span data-ttu-id="8e808-127">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-127">✔️</span></span>              |
| <xref:System.Collections.BitArray>        | <span data-ttu-id="8e808-128">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-128">✔️</span></span>           | ❌              |
| <xref:System.Collections.DictionaryEntry> | <span data-ttu-id="8e808-129">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-129">✔️</span></span>           | <span data-ttu-id="8e808-130">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-130">✔️</span></span>              |
| <xref:System.Collections.Hashtable>       | <span data-ttu-id="8e808-131">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-131">✔️</span></span>           | <span data-ttu-id="8e808-132">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-132">✔️</span></span>              |
| <xref:System.Collections.Queue>           | <span data-ttu-id="8e808-133">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-133">✔️</span></span>           | <span data-ttu-id="8e808-134">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-134">✔️</span></span>              |
| <xref:System.Collections.SortedList>      | <span data-ttu-id="8e808-135">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-135">✔️</span></span>           | <span data-ttu-id="8e808-136">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-136">✔️</span></span>              |
| <xref:System.Collections.Stack>           | <span data-ttu-id="8e808-137">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-137">✔️</span></span>           | <span data-ttu-id="8e808-138">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-138">✔️</span></span>              |
| <xref:System.Collections.ICollection>     | <span data-ttu-id="8e808-139">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-139">✔️</span></span>           | <span data-ttu-id="8e808-140">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-140">✔️</span></span>              |
| <xref:System.Collections.IDictionary>     | <span data-ttu-id="8e808-141">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-141">✔️</span></span>           | <span data-ttu-id="8e808-142">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-142">✔️</span></span>              |
| <xref:System.Collections.IEnumerable>     | <span data-ttu-id="8e808-143">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-143">✔️</span></span>           | <span data-ttu-id="8e808-144">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-144">✔️</span></span>              |
| <xref:System.Collections.IList>           | <span data-ttu-id="8e808-145">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-145">✔️</span></span>           | <span data-ttu-id="8e808-146">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-146">✔️</span></span>              |

## <a name="systemcollectionsgeneric-namespace"></a><span data-ttu-id="8e808-147">System. Collections. Generic ad alanı</span><span class="sxs-lookup"><span data-stu-id="8e808-147">System.Collections.Generic namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="8e808-148">Tür</span><span class="sxs-lookup"><span data-stu-id="8e808-148">Type</span></span>                                                      | <span data-ttu-id="8e808-149">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8e808-149">Serialization</span></span> | <span data-ttu-id="8e808-150">Seri</span><span class="sxs-lookup"><span data-stu-id="8e808-150">Deserialization</span></span> |
|-----------------------------------------------------------|---------------|-----------------|
| <span data-ttu-id="8e808-151"><xref:System.Collections.Generic.Dictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="8e808-151"><xref:System.Collections.Generic.Dictionary%602> \*</span></span>       | <span data-ttu-id="8e808-152">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-152">✔️</span></span>           | <span data-ttu-id="8e808-153">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-153">✔️</span></span>              |
| <xref:System.Collections.Generic.HashSet%601>             | <span data-ttu-id="8e808-154">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-154">✔️</span></span>           | <span data-ttu-id="8e808-155">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-155">✔️</span></span>              |
| <xref:System.Collections.Generic.KeyValuePair%602>        | <span data-ttu-id="8e808-156">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-156">✔️</span></span>           | <span data-ttu-id="8e808-157">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-157">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedList%601>          | <span data-ttu-id="8e808-158">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-158">✔️</span></span>           | <span data-ttu-id="8e808-159">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-159">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedListNode%601>      | <span data-ttu-id="8e808-160">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-160">✔️</span></span>           | ❌              |
| <xref:System.Collections.Generic.List%601>                | <span data-ttu-id="8e808-161">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-161">✔️</span></span>           | <span data-ttu-id="8e808-162">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-162">✔️</span></span>              |
| <xref:System.Collections.Generic.Queue%601>               | <span data-ttu-id="8e808-163">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-163">✔️</span></span>           | <span data-ttu-id="8e808-164">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-164">✔️</span></span>              |
| <span data-ttu-id="8e808-165"><xref:System.Collections.Generic.SortedDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="8e808-165"><xref:System.Collections.Generic.SortedDictionary%602> \*</span></span> | <span data-ttu-id="8e808-166">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-166">✔️</span></span>           | <span data-ttu-id="8e808-167">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-167">✔️</span></span>              |
| <span data-ttu-id="8e808-168"><xref:System.Collections.Generic.SortedList%602> \*</span><span class="sxs-lookup"><span data-stu-id="8e808-168"><xref:System.Collections.Generic.SortedList%602> \*</span></span>       | <span data-ttu-id="8e808-169">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-169">✔️</span></span>           | <span data-ttu-id="8e808-170">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-170">✔️</span></span>              |
| <xref:System.Collections.Generic.SortedSet%601>           | <span data-ttu-id="8e808-171">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-171">✔️</span></span>           | <span data-ttu-id="8e808-172">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-172">✔️</span></span>              |
| <xref:System.Collections.Generic.Stack%601>               | <span data-ttu-id="8e808-173">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-173">✔️</span></span>           | <span data-ttu-id="8e808-174">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-174">✔️</span></span>              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>    | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>         | <span data-ttu-id="8e808-175">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-175">✔️</span></span>           | <span data-ttu-id="8e808-176">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-176">✔️</span></span>              |
| <span data-ttu-id="8e808-177"><xref:System.Collections.Generic.IDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="8e808-177"><xref:System.Collections.Generic.IDictionary%602> \*</span></span>      | <span data-ttu-id="8e808-178">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-178">✔️</span></span>           | <span data-ttu-id="8e808-179">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-179">✔️</span></span>              |
| <xref:System.Collections.Generic.IEnumerable%601>         | <span data-ttu-id="8e808-180">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-180">✔️</span></span>           | <span data-ttu-id="8e808-181">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-181">✔️</span></span>              |
| <xref:System.Collections.Generic.IList%601>               | <span data-ttu-id="8e808-182">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-182">✔️</span></span>           | <span data-ttu-id="8e808-183">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-183">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601> | <span data-ttu-id="8e808-184">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-184">✔️</span></span>           | <span data-ttu-id="8e808-185">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-185">✔️</span></span>              |
| <span data-ttu-id="8e808-186"><xref:System.Collections.Generic.IReadOnlyDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="8e808-186"><xref:System.Collections.Generic.IReadOnlyDictionary%602> \*</span></span> | <span data-ttu-id="8e808-187">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-187">✔️</span></span>        | <span data-ttu-id="8e808-188">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-188">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyList%601>       | <span data-ttu-id="8e808-189">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-189">✔️</span></span>           | <span data-ttu-id="8e808-190">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-190">✔️</span></span>              |
| <xref:System.Collections.Generic.ISet%601>                | <span data-ttu-id="8e808-191">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-191">✔️</span></span>           | <span data-ttu-id="8e808-192">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-192">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="8e808-193">Tür</span><span class="sxs-lookup"><span data-stu-id="8e808-193">Type</span></span>                                                                                            | <span data-ttu-id="8e808-194">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8e808-194">Serialization</span></span> | <span data-ttu-id="8e808-195">Seri</span><span class="sxs-lookup"><span data-stu-id="8e808-195">Deserialization</span></span> |
|-------------------------------------------------------------------------------------------------|---------------|-----------------|
| <span data-ttu-id="8e808-196">[Sözlük \<string, TValue> ](xref:System.Collections.Generic.Dictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="8e808-196">[Dictionary\<string, TValue>](xref:System.Collections.Generic.Dictionary%602) \*</span></span>                | <span data-ttu-id="8e808-197">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-197">✔️</span></span>           | <span data-ttu-id="8e808-198">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-198">✔️</span></span>              |
| <xref:System.Collections.Generic.HashSet%601>                                                   | <span data-ttu-id="8e808-199">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-199">✔️</span></span>           | <span data-ttu-id="8e808-200">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-200">✔️</span></span>              |
| <xref:System.Collections.Generic.KeyValuePair%602>                                              | <span data-ttu-id="8e808-201">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-201">✔️</span></span>           | <span data-ttu-id="8e808-202">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-202">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedList%601>                                                | <span data-ttu-id="8e808-203">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-203">✔️</span></span>           | <span data-ttu-id="8e808-204">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-204">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedListNode%601>                                            | <span data-ttu-id="8e808-205">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-205">✔️</span></span>           | ❌              |
| <xref:System.Collections.Generic.List%601>                                                      | <span data-ttu-id="8e808-206">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-206">✔️</span></span>           | <span data-ttu-id="8e808-207">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-207">✔️</span></span>              |
| <xref:System.Collections.Generic.Queue%601>                                                     | <span data-ttu-id="8e808-208">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-208">✔️</span></span>           | <span data-ttu-id="8e808-209">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-209">✔️</span></span>              |
| <span data-ttu-id="8e808-210">[SortedDictionary \<string, TValue> ](xref:System.Collections.Generic.SortedDictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="8e808-210">[SortedDictionary\<string, TValue>](xref:System.Collections.Generic.SortedDictionary%602) \*</span></span>    | <span data-ttu-id="8e808-211">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-211">✔️</span></span>           | <span data-ttu-id="8e808-212">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-212">✔️</span></span>              |
| <span data-ttu-id="8e808-213">[SortedList \<string, TValue> ](xref:System.Collections.Generic.SortedList%602)\*</span><span class="sxs-lookup"><span data-stu-id="8e808-213">[SortedList\<string, TValue>](xref:System.Collections.Generic.SortedList%602) \*</span></span>                | <span data-ttu-id="8e808-214">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-214">✔️</span></span>           | <span data-ttu-id="8e808-215">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-215">✔️</span></span>              |
| <xref:System.Collections.Generic.SortedSet%601>                                                 | <span data-ttu-id="8e808-216">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-216">✔️</span></span>           | <span data-ttu-id="8e808-217">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-217">✔️</span></span>              |
| <xref:System.Collections.Generic.Stack%601>                                                     | <span data-ttu-id="8e808-218">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-218">✔️</span></span>           | <span data-ttu-id="8e808-219">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-219">✔️</span></span>              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>                                          | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>                                               | <span data-ttu-id="8e808-220">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-220">✔️</span></span>           | <span data-ttu-id="8e808-221">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-221">✔️</span></span>              |
| <span data-ttu-id="8e808-222">[IDictionary \<string, TValue> ](xref:System.Collections.Generic.IDictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="8e808-222">[IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \*</span></span>              | <span data-ttu-id="8e808-223">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-223">✔️</span></span>           | <span data-ttu-id="8e808-224">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-224">✔️</span></span>              |
| <xref:System.Collections.Generic.IEnumerable%601>                                               | <span data-ttu-id="8e808-225">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-225">✔️</span></span>           | <span data-ttu-id="8e808-226">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-226">✔️</span></span>              |
| <xref:System.Collections.Generic.IList%601>                                                     | <span data-ttu-id="8e808-227">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-227">✔️</span></span>           | <span data-ttu-id="8e808-228">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-228">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601>                                       | <span data-ttu-id="8e808-229">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-229">✔️</span></span>           | <span data-ttu-id="8e808-230">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-230">✔️</span></span>              |
| <span data-ttu-id="8e808-231">[IReadOnlyDictionary \<string, TValue> ](xref:System.Collections.Generic.IReadOnlyDictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="8e808-231">[IReadOnlyDictionary\<string, TValue>](xref:System.Collections.Generic.IReadOnlyDictionary%602) \*</span></span> | <span data-ttu-id="8e808-232">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-232">✔️</span></span>        | <span data-ttu-id="8e808-233">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-233">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyList%601>                                             | <span data-ttu-id="8e808-234">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-234">✔️</span></span>           | <span data-ttu-id="8e808-235">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-235">✔️</span></span>              |
| <xref:System.Collections.Generic.ISet%601>                                                      | <span data-ttu-id="8e808-236">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-236">✔️</span></span>           | <span data-ttu-id="8e808-237">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-237">✔️</span></span>              |

::: zone-end

<span data-ttu-id="8e808-238">\* Bkz. [desteklenen anahtar türleri](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="8e808-238">\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsimmutable-namespace"></a><span data-ttu-id="8e808-239">System. Collections. sabit ad alanı</span><span class="sxs-lookup"><span data-stu-id="8e808-239">System.Collections.Immutable namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="8e808-240">Tür</span><span class="sxs-lookup"><span data-stu-id="8e808-240">Type</span></span>                                                              | <span data-ttu-id="8e808-241">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8e808-241">Serialization</span></span> | <span data-ttu-id="8e808-242">Seri</span><span class="sxs-lookup"><span data-stu-id="8e808-242">Deserialization</span></span> |
|-------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>            | <span data-ttu-id="8e808-243">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-243">✔️</span></span>           | <span data-ttu-id="8e808-244">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-244">✔️</span></span>              |
| <span data-ttu-id="8e808-245"><xref:System.Collections.Immutable.ImmutableDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="8e808-245"><xref:System.Collections.Immutable.ImmutableDictionary%602> \*\*</span></span>  | <span data-ttu-id="8e808-246">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-246">✔️</span></span>           | <span data-ttu-id="8e808-247">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-247">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>          | <span data-ttu-id="8e808-248">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-248">✔️</span></span>           | <span data-ttu-id="8e808-249">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-249">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | <span data-ttu-id="8e808-250">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-250">✔️</span></span>           | <span data-ttu-id="8e808-251">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-251">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>            | <span data-ttu-id="8e808-252">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-252">✔️</span></span>           | <span data-ttu-id="8e808-253">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-253">✔️</span></span>              |
| <span data-ttu-id="8e808-254"><xref:System.Collections.Immutable.ImmutableSortedDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="8e808-254"><xref:System.Collections.Immutable.ImmutableSortedDictionary%602> \*\*</span></span> | <span data-ttu-id="8e808-255">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-255">✔️</span></span>      | <span data-ttu-id="8e808-256">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-256">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>        | <span data-ttu-id="8e808-257">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-257">✔️</span></span>           | <span data-ttu-id="8e808-258">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-258">✔️</span></span>              |
| <span data-ttu-id="8e808-259"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8e808-259"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span></span>         | <span data-ttu-id="8e808-260">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-260">✔️</span></span>           | <span data-ttu-id="8e808-261">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-261">✔️</span></span>              |
| <span data-ttu-id="8e808-262"><xref:System.Collections.Immutable.IImmutableDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="8e808-262"><xref:System.Collections.Immutable.IImmutableDictionary%602> \*\*</span></span> | <span data-ttu-id="8e808-263">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-263">✔️</span></span>           | <span data-ttu-id="8e808-264">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-264">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | <span data-ttu-id="8e808-265">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-265">✔️</span></span>           | <span data-ttu-id="8e808-266">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-266">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>           | <span data-ttu-id="8e808-267">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-267">✔️</span></span>           | <span data-ttu-id="8e808-268">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-268">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableSet%601>             | <span data-ttu-id="8e808-269">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-269">✔️</span></span>           | <span data-ttu-id="8e808-270">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-270">✔️</span></span>              |
| <span data-ttu-id="8e808-271"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8e808-271"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span></span>        | <span data-ttu-id="8e808-272">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-272">✔️</span></span>           | <span data-ttu-id="8e808-273">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-273">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="8e808-274">Tür</span><span class="sxs-lookup"><span data-stu-id="8e808-274">Type</span></span>                                                                                                          | <span data-ttu-id="8e808-275">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8e808-275">Serialization</span></span> | <span data-ttu-id="8e808-276">Seri</span><span class="sxs-lookup"><span data-stu-id="8e808-276">Deserialization</span></span> |
|---------------------------------------------------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>                                                        | <span data-ttu-id="8e808-277">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-277">✔️</span></span>           | <span data-ttu-id="8e808-278">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-278">✔️</span></span>              |
| <span data-ttu-id="8e808-279">[ImmutableDictionary \<string, TValue> ](xref:System.Collections.Immutable.ImmutableDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="8e808-279">[ImmutableDictionary\<string, TValue>](xref:System.Collections.Immutable.ImmutableDictionary%602) \*\*</span></span>        | <span data-ttu-id="8e808-280">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-280">✔️</span></span>           | <span data-ttu-id="8e808-281">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-281">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>                                                      | <span data-ttu-id="8e808-282">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-282">✔️</span></span>           | <span data-ttu-id="8e808-283">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-283">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | <span data-ttu-id="8e808-284">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-284">✔️</span></span>           | <span data-ttu-id="8e808-285">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-285">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>                                                        | <span data-ttu-id="8e808-286">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-286">✔️</span></span>           | <span data-ttu-id="8e808-287">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-287">✔️</span></span>              |
| <span data-ttu-id="8e808-288">[ImmutableSortedDictionary \<string, TValue> ](xref:System.Collections.Immutable.ImmutableSortedDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="8e808-288">[ImmutableSortedDictionary\<string, TValue>](xref:System.Collections.Immutable.ImmutableSortedDictionary%602) \*\*</span></span>| <span data-ttu-id="8e808-289">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-289">✔️</span></span>       | <span data-ttu-id="8e808-290">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-290">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>                                                    | <span data-ttu-id="8e808-291">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-291">✔️</span></span>           | <span data-ttu-id="8e808-292">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-292">✔️</span></span>              |
| <span data-ttu-id="8e808-293"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8e808-293"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span></span>                                                     | <span data-ttu-id="8e808-294">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-294">✔️</span></span>           | <span data-ttu-id="8e808-295">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-295">✔️</span></span>              |
| <span data-ttu-id="8e808-296">[IImmutableDictionary \<string, TValue> ](xref:System.Collections.Immutable.IImmutableDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="8e808-296">[IImmutableDictionary\<string, TValue>](xref:System.Collections.Immutable.IImmutableDictionary%602) \*\*</span></span>      | <span data-ttu-id="8e808-297">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-297">✔️</span></span>           | <span data-ttu-id="8e808-298">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-298">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | <span data-ttu-id="8e808-299">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-299">✔️</span></span>           | <span data-ttu-id="8e808-300">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-300">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>                                                       | <span data-ttu-id="8e808-301">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-301">✔️</span></span>           | <span data-ttu-id="8e808-302">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-302">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableSet%601>                                                         | <span data-ttu-id="8e808-303">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-303">✔️</span></span>           | <span data-ttu-id="8e808-304">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-304">✔️</span></span>              |
| <span data-ttu-id="8e808-305"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8e808-305"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span></span>                                                    | <span data-ttu-id="8e808-306">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-306">✔️</span></span>           | <span data-ttu-id="8e808-307">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-307">✔️</span></span>              |

::: zone-end

<span data-ttu-id="8e808-308">\*Bkz. [yığın \<T> için gidiş yolculuğu destekleme](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="8e808-308">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

<span data-ttu-id="8e808-309">\*\* Bkz. [desteklenen anahtar türleri](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="8e808-309">\*\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsspecialized-namespace"></a><span data-ttu-id="8e808-310">System. Collections. özelleşmiş ad alanı</span><span class="sxs-lookup"><span data-stu-id="8e808-310">System.Collections.Specialized namespace</span></span>

| <span data-ttu-id="8e808-311">Tür</span><span class="sxs-lookup"><span data-stu-id="8e808-311">Type</span></span>                                                      | <span data-ttu-id="8e808-312">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8e808-312">Serialization</span></span> | <span data-ttu-id="8e808-313">Seri</span><span class="sxs-lookup"><span data-stu-id="8e808-313">Deserialization</span></span> |
|-----------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Specialized.BitVector32>         | <span data-ttu-id="8e808-314">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-314">✔️</span></span>           | ❌\*            |
| <xref:System.Collections.Specialized.HybridDictionary>    | <span data-ttu-id="8e808-315">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-315">✔️</span></span>           | <span data-ttu-id="8e808-316">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-316">✔️</span></span>              |
| <xref:System.Collections.Specialized.IOrderedDictionary>  | <span data-ttu-id="8e808-317">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-317">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.ListDictionary>      | <span data-ttu-id="8e808-318">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-318">✔️</span></span>           | <span data-ttu-id="8e808-319">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-319">✔️</span></span>              |
| <xref:System.Collections.Specialized.StringCollection>    | <span data-ttu-id="8e808-320">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-320">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.StringDictionary>    | <span data-ttu-id="8e808-321">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-321">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.NameValueCollection> | <span data-ttu-id="8e808-322">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-322">✔️</span></span>           | ❌              |

<span data-ttu-id="8e808-323">\*<xref:System.Collections.Specialized.BitVector32>Seri durumdan kaldırıldığında, <xref:System.Collections.Specialized.BitVector32.Data> özelliği ortak bir ayarlayıcısı olmadığından atlanır.</span><span class="sxs-lookup"><span data-stu-id="8e808-323">\* When <xref:System.Collections.Specialized.BitVector32> is deserialized, the <xref:System.Collections.Specialized.BitVector32.Data> property is skipped because it doesn't have a public setter.</span></span> <span data-ttu-id="8e808-324">Özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="8e808-324">No exception is thrown.</span></span>

## <a name="systemcollectionsconcurrent-namespace"></a><span data-ttu-id="8e808-325">System. Collections. eşzamanlı ad alanı</span><span class="sxs-lookup"><span data-stu-id="8e808-325">System.Collections.Concurrent namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="8e808-326">Tür</span><span class="sxs-lookup"><span data-stu-id="8e808-326">Type</span></span>                                                          | <span data-ttu-id="8e808-327">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8e808-327">Serialization</span></span> | <span data-ttu-id="8e808-328">Seri</span><span class="sxs-lookup"><span data-stu-id="8e808-328">Deserialization</span></span> |
|---------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601>   | <span data-ttu-id="8e808-329">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-329">✔️</span></span>           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>        | <span data-ttu-id="8e808-330">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-330">✔️</span></span>           | ❌              |
| <span data-ttu-id="8e808-331"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="8e808-331"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> \*\*</span></span> | <span data-ttu-id="8e808-332">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-332">✔️</span></span>      | <span data-ttu-id="8e808-333">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-333">✔️</span></span>              |
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>      | <span data-ttu-id="8e808-334">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-334">✔️</span></span>           | <span data-ttu-id="8e808-335">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-335">✔️</span></span>              |
| <span data-ttu-id="8e808-336"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8e808-336"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>   | <span data-ttu-id="8e808-337">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-337">✔️</span></span>           | <span data-ttu-id="8e808-338">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-338">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="8e808-339">Tür</span><span class="sxs-lookup"><span data-stu-id="8e808-339">Type</span></span>                                                        | <span data-ttu-id="8e808-340">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8e808-340">Serialization</span></span> | <span data-ttu-id="8e808-341">Seri</span><span class="sxs-lookup"><span data-stu-id="8e808-341">Deserialization</span></span> |
|-------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601> | <span data-ttu-id="8e808-342">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-342">✔️</span></span>           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>      | <span data-ttu-id="8e808-343">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-343">✔️</span></span>           | ❌              |
| <span data-ttu-id="8e808-344">[ConcurrentDictionary \<string, TValue> ](xref:System.Collections.Concurrent.ConcurrentDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="8e808-344">[ConcurrentDictionary\<string, TValue>](xref:System.Collections.Concurrent.ConcurrentDictionary%602) \*\*</span></span> |<span data-ttu-id="8e808-345">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-345">✔️</span></span>|<span data-ttu-id="8e808-346">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-346">✔️</span></span>|
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>    | <span data-ttu-id="8e808-347">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-347">✔️</span></span>           | <span data-ttu-id="8e808-348">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-348">✔️</span></span>              |
| <span data-ttu-id="8e808-349"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8e808-349"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span> | <span data-ttu-id="8e808-350">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-350">✔️</span></span>           | <span data-ttu-id="8e808-351">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-351">✔️</span></span>              |

::: zone-end

<span data-ttu-id="8e808-352">\*Bkz. [yığın \<T> için gidiş yolculuğu destekleme](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="8e808-352">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

<span data-ttu-id="8e808-353">\*\* Bkz. [desteklenen anahtar türleri](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="8e808-353">\*\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsobjectmodel-namespace"></a><span data-ttu-id="8e808-354">System. Collections. ObjectModel Ad alanı</span><span class="sxs-lookup"><span data-stu-id="8e808-354">System.Collections.ObjectModel namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="8e808-355">Tür</span><span class="sxs-lookup"><span data-stu-id="8e808-355">Type</span></span>                                                           | <span data-ttu-id="8e808-356">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8e808-356">Serialization</span></span> | <span data-ttu-id="8e808-357">Seri</span><span class="sxs-lookup"><span data-stu-id="8e808-357">Deserialization</span></span> |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | <span data-ttu-id="8e808-358">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-358">✔️</span></span>            | <span data-ttu-id="8e808-359">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-359">✔️</span></span>             |
| <span data-ttu-id="8e808-360">[KeyedCollection \<string, TValue> ](xref:System.Collections.ObjectModel.KeyedCollection%602)\*</span><span class="sxs-lookup"><span data-stu-id="8e808-360">[KeyedCollection\<string, TValue>](xref:System.Collections.ObjectModel.KeyedCollection%602) \*</span></span> |<span data-ttu-id="8e808-361">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-361">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | <span data-ttu-id="8e808-362">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-362">✔️</span></span>            | <span data-ttu-id="8e808-363">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-363">✔️</span></span>             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | <span data-ttu-id="8e808-364">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-364">✔️</span></span>            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602>   | <span data-ttu-id="8e808-365">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-365">✔️</span></span>            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601> | <span data-ttu-id="8e808-366">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-366">✔️</span></span>    | ❌             |

<span data-ttu-id="8e808-367">\* Anahtarlar olmayanlar `string` desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="8e808-367">\* Non-`string` keys are not supported.</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="8e808-368">Tür</span><span class="sxs-lookup"><span data-stu-id="8e808-368">Type</span></span>                                                           | <span data-ttu-id="8e808-369">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8e808-369">Serialization</span></span> | <span data-ttu-id="8e808-370">Seri</span><span class="sxs-lookup"><span data-stu-id="8e808-370">Deserialization</span></span> |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | <span data-ttu-id="8e808-371">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-371">✔️</span></span>            | <span data-ttu-id="8e808-372">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-372">✔️</span></span>             |
| <span data-ttu-id="8e808-373">[KeyedCollection \<string, TValue> ](xref:System.Collections.ObjectModel.KeyedCollection%602)\*</span><span class="sxs-lookup"><span data-stu-id="8e808-373">[KeyedCollection\<string, TValue>](xref:System.Collections.ObjectModel.KeyedCollection%602) \*</span></span> |<span data-ttu-id="8e808-374">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-374">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | <span data-ttu-id="8e808-375">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-375">✔️</span></span>            | <span data-ttu-id="8e808-376">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-376">✔️</span></span>             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | <span data-ttu-id="8e808-377">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-377">✔️</span></span>            | ❌             |
| <span data-ttu-id="8e808-378">[ReadOnlyDictionary \<string, TValue> ](xref:System.Collections.ObjectModel.ReadOnlyDictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="8e808-378">[ReadOnlyDictionary\<string, TValue>](xref:System.Collections.ObjectModel.ReadOnlyDictionary%602) \*</span></span> |<span data-ttu-id="8e808-379">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-379">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601>| <span data-ttu-id="8e808-380">✔️</span><span class="sxs-lookup"><span data-stu-id="8e808-380">✔️</span></span>     | ❌             |

<span data-ttu-id="8e808-381">\* Bkz. [desteklenen anahtar türleri](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="8e808-381">\* See [Supported key types](#supported-key-types).</span></span>

::: zone-end

## <a name="custom-collections"></a><span data-ttu-id="8e808-382">Özel koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="8e808-382">Custom collections</span></span>

<span data-ttu-id="8e808-383">Önceki ad alanlarından birinde olmayan herhangi bir koleksiyon türü özel bir koleksiyon olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="8e808-383">Any collection type that isn't in one of the preceding namespaces is considered a custom collection.</span></span> <span data-ttu-id="8e808-384">Bu tür türler, ASP.NET Core tarafından tanımlanan Kullanıcı tanımlı türleri ve türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="8e808-384">Such types include user-defined types and types defined by ASP.NET Core.</span></span> <span data-ttu-id="8e808-385">Örneğin, <xref:Microsoft.Extensions.Primitives?displayProperty=fullName> Bu grupta bulunur.</span><span class="sxs-lookup"><span data-stu-id="8e808-385">For example, <xref:Microsoft.Extensions.Primitives?displayProperty=fullName> is in this group.</span></span>

<span data-ttu-id="8e808-386">Tüm özel koleksiyonlar (türetilen her şey `IEnumerable` ), öğe türleri desteklendiği sürece serileştirme için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="8e808-386">All custom collections (everything that derives from `IEnumerable`) are supported for serialization, as long as their element types are supported.</span></span>

### <a name="custom-collections-with-deserialization-support"></a><span data-ttu-id="8e808-387">Seri durumdan çıkarma desteği olan özel koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="8e808-387">Custom collections with deserialization support</span></span>

<span data-ttu-id="8e808-388">Özel bir koleksiyon, seri durumdan çıkarma için desteklenir:</span><span class="sxs-lookup"><span data-stu-id="8e808-388">A custom collection is supported for deserialization if it:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="8e808-389">Bir arabirim veya Özet değil.</span><span class="sxs-lookup"><span data-stu-id="8e808-389">Isn't an interface or abstract.</span></span>
* <span data-ttu-id="8e808-390">Parametresiz oluşturucusu vardır.</span><span class="sxs-lookup"><span data-stu-id="8e808-390">Has a parameterless constructor.</span></span>
* <span data-ttu-id="8e808-391">Tarafından desteklenen öğe türlerini içerir <xref:System.Text.Json.JsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="8e808-391">Contains element types that are supported by <xref:System.Text.Json.JsonSerializer>.</span></span>
* <span data-ttu-id="8e808-392">Aşağıdaki arabirimlerden veya sınıflardan birini veya daha fazlasını uygular veya devralır:</span><span class="sxs-lookup"><span data-stu-id="8e808-392">Implements or inherits one or more of the following interfaces or classes:</span></span>
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <span data-ttu-id="8e808-393"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8e808-393"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * <span data-ttu-id="8e808-394"><xref:System.Collections.Generic.IDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="8e808-394"><xref:System.Collections.Generic.IDictionary%602> \*\*</span></span>
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <span data-ttu-id="8e808-395"><xref:System.Collections.Stack> \*</span><span class="sxs-lookup"><span data-stu-id="8e808-395"><xref:System.Collections.Stack> \*</span></span>
  * <span data-ttu-id="8e808-396"><xref:System.Collections.Generic.Stack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8e808-396"><xref:System.Collections.Generic.Stack%601> \*</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="8e808-397">Bir arabirim veya Özet değil.</span><span class="sxs-lookup"><span data-stu-id="8e808-397">Isn't an interface or abstract.</span></span>
* <span data-ttu-id="8e808-398">Parametresiz oluşturucusu vardır.</span><span class="sxs-lookup"><span data-stu-id="8e808-398">Has a parameterless constructor.</span></span>
* <span data-ttu-id="8e808-399">Tarafından desteklenen öğe türlerini içerir <xref:System.Text.Json.JsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="8e808-399">Contains element types that are supported by <xref:System.Text.Json.JsonSerializer>.</span></span>
* <span data-ttu-id="8e808-400">Aşağıdaki arabirimlerden veya sınıflardan birini veya daha fazlasını uygular veya devralır:</span><span class="sxs-lookup"><span data-stu-id="8e808-400">Implements or inherits one or more of the following interfaces or classes:</span></span>
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <span data-ttu-id="8e808-401"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8e808-401"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * <span data-ttu-id="8e808-402">[IDictionary \<string, TValue> ](xref:System.Collections.Generic.IDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="8e808-402">[IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \*\*</span></span>
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <span data-ttu-id="8e808-403"><xref:System.Collections.Stack> \*</span><span class="sxs-lookup"><span data-stu-id="8e808-403"><xref:System.Collections.Stack> \*</span></span>
  * <span data-ttu-id="8e808-404"><xref:System.Collections.Generic.Stack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8e808-404"><xref:System.Collections.Generic.Stack%601> \*</span></span>

::: zone-end

  <span data-ttu-id="8e808-405">\*Bkz. [yığın \<T> için gidiş yolculuğu destekleme](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="8e808-405">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

  <span data-ttu-id="8e808-406">\*\* Bkz. [desteklenen anahtar türleri](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="8e808-406">\*\* See [Supported key types](#supported-key-types).</span></span>

### <a name="custom-collections-with-known-issues"></a><span data-ttu-id="8e808-407">Bilinen sorunları olan özel koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="8e808-407">Custom collections with known issues</span></span>

<span data-ttu-id="8e808-408">Aşağıdaki özel koleksiyonlarla ilgili bilinen sorunlar vardır:</span><span class="sxs-lookup"><span data-stu-id="8e808-408">There are known issues with the following custom collections:</span></span>

- <span data-ttu-id="8e808-409"><xref:System.Dynamic.ExpandoObject>: Bkz. [DotNet/Runtime # 29690](https://github.com/dotnet/runtime/issues/29690).</span><span class="sxs-lookup"><span data-stu-id="8e808-409"><xref:System.Dynamic.ExpandoObject>: See [dotnet/runtime#29690](https://github.com/dotnet/runtime/issues/29690).</span></span>
- <span data-ttu-id="8e808-410"><xref:System.Dynamic.DynamicObject>: Bkz. [DotNet/Runtime # 1808](https://github.com/dotnet/runtime/issues/1808).</span><span class="sxs-lookup"><span data-stu-id="8e808-410"><xref:System.Dynamic.DynamicObject>: See [dotnet/runtime#1808](https://github.com/dotnet/runtime/issues/1808).</span></span>
- <span data-ttu-id="8e808-411"><xref:System.Data.DataTable>: Bkz. [DotNet/docs # 21366](https://github.com/dotnet/docs/issues/21366).</span><span class="sxs-lookup"><span data-stu-id="8e808-411"><xref:System.Data.DataTable>: See [dotnet/docs#21366](https://github.com/dotnet/docs/issues/21366).</span></span>
- <span data-ttu-id="8e808-412"><xref:Microsoft.AspNetCore.Http.FormFile?displayProperty=fullName>: Bkz. [DotNet/Runtime # 1559](https://github.com/dotnet/runtime/issues/1559).</span><span class="sxs-lookup"><span data-stu-id="8e808-412"><xref:Microsoft.AspNetCore.Http.FormFile?displayProperty=fullName>: See [dotnet/runtime#1559](https://github.com/dotnet/runtime/issues/1559).</span></span>
- <span data-ttu-id="8e808-413"><xref:Microsoft.AspNetCore.Http.IFormCollection?displayProperty=fullName>: Bkz. [DotNet/Runtime # 1559](https://github.com/dotnet/runtime/issues/1559).</span><span class="sxs-lookup"><span data-stu-id="8e808-413"><xref:Microsoft.AspNetCore.Http.IFormCollection?displayProperty=fullName>: See [dotnet/runtime#1559](https://github.com/dotnet/runtime/issues/1559).</span></span>

<span data-ttu-id="8e808-414">Bilinen sorunlar hakkında daha fazla bilgi için [ System.Text.Json içindeki açık sorunlar ](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8e808-414">For more information about known issues, see the [open issues in System.Text.Json](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json).</span></span>

## <a name="supported-key-types"></a><span data-ttu-id="8e808-415">Desteklenen anahtar türleri</span><span class="sxs-lookup"><span data-stu-id="8e808-415">Supported key types</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="8e808-416">Anahtarlar ve türleri için desteklenen türler `Dictionary` `SortedList` şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8e808-416">Supported types for the keys of `Dictionary` and `SortedList` types include the following:</span></span>

* `Boolean`
* `Byte`
* `DateTime`
* `DateTimeOffset`
* `Decimal`
* `Double`
* `Enum`
* `Guid`
* `Int16`
* `Int32`
* `Int64`
* <span data-ttu-id="8e808-417">`Object` (Yalnızca serileştirme ve çalışma zamanı türü bu listede desteklenen türlerden biri ise.)</span><span class="sxs-lookup"><span data-stu-id="8e808-417">`Object` (Only on serialization and if the runtime type is one of the supported types in this list.)</span></span>
* `SByte`
* `Single`
* `String`
* `UInt16`
* `UInt32`
* `UInt64`

::: zone-end

::: zone pivot="dotnet-core-3-1"

<span data-ttu-id="8e808-418">\*\*`string`Anahtarlar `Dictionary` ve `SortedList` türler .NET Core 3,1 ' de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="8e808-418">\*\* Non-`string` keys for `Dictionary` and `SortedList` types are not supported in .NET Core 3.1.</span></span>

::: zone-end

## <a name="see-also"></a><span data-ttu-id="8e808-419">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e808-419">See also</span></span>

* [<span data-ttu-id="8e808-420">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="8e808-420">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="8e808-421">JsonSerializerOptions örneklerinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="8e808-421">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="8e808-422">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="8e808-422">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="8e808-423">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="8e808-423">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="8e808-424">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="8e808-424">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="8e808-425">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="8e808-425">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="8e808-426">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="8e808-426">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="8e808-427">Başvuruları koruma</span><span class="sxs-lookup"><span data-stu-id="8e808-427">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="8e808-428">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="8e808-428">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="8e808-429">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="8e808-429">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="8e808-430">Üzerinde Newtonsoft.Jsgeçir System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="8e808-430">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="8e808-431">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="8e808-431">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="8e808-432">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="8e808-432">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="8e808-433">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="8e808-433">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="8e808-434">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="8e808-434">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="8e808-435">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="8e808-435">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="8e808-436">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="8e808-436">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
