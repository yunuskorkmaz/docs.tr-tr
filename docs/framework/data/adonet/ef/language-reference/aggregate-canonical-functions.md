---
title: Toplu Kurallı İşlevler
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: 2738d649190b088c34272de5b3e8732d87811a59
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489515"
---
# <a name="aggregate-canonical-functions"></a><span data-ttu-id="0a0d8-102">Toplu Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="0a0d8-102">Aggregate Canonical Functions</span></span>

<span data-ttu-id="0a0d8-103">Toplamlar, örneğin, tek bir değer giriş değerlerini bir dizi azaltan ifadelerdir.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-103">Aggregates are expressions that reduce a series of input values into, for example, a single value.</span></span> <span data-ttu-id="0a0d8-104">Toplamlar normalde seçin ifadesinin GROUP BY yan tümcesi ile birlikte kullanılır ve burada kullanılabilirler üzerindeki kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-104">Aggregates are normally used in conjunction with the GROUP BY clause of the SELECT expression, and there are constraints on where they can be used.</span></span>

## <a name="aggregate-entity-sql-canonical-functions"></a><span data-ttu-id="0a0d8-105">Entity SQL toplu kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="0a0d8-105">Aggregate Entity SQL canonical functions</span></span>

<span data-ttu-id="0a0d8-106">Entity SQL toplu kurallı işlevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0a0d8-106">The following are the aggregate Entity SQL canonical functions.</span></span>

### <a name="avgexpression"></a><span data-ttu-id="0a0d8-107">AVG(Expression)</span><span class="sxs-lookup"><span data-stu-id="0a0d8-107">Avg(expression)</span></span>

<span data-ttu-id="0a0d8-108">Null olmayan değerlerin ortalamasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-108">Returns the average of the non-null values.</span></span>

<span data-ttu-id="0a0d8-109">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-109">**Arguments**</span></span>

<span data-ttu-id="0a0d8-110">Bir `Int32`, `Int64`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-110">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="0a0d8-111">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-111">**Return Value**</span></span>

<span data-ttu-id="0a0d8-112">Türünü `expression`, veya `null` tüm giriş değerlerini varsa `null` değerleri.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-112">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="0a0d8-113">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-113">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a><span data-ttu-id="0a0d8-114">BigCount(expression)</span><span class="sxs-lookup"><span data-stu-id="0a0d8-114">BigCount(expression)</span></span>

<span data-ttu-id="0a0d8-115">Null ve yinelenen değerleri dahil olmak üzere toplam boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-115">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="0a0d8-116">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-116">**Arguments**</span></span>

<span data-ttu-id="0a0d8-117">Herhangi bir türü.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-117">Any type.</span></span>

<span data-ttu-id="0a0d8-118">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-118">**Return Value**</span></span>

<span data-ttu-id="0a0d8-119">Bir `Int64`.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-119">An `Int64`.</span></span>

<span data-ttu-id="0a0d8-120">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-120">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a><span data-ttu-id="0a0d8-121">Count (deyim)</span><span class="sxs-lookup"><span data-stu-id="0a0d8-121">Count(expression)</span></span>

<span data-ttu-id="0a0d8-122">Null ve yinelenen değerleri dahil olmak üzere toplam boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-122">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="0a0d8-123">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-123">**Arguments**</span></span>

<span data-ttu-id="0a0d8-124">Herhangi bir türü.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-124">Any type.</span></span>

<span data-ttu-id="0a0d8-125">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-125">**Return Value**</span></span>

<span data-ttu-id="0a0d8-126">Bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-126">An `Int32`.</span></span>

<span data-ttu-id="0a0d8-127">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-127">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a><span data-ttu-id="0a0d8-128">Max(Expression)</span><span class="sxs-lookup"><span data-stu-id="0a0d8-128">Max(expression)</span></span>

<span data-ttu-id="0a0d8-129">Maksimum null olmayan değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-129">Returns the maximum of the non-null values.</span></span>

<span data-ttu-id="0a0d8-130">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-130">**Arguments**</span></span>

<span data-ttu-id="0a0d8-131">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-131">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="0a0d8-132">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-132">**Return Value**</span></span>

<span data-ttu-id="0a0d8-133">Türünü `expression`, veya `null` tüm giriş değerlerini varsa `null` değerleri.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-133">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="0a0d8-134">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-134">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a><span data-ttu-id="0a0d8-135">Min(Expression)</span><span class="sxs-lookup"><span data-stu-id="0a0d8-135">Min(expression)</span></span>

<span data-ttu-id="0a0d8-136">Boş olmayan değerlerinin en küçüğünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-136">Returns the minimum of the non-null values.</span></span>

