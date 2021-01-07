---
title: İçinde desteklenen koleksiyon türleri System.Text.Json
description: Ad alanındaki API 'Ler tarafından serileştirme için hangi koleksiyon türlerinin desteklendiğini öğrenin System.Text.Json .
ms.date: 01/06/2021
no-loc:
- System.Text.Json
ms.topic: reference
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 48033689e844dd29c999395255b5a1565fa2996e
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970995"
---
# <a name="supported-collection-types-in-no-locsystemtextjson"></a><span data-ttu-id="8c2ce-103">İçinde desteklenen koleksiyon türleri System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="8c2ce-103">Supported collection types in System.Text.Json</span></span>

<span data-ttu-id="8c2ce-104">Bu makale serileştirme ve seri durumundan çıkarma için hangi koleksiyonların desteklendiği hakkında genel bakış sunar.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-104">This article gives an overview of which collections are supported for serialization and deserialization.</span></span> <span data-ttu-id="8c2ce-105"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> , serileştirme için bir koleksiyon türünü destekler:</span><span class="sxs-lookup"><span data-stu-id="8c2ce-105"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> supports a collection type for serialization if it:</span></span>

* <span data-ttu-id="8c2ce-106">Türetiliyor <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="8c2ce-106">Derives from <xref:System.Collections.IEnumerable>.</span></span>
* <span data-ttu-id="8c2ce-107">Seri hale getirilebilir öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-107">Contains elements that are serializable.</span></span>

<span data-ttu-id="8c2ce-108">Seri hale getirici <xref:System.Collections.IEnumerable.GetEnumerator> yöntemini çağırır ve öğeleri yazar.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-108">The serializer calls the <xref:System.Collections.IEnumerable.GetEnumerator> method, and writes the elements.</span></span>

<span data-ttu-id="8c2ce-109">Seri durumdan çıkarma daha karmaşıktır ve bazı koleksiyon türleri için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-109">Deserialization is more complicated and is not supported for some collection types.</span></span>

<span data-ttu-id="8c2ce-110">Aşağıdaki bölümler ad alanına göre düzenlenmiştir ve serileştirme ve seri durumdan çıkarma için hangi türlerin desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-110">The following sections are organized by namespace and show which types are supported for serialization and deserialization.</span></span>

## <a name="systemcollections-namespace"></a><span data-ttu-id="8c2ce-111">System. Collections ad alanı</span><span class="sxs-lookup"><span data-stu-id="8c2ce-111">System.Collections namespace</span></span>

| <span data-ttu-id="8c2ce-112">Tür</span><span class="sxs-lookup"><span data-stu-id="8c2ce-112">Type</span></span>                                      | <span data-ttu-id="8c2ce-113">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8c2ce-113">Serialization</span></span> | <span data-ttu-id="8c2ce-114">Seri</span><span class="sxs-lookup"><span data-stu-id="8c2ce-114">Deserialization</span></span> |
|-------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ArrayList>       | <span data-ttu-id="8c2ce-115">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-115">✔️</span></span>           | <span data-ttu-id="8c2ce-116">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-116">✔️</span></span>              |
| <xref:System.Collections.BitArray>        | <span data-ttu-id="8c2ce-117">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-117">✔️</span></span>           | ❌              |
| <xref:System.Collections.DictionaryEntry> | <span data-ttu-id="8c2ce-118">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-118">✔️</span></span>           | <span data-ttu-id="8c2ce-119">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-119">✔️</span></span>              |
| <xref:System.Collections.Hashtable>       | <span data-ttu-id="8c2ce-120">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-120">✔️</span></span>           | <span data-ttu-id="8c2ce-121">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-121">✔️</span></span>              |
| <xref:System.Collections.Queue>           | <span data-ttu-id="8c2ce-122">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-122">✔️</span></span>           | <span data-ttu-id="8c2ce-123">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-123">✔️</span></span>              |
| <xref:System.Collections.SortedList>      | <span data-ttu-id="8c2ce-124">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-124">✔️</span></span>           | <span data-ttu-id="8c2ce-125">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-125">✔️</span></span>              |
| <xref:System.Collections.Stack>           | <span data-ttu-id="8c2ce-126">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-126">✔️</span></span>           | <span data-ttu-id="8c2ce-127">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-127">✔️</span></span>              |
| <xref:System.Collections.ICollection>     | <span data-ttu-id="8c2ce-128">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-128">✔️</span></span>           | <span data-ttu-id="8c2ce-129">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-129">✔️</span></span>              |
| <xref:System.Collections.IDictionary>     | <span data-ttu-id="8c2ce-130">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-130">✔️</span></span>           | <span data-ttu-id="8c2ce-131">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-131">✔️</span></span>              |
| <xref:System.Collections.IEnumerable>     | <span data-ttu-id="8c2ce-132">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-132">✔️</span></span>           | <span data-ttu-id="8c2ce-133">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-133">✔️</span></span>              |
| <xref:System.Collections.IList>           | <span data-ttu-id="8c2ce-134">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-134">✔️</span></span>           | <span data-ttu-id="8c2ce-135">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-135">✔️</span></span>              |

