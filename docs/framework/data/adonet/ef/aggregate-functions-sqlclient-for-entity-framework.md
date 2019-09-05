---
title: Toplama Işlevleri (Entity Framework için SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: cf476192cf049f230c1956e390d215ad4abaa821
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251701"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="4bf32-102">Toplama Işlevleri (Entity Framework için SqlClient)</span><span class="sxs-lookup"><span data-stu-id="4bf32-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="4bf32-103">SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı toplama işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4bf32-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="4bf32-104">Toplama işlevleri, bir giriş değerleri kümesi üzerinde hesaplamalar gerçekleştirir ve bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bf32-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="4bf32-105">Bu işlevler, SqlClient kullandığınızda kullanılabilir olan SqlServer ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="4bf32-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="4bf32-106">Bir sağlayıcının ad alanı özelliği Entity Framework, bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan öneki bulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4bf32-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="4bf32-107">Aşağıdaki, SqlClient toplama işlevleridir.</span><span class="sxs-lookup"><span data-stu-id="4bf32-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="4bf32-108">Ort (ifade)</span><span class="sxs-lookup"><span data-stu-id="4bf32-108">AVG(expression)</span></span>

<span data-ttu-id="4bf32-109">Bir koleksiyondaki değerlerin ortalamasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bf32-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="4bf32-110">Null değerler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="4bf32-110">Null values are ignored.</span></span>

<span data-ttu-id="4bf32-111">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="4bf32-111">**Arguments**</span></span>

<span data-ttu-id="4bf32-112">`Int32` ,`Int64`, Ve .`Decimal` `Double`</span><span class="sxs-lookup"><span data-stu-id="4bf32-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="4bf32-113">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="4bf32-113">**Return Value**</span></span>

<span data-ttu-id="4bf32-114">Türü `expression`.</span><span class="sxs-lookup"><span data-stu-id="4bf32-114">The type of `expression`.</span></span>

<span data-ttu-id="4bf32-115">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4bf32-115">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="4bf32-116">CHECKSUM_AGG (koleksiyon)</span><span class="sxs-lookup"><span data-stu-id="4bf32-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="4bf32-117">Bir koleksiyondaki değerlerin sağlama toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bf32-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="4bf32-118">Null değerler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="4bf32-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="4bf32-119">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="4bf32-119">**Arguments**</span></span>
 
 <span data-ttu-id="4bf32-120">Bir koleksiyon (`Int32`).</span><span class="sxs-lookup"><span data-stu-id="4bf32-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="4bf32-121">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="4bf32-121">**Return Value**</span></span>
 
 <span data-ttu-id="4bf32-122">Bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="4bf32-122">An `Int32`.</span></span>
 
 <span data-ttu-id="4bf32-123">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4bf32-123">**Example**</span></span>
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="4bf32-124">COUNT (ifade)</span><span class="sxs-lookup"><span data-stu-id="4bf32-124">COUNT(expression)</span></span>

<span data-ttu-id="4bf32-125">Bir koleksiyondaki öğelerin sayısını bir `Int32`olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bf32-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="4bf32-126">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="4bf32-126">**Arguments**</span></span>

<span data-ttu-id="4bf32-127">Bir koleksiyon\<t >, burada T aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="4bf32-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="4bf32-128">`Guid`(SQL Server 2000 ' de döndürülmez)</span><span class="sxs-lookup"><span data-stu-id="4bf32-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="4bf32-129">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="4bf32-129">**Return Value**</span></span>

<span data-ttu-id="4bf32-130">Bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="4bf32-130">An `Int32`.</span></span>

<span data-ttu-id="4bf32-131">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4bf32-131">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
<span data-ttu-id="4bf32-132">[! Code-SQL[DP EntityServices kavramları # SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span><span class="sxs-lookup"><span data-stu-id="4bf32-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span></span>
 
## <a name="count_bigexpression"></a><span data-ttu-id="4bf32-133">COUNT_BıG (ifade)</span><span class="sxs-lookup"><span data-stu-id="4bf32-133">COUNT_BIG(expression)</span></span>
 
 <span data-ttu-id="4bf32-134">Bir koleksiyondaki öğelerin sayısını bir `bigint`olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bf32-134">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="4bf32-135">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="4bf32-135">**Arguments**</span></span>
 
 <span data-ttu-id="4bf32-136">Bir koleksiyon (T), burada T aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="4bf32-136">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="4bf32-137">`Guid`(SQL Server 2000 ' de döndürülmez)</span><span class="sxs-lookup"><span data-stu-id="4bf32-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="4bf32-138">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="4bf32-138">**Return Value**</span></span>

<span data-ttu-id="4bf32-139">Bir `Int64`.</span><span class="sxs-lookup"><span data-stu-id="4bf32-139">An `Int64`.</span></span>

<span data-ttu-id="4bf32-140">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4bf32-140">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="4bf32-141">MAX (ifade)</span><span class="sxs-lookup"><span data-stu-id="4bf32-141">MAX(expression)</span></span>

<span data-ttu-id="4bf32-142">Koleksiyonun en büyük değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bf32-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="4bf32-143">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="4bf32-143">**Arguments**</span></span>

<span data-ttu-id="4bf32-144">Bir koleksiyon (T), burada T aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="4bf32-144">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="4bf32-145">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="4bf32-145">**Return Value**</span></span>

<span data-ttu-id="4bf32-146">Türü `expression`.</span><span class="sxs-lookup"><span data-stu-id="4bf32-146">The type of `expression`.</span></span>

<span data-ttu-id="4bf32-147">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4bf32-147">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="4bf32-148">MIN (ifade)</span><span class="sxs-lookup"><span data-stu-id="4bf32-148">MIN(expression)</span></span>

<span data-ttu-id="4bf32-149">Bir koleksiyondaki en küçük değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bf32-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="4bf32-150">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="4bf32-150">**Arguments**</span></span>

<span data-ttu-id="4bf32-151">Bir koleksiyon (T), burada T aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="4bf32-151">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="4bf32-152">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="4bf32-152">**Return Value**</span></span>

<span data-ttu-id="4bf32-153">Türü `expression`.</span><span class="sxs-lookup"><span data-stu-id="4bf32-153">The type of `expression`.</span></span>

<span data-ttu-id="4bf32-154">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4bf32-154">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="4bf32-155">STDEV (ifade)</span><span class="sxs-lookup"><span data-stu-id="4bf32-155">STDEV(expression)</span></span>

<span data-ttu-id="4bf32-156">Belirtilen ifadedeki tüm değerlerin istatistiksel standart sapmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bf32-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="4bf32-157">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="4bf32-157">**Arguments**</span></span>

<span data-ttu-id="4bf32-158">Bir koleksiyon (`Double`).</span><span class="sxs-lookup"><span data-stu-id="4bf32-158">A Collection(`Double`).</span></span>

<span data-ttu-id="4bf32-159">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="4bf32-159">**Return Value**</span></span>

<span data-ttu-id="4bf32-160">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4bf32-160">A `Double`.</span></span>

<span data-ttu-id="4bf32-161">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4bf32-161">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="4bf32-162">STDSAPMAS (ifade)</span><span class="sxs-lookup"><span data-stu-id="4bf32-162">STDEVP(expression)</span></span>

<span data-ttu-id="4bf32-163">Belirtilen ifadedeki tüm değerler için popülasyonun istatistiksel standart sapmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bf32-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="4bf32-164">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="4bf32-164">**Arguments**</span></span>

<span data-ttu-id="4bf32-165">Bir koleksiyon (`Double`).</span><span class="sxs-lookup"><span data-stu-id="4bf32-165">A Collection(`Double`).</span></span>

<span data-ttu-id="4bf32-166">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="4bf32-166">**Return Value**</span></span>

<span data-ttu-id="4bf32-167">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4bf32-167">A `Double`.</span></span>

<span data-ttu-id="4bf32-168">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4bf32-168">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="4bf32-169">SUM (ifade)</span><span class="sxs-lookup"><span data-stu-id="4bf32-169">SUM(expression)</span></span>

<span data-ttu-id="4bf32-170">Koleksiyondaki tüm değerlerin toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bf32-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="4bf32-171">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="4bf32-171">**Arguments**</span></span>

<span data-ttu-id="4bf32-172">T (T) `Int32`:, `Int64`, `Double` `Decimal`,.</span><span class="sxs-lookup"><span data-stu-id="4bf32-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="4bf32-173">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="4bf32-173">**Return Value**</span></span>

<span data-ttu-id="4bf32-174">Türü `expression`.</span><span class="sxs-lookup"><span data-stu-id="4bf32-174">The type of `expression`.</span></span>

<span data-ttu-id="4bf32-175">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4bf32-175">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="4bf32-176">VAR (ifade)</span><span class="sxs-lookup"><span data-stu-id="4bf32-176">VAR(expression)</span></span>

<span data-ttu-id="4bf32-177">Belirtilen ifadedeki tüm değerlerin istatistiksel varyansını döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bf32-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="4bf32-178">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="4bf32-178">**Arguments**</span></span>

<span data-ttu-id="4bf32-179">Bir koleksiyon (`Double`).</span><span class="sxs-lookup"><span data-stu-id="4bf32-179">A Collection(`Double`).</span></span>

<span data-ttu-id="4bf32-180">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="4bf32-180">**Return Value**</span></span>

<span data-ttu-id="4bf32-181">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4bf32-181">A `Double`.</span></span>

<span data-ttu-id="4bf32-182">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4bf32-182">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="4bf32-183">VARP (ifade)</span><span class="sxs-lookup"><span data-stu-id="4bf32-183">VARP(expression)</span></span>

<span data-ttu-id="4bf32-184">Belirtilen ifadedeki tüm değerler için popülasyon için istatistiksel varyansı döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bf32-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="4bf32-185">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="4bf32-185">**Arguments**</span></span>

<span data-ttu-id="4bf32-186">Bir koleksiyon (`Double`).</span><span class="sxs-lookup"><span data-stu-id="4bf32-186">A Collection(`Double`).</span></span>

<span data-ttu-id="4bf32-187">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="4bf32-187">**Return Value**</span></span>

<span data-ttu-id="4bf32-188">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4bf32-188">A `Double`.</span></span>

<span data-ttu-id="4bf32-189">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="4bf32-189">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="4bf32-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bf32-190">See also</span></span>

<span data-ttu-id="4bf32-191">SqlClient tarafından desteklenen toplama işlevleri hakkında daha fazla bilgi için, SqlClient sağlayıcısı bildiriminde belirttiğiniz SQL Server sürümü için belgelere bakın:</span><span class="sxs-lookup"><span data-stu-id="4bf32-191">For more information about the aggregate functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="4bf32-192">**SQL Server 2005:** [Toplama Işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="4bf32-192">**SQL Server 2005:** [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span></span>
- <span data-ttu-id="4bf32-193">**SQL Server 2008 ve üzeri:** [Toplama Işlevleri (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="4bf32-193">**SQL Server 2008 and later:** [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span></span>

- [<span data-ttu-id="4bf32-194">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="4bf32-194">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="4bf32-195">Toplu Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="4bf32-195">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
