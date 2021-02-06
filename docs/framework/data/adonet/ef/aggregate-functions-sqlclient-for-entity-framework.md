---
description: 'Daha fazla bilgi edinin: toplama Işlevleri (Entity Framework için SqlClient)'
title: Toplama Işlevleri (Entity Framework için SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: b9f1ff8c75fc09de7532b459090b0b5cd1d47262
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651086"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="be37c-103">Toplama Işlevleri (Entity Framework için SqlClient)</span><span class="sxs-lookup"><span data-stu-id="be37c-103">Aggregate Functions (SqlClient for Entity Framework)</span></span>

<span data-ttu-id="be37c-104">SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı toplama işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="be37c-104">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="be37c-105">Toplama işlevleri, bir giriş değerleri kümesi üzerinde hesaplamalar gerçekleştirir ve bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="be37c-105">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="be37c-106">Bu işlevler, SqlClient kullandığınızda kullanılabilir olan SqlServer ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="be37c-106">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="be37c-107">Bir sağlayıcının ad alanı özelliği Entity Framework, bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan öneki bulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="be37c-107">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="be37c-108">Aşağıdaki, SqlClient toplama işlevleridir.</span><span class="sxs-lookup"><span data-stu-id="be37c-108">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="be37c-109">Ort (ifade)</span><span class="sxs-lookup"><span data-stu-id="be37c-109">AVG(expression)</span></span>

<span data-ttu-id="be37c-110">Bir koleksiyondaki değerlerin ortalamasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="be37c-110">Returns the average of the values in a collection.</span></span> <span data-ttu-id="be37c-111">Null değerler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="be37c-111">Null values are ignored.</span></span>

<span data-ttu-id="be37c-112">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="be37c-112">**Arguments**</span></span>

<span data-ttu-id="be37c-113">`Int32`,, `Int64` `Double` Ve `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="be37c-113">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="be37c-114">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="be37c-114">**Return Value**</span></span>

<span data-ttu-id="be37c-115">Türü `expression` .</span><span class="sxs-lookup"><span data-stu-id="be37c-115">The type of `expression`.</span></span>

<span data-ttu-id="be37c-116">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="be37c-116">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="be37c-117">CHECKSUM_AGG (koleksiyon)</span><span class="sxs-lookup"><span data-stu-id="be37c-117">CHECKSUM_AGG(collection)</span></span>

 <span data-ttu-id="be37c-118">Bir koleksiyondaki değerlerin sağlama toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="be37c-118">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="be37c-119">Null değerler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="be37c-119">Null values are ignored.</span></span>

 <span data-ttu-id="be37c-120">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="be37c-120">**Arguments**</span></span>

 <span data-ttu-id="be37c-121">Bir koleksiyon ( `Int32` ).</span><span class="sxs-lookup"><span data-stu-id="be37c-121">A Collection(`Int32`).</span></span>

 <span data-ttu-id="be37c-122">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="be37c-122">**Return Value**</span></span>

 <span data-ttu-id="be37c-123">Bir `Int32` .</span><span class="sxs-lookup"><span data-stu-id="be37c-123">An `Int32`.</span></span>

 <span data-ttu-id="be37c-124">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="be37c-124">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a><span data-ttu-id="be37c-125">COUNT (ifade)</span><span class="sxs-lookup"><span data-stu-id="be37c-125">COUNT(expression)</span></span>

<span data-ttu-id="be37c-126">Bir koleksiyondaki öğelerin sayısını bir olarak döndürür `Int32` .</span><span class="sxs-lookup"><span data-stu-id="be37c-126">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="be37c-127">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="be37c-127">**Arguments**</span></span>

<span data-ttu-id="be37c-128">Bir koleksiyon \<T> , T aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="be37c-128">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="be37c-129">`Guid` (SQL Server 2000 ' de döndürülmez)</span><span class="sxs-lookup"><span data-stu-id="be37c-129">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="be37c-130">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="be37c-130">**Return Value**</span></span>

<span data-ttu-id="be37c-131">Bir `Int32` .</span><span class="sxs-lookup"><span data-stu-id="be37c-131">An `Int32`.</span></span>

<span data-ttu-id="be37c-132">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="be37c-132">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a><span data-ttu-id="be37c-133">COUNT_BIG (ifade)</span><span class="sxs-lookup"><span data-stu-id="be37c-133">COUNT_BIG(expression)</span></span>

<span data-ttu-id="be37c-134">Bir koleksiyondaki öğelerin sayısını bir olarak döndürür `bigint` .</span><span class="sxs-lookup"><span data-stu-id="be37c-134">Returns the number of items in a collection as a `bigint`.</span></span>

 <span data-ttu-id="be37c-135">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="be37c-135">**Arguments**</span></span>

 <span data-ttu-id="be37c-136">Bir koleksiyon (T), burada T aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="be37c-136">A Collection(T), where T is one of the following types:</span></span>

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="be37c-137">`Guid` (SQL Server 2000 ' de döndürülmez)</span><span class="sxs-lookup"><span data-stu-id="be37c-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="be37c-138">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="be37c-138">**Return Value**</span></span>

<span data-ttu-id="be37c-139">Bir `Int64` .</span><span class="sxs-lookup"><span data-stu-id="be37c-139">An `Int64`.</span></span>

<span data-ttu-id="be37c-140">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="be37c-140">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="be37c-141">MAX (ifade)</span><span class="sxs-lookup"><span data-stu-id="be37c-141">MAX(expression)</span></span>

<span data-ttu-id="be37c-142">Koleksiyonun en büyük değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="be37c-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="be37c-143">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="be37c-143">**Arguments**</span></span>

<span data-ttu-id="be37c-144">Bir koleksiyon (T), burada T aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="be37c-144">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="be37c-145">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="be37c-145">**Return Value**</span></span>

<span data-ttu-id="be37c-146">Türü `expression` .</span><span class="sxs-lookup"><span data-stu-id="be37c-146">The type of `expression`.</span></span>

<span data-ttu-id="be37c-147">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="be37c-147">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="be37c-148">MIN (ifade)</span><span class="sxs-lookup"><span data-stu-id="be37c-148">MIN(expression)</span></span>

<span data-ttu-id="be37c-149">Bir koleksiyondaki en küçük değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="be37c-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="be37c-150">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="be37c-150">**Arguments**</span></span>

<span data-ttu-id="be37c-151">Bir koleksiyon (T), burada T aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="be37c-151">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="be37c-152">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="be37c-152">**Return Value**</span></span>

<span data-ttu-id="be37c-153">Türü `expression` .</span><span class="sxs-lookup"><span data-stu-id="be37c-153">The type of `expression`.</span></span>

<span data-ttu-id="be37c-154">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="be37c-154">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="be37c-155">STDEV (ifade)</span><span class="sxs-lookup"><span data-stu-id="be37c-155">STDEV(expression)</span></span>

<span data-ttu-id="be37c-156">Belirtilen ifadedeki tüm değerlerin istatistiksel standart sapmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="be37c-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="be37c-157">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="be37c-157">**Arguments**</span></span>

<span data-ttu-id="be37c-158">Bir koleksiyon ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="be37c-158">A Collection(`Double`).</span></span>

<span data-ttu-id="be37c-159">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="be37c-159">**Return Value**</span></span>

<span data-ttu-id="be37c-160">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="be37c-160">A `Double`.</span></span>

<span data-ttu-id="be37c-161">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="be37c-161">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="be37c-162">STDSAPMAS (ifade)</span><span class="sxs-lookup"><span data-stu-id="be37c-162">STDEVP(expression)</span></span>

<span data-ttu-id="be37c-163">Belirtilen ifadedeki tüm değerler için popülasyonun istatistiksel standart sapmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="be37c-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="be37c-164">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="be37c-164">**Arguments**</span></span>

<span data-ttu-id="be37c-165">Bir koleksiyon ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="be37c-165">A Collection(`Double`).</span></span>

<span data-ttu-id="be37c-166">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="be37c-166">**Return Value**</span></span>

<span data-ttu-id="be37c-167">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="be37c-167">A `Double`.</span></span>

<span data-ttu-id="be37c-168">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="be37c-168">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="be37c-169">SUM (ifade)</span><span class="sxs-lookup"><span data-stu-id="be37c-169">SUM(expression)</span></span>

<span data-ttu-id="be37c-170">Koleksiyondaki tüm değerlerin toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="be37c-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="be37c-171">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="be37c-171">**Arguments**</span></span>

<span data-ttu-id="be37c-172">T (T): `Int32` , `Int64` ,, `Double` `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="be37c-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="be37c-173">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="be37c-173">**Return Value**</span></span>

<span data-ttu-id="be37c-174">Türü `expression` .</span><span class="sxs-lookup"><span data-stu-id="be37c-174">The type of `expression`.</span></span>

<span data-ttu-id="be37c-175">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="be37c-175">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="be37c-176">VAR (ifade)</span><span class="sxs-lookup"><span data-stu-id="be37c-176">VAR(expression)</span></span>

<span data-ttu-id="be37c-177">Belirtilen ifadedeki tüm değerlerin istatistiksel varyansını döndürür.</span><span class="sxs-lookup"><span data-stu-id="be37c-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="be37c-178">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="be37c-178">**Arguments**</span></span>

<span data-ttu-id="be37c-179">Bir koleksiyon ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="be37c-179">A Collection(`Double`).</span></span>

<span data-ttu-id="be37c-180">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="be37c-180">**Return Value**</span></span>

<span data-ttu-id="be37c-181">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="be37c-181">A `Double`.</span></span>

<span data-ttu-id="be37c-182">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="be37c-182">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="be37c-183">VARP (ifade)</span><span class="sxs-lookup"><span data-stu-id="be37c-183">VARP(expression)</span></span>

<span data-ttu-id="be37c-184">Belirtilen ifadedeki tüm değerler için popülasyon için istatistiksel varyansı döndürür.</span><span class="sxs-lookup"><span data-stu-id="be37c-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="be37c-185">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="be37c-185">**Arguments**</span></span>

<span data-ttu-id="be37c-186">Bir koleksiyon ( `Double` ).</span><span class="sxs-lookup"><span data-stu-id="be37c-186">A Collection(`Double`).</span></span>

<span data-ttu-id="be37c-187">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="be37c-187">**Return Value**</span></span>

<span data-ttu-id="be37c-188">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="be37c-188">A `Double`.</span></span>

<span data-ttu-id="be37c-189">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="be37c-189">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a><span data-ttu-id="be37c-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be37c-190">See also</span></span>

- [<span data-ttu-id="be37c-191">Toplama Işlevleri (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="be37c-191">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="be37c-192">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="be37c-192">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="be37c-193">Toplu Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="be37c-193">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