<span data-ttu-id="0a0d8-137">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-137">**Arguments**</span></span>

<span data-ttu-id="0a0d8-138">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-138">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="0a0d8-139">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-139">**Return Value**</span></span>

<span data-ttu-id="0a0d8-140">Türünü `expression`, veya `null` tüm giriş değerlerini varsa `null` değerleri.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-140">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="0a0d8-141">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-141">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a><span data-ttu-id="0a0d8-142">StDev(expression)</span><span class="sxs-lookup"><span data-stu-id="0a0d8-142">StDev(expression)</span></span>

<span data-ttu-id="0a0d8-143">Boş olmayan değerlerinin standart sapmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-143">Returns the standard deviation of the non-null values.</span></span>

<span data-ttu-id="0a0d8-144">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-144">**Arguments**</span></span>

<span data-ttu-id="0a0d8-145">Bir `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-145">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="0a0d8-146">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-146">**Return Value**</span></span>

<span data-ttu-id="0a0d8-147">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-147">A `Double`.</span></span> <span data-ttu-id="0a0d8-148">`Null`, tüm giriş değerlerini varsa `null` değerleri.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-148">`Null`, if all input values are `null` values.</span></span>

<span data-ttu-id="0a0d8-149">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-149">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a><span data-ttu-id="0a0d8-150">StDevP(expression)</span><span class="sxs-lookup"><span data-stu-id="0a0d8-150">StDevP(expression)</span></span>

<span data-ttu-id="0a0d8-151">İçin tüm değerlerin popülasyon standart sapmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-151">Returns the standard deviation for the population of all values.</span></span>

<span data-ttu-id="0a0d8-152">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-152">**Arguments**</span></span>

<span data-ttu-id="0a0d8-153">Bir `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-153">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="0a0d8-154">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-154">**Return Value**</span></span>

<span data-ttu-id="0a0d8-155">A `Double`, veya `null` tüm giriş değerlerini varsa `null` değerleri.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-155">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="0a0d8-156">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-156">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a><span data-ttu-id="0a0d8-157">SUM(Expression)</span><span class="sxs-lookup"><span data-stu-id="0a0d8-157">Sum(expression)</span></span>

<span data-ttu-id="0a0d8-158">Null olmayan değerlerin toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-158">Returns the sum of the non-null values.</span></span>

<span data-ttu-id="0a0d8-159">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-159">**Arguments**</span></span>

<span data-ttu-id="0a0d8-160">Bir `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-160">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="0a0d8-161">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-161">**Return Value**</span></span>

<span data-ttu-id="0a0d8-162">A `Double`, veya `null` tüm giriş değerlerini varsa `null` değerleri.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-162">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="0a0d8-163">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-163">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a><span data-ttu-id="0a0d8-164">Var(Expression)</span><span class="sxs-lookup"><span data-stu-id="0a0d8-164">Var(expression)</span></span>

<span data-ttu-id="0a0d8-165">Null olmayan tüm değerlerin varyansını döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-165">Returns the variance of all non-null values.</span></span>

<span data-ttu-id="0a0d8-166">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-166">**Arguments**</span></span>

<span data-ttu-id="0a0d8-167">Bir `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-167">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="0a0d8-168">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-168">**Return Value**</span></span>

<span data-ttu-id="0a0d8-169">A `Double`, veya `null` tüm giriş değerlerini varsa `null` değerleri.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-169">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="0a0d8-170">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-170">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a><span data-ttu-id="0a0d8-171">VarP(expression)</span><span class="sxs-lookup"><span data-stu-id="0a0d8-171">VarP(expression)</span></span>

<span data-ttu-id="0a0d8-172">Null olmayan tüm değerlerin popülasyon varyansını döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-172">Returns the variance for the population of all non-null values.</span></span>

<span data-ttu-id="0a0d8-173">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-173">**Arguments**</span></span>

