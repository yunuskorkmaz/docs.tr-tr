---
title: Toplu Kurallı İşlevler
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: 3f4bb84c45e503fc0018e7869f3b41ddab4581a6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251350"
---
# <a name="aggregate-canonical-functions"></a><span data-ttu-id="2ceb8-102">Toplu Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="2ceb8-102">Aggregate Canonical Functions</span></span>

<span data-ttu-id="2ceb8-103">Toplamalar, bir giriş değerlerini serisini, örneğin tek bir değer gibi azaltan ifadelerdir.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-103">Aggregates are expressions that reduce a series of input values into, for example, a single value.</span></span> <span data-ttu-id="2ceb8-104">Toplamalar normalde SELECT ifadesinin GROUP BY yan tümcesiyle birlikte kullanılır ve nerede kullanılabilecekleri konusunda kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-104">Aggregates are normally used in conjunction with the GROUP BY clause of the SELECT expression, and there are constraints on where they can be used.</span></span>

## <a name="aggregate-entity-sql-canonical-functions"></a><span data-ttu-id="2ceb8-105">Entity SQL kurallı işlevleri toplama</span><span class="sxs-lookup"><span data-stu-id="2ceb8-105">Aggregate Entity SQL canonical functions</span></span>

<span data-ttu-id="2ceb8-106">Aşağıda, toplu Entity SQL kurallı işlevler verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-106">The following are the aggregate Entity SQL canonical functions.</span></span>

### <a name="avgexpression"></a><span data-ttu-id="2ceb8-107">Ort (ifade)</span><span class="sxs-lookup"><span data-stu-id="2ceb8-107">Avg(expression)</span></span>

<span data-ttu-id="2ceb8-108">Null olmayan değerlerin ortalamasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-108">Returns the average of the non-null values.</span></span>

<span data-ttu-id="2ceb8-109">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-109">**Arguments**</span></span>

<span data-ttu-id="2ceb8-110">`Int32` ,`Int64`, Ve .`Decimal` `Double`</span><span class="sxs-lookup"><span data-stu-id="2ceb8-110">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="2ceb8-111">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-111">**Return Value**</span></span>

<span data-ttu-id="2ceb8-112">Türü `expression` `null` veya `null` tüm giriş değerleri değer ise.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-112">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="2ceb8-113">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-113">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a><span data-ttu-id="2ceb8-114">BigCount (ifade)</span><span class="sxs-lookup"><span data-stu-id="2ceb8-114">BigCount(expression)</span></span>

<span data-ttu-id="2ceb8-115">Null ve yinelenen değerler dahil olmak üzere toplamanın boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-115">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="2ceb8-116">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-116">**Arguments**</span></span>

<span data-ttu-id="2ceb8-117">Herhangi bir tür.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-117">Any type.</span></span>

<span data-ttu-id="2ceb8-118">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-118">**Return Value**</span></span>

<span data-ttu-id="2ceb8-119">Bir `Int64`.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-119">An `Int64`.</span></span>

<span data-ttu-id="2ceb8-120">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-120">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a><span data-ttu-id="2ceb8-121">Count (ifade)</span><span class="sxs-lookup"><span data-stu-id="2ceb8-121">Count(expression)</span></span>

<span data-ttu-id="2ceb8-122">Null ve yinelenen değerler dahil olmak üzere toplamanın boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-122">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="2ceb8-123">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-123">**Arguments**</span></span>

<span data-ttu-id="2ceb8-124">Herhangi bir tür.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-124">Any type.</span></span>

<span data-ttu-id="2ceb8-125">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-125">**Return Value**</span></span>

<span data-ttu-id="2ceb8-126">Bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-126">An `Int32`.</span></span>

<span data-ttu-id="2ceb8-127">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-127">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a><span data-ttu-id="2ceb8-128">Max (ifade)</span><span class="sxs-lookup"><span data-stu-id="2ceb8-128">Max(expression)</span></span>

<span data-ttu-id="2ceb8-129">Null olmayan değerlerin en büyük değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-129">Returns the maximum of the non-null values.</span></span>

<span data-ttu-id="2ceb8-130">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-130">**Arguments**</span></span>

<span data-ttu-id="2ceb8-131">A `Byte`, `Int16`, ,`Int32` ,,`Single`, ,`Decimal`,,,, ,`String`. `Double` `DateTime` `DateTimeOffset` `Time` `Byte` `Int64` `Binary`</span><span class="sxs-lookup"><span data-stu-id="2ceb8-131">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="2ceb8-132">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-132">**Return Value**</span></span>

<span data-ttu-id="2ceb8-133">Türü `expression` `null` veya `null` tüm giriş değerleri değer ise.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-133">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="2ceb8-134">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-134">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a><span data-ttu-id="2ceb8-135">Min (ifade)</span><span class="sxs-lookup"><span data-stu-id="2ceb8-135">Min(expression)</span></span>

<span data-ttu-id="2ceb8-136">Null olmayan değerlerin en küçük değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-136">Returns the minimum of the non-null values.</span></span>

<span data-ttu-id="2ceb8-137">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-137">**Arguments**</span></span>

