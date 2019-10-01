---
title: Toplama Işlevleri (Entity Framework için SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 3dbd4c0a24a5fc41153ea16747325e824669b0e5
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700053"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="367e5-102">Toplama Işlevleri (Entity Framework için SqlClient)</span><span class="sxs-lookup"><span data-stu-id="367e5-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="367e5-103">SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı toplama işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="367e5-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="367e5-104">Toplama işlevleri, bir giriş değerleri kümesi üzerinde hesaplamalar gerçekleştirir ve bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="367e5-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="367e5-105">Bu işlevler, SqlClient kullandığınızda kullanılabilir olan SqlServer ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="367e5-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="367e5-106">Bir sağlayıcının ad alanı özelliği Entity Framework, bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan öneki bulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="367e5-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="367e5-107">Aşağıdaki, SqlClient toplama işlevleridir.</span><span class="sxs-lookup"><span data-stu-id="367e5-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="367e5-108">Ort (ifade)</span><span class="sxs-lookup"><span data-stu-id="367e5-108">AVG(expression)</span></span>

<span data-ttu-id="367e5-109">Bir koleksiyondaki değerlerin ortalamasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="367e5-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="367e5-110">Null değerler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="367e5-110">Null values are ignored.</span></span>

<span data-ttu-id="367e5-111">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="367e5-111">**Arguments**</span></span>

<span data-ttu-id="367e5-112">@No__t-0, `Int64`, `Double` ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="367e5-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="367e5-113">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="367e5-113">**Return Value**</span></span>

<span data-ttu-id="367e5-114">@No__t türü-0.</span><span class="sxs-lookup"><span data-stu-id="367e5-114">The type of `expression`.</span></span>

<span data-ttu-id="367e5-115">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="367e5-115">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="367e5-116">CHECKSUM_AGG (koleksiyon)</span><span class="sxs-lookup"><span data-stu-id="367e5-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="367e5-117">Bir koleksiyondaki değerlerin sağlama toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="367e5-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="367e5-118">Null değerler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="367e5-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="367e5-119">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="367e5-119">**Arguments**</span></span>
 
 <span data-ttu-id="367e5-120">Bir koleksiyon (`Int32`).</span><span class="sxs-lookup"><span data-stu-id="367e5-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="367e5-121">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="367e5-121">**Return Value**</span></span>
 
 <span data-ttu-id="367e5-122">@No__t-0.</span><span class="sxs-lookup"><span data-stu-id="367e5-122">An `Int32`.</span></span>
 
 <span data-ttu-id="367e5-123">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="367e5-123">**Example**</span></span>
 
[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="367e5-124">COUNT (ifade)</span><span class="sxs-lookup"><span data-stu-id="367e5-124">COUNT(expression)</span></span>

<span data-ttu-id="367e5-125">Bir koleksiyondaki öğelerin sayısını `Int32` olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="367e5-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="367e5-126">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="367e5-126">**Arguments**</span></span>

<span data-ttu-id="367e5-127">Bir Collection @ no__t-0T >, burada T aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="367e5-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="367e5-128">`Guid` (SQL Server 2000 ' de döndürülmez)</span><span class="sxs-lookup"><span data-stu-id="367e5-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="367e5-129">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="367e5-129">**Return Value**</span></span>

<span data-ttu-id="367e5-130">@No__t-0.</span><span class="sxs-lookup"><span data-stu-id="367e5-130">An `Int32`.</span></span>

<span data-ttu-id="367e5-131">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="367e5-131">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]
 
## <a name="count_bigexpression"></a><span data-ttu-id="367e5-132">COUNT_BıG (ifade)</span><span class="sxs-lookup"><span data-stu-id="367e5-132">COUNT_BIG(expression)</span></span>
 
<span data-ttu-id="367e5-133">Bir koleksiyondaki öğelerin sayısını `bigint` olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="367e5-133">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="367e5-134">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="367e5-134">**Arguments**</span></span>
 
 <span data-ttu-id="367e5-135">Bir koleksiyon (T), burada T aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="367e5-135">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="367e5-136">`Guid` (SQL Server 2000 ' de döndürülmez)</span><span class="sxs-lookup"><span data-stu-id="367e5-136">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="367e5-137">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="367e5-137">**Return Value**</span></span>

<span data-ttu-id="367e5-138">@No__t-0.</span><span class="sxs-lookup"><span data-stu-id="367e5-138">An `Int64`.</span></span>

<span data-ttu-id="367e5-139">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="367e5-139">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="367e5-140">MAX (ifade)</span><span class="sxs-lookup"><span data-stu-id="367e5-140">MAX(expression)</span></span>

<span data-ttu-id="367e5-141">Koleksiyonun en büyük değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="367e5-141">Returns the maximum value the collection.</span></span>

<span data-ttu-id="367e5-142">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="367e5-142">**Arguments**</span></span>

<span data-ttu-id="367e5-143">Bir koleksiyon (T), burada T aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="367e5-143">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="367e5-144">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="367e5-144">**Return Value**</span></span>

<span data-ttu-id="367e5-145">@No__t türü-0.</span><span class="sxs-lookup"><span data-stu-id="367e5-145">The type of `expression`.</span></span>

<span data-ttu-id="367e5-146">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="367e5-146">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="367e5-147">MIN (ifade)</span><span class="sxs-lookup"><span data-stu-id="367e5-147">MIN(expression)</span></span>

<span data-ttu-id="367e5-148">Bir koleksiyondaki en küçük değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="367e5-148">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="367e5-149">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="367e5-149">**Arguments**</span></span>

<span data-ttu-id="367e5-150">Bir koleksiyon (T), burada T aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="367e5-150">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="367e5-151">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="367e5-151">**Return Value**</span></span>

<span data-ttu-id="367e5-152">@No__t türü-0.</span><span class="sxs-lookup"><span data-stu-id="367e5-152">The type of `expression`.</span></span>

<span data-ttu-id="367e5-153">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="367e5-153">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="367e5-154">STDEV (ifade)</span><span class="sxs-lookup"><span data-stu-id="367e5-154">STDEV(expression)</span></span>

<span data-ttu-id="367e5-155">Belirtilen ifadedeki tüm değerlerin istatistiksel standart sapmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="367e5-155">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="367e5-156">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="367e5-156">**Arguments**</span></span>

<span data-ttu-id="367e5-157">Bir koleksiyon (`Double`).</span><span class="sxs-lookup"><span data-stu-id="367e5-157">A Collection(`Double`).</span></span>

<span data-ttu-id="367e5-158">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="367e5-158">**Return Value**</span></span>

<span data-ttu-id="367e5-159">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="367e5-159">A `Double`.</span></span>

<span data-ttu-id="367e5-160">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="367e5-160">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="367e5-161">STDSAPMAS (ifade)</span><span class="sxs-lookup"><span data-stu-id="367e5-161">STDEVP(expression)</span></span>

<span data-ttu-id="367e5-162">Belirtilen ifadedeki tüm değerler için popülasyonun istatistiksel standart sapmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="367e5-162">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="367e5-163">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="367e5-163">**Arguments**</span></span>

<span data-ttu-id="367e5-164">Bir koleksiyon (`Double`).</span><span class="sxs-lookup"><span data-stu-id="367e5-164">A Collection(`Double`).</span></span>

<span data-ttu-id="367e5-165">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="367e5-165">**Return Value**</span></span>

<span data-ttu-id="367e5-166">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="367e5-166">A `Double`.</span></span>

<span data-ttu-id="367e5-167">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="367e5-167">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="367e5-168">SUM (ifade)</span><span class="sxs-lookup"><span data-stu-id="367e5-168">SUM(expression)</span></span>

<span data-ttu-id="367e5-169">Koleksiyondaki tüm değerlerin toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="367e5-169">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="367e5-170">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="367e5-170">**Arguments**</span></span>

<span data-ttu-id="367e5-171">T 'nin şu türlerden biri olduğu bir koleksiyon (T): `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="367e5-171">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="367e5-172">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="367e5-172">**Return Value**</span></span>

<span data-ttu-id="367e5-173">@No__t türü-0.</span><span class="sxs-lookup"><span data-stu-id="367e5-173">The type of `expression`.</span></span>

<span data-ttu-id="367e5-174">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="367e5-174">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="367e5-175">VAR (ifade)</span><span class="sxs-lookup"><span data-stu-id="367e5-175">VAR(expression)</span></span>

<span data-ttu-id="367e5-176">Belirtilen ifadedeki tüm değerlerin istatistiksel varyansını döndürür.</span><span class="sxs-lookup"><span data-stu-id="367e5-176">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="367e5-177">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="367e5-177">**Arguments**</span></span>

<span data-ttu-id="367e5-178">Bir koleksiyon (`Double`).</span><span class="sxs-lookup"><span data-stu-id="367e5-178">A Collection(`Double`).</span></span>

<span data-ttu-id="367e5-179">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="367e5-179">**Return Value**</span></span>

<span data-ttu-id="367e5-180">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="367e5-180">A `Double`.</span></span>

<span data-ttu-id="367e5-181">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="367e5-181">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="367e5-182">VARP (ifade)</span><span class="sxs-lookup"><span data-stu-id="367e5-182">VARP(expression)</span></span>

<span data-ttu-id="367e5-183">Belirtilen ifadedeki tüm değerler için popülasyon için istatistiksel varyansı döndürür.</span><span class="sxs-lookup"><span data-stu-id="367e5-183">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="367e5-184">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="367e5-184">**Arguments**</span></span>

<span data-ttu-id="367e5-185">Bir koleksiyon (`Double`).</span><span class="sxs-lookup"><span data-stu-id="367e5-185">A Collection(`Double`).</span></span>

<span data-ttu-id="367e5-186">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="367e5-186">**Return Value**</span></span>

<span data-ttu-id="367e5-187">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="367e5-187">A `Double`.</span></span>

<span data-ttu-id="367e5-188">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="367e5-188">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="367e5-189">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="367e5-189">See also</span></span>

- [<span data-ttu-id="367e5-190">Toplama Işlevleri (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="367e5-190">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="367e5-191">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="367e5-191">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="367e5-192">Toplu Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="367e5-192">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
