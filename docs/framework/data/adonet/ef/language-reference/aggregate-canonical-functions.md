---
description: 'Daha fazla bilgi edinin: Birleşik kurallı Işlevler'
title: Toplu Kurallı İşlevler
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: e26888ac15553a592f7d2cb9b1a0941161115615
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697302"
---
# <a name="aggregate-canonical-functions"></a><span data-ttu-id="bbc6d-103">Toplu Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="bbc6d-103">Aggregate Canonical Functions</span></span>

<span data-ttu-id="bbc6d-104">Toplamalar, bir giriş değerlerini serisini, örneğin tek bir değer gibi azaltan ifadelerdir.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-104">Aggregates are expressions that reduce a series of input values into, for example, a single value.</span></span> <span data-ttu-id="bbc6d-105">Toplamalar normalde SELECT ifadesinin GROUP BY yan tümcesiyle birlikte kullanılır ve nerede kullanılabilecekleri konusunda kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-105">Aggregates are normally used in conjunction with the GROUP BY clause of the SELECT expression, and there are constraints on where they can be used.</span></span>

## <a name="aggregate-entity-sql-canonical-functions"></a><span data-ttu-id="bbc6d-106">Entity SQL kurallı işlevleri toplama</span><span class="sxs-lookup"><span data-stu-id="bbc6d-106">Aggregate Entity SQL canonical functions</span></span>

<span data-ttu-id="bbc6d-107">Aşağıda, toplu Entity SQL kurallı işlevler verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-107">The following are the aggregate Entity SQL canonical functions.</span></span>

### <a name="avgexpression"></a><span data-ttu-id="bbc6d-108">Ort (ifade)</span><span class="sxs-lookup"><span data-stu-id="bbc6d-108">Avg(expression)</span></span>

<span data-ttu-id="bbc6d-109">Null olmayan değerlerin ortalamasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-109">Returns the average of the non-null values.</span></span>

<span data-ttu-id="bbc6d-110">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-110">**Arguments**</span></span>

<span data-ttu-id="bbc6d-111">`Int32`,, `Int64` `Double` Ve `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="bbc6d-111">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="bbc6d-112">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-112">**Return Value**</span></span>

<span data-ttu-id="bbc6d-113">Türü `expression` veya `null` tüm giriş değerleri `null` değer ise.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-113">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="bbc6d-114">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-114">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a><span data-ttu-id="bbc6d-115">BigCount (ifade)</span><span class="sxs-lookup"><span data-stu-id="bbc6d-115">BigCount(expression)</span></span>

<span data-ttu-id="bbc6d-116">Null ve yinelenen değerler dahil olmak üzere toplamanın boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-116">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="bbc6d-117">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-117">**Arguments**</span></span>

<span data-ttu-id="bbc6d-118">Herhangi bir tür.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-118">Any type.</span></span>

<span data-ttu-id="bbc6d-119">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-119">**Return Value**</span></span>

<span data-ttu-id="bbc6d-120">Bir `Int64` .</span><span class="sxs-lookup"><span data-stu-id="bbc6d-120">An `Int64`.</span></span>

<span data-ttu-id="bbc6d-121">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-121">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a><span data-ttu-id="bbc6d-122">Count (ifade)</span><span class="sxs-lookup"><span data-stu-id="bbc6d-122">Count(expression)</span></span>

<span data-ttu-id="bbc6d-123">Null ve yinelenen değerler dahil olmak üzere toplamanın boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-123">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="bbc6d-124">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-124">**Arguments**</span></span>

<span data-ttu-id="bbc6d-125">Herhangi bir tür.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-125">Any type.</span></span>

<span data-ttu-id="bbc6d-126">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-126">**Return Value**</span></span>

<span data-ttu-id="bbc6d-127">Bir `Int32` .</span><span class="sxs-lookup"><span data-stu-id="bbc6d-127">An `Int32`.</span></span>

<span data-ttu-id="bbc6d-128">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-128">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a><span data-ttu-id="bbc6d-129">Max (ifade)</span><span class="sxs-lookup"><span data-stu-id="bbc6d-129">Max(expression)</span></span>

<span data-ttu-id="bbc6d-130">Null olmayan değerlerin en büyük değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-130">Returns the maximum of the non-null values.</span></span>

<span data-ttu-id="bbc6d-131">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-131">**Arguments**</span></span>

<span data-ttu-id="bbc6d-132">A `Byte` , `Int16` , `Int32` , `Int64` , `Byte` , `Single` , `Double` , `Decimal` , `DateTime` , `DateTimeOffset` , `Time` , `String` , `Binary` .</span><span class="sxs-lookup"><span data-stu-id="bbc6d-132">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="bbc6d-133">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-133">**Return Value**</span></span>

<span data-ttu-id="bbc6d-134">Türü `expression` veya `null` tüm giriş değerleri `null` değer ise.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-134">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="bbc6d-135">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-135">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a><span data-ttu-id="bbc6d-136">Min (ifade)</span><span class="sxs-lookup"><span data-stu-id="bbc6d-136">Min(expression)</span></span>

<span data-ttu-id="bbc6d-137">Null olmayan değerlerin en küçük değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-137">Returns the minimum of the non-null values.</span></span>

<span data-ttu-id="bbc6d-138">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-138">**Arguments**</span></span>

<span data-ttu-id="bbc6d-139">A `Byte` , `Int16` , `Int32` , `Int64` , `Byte` , `Single` , `Double` , `Decimal` , `DateTime` , `DateTimeOffset` , `Time` , `String` , `Binary` .</span><span class="sxs-lookup"><span data-stu-id="bbc6d-139">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="bbc6d-140">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-140">**Return Value**</span></span>

<span data-ttu-id="bbc6d-141">Türü `expression` veya `null` tüm giriş değerleri `null` değer ise.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-141">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="bbc6d-142">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-142">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a><span data-ttu-id="bbc6d-143">StDev (ifade)</span><span class="sxs-lookup"><span data-stu-id="bbc6d-143">StDev(expression)</span></span>

<span data-ttu-id="bbc6d-144">Null olmayan değerlerin standart sapmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-144">Returns the standard deviation of the non-null values.</span></span>

<span data-ttu-id="bbc6d-145">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-145">**Arguments**</span></span>

<span data-ttu-id="bbc6d-146">Bir `Int32` , `Int64` , `Double` , `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="bbc6d-146">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="bbc6d-147">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-147">**Return Value**</span></span>