<span data-ttu-id="2ceb8-138">A `Byte`, `Int16`, ,`Int32` ,,`Single`, ,`Decimal`,,,, ,`String`. `Double` `DateTime` `DateTimeOffset` `Time` `Byte` `Int64` `Binary`</span><span class="sxs-lookup"><span data-stu-id="2ceb8-138">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="2ceb8-139">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-139">**Return Value**</span></span>

<span data-ttu-id="2ceb8-140">Türü `expression` `null` veya `null` tüm giriş değerleri değer ise.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-140">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="2ceb8-141">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-141">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a><span data-ttu-id="2ceb8-142">StDev (ifade)</span><span class="sxs-lookup"><span data-stu-id="2ceb8-142">StDev(expression)</span></span>

<span data-ttu-id="2ceb8-143">Null olmayan değerlerin standart sapmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-143">Returns the standard deviation of the non-null values.</span></span>

<span data-ttu-id="2ceb8-144">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-144">**Arguments**</span></span>

<span data-ttu-id="2ceb8-145">Bir `Int32` ,`Int64`, ,.`Double` `Decimal`</span><span class="sxs-lookup"><span data-stu-id="2ceb8-145">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="2ceb8-146">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-146">**Return Value**</span></span>

<span data-ttu-id="2ceb8-147">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-147">A `Double`.</span></span> <span data-ttu-id="2ceb8-148">`Null`Tüm giriş değerleri `null` değer ise.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-148">`Null`, if all input values are `null` values.</span></span>

<span data-ttu-id="2ceb8-149">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-149">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a><span data-ttu-id="2ceb8-150">STDSAPMAS (ifade)</span><span class="sxs-lookup"><span data-stu-id="2ceb8-150">StDevP(expression)</span></span>

<span data-ttu-id="2ceb8-151">Tüm değerlerin popülasyonu için standart sapmayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-151">Returns the standard deviation for the population of all values.</span></span>

<span data-ttu-id="2ceb8-152">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-152">**Arguments**</span></span>

<span data-ttu-id="2ceb8-153">Bir `Int32` ,`Int64`, ,.`Double` `Decimal`</span><span class="sxs-lookup"><span data-stu-id="2ceb8-153">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="2ceb8-154">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-154">**Return Value**</span></span>

<span data-ttu-id="2ceb8-155">`null` Ya `Double` datümgiriş`null` değerleri değer ise.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-155">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="2ceb8-156">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-156">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a><span data-ttu-id="2ceb8-157">Sum (ifade)</span><span class="sxs-lookup"><span data-stu-id="2ceb8-157">Sum(expression)</span></span>

<span data-ttu-id="2ceb8-158">Null olmayan değerlerin toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-158">Returns the sum of the non-null values.</span></span>

<span data-ttu-id="2ceb8-159">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-159">**Arguments**</span></span>

<span data-ttu-id="2ceb8-160">Bir `Int32` ,`Int64`, ,.`Double` `Decimal`</span><span class="sxs-lookup"><span data-stu-id="2ceb8-160">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="2ceb8-161">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-161">**Return Value**</span></span>

<span data-ttu-id="2ceb8-162">`null` Ya `Double` datümgiriş`null` değerleri değer ise.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-162">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="2ceb8-163">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-163">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a><span data-ttu-id="2ceb8-164">Var (ifade)</span><span class="sxs-lookup"><span data-stu-id="2ceb8-164">Var(expression)</span></span>

<span data-ttu-id="2ceb8-165">Null olmayan tüm değerlerin varyansını döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-165">Returns the variance of all non-null values.</span></span>

<span data-ttu-id="2ceb8-166">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-166">**Arguments**</span></span>

<span data-ttu-id="2ceb8-167">Bir `Int32` ,`Int64`, ,.`Double` `Decimal`</span><span class="sxs-lookup"><span data-stu-id="2ceb8-167">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="2ceb8-168">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-168">**Return Value**</span></span>

<span data-ttu-id="2ceb8-169">`null` Ya `Double` datümgiriş`null` değerleri değer ise.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-169">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="2ceb8-170">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-170">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a><span data-ttu-id="2ceb8-171">VarP (ifade)</span><span class="sxs-lookup"><span data-stu-id="2ceb8-171">VarP(expression)</span></span>

<span data-ttu-id="2ceb8-172">Null olmayan tüm değerlerin popülasyon varyansını döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-172">Returns the variance for the population of all non-null values.</span></span>

<span data-ttu-id="2ceb8-173">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-173">**Arguments**</span></span>

<span data-ttu-id="2ceb8-174">Bir `Int32` ,`Int64`, ,.`Double` `Decimal`</span><span class="sxs-lookup"><span data-stu-id="2ceb8-174">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="2ceb8-175">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-175">**Return Value**</span></span>

<span data-ttu-id="2ceb8-176">`null` Ya `Double` datümgiriş`null` değerleri değer ise.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-176">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="2ceb8-177">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="2ceb8-177">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]