## <a name="systemcollectionsgeneric-namespace"></a><span data-ttu-id="8c2ce-136">System. Collections. Generic ad alanı</span><span class="sxs-lookup"><span data-stu-id="8c2ce-136">System.Collections.Generic namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="8c2ce-137">Tür</span><span class="sxs-lookup"><span data-stu-id="8c2ce-137">Type</span></span>                                                      | <span data-ttu-id="8c2ce-138">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8c2ce-138">Serialization</span></span> | <span data-ttu-id="8c2ce-139">Seri</span><span class="sxs-lookup"><span data-stu-id="8c2ce-139">Deserialization</span></span> |
|-----------------------------------------------------------|---------------|-----------------|
| <span data-ttu-id="8c2ce-140"><xref:System.Collections.Generic.Dictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-140"><xref:System.Collections.Generic.Dictionary%602> \*</span></span>       | <span data-ttu-id="8c2ce-141">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-141">✔️</span></span>           | <span data-ttu-id="8c2ce-142">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-142">✔️</span></span>              |
| <xref:System.Collections.Generic.HashSet%601>             | <span data-ttu-id="8c2ce-143">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-143">✔️</span></span>           | <span data-ttu-id="8c2ce-144">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-144">✔️</span></span>              |
| <xref:System.Collections.Generic.KeyValuePair%602>        | <span data-ttu-id="8c2ce-145">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-145">✔️</span></span>           | <span data-ttu-id="8c2ce-146">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-146">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedList%601>          | <span data-ttu-id="8c2ce-147">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-147">✔️</span></span>           | <span data-ttu-id="8c2ce-148">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-148">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedListNode%601>      | <span data-ttu-id="8c2ce-149">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-149">✔️</span></span>           | ❌              |
| <xref:System.Collections.Generic.List%601>                | <span data-ttu-id="8c2ce-150">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-150">✔️</span></span>           | <span data-ttu-id="8c2ce-151">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-151">✔️</span></span>              |
| <xref:System.Collections.Generic.Queue%601>               | <span data-ttu-id="8c2ce-152">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-152">✔️</span></span>           | <span data-ttu-id="8c2ce-153">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-153">✔️</span></span>              |
| <span data-ttu-id="8c2ce-154"><xref:System.Collections.Generic.SortedDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-154"><xref:System.Collections.Generic.SortedDictionary%602> \*</span></span> | <span data-ttu-id="8c2ce-155">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-155">✔️</span></span>           | <span data-ttu-id="8c2ce-156">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-156">✔️</span></span>              |
| <span data-ttu-id="8c2ce-157"><xref:System.Collections.Generic.SortedList%602> \*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-157"><xref:System.Collections.Generic.SortedList%602> \*</span></span>       | <span data-ttu-id="8c2ce-158">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-158">✔️</span></span>           | <span data-ttu-id="8c2ce-159">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-159">✔️</span></span>              |
| <xref:System.Collections.Generic.SortedSet%601>           | <span data-ttu-id="8c2ce-160">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-160">✔️</span></span>           | <span data-ttu-id="8c2ce-161">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-161">✔️</span></span>              |
| <xref:System.Collections.Generic.Stack%601>               | <span data-ttu-id="8c2ce-162">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-162">✔️</span></span>           | <span data-ttu-id="8c2ce-163">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-163">✔️</span></span>              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>    | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>         | <span data-ttu-id="8c2ce-164">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-164">✔️</span></span>           | <span data-ttu-id="8c2ce-165">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-165">✔️</span></span>              |
| <span data-ttu-id="8c2ce-166"><xref:System.Collections.Generic.IDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-166"><xref:System.Collections.Generic.IDictionary%602> \*</span></span>      | <span data-ttu-id="8c2ce-167">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-167">✔️</span></span>           | <span data-ttu-id="8c2ce-168">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-168">✔️</span></span>              |
| <xref:System.Collections.Generic.IEnumerable%601>         | <span data-ttu-id="8c2ce-169">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-169">✔️</span></span>           | <span data-ttu-id="8c2ce-170">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-170">✔️</span></span>              |
| <xref:System.Collections.Generic.IList%601>               | <span data-ttu-id="8c2ce-171">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-171">✔️</span></span>           | <span data-ttu-id="8c2ce-172">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-172">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601> | <span data-ttu-id="8c2ce-173">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-173">✔️</span></span>           | <span data-ttu-id="8c2ce-174">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-174">✔️</span></span>              |
| <span data-ttu-id="8c2ce-175"><xref:System.Collections.Generic.IReadOnlyDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-175"><xref:System.Collections.Generic.IReadOnlyDictionary%602> \*</span></span> | <span data-ttu-id="8c2ce-176">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-176">✔️</span></span>        | <span data-ttu-id="8c2ce-177">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-177">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyList%601>       | <span data-ttu-id="8c2ce-178">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-178">✔️</span></span>           | <span data-ttu-id="8c2ce-179">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-179">✔️</span></span>              |
| <xref:System.Collections.Generic.ISet%601>                | <span data-ttu-id="8c2ce-180">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-180">✔️</span></span>           | <span data-ttu-id="8c2ce-181">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-181">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="8c2ce-182">Tür</span><span class="sxs-lookup"><span data-stu-id="8c2ce-182">Type</span></span>                                                                                            | <span data-ttu-id="8c2ce-183">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8c2ce-183">Serialization</span></span> | <span data-ttu-id="8c2ce-184">Seri</span><span class="sxs-lookup"><span data-stu-id="8c2ce-184">Deserialization</span></span> |
|-------------------------------------------------------------------------------------------------|---------------|-----------------|
| <span data-ttu-id="8c2ce-185">[Sözlük \<string, TValue> ](xref:System.Collections.Generic.Dictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-185">[Dictionary\<string, TValue>](xref:System.Collections.Generic.Dictionary%602) \*</span></span>                | <span data-ttu-id="8c2ce-186">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-186">✔️</span></span>           | <span data-ttu-id="8c2ce-187">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-187">✔️</span></span>              |
| <xref:System.Collections.Generic.HashSet%601>                                                   | <span data-ttu-id="8c2ce-188">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-188">✔️</span></span>           | <span data-ttu-id="8c2ce-189">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-189">✔️</span></span>              |
| <xref:System.Collections.Generic.KeyValuePair%602>                                              | <span data-ttu-id="8c2ce-190">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-190">✔️</span></span>           | <span data-ttu-id="8c2ce-191">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-191">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedList%601>                                                | <span data-ttu-id="8c2ce-192">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-192">✔️</span></span>           | <span data-ttu-id="8c2ce-193">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-193">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedListNode%601>                                            | <span data-ttu-id="8c2ce-194">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-194">✔️</span></span>           | ❌              |
| <xref:System.Collections.Generic.List%601>                                                      | <span data-ttu-id="8c2ce-195">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-195">✔️</span></span>           | <span data-ttu-id="8c2ce-196">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-196">✔️</span></span>              |
| <xref:System.Collections.Generic.Queue%601>                                                     | <span data-ttu-id="8c2ce-197">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-197">✔️</span></span>           | <span data-ttu-id="8c2ce-198">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-198">✔️</span></span>              |
| <span data-ttu-id="8c2ce-199">[SortedDictionary \<string, TValue> ](xref:System.Collections.Generic.SortedDictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-199">[SortedDictionary\<string, TValue>](xref:System.Collections.Generic.SortedDictionary%602) \*</span></span>    | <span data-ttu-id="8c2ce-200">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-200">✔️</span></span>           | <span data-ttu-id="8c2ce-201">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-201">✔️</span></span>              |
| <span data-ttu-id="8c2ce-202">[SortedList \<string, TValue> ](xref:System.Collections.Generic.SortedList%602)\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-202">[SortedList\<string, TValue>](xref:System.Collections.Generic.SortedList%602) \*</span></span>                | <span data-ttu-id="8c2ce-203">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-203">✔️</span></span>           | <span data-ttu-id="8c2ce-204">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-204">✔️</span></span>              |
| <xref:System.Collections.Generic.SortedSet%601>                                                 | <span data-ttu-id="8c2ce-205">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-205">✔️</span></span>           | <span data-ttu-id="8c2ce-206">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-206">✔️</span></span>              |
| <xref:System.Collections.Generic.Stack%601>                                                     | <span data-ttu-id="8c2ce-207">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-207">✔️</span></span>           | <span data-ttu-id="8c2ce-208">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-208">✔️</span></span>              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>                                          | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>                                               | <span data-ttu-id="8c2ce-209">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-209">✔️</span></span>           | <span data-ttu-id="8c2ce-210">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-210">✔️</span></span>              |
| <span data-ttu-id="8c2ce-211">[IDictionary \<string, TValue> ](xref:System.Collections.Generic.IDictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-211">[IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \*</span></span>              | <span data-ttu-id="8c2ce-212">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-212">✔️</span></span>           | <span data-ttu-id="8c2ce-213">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-213">✔️</span></span>              |
| <xref:System.Collections.Generic.IEnumerable%601>                                               | <span data-ttu-id="8c2ce-214">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-214">✔️</span></span>           | <span data-ttu-id="8c2ce-215">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-215">✔️</span></span>              |
| <xref:System.Collections.Generic.IList%601>                                                     | <span data-ttu-id="8c2ce-216">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-216">✔️</span></span>           | <span data-ttu-id="8c2ce-217">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-217">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601>                                       | <span data-ttu-id="8c2ce-218">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-218">✔️</span></span>           | <span data-ttu-id="8c2ce-219">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-219">✔️</span></span>              |
| <span data-ttu-id="8c2ce-220">[IReadOnlyDictionary \<string, TValue> ](xref:System.Collections.Generic.IReadOnlyDictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-220">[IReadOnlyDictionary\<string, TValue>](xref:System.Collections.Generic.IReadOnlyDictionary%602) \*</span></span> | <span data-ttu-id="8c2ce-221">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-221">✔️</span></span>        | <span data-ttu-id="8c2ce-222">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-222">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyList%601>                                             | <span data-ttu-id="8c2ce-223">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-223">✔️</span></span>           | <span data-ttu-id="8c2ce-224">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-224">✔️</span></span>              |
| <xref:System.Collections.Generic.ISet%601>                                                      | <span data-ttu-id="8c2ce-225">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-225">✔️</span></span>           | <span data-ttu-id="8c2ce-226">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-226">✔️</span></span>              |

::: zone-end

<span data-ttu-id="8c2ce-227">\* Bkz. [desteklenen anahtar türleri](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="8c2ce-227">\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsimmutable-namespace"></a><span data-ttu-id="8c2ce-228">System. Collections. sabit ad alanı</span><span class="sxs-lookup"><span data-stu-id="8c2ce-228">System.Collections.Immutable namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="8c2ce-229">Tür</span><span class="sxs-lookup"><span data-stu-id="8c2ce-229">Type</span></span>                                                              | <span data-ttu-id="8c2ce-230">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8c2ce-230">Serialization</span></span> | <span data-ttu-id="8c2ce-231">Seri</span><span class="sxs-lookup"><span data-stu-id="8c2ce-231">Deserialization</span></span> |
|-------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>            | <span data-ttu-id="8c2ce-232">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-232">✔️</span></span>           | <span data-ttu-id="8c2ce-233">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-233">✔️</span></span>              |
| <span data-ttu-id="8c2ce-234"><xref:System.Collections.Immutable.ImmutableDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-234"><xref:System.Collections.Immutable.ImmutableDictionary%602> \*\*</span></span>  | <span data-ttu-id="8c2ce-235">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-235">✔️</span></span>           | <span data-ttu-id="8c2ce-236">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-236">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>          | <span data-ttu-id="8c2ce-237">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-237">✔️</span></span>           | <span data-ttu-id="8c2ce-238">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-238">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | <span data-ttu-id="8c2ce-239">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-239">✔️</span></span>           | <span data-ttu-id="8c2ce-240">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-240">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>            | <span data-ttu-id="8c2ce-241">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-241">✔️</span></span>           | <span data-ttu-id="8c2ce-242">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-242">✔️</span></span>              |
| <span data-ttu-id="8c2ce-243"><xref:System.Collections.Immutable.ImmutableSortedDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-243"><xref:System.Collections.Immutable.ImmutableSortedDictionary%602> \*\*</span></span> | <span data-ttu-id="8c2ce-244">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-244">✔️</span></span>      | <span data-ttu-id="8c2ce-245">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-245">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>        | <span data-ttu-id="8c2ce-246">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-246">✔️</span></span>           | <span data-ttu-id="8c2ce-247">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-247">✔️</span></span>              |
| <span data-ttu-id="8c2ce-248"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-248"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span></span>         | <span data-ttu-id="8c2ce-249">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-249">✔️</span></span>           | <span data-ttu-id="8c2ce-250">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-250">✔️</span></span>              |
| <span data-ttu-id="8c2ce-251"><xref:System.Collections.Immutable.IImmutableDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-251"><xref:System.Collections.Immutable.IImmutableDictionary%602> \*\*</span></span> | <span data-ttu-id="8c2ce-252">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-252">✔️</span></span>           | <span data-ttu-id="8c2ce-253">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-253">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | <span data-ttu-id="8c2ce-254">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-254">✔️</span></span>           | <span data-ttu-id="8c2ce-255">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-255">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>           | <span data-ttu-id="8c2ce-256">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-256">✔️</span></span>           | <span data-ttu-id="8c2ce-257">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-257">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableSet%601>             | <span data-ttu-id="8c2ce-258">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-258">✔️</span></span>           | <span data-ttu-id="8c2ce-259">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-259">✔️</span></span>              |
| <span data-ttu-id="8c2ce-260"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-260"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span></span>        | <span data-ttu-id="8c2ce-261">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-261">✔️</span></span>           | <span data-ttu-id="8c2ce-262">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-262">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="8c2ce-263">Tür</span><span class="sxs-lookup"><span data-stu-id="8c2ce-263">Type</span></span>                                                                                                          | <span data-ttu-id="8c2ce-264">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8c2ce-264">Serialization</span></span> | <span data-ttu-id="8c2ce-265">Seri</span><span class="sxs-lookup"><span data-stu-id="8c2ce-265">Deserialization</span></span> |
|---------------------------------------------------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>                                                        | <span data-ttu-id="8c2ce-266">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-266">✔️</span></span>           | <span data-ttu-id="8c2ce-267">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-267">✔️</span></span>              |
| <span data-ttu-id="8c2ce-268">[ImmutableDictionary \<string, TValue> ](xref:System.Collections.Immutable.ImmutableDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-268">[ImmutableDictionary\<string, TValue>](xref:System.Collections.Immutable.ImmutableDictionary%602) \*\*</span></span>        | <span data-ttu-id="8c2ce-269">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-269">✔️</span></span>           | <span data-ttu-id="8c2ce-270">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-270">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>                                                      | <span data-ttu-id="8c2ce-271">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-271">✔️</span></span>           | <span data-ttu-id="8c2ce-272">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-272">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | <span data-ttu-id="8c2ce-273">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-273">✔️</span></span>           | <span data-ttu-id="8c2ce-274">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-274">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>                                                        | <span data-ttu-id="8c2ce-275">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-275">✔️</span></span>           | <span data-ttu-id="8c2ce-276">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-276">✔️</span></span>              |
| <span data-ttu-id="8c2ce-277">[ImmutableSortedDictionary \<string, TValue> ](xref:System.Collections.Immutable.ImmutableSortedDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-277">[ImmutableSortedDictionary\<string, TValue>](xref:System.Collections.Immutable.ImmutableSortedDictionary%602) \*\*</span></span>| <span data-ttu-id="8c2ce-278">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-278">✔️</span></span>       | <span data-ttu-id="8c2ce-279">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-279">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>                                                    | <span data-ttu-id="8c2ce-280">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-280">✔️</span></span>           | <span data-ttu-id="8c2ce-281">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-281">✔️</span></span>              |
| <span data-ttu-id="8c2ce-282"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-282"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span></span>                                                     | <span data-ttu-id="8c2ce-283">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-283">✔️</span></span>           | <span data-ttu-id="8c2ce-284">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-284">✔️</span></span>              |
| <span data-ttu-id="8c2ce-285">[IImmutableDictionary \<string, TValue> ](xref:System.Collections.Immutable.IImmutableDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-285">[IImmutableDictionary\<string, TValue>](xref:System.Collections.Immutable.IImmutableDictionary%602) \*\*</span></span>      | <span data-ttu-id="8c2ce-286">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-286">✔️</span></span>           | <span data-ttu-id="8c2ce-287">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-287">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | <span data-ttu-id="8c2ce-288">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-288">✔️</span></span>           | <span data-ttu-id="8c2ce-289">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-289">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>                                                       | <span data-ttu-id="8c2ce-290">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-290">✔️</span></span>           | <span data-ttu-id="8c2ce-291">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-291">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableSet%601>                                                         | <span data-ttu-id="8c2ce-292">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-292">✔️</span></span>           | <span data-ttu-id="8c2ce-293">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-293">✔️</span></span>              |
| <span data-ttu-id="8c2ce-294"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-294"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span></span>                                                    | <span data-ttu-id="8c2ce-295">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-295">✔️</span></span>           | <span data-ttu-id="8c2ce-296">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-296">✔️</span></span>              |

::: zone-end

<span data-ttu-id="8c2ce-297">\*Bkz. [yığın \<T> için gidiş yolculuğu destekleme](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="8c2ce-297">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

<span data-ttu-id="8c2ce-298">\*\* Bkz. [desteklenen anahtar türleri](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="8c2ce-298">\*\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsspecialized-namespace"></a><span data-ttu-id="8c2ce-299">System. Collections. özelleşmiş ad alanı</span><span class="sxs-lookup"><span data-stu-id="8c2ce-299">System.Collections.Specialized namespace</span></span>

| <span data-ttu-id="8c2ce-300">Tür</span><span class="sxs-lookup"><span data-stu-id="8c2ce-300">Type</span></span>                                                      | <span data-ttu-id="8c2ce-301">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8c2ce-301">Serialization</span></span> | <span data-ttu-id="8c2ce-302">Seri</span><span class="sxs-lookup"><span data-stu-id="8c2ce-302">Deserialization</span></span> |
|-----------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Specialized.BitVector32>         | <span data-ttu-id="8c2ce-303">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-303">✔️</span></span>           | ❌\*            |
| <xref:System.Collections.Specialized.HybridDictionary>    | <span data-ttu-id="8c2ce-304">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-304">✔️</span></span>           | <span data-ttu-id="8c2ce-305">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-305">✔️</span></span>              |
| <xref:System.Collections.Specialized.IOrderedDictionary>  | <span data-ttu-id="8c2ce-306">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-306">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.ListDictionary>      | <span data-ttu-id="8c2ce-307">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-307">✔️</span></span>           | <span data-ttu-id="8c2ce-308">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-308">✔️</span></span>              |
| <xref:System.Collections.Specialized.StringCollection>    | <span data-ttu-id="8c2ce-309">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-309">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.StringDictionary>    | <span data-ttu-id="8c2ce-310">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-310">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.NameValueCollection> | <span data-ttu-id="8c2ce-311">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-311">✔️</span></span>           | ❌              |

<span data-ttu-id="8c2ce-312">\*<xref:System.Collections.Specialized.BitVector32>Seri durumdan kaldırıldığında, <xref:System.Collections.Specialized.BitVector32.Data> özelliği ortak bir ayarlayıcısı olmadığından atlanır.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-312">\* When <xref:System.Collections.Specialized.BitVector32> is deserialized, the <xref:System.Collections.Specialized.BitVector32.Data> property is skipped because it doesn't have a public setter.</span></span> <span data-ttu-id="8c2ce-313">Özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-313">No exception is thrown.</span></span>

## <a name="systemcollectionsconcurrent-namespace"></a><span data-ttu-id="8c2ce-314">System. Collections. eşzamanlı ad alanı</span><span class="sxs-lookup"><span data-stu-id="8c2ce-314">System.Collections.Concurrent namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="8c2ce-315">Tür</span><span class="sxs-lookup"><span data-stu-id="8c2ce-315">Type</span></span>                                                          | <span data-ttu-id="8c2ce-316">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8c2ce-316">Serialization</span></span> | <span data-ttu-id="8c2ce-317">Seri</span><span class="sxs-lookup"><span data-stu-id="8c2ce-317">Deserialization</span></span> |
|---------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601>   | <span data-ttu-id="8c2ce-318">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-318">✔️</span></span>           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>        | <span data-ttu-id="8c2ce-319">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-319">✔️</span></span>           | ❌              |
| <span data-ttu-id="8c2ce-320"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-320"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> \*\*</span></span> | <span data-ttu-id="8c2ce-321">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-321">✔️</span></span>      | <span data-ttu-id="8c2ce-322">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-322">✔️</span></span>              |
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>      | <span data-ttu-id="8c2ce-323">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-323">✔️</span></span>           | <span data-ttu-id="8c2ce-324">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-324">✔️</span></span>              |
| <span data-ttu-id="8c2ce-325"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-325"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>   | <span data-ttu-id="8c2ce-326">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-326">✔️</span></span>           | <span data-ttu-id="8c2ce-327">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-327">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="8c2ce-328">Tür</span><span class="sxs-lookup"><span data-stu-id="8c2ce-328">Type</span></span>                                                        | <span data-ttu-id="8c2ce-329">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8c2ce-329">Serialization</span></span> | <span data-ttu-id="8c2ce-330">Seri</span><span class="sxs-lookup"><span data-stu-id="8c2ce-330">Deserialization</span></span> |
|-------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601> | <span data-ttu-id="8c2ce-331">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-331">✔️</span></span>           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>      | <span data-ttu-id="8c2ce-332">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-332">✔️</span></span>           | ❌              |
| <span data-ttu-id="8c2ce-333">[ConcurrentDictionary \<string, TValue> ](xref:System.Collections.Concurrent.ConcurrentDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-333">[ConcurrentDictionary\<string, TValue>](xref:System.Collections.Concurrent.ConcurrentDictionary%602) \*\*</span></span> |<span data-ttu-id="8c2ce-334">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-334">✔️</span></span>|<span data-ttu-id="8c2ce-335">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-335">✔️</span></span>|
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>    | <span data-ttu-id="8c2ce-336">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-336">✔️</span></span>           | <span data-ttu-id="8c2ce-337">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-337">✔️</span></span>              |
| <span data-ttu-id="8c2ce-338"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-338"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span> | <span data-ttu-id="8c2ce-339">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-339">✔️</span></span>           | <span data-ttu-id="8c2ce-340">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-340">✔️</span></span>              |

::: zone-end

<span data-ttu-id="8c2ce-341">\*Bkz. [yığın \<T> için gidiş yolculuğu destekleme](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="8c2ce-341">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

<span data-ttu-id="8c2ce-342">\*\* Bkz. [desteklenen anahtar türleri](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="8c2ce-342">\*\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsobjectmodel-namespace"></a><span data-ttu-id="8c2ce-343">System. Collections. ObjectModel Ad alanı</span><span class="sxs-lookup"><span data-stu-id="8c2ce-343">System.Collections.ObjectModel namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="8c2ce-344">Tür</span><span class="sxs-lookup"><span data-stu-id="8c2ce-344">Type</span></span>                                                           | <span data-ttu-id="8c2ce-345">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8c2ce-345">Serialization</span></span> | <span data-ttu-id="8c2ce-346">Seri</span><span class="sxs-lookup"><span data-stu-id="8c2ce-346">Deserialization</span></span> |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | <span data-ttu-id="8c2ce-347">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-347">✔️</span></span>            | <span data-ttu-id="8c2ce-348">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-348">✔️</span></span>             |
| <span data-ttu-id="8c2ce-349">[KeyedCollection \<string, TValue> ](xref:System.Collections.ObjectModel.KeyedCollection%602)\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-349">[KeyedCollection\<string, TValue>](xref:System.Collections.ObjectModel.KeyedCollection%602) \*</span></span> |<span data-ttu-id="8c2ce-350">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-350">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | <span data-ttu-id="8c2ce-351">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-351">✔️</span></span>            | <span data-ttu-id="8c2ce-352">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-352">✔️</span></span>             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | <span data-ttu-id="8c2ce-353">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-353">✔️</span></span>            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602>   | <span data-ttu-id="8c2ce-354">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-354">✔️</span></span>            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601> | <span data-ttu-id="8c2ce-355">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-355">✔️</span></span>    | ❌             |

<span data-ttu-id="8c2ce-356">\* Anahtarlar olmayanlar `string` desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-356">\* Non-`string` keys are not supported.</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="8c2ce-357">Tür</span><span class="sxs-lookup"><span data-stu-id="8c2ce-357">Type</span></span>                                                           | <span data-ttu-id="8c2ce-358">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8c2ce-358">Serialization</span></span> | <span data-ttu-id="8c2ce-359">Seri</span><span class="sxs-lookup"><span data-stu-id="8c2ce-359">Deserialization</span></span> |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | <span data-ttu-id="8c2ce-360">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-360">✔️</span></span>            | <span data-ttu-id="8c2ce-361">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-361">✔️</span></span>             |
| <span data-ttu-id="8c2ce-362">[KeyedCollection \<string, TValue> ](xref:System.Collections.ObjectModel.KeyedCollection%602)\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-362">[KeyedCollection\<string, TValue>](xref:System.Collections.ObjectModel.KeyedCollection%602) \*</span></span> |<span data-ttu-id="8c2ce-363">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-363">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | <span data-ttu-id="8c2ce-364">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-364">✔️</span></span>            | <span data-ttu-id="8c2ce-365">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-365">✔️</span></span>             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | <span data-ttu-id="8c2ce-366">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-366">✔️</span></span>            | ❌             |
| <span data-ttu-id="8c2ce-367">[ReadOnlyDictionary \<string, TValue> ](xref:System.Collections.ObjectModel.ReadOnlyDictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-367">[ReadOnlyDictionary\<string, TValue>](xref:System.Collections.ObjectModel.ReadOnlyDictionary%602) \*</span></span> |<span data-ttu-id="8c2ce-368">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-368">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601>| <span data-ttu-id="8c2ce-369">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2ce-369">✔️</span></span>     | ❌             |

<span data-ttu-id="8c2ce-370">\* Bkz. [desteklenen anahtar türleri](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="8c2ce-370">\* See [Supported key types](#supported-key-types).</span></span>

::: zone-end

## <a name="custom-collections"></a><span data-ttu-id="8c2ce-371">Özel koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="8c2ce-371">Custom collections</span></span>

<span data-ttu-id="8c2ce-372">Önceki ad alanlarından birinde olmayan herhangi bir koleksiyon türü özel bir koleksiyon olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-372">Any collection type that isn't in one of the preceding namespaces is considered a custom collection.</span></span> <span data-ttu-id="8c2ce-373">Bu tür türler, ASP.NET Core tarafından tanımlanan Kullanıcı tanımlı türleri ve türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-373">Such types include user-defined types and types defined by ASP.NET Core.</span></span> <span data-ttu-id="8c2ce-374">Örneğin, <xref:Microsoft.Extensions.Primitives?displayProperty=fullName> Bu grupta bulunur.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-374">For example, <xref:Microsoft.Extensions.Primitives?displayProperty=fullName> is in this group.</span></span>

<span data-ttu-id="8c2ce-375">Tüm özel koleksiyonlar (türetilen her şey `IEnumerable` ), öğe türleri desteklendiği sürece serileştirme için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-375">All custom collections (everything that derives from `IEnumerable`) are supported for serialization, as long as their element types are supported.</span></span>

### <a name="custom-collections-with-deserialization-support"></a><span data-ttu-id="8c2ce-376">Seri durumdan çıkarma desteği olan özel koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="8c2ce-376">Custom collections with deserialization support</span></span>

<span data-ttu-id="8c2ce-377">Özel bir koleksiyon, seri durumdan çıkarma için desteklenir:</span><span class="sxs-lookup"><span data-stu-id="8c2ce-377">A custom collection is supported for deserialization if it:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="8c2ce-378">Bir arabirim veya Özet değil.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-378">Isn't an interface or abstract.</span></span>
* <span data-ttu-id="8c2ce-379">Parametresiz oluşturucusu vardır.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-379">Has a parameterless constructor.</span></span>
* <span data-ttu-id="8c2ce-380">Tarafından desteklenen öğe türlerini içerir <xref:System.Text.Json.JsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="8c2ce-380">Contains element types that are supported by <xref:System.Text.Json.JsonSerializer>.</span></span>
* <span data-ttu-id="8c2ce-381">Aşağıdaki arabirimlerden veya sınıflardan birini veya daha fazlasını uygular veya devralır:</span><span class="sxs-lookup"><span data-stu-id="8c2ce-381">Implements or inherits one or more of the following interfaces or classes:</span></span>
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <span data-ttu-id="8c2ce-382"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-382"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * <span data-ttu-id="8c2ce-383"><xref:System.Collections.Generic.IDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-383"><xref:System.Collections.Generic.IDictionary%602> \*\*</span></span>
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <span data-ttu-id="8c2ce-384"><xref:System.Collections.Stack> \*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-384"><xref:System.Collections.Stack> \*</span></span>
  * <span data-ttu-id="8c2ce-385"><xref:System.Collections.Generic.Stack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-385"><xref:System.Collections.Generic.Stack%601> \*</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="8c2ce-386">Bir arabirim veya Özet değil.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-386">Isn't an interface or abstract.</span></span>
* <span data-ttu-id="8c2ce-387">Parametresiz oluşturucusu vardır.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-387">Has a parameterless constructor.</span></span>
* <span data-ttu-id="8c2ce-388">Tarafından desteklenen öğe türlerini içerir <xref:System.Text.Json.JsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="8c2ce-388">Contains element types that are supported by <xref:System.Text.Json.JsonSerializer>.</span></span>
* <span data-ttu-id="8c2ce-389">Aşağıdaki arabirimlerden veya sınıflardan birini veya daha fazlasını uygular veya devralır:</span><span class="sxs-lookup"><span data-stu-id="8c2ce-389">Implements or inherits one or more of the following interfaces or classes:</span></span>
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <span data-ttu-id="8c2ce-390"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-390"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * <span data-ttu-id="8c2ce-391">[IDictionary \<string, TValue> ](xref:System.Collections.Generic.IDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-391">[IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \*\*</span></span>
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <span data-ttu-id="8c2ce-392"><xref:System.Collections.Stack> \*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-392"><xref:System.Collections.Stack> \*</span></span>
  * <span data-ttu-id="8c2ce-393"><xref:System.Collections.Generic.Stack%601> \*</span><span class="sxs-lookup"><span data-stu-id="8c2ce-393"><xref:System.Collections.Generic.Stack%601> \*</span></span>

::: zone-end

  <span data-ttu-id="8c2ce-394">\*Bkz. [yığın \<T> için gidiş yolculuğu destekleme](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="8c2ce-394">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

  <span data-ttu-id="8c2ce-395">\*\* Bkz. [desteklenen anahtar türleri](#supported-key-types).</span><span class="sxs-lookup"><span data-stu-id="8c2ce-395">\*\* See [Supported key types](#supported-key-types).</span></span>

### <a name="custom-collections-with-known-issues"></a><span data-ttu-id="8c2ce-396">Bilinen sorunları olan özel koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="8c2ce-396">Custom collections with known issues</span></span>

<span data-ttu-id="8c2ce-397">Aşağıdaki özel koleksiyonlarla ilgili bilinen sorunlar vardır:</span><span class="sxs-lookup"><span data-stu-id="8c2ce-397">There are known issues with the following custom collections:</span></span>

- <span data-ttu-id="8c2ce-398"><xref:System.Dynamic.ExpandoObject>: Bkz. [DotNet/Runtime # 29690](https://github.com/dotnet/runtime/issues/29690).</span><span class="sxs-lookup"><span data-stu-id="8c2ce-398"><xref:System.Dynamic.ExpandoObject>: See [dotnet/runtime#29690](https://github.com/dotnet/runtime/issues/29690).</span></span>
- <span data-ttu-id="8c2ce-399"><xref:System.Dynamic.DynamicObject>: Bkz. [DotNet/Runtime # 1808](https://github.com/dotnet/runtime/issues/1808).</span><span class="sxs-lookup"><span data-stu-id="8c2ce-399"><xref:System.Dynamic.DynamicObject>: See [dotnet/runtime#1808](https://github.com/dotnet/runtime/issues/1808).</span></span>
- <span data-ttu-id="8c2ce-400"><xref:System.Data.DataTable>: Bkz. [DotNet/docs # 21366](https://github.com/dotnet/docs/issues/21366).</span><span class="sxs-lookup"><span data-stu-id="8c2ce-400"><xref:System.Data.DataTable>: See [dotnet/docs#21366](https://github.com/dotnet/docs/issues/21366).</span></span>
- <span data-ttu-id="8c2ce-401"><xref:Microsoft.AspNetCore.Http.FormFile?displayProperty=fullName>: Bkz. [DotNet/Runtime # 1559](https://github.com/dotnet/runtime/issues/1559).</span><span class="sxs-lookup"><span data-stu-id="8c2ce-401"><xref:Microsoft.AspNetCore.Http.FormFile?displayProperty=fullName>: See [dotnet/runtime#1559](https://github.com/dotnet/runtime/issues/1559).</span></span>
- <span data-ttu-id="8c2ce-402"><xref:Microsoft.AspNetCore.Http.IFormCollection?displayProperty=fullName>: Bkz. [DotNet/Runtime # 1559](https://github.com/dotnet/runtime/issues/1559).</span><span class="sxs-lookup"><span data-stu-id="8c2ce-402"><xref:Microsoft.AspNetCore.Http.IFormCollection?displayProperty=fullName>: See [dotnet/runtime#1559](https://github.com/dotnet/runtime/issues/1559).</span></span>

<span data-ttu-id="8c2ce-403">Bilinen sorunlar hakkında daha fazla bilgi için [ System.Text.Json içindeki açık sorunlar ](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-403">For more information about known issues, see the [open issues in System.Text.Json](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json).</span></span>

## <a name="supported-key-types"></a><span data-ttu-id="8c2ce-404">Desteklenen anahtar türleri</span><span class="sxs-lookup"><span data-stu-id="8c2ce-404">Supported key types</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="8c2ce-405">Anahtarlar ve türleri için desteklenen türler `Dictionary` `SortedList` şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8c2ce-405">Supported types for the keys of `Dictionary` and `SortedList` types include the following:</span></span>

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
* <span data-ttu-id="8c2ce-406">`Object` (Yalnızca serileştirme ve çalışma zamanı türü bu listede desteklenen türlerden biri ise.)</span><span class="sxs-lookup"><span data-stu-id="8c2ce-406">`Object` (Only on serialization and if the runtime type is one of the supported types in this list.)</span></span>
* `SByte`
* `Single`
* `String`
* `UInt16`
* `UInt32`
* `UInt64`

::: zone-end

::: zone pivot="dotnet-core-3-1"

<span data-ttu-id="8c2ce-407">\*\*`string`Anahtarlar `Dictionary` ve `SortedList` türler .NET Core 3,1 ' de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-407">\*\* Non-`string` keys for `Dictionary` and `SortedList` types are not supported in .NET Core 3.1.</span></span>

::: zone-end

## <a name="see-also"></a><span data-ttu-id="8c2ce-408">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c2ce-408">See also</span></span>

* [<span data-ttu-id="8c2ce-409">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="8c2ce-409">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="8c2ce-410">JsonSerializerOptions örneklerinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="8c2ce-410">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="8c2ce-411">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="8c2ce-411">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="8c2ce-412">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="8c2ce-412">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="8c2ce-413">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="8c2ce-413">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="8c2ce-414">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="8c2ce-414">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="8c2ce-415">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="8c2ce-415">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="8c2ce-416">Başvuruları koruma</span><span class="sxs-lookup"><span data-stu-id="8c2ce-416">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="8c2ce-417">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="8c2ce-417">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="8c2ce-418">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="8c2ce-418">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="8c2ce-419">Üzerinde Newtonsoft.Jsgeçir System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="8c2ce-419">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="8c2ce-420">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="8c2ce-420">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="8c2ce-421">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="8c2ce-421">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="8c2ce-422">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="8c2ce-422">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="8c2ce-423">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="8c2ce-423">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="8c2ce-424">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="8c2ce-424">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="8c2ce-425">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="8c2ce-425">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