<span data-ttu-id="bbc6d-148">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-148">A `Double`.</span></span> <span data-ttu-id="bbc6d-149">`Null`Tüm giriş değerleri `null` değer ise.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-149">`Null`, if all input values are `null` values.</span></span>

<span data-ttu-id="bbc6d-150">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-150">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a><span data-ttu-id="bbc6d-151">STDSAPMAS (ifade)</span><span class="sxs-lookup"><span data-stu-id="bbc6d-151">StDevP(expression)</span></span>

<span data-ttu-id="bbc6d-152">Tüm değerlerin popülasyonu için standart sapmayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-152">Returns the standard deviation for the population of all values.</span></span>

<span data-ttu-id="bbc6d-153">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-153">**Arguments**</span></span>

<span data-ttu-id="bbc6d-154">Bir `Int32` , `Int64` , `Double` , `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="bbc6d-154">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="bbc6d-155">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-155">**Return Value**</span></span>

<span data-ttu-id="bbc6d-156">`Double`Ya da `null` tüm giriş değerleri `null` değer ise.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-156">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="bbc6d-157">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-157">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a><span data-ttu-id="bbc6d-158">Sum (ifade)</span><span class="sxs-lookup"><span data-stu-id="bbc6d-158">Sum(expression)</span></span>

<span data-ttu-id="bbc6d-159">Null olmayan değerlerin toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-159">Returns the sum of the non-null values.</span></span>

<span data-ttu-id="bbc6d-160">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-160">**Arguments**</span></span>

<span data-ttu-id="bbc6d-161">Bir `Int32` , `Int64` , `Double` , `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="bbc6d-161">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="bbc6d-162">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-162">**Return Value**</span></span>

<span data-ttu-id="bbc6d-163">`Double`Ya da `null` tüm giriş değerleri `null` değer ise.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-163">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="bbc6d-164">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-164">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a><span data-ttu-id="bbc6d-165">Var (ifade)</span><span class="sxs-lookup"><span data-stu-id="bbc6d-165">Var(expression)</span></span>

<span data-ttu-id="bbc6d-166">Null olmayan tüm değerlerin varyansını döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-166">Returns the variance of all non-null values.</span></span>

<span data-ttu-id="bbc6d-167">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-167">**Arguments**</span></span>

<span data-ttu-id="bbc6d-168">Bir `Int32` , `Int64` , `Double` , `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="bbc6d-168">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="bbc6d-169">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-169">**Return Value**</span></span>

<span data-ttu-id="bbc6d-170">`Double`Ya da `null` tüm giriş değerleri `null` değer ise.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-170">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="bbc6d-171">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-171">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a><span data-ttu-id="bbc6d-172">VarP (ifade)</span><span class="sxs-lookup"><span data-stu-id="bbc6d-172">VarP(expression)</span></span>

<span data-ttu-id="bbc6d-173">Null olmayan tüm değerlerin popülasyon varyansını döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-173">Returns the variance for the population of all non-null values.</span></span>

<span data-ttu-id="bbc6d-174">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-174">**Arguments**</span></span>

<span data-ttu-id="bbc6d-175">Bir `Int32` , `Int64` , `Double` , `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="bbc6d-175">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="bbc6d-176">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-176">**Return Value**</span></span>

<span data-ttu-id="bbc6d-177">`Double`Ya da `null` tüm giriş değerleri `null` değer ise.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-177">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="bbc6d-178">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="bbc6d-178">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]

<span data-ttu-id="bbc6d-179">Eşdeğer işlevsellik, Microsoft SQL Istemci tarafından yönetilen sağlayıcıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-179">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="bbc6d-180">Daha fazla bilgi için bkz. [Entity Framework işlevleri Için SqlClient](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="bbc6d-180">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>