<span data-ttu-id="2ceb8-178">Eşdeğer işlevsellik, Microsoft SQL Istemci tarafından yönetilen sağlayıcıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-178">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="2ceb8-179">Daha fazla bilgi için bkz. [Entity Framework işlevleri Için SqlClient](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="2ceb8-179">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>

## <a name="collection-based-aggregates"></a><span data-ttu-id="2ceb8-180">Koleksiyon tabanlı toplamalar</span><span class="sxs-lookup"><span data-stu-id="2ceb8-180">Collection-based aggregates</span></span>

<span data-ttu-id="2ceb8-181">Koleksiyon tabanlı toplamalar (koleksiyon işlevleri) koleksiyonlar üzerinde çalışır ve bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-181">Collection-based aggregates (collection functions) operate on collections and return a value.</span></span> <span data-ttu-id="2ceb8-182">Örneğin, SIPARIŞLER tüm siparişlerin bir koleksiyonudur, en erken sevk tarihini aşağıdaki ifadeyle hesaplayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2ceb8-182">For example if ORDERS is a collection of all orders, you can calculate the earliest ship date with the following expression:</span></span>

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

<span data-ttu-id="2ceb8-183">Koleksiyon tabanlı toplamaların içindeki ifadeler geçerli ortam adı çözümleme kapsamı içinde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-183">Expressions inside collection-based aggregates are evaluated within the current ambient name-resolution scope.</span></span>

## <a name="group-based-aggregates"></a><span data-ttu-id="2ceb8-184">Grup tabanlı toplamalar</span><span class="sxs-lookup"><span data-stu-id="2ceb8-184">Group-based aggregates</span></span>

<span data-ttu-id="2ceb8-185">Grup tabanlı toplamalar GROUP BY yan tümcesi tarafından tanımlanan bir grup üzerinden hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-185">Group-based aggregates are calculated over a group as defined by the GROUP BY clause.</span></span> <span data-ttu-id="2ceb8-186">Sonuç içindeki her grup için, her bir gruptaki öğeler toplam hesaplamaya giriş olarak kullanılarak ayrı bir toplama hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-186">For each group in the result, a separate aggregate is calculated by using the elements in each group as input to the aggregate calculation.</span></span> <span data-ttu-id="2ceb8-187">Bir Group by yan tümcesi bir Select ifadesinde kullanıldığında, yalnızca gruplandırma ifadesi adları, toplamalar veya sabit ifadeler İzdüşüm veya order by yan tümcesinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-187">When a group-by clause is used in a select expression, only grouping expression names, aggregates, or constant expressions can be present in the projection or order-by clause.</span></span>

<span data-ttu-id="2ceb8-188">Aşağıdaki örnek, her bir ürün için sipariş edilen ortalama miktarı hesaplar:</span><span class="sxs-lookup"><span data-stu-id="2ceb8-188">The following example calculates the average quantity ordered for each product:</span></span>

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol
  group by ol.Product as p
```

<span data-ttu-id="2ceb8-189">SELECT ifadesinde açık bir Group by yan tümcesi olmadan grup tabanlı bir toplamaya sahip olmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-189">It's possible to have a group-based aggregate without an explicit group-by clause in the SELECT expression.</span></span> <span data-ttu-id="2ceb8-190">Bu durumda, tüm öğeler tek bir grup olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-190">In this case, all elements are treated as a single group.</span></span> <span data-ttu-id="2ceb8-191">Bu, bir sabiti temel alan bir gruplama belirtmeyle eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-191">This is equivalent of specifying a grouping based on a constant.</span></span> <span data-ttu-id="2ceb8-192">Örneğin, aşağıdaki ifadeyi alın:</span><span class="sxs-lookup"><span data-stu-id="2ceb8-192">Take, for example, the following expression:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

<span data-ttu-id="2ceb8-193">Bu, aşağıdaki gibi eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="2ceb8-193">This is equivalent to the following:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

<span data-ttu-id="2ceb8-194">Grup tabanlı toplamanın içindeki ifadeler, WHERE yan tümcesi ifadesinde görünür olacak ad çözümleme kapsamı içinde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-194">Expressions inside the group-based aggregate are evaluated within the name-resolution scope that would be visible to the WHERE clause expression.</span></span>

<span data-ttu-id="2ceb8-195">Transact-SQL ' de olduğu gibi, grup tabanlı toplamalarda de tümü veya ayrı bir değiştirici belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-195">As in Transact-SQL, group-based aggregates can also specify an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="2ceb8-196">AYRı değiştirici belirtilirse, toplama hesaplanmadan önce, yinelenen giriş koleksiyonundan yinelemeler ortadan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-196">If the DISTINCT modifier is specified, duplicates are eliminated from the aggregate input collection, before the aggregate is computed.</span></span> <span data-ttu-id="2ceb8-197">Tüm değiştirici belirtilirse (ya da değiştirici belirtilmemişse), yinelenen eleme yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-197">If the ALL modifier is specified (or if no modifier is specified), no duplicate elimination is performed.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ceb8-198">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ceb8-198">See also</span></span>

- [<span data-ttu-id="2ceb8-199">Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="2ceb8-199">Canonical Functions</span></span>](canonical-functions.md)