<span data-ttu-id="0a0d8-174">Bir `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-174">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="0a0d8-175">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-175">**Return Value**</span></span>

<span data-ttu-id="0a0d8-176">A `Double`, veya `null` tüm giriş değerlerini varsa `null` değerleri.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-176">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="0a0d8-177">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="0a0d8-177">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]

<span data-ttu-id="0a0d8-178">Microsoft SQL istemci yönetilen sağlayıcısında eşdeğer bir işlevselliği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-178">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="0a0d8-179">Daha fazla bilgi için [Entity Framework işlevleri için SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="0a0d8-179">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>

## <a name="collection-based-aggregates"></a><span data-ttu-id="0a0d8-180">Koleksiyon tabanlı toplamaları</span><span class="sxs-lookup"><span data-stu-id="0a0d8-180">Collection-based aggregates</span></span>

<span data-ttu-id="0a0d8-181">Koleksiyon tabanlı toplamlar (toplama işlevleri), koleksiyonlar üzerinde çalışır ve bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-181">Collection-based aggregates (collection functions) operate on collections and return a value.</span></span> <span data-ttu-id="0a0d8-182">Örneğin SİPARİŞLER varsa tüm siparişleri koleksiyonunu sevk tarihten şu ifadeyle hesaplayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0a0d8-182">For example if ORDERS is a collection of all orders, you can calculate the earliest ship date with the following expression:</span></span>

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

<span data-ttu-id="0a0d8-183">Koleksiyon tabanlı toplamalar içindeki ifadeler, geçerli ortam ad çözümlemesi kapsamında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-183">Expressions inside collection-based aggregates are evaluated within the current ambient name-resolution scope.</span></span>

## <a name="group-based-aggregates"></a><span data-ttu-id="0a0d8-184">Grup tabanlı toplamaları</span><span class="sxs-lookup"><span data-stu-id="0a0d8-184">Group-based aggregates</span></span>

<span data-ttu-id="0a0d8-185">Grup tabanlı toplamalar GROUP BY yan tümcesi tarafından tanımlanan bir grup üzerinden hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-185">Group-based aggregates are calculated over a group as defined by the GROUP BY clause.</span></span> <span data-ttu-id="0a0d8-186">Sonuçta her bir grup için ayrı bir toplama, toplam hesaplaması için giriş olarak her gruba öğeleri kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-186">For each group in the result, a separate aggregate is calculated by using the elements in each group as input to the aggregate calculation.</span></span> <span data-ttu-id="0a0d8-187">Group by yan tümcesi select ifadesinde kullanıldığında, ifade adlarının, toplamlar ve sabit ifadeler yalnızca gruplandırma projeksiyon veya order by yan tümcesi içinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-187">When a group-by clause is used in a select expression, only grouping expression names, aggregates, or constant expressions can be present in the projection or order-by clause.</span></span>

<span data-ttu-id="0a0d8-188">Aşağıdaki örnek, her ürün için sıralı ortalama miktarı hesaplar:</span><span class="sxs-lookup"><span data-stu-id="0a0d8-188">The following example calculates the average quantity ordered for each product:</span></span>

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol
  group by ol.Product as p
```

<span data-ttu-id="0a0d8-189">Bir grup tabanlı toplama açık group by yan tümcesi olmadan seçme olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-189">It's possible to have a group-based aggregate without an explicit group-by clause in the SELECT expression.</span></span> <span data-ttu-id="0a0d8-190">Bu durumda, tüm öğeleri tek bir grup kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-190">In this case, all elements are treated as a single group.</span></span> <span data-ttu-id="0a0d8-191">Bu, bir sabit üzerinde temel alan bir gruplama belirtme eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-191">This is equivalent of specifying a grouping based on a constant.</span></span> <span data-ttu-id="0a0d8-192">Örneğin, aşağıdaki ifade'yı uygulayın:</span><span class="sxs-lookup"><span data-stu-id="0a0d8-192">Take, for example, the following expression:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

<span data-ttu-id="0a0d8-193">Bu aşağıdakine eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="0a0d8-193">This is equivalent to the following:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

<span data-ttu-id="0a0d8-194">Grup tabanlı toplama içinde ifadeler, WHERE yan tümcesi ifade görünür olur ad çözümlemesi kapsamında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-194">Expressions inside the group-based aggregate are evaluated within the name-resolution scope that would be visible to the WHERE clause expression.</span></span>

<span data-ttu-id="0a0d8-195">Transact-SQL olduğu gibi Grup tabanlı toplamalar da BÜTÜN belirtebilirsiniz veya ayrı değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-195">As in Transact-SQL, group-based aggregates can also specify an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="0a0d8-196">AYRI değiştiricisi belirtilmemişse, toplama hesaplanan önce yinelenenleri birleşik giriş koleksiyondan ortadan kalkar.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-196">If the DISTINCT modifier is specified, duplicates are eliminated from the aggregate input collection, before the aggregate is computed.</span></span> <span data-ttu-id="0a0d8-197">Tüm değiştirici belirtilirse (veya herhangi bir değiştiricisi belirtilmişse), hiçbir yinelenen eleme gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-197">If the ALL modifier is specified (or if no modifier is specified), no duplicate elimination is performed.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a0d8-198">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-198">See also</span></span>

- [<span data-ttu-id="0a0d8-199">Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="0a0d8-199">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