## <a name="collection-based-aggregates"></a><span data-ttu-id="bbc6d-181">Koleksiyon tabanlı toplamalar</span><span class="sxs-lookup"><span data-stu-id="bbc6d-181">Collection-based aggregates</span></span>

<span data-ttu-id="bbc6d-182">Koleksiyon tabanlı toplamalar (koleksiyon işlevleri) koleksiyonlar üzerinde çalışır ve bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-182">Collection-based aggregates (collection functions) operate on collections and return a value.</span></span> <span data-ttu-id="bbc6d-183">Örneğin, SIPARIŞLER tüm siparişlerin bir koleksiyonudur, en erken sevk tarihini aşağıdaki ifadeyle hesaplayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bbc6d-183">For example if ORDERS is a collection of all orders, you can calculate the earliest ship date with the following expression:</span></span>

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

<span data-ttu-id="bbc6d-184">Koleksiyon tabanlı toplamaların içindeki ifadeler geçerli ortam adı çözümleme kapsamı içinde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-184">Expressions inside collection-based aggregates are evaluated within the current ambient name-resolution scope.</span></span>

## <a name="group-based-aggregates"></a><span data-ttu-id="bbc6d-185">Grup tabanlı toplamalar</span><span class="sxs-lookup"><span data-stu-id="bbc6d-185">Group-based aggregates</span></span>

<span data-ttu-id="bbc6d-186">Grup tabanlı toplamalar GROUP BY yan tümcesi tarafından tanımlanan bir grup üzerinden hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-186">Group-based aggregates are calculated over a group as defined by the GROUP BY clause.</span></span> <span data-ttu-id="bbc6d-187">Sonuç içindeki her grup için, her bir gruptaki öğeler toplam hesaplamaya giriş olarak kullanılarak ayrı bir toplama hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-187">For each group in the result, a separate aggregate is calculated by using the elements in each group as input to the aggregate calculation.</span></span> <span data-ttu-id="bbc6d-188">Bir Group by yan tümcesi bir Select ifadesinde kullanıldığında, yalnızca gruplandırma ifadesi adları, toplamalar veya sabit ifadeler İzdüşüm veya order by yan tümcesinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-188">When a group-by clause is used in a select expression, only grouping expression names, aggregates, or constant expressions can be present in the projection or order-by clause.</span></span>

<span data-ttu-id="bbc6d-189">Aşağıdaki örnek, her bir ürün için sipariş edilen ortalama miktarı hesaplar:</span><span class="sxs-lookup"><span data-stu-id="bbc6d-189">The following example calculates the average quantity ordered for each product:</span></span>

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol
  group by ol.Product as p
```

<span data-ttu-id="bbc6d-190">SELECT ifadesinde açık bir Group by yan tümcesi olmadan grup tabanlı bir toplamaya sahip olmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-190">It's possible to have a group-based aggregate without an explicit group-by clause in the SELECT expression.</span></span> <span data-ttu-id="bbc6d-191">Bu durumda, tüm öğeler tek bir grup olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-191">In this case, all elements are treated as a single group.</span></span> <span data-ttu-id="bbc6d-192">Bu, bir sabiti temel alan bir gruplama belirtmeyle eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-192">This is equivalent of specifying a grouping based on a constant.</span></span> <span data-ttu-id="bbc6d-193">Örneğin, aşağıdaki ifadeyi alın:</span><span class="sxs-lookup"><span data-stu-id="bbc6d-193">Take, for example, the following expression:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

<span data-ttu-id="bbc6d-194">Bu, aşağıdaki gibi eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="bbc6d-194">This is equivalent to the following:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

<span data-ttu-id="bbc6d-195">Grup tabanlı toplamanın içindeki ifadeler, WHERE yan tümcesi ifadesinde görünür olacak ad çözümleme kapsamı içinde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-195">Expressions inside the group-based aggregate are evaluated within the name-resolution scope that would be visible to the WHERE clause expression.</span></span>

<span data-ttu-id="bbc6d-196">Transact-SQL ' de olduğu gibi, grup tabanlı toplamalarda de tümü veya ayrı bir değiştirici belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-196">As in Transact-SQL, group-based aggregates can also specify an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="bbc6d-197">AYRı değiştirici belirtilirse, toplama hesaplanmadan önce, yinelenen giriş koleksiyonundan yinelemeler ortadan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-197">If the DISTINCT modifier is specified, duplicates are eliminated from the aggregate input collection, before the aggregate is computed.</span></span> <span data-ttu-id="bbc6d-198">Tüm değiştirici belirtilirse (ya da değiştirici belirtilmemişse), yinelenen eleme yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-198">If the ALL modifier is specified (or if no modifier is specified), no duplicate elimination is performed.</span></span>

## <a name="see-also"></a><span data-ttu-id="bbc6d-199">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbc6d-199">See also</span></span>

- [<span data-ttu-id="bbc6d-200">Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="bbc6d-200">Canonical Functions</span></span>](canonical-functions.md)
