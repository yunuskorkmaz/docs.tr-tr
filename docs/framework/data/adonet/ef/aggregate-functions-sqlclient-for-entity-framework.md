---
title: Toplama işlevleri (Entity Framework için SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 8ed9a58da9914724fe312876d6594cb526f2e0e9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856523"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="96c7a-102">Toplama işlevleri (Entity Framework için SqlClient)</span><span class="sxs-lookup"><span data-stu-id="96c7a-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="96c7a-103">SQL Server (SqlClient) için .NET Framework veri sağlayıcısı toplama işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="96c7a-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="96c7a-104">Toplama işlevleri, bir giriş değerleri kümesi üzerinde hesaplamalar ve bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="96c7a-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="96c7a-105">Bu işlevler SqlServer ad alanında SqlClient kullanırken, kullanılabilir bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="96c7a-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="96c7a-106">Bir sağlayıcının ad özelliği, hangi önekin türleri ve işlevleri gibi belirli yapılar için bu sağlayıcı tarafından kullanılan bulmak Entity Framework sağlar.</span><span class="sxs-lookup"><span data-stu-id="96c7a-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="96c7a-107">SqlClient toplama işlevleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="96c7a-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="96c7a-108">AVG(Expression)</span><span class="sxs-lookup"><span data-stu-id="96c7a-108">AVG(expression)</span></span>

<span data-ttu-id="96c7a-109">Bir koleksiyondaki değerlerin ortalamasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="96c7a-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="96c7a-110">Null değerler yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="96c7a-110">Null values are ignored.</span></span>

<span data-ttu-id="96c7a-111">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="96c7a-111">**Arguments**</span></span>

<span data-ttu-id="96c7a-112">Bir `Int32`, `Int64`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="96c7a-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="96c7a-113">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="96c7a-113">**Return Value**</span></span>

<span data-ttu-id="96c7a-114">Türünü `expression`.</span><span class="sxs-lookup"><span data-stu-id="96c7a-114">The type of `expression`.</span></span>

<span data-ttu-id="96c7a-115">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="96c7a-115">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksumaggcollection"></a><span data-ttu-id="96c7a-116">CHECKSUM_AGG(Collection)</span><span class="sxs-lookup"><span data-stu-id="96c7a-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="96c7a-117">Sağlama toplamı değerleri, bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="96c7a-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="96c7a-118">Null değerler yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="96c7a-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="96c7a-119">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="96c7a-119">**Arguments**</span></span>
 
 <span data-ttu-id="96c7a-120">Bir koleksiyon (`Int32`).</span><span class="sxs-lookup"><span data-stu-id="96c7a-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="96c7a-121">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="96c7a-121">**Return Value**</span></span>
 
 <span data-ttu-id="96c7a-122">Bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="96c7a-122">An `Int32`.</span></span>
 
 <span data-ttu-id="96c7a-123">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="96c7a-123">**Example**</span></span>
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="96c7a-124">Count (deyim)</span><span class="sxs-lookup"><span data-stu-id="96c7a-124">COUNT(expression)</span></span>

<span data-ttu-id="96c7a-125">Bir koleksiyondaki öğe sayısını döndürür. bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="96c7a-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="96c7a-126">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="96c7a-126">**Arguments**</span></span>

<span data-ttu-id="96c7a-127">Bir koleksiyon\<T >, burada T aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="96c7a-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="96c7a-128">`Guid` (SQL Server 2000'de döndürülmez)</span><span class="sxs-lookup"><span data-stu-id="96c7a-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="96c7a-129">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="96c7a-129">**Return Value**</span></span>

<span data-ttu-id="96c7a-130">Bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="96c7a-130">An `Int32`.</span></span>

<span data-ttu-id="96c7a-131">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="96c7a-131">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
<span data-ttu-id="96c7a-132">[! kod sql[#SQLSERVER_COUNT DP EntityServices kavramları](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span><span class="sxs-lookup"><span data-stu-id="96c7a-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span></span>
 
## <a name="countbigexpression"></a><span data-ttu-id="96c7a-133">COUNT_BIG(Expression)</span><span class="sxs-lookup"><span data-stu-id="96c7a-133">COUNT_BIG(expression)</span></span>
 
 <span data-ttu-id="96c7a-134">Bir koleksiyondaki öğe sayısını döndürür. bir `bigint`.</span><span class="sxs-lookup"><span data-stu-id="96c7a-134">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="96c7a-135">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="96c7a-135">**Arguments**</span></span>
 
 <span data-ttu-id="96c7a-136">Burada T aşağıdaki türlerden biri, bir Collection(T):</span><span class="sxs-lookup"><span data-stu-id="96c7a-136">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="96c7a-137">`Guid` (SQL Server 2000'de döndürülmez)</span><span class="sxs-lookup"><span data-stu-id="96c7a-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="96c7a-138">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="96c7a-138">**Return Value**</span></span>

<span data-ttu-id="96c7a-139">Bir `Int64`.</span><span class="sxs-lookup"><span data-stu-id="96c7a-139">An `Int64`.</span></span>

<span data-ttu-id="96c7a-140">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="96c7a-140">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="96c7a-141">MAX(Expression)</span><span class="sxs-lookup"><span data-stu-id="96c7a-141">MAX(expression)</span></span>

<span data-ttu-id="96c7a-142">En yüksek değer koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="96c7a-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="96c7a-143">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="96c7a-143">**Arguments**</span></span>

<span data-ttu-id="96c7a-144">Burada T aşağıdaki türlerden biri, bir Collection(T):</span><span class="sxs-lookup"><span data-stu-id="96c7a-144">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="96c7a-145">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="96c7a-145">**Return Value**</span></span>

<span data-ttu-id="96c7a-146">Türünü `expression`.</span><span class="sxs-lookup"><span data-stu-id="96c7a-146">The type of `expression`.</span></span>

<span data-ttu-id="96c7a-147">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="96c7a-147">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="96c7a-148">MIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="96c7a-148">MIN(expression)</span></span>

<span data-ttu-id="96c7a-149">En düşük değer, bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="96c7a-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="96c7a-150">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="96c7a-150">**Arguments**</span></span>

<span data-ttu-id="96c7a-151">Burada T aşağıdaki türlerden biri, bir Collection(T):</span><span class="sxs-lookup"><span data-stu-id="96c7a-151">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="96c7a-152">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="96c7a-152">**Return Value**</span></span>

<span data-ttu-id="96c7a-153">Türünü `expression`.</span><span class="sxs-lookup"><span data-stu-id="96c7a-153">The type of `expression`.</span></span>

<span data-ttu-id="96c7a-154">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="96c7a-154">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="96c7a-155">STDEV(Expression)</span><span class="sxs-lookup"><span data-stu-id="96c7a-155">STDEV(expression)</span></span>

<span data-ttu-id="96c7a-156">Belirtilen ifadedeki istatistiksel tüm değerlerin standart sapmasını verir.</span><span class="sxs-lookup"><span data-stu-id="96c7a-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="96c7a-157">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="96c7a-157">**Arguments**</span></span>

<span data-ttu-id="96c7a-158">Bir koleksiyon (`Double`).</span><span class="sxs-lookup"><span data-stu-id="96c7a-158">A Collection(`Double`).</span></span>

<span data-ttu-id="96c7a-159">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="96c7a-159">**Return Value**</span></span>

<span data-ttu-id="96c7a-160">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="96c7a-160">A `Double`.</span></span>

<span data-ttu-id="96c7a-161">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="96c7a-161">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="96c7a-162">StDevP(Expression)</span><span class="sxs-lookup"><span data-stu-id="96c7a-162">STDEVP(expression)</span></span>

<span data-ttu-id="96c7a-163">Belirtilen ifadedeki tüm değerlerin popülasyon için istatistiksel standart sapma döndürür.</span><span class="sxs-lookup"><span data-stu-id="96c7a-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="96c7a-164">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="96c7a-164">**Arguments**</span></span>

<span data-ttu-id="96c7a-165">Bir koleksiyon (`Double`).</span><span class="sxs-lookup"><span data-stu-id="96c7a-165">A Collection(`Double`).</span></span>

<span data-ttu-id="96c7a-166">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="96c7a-166">**Return Value**</span></span>

<span data-ttu-id="96c7a-167">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="96c7a-167">A `Double`.</span></span>

<span data-ttu-id="96c7a-168">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="96c7a-168">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="96c7a-169">SUM(Expression)</span><span class="sxs-lookup"><span data-stu-id="96c7a-169">SUM(expression)</span></span>

<span data-ttu-id="96c7a-170">Koleksiyondaki tüm değerlerin toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="96c7a-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="96c7a-171">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="96c7a-171">**Arguments**</span></span>

<span data-ttu-id="96c7a-172">Burada T, şu türlerden birinde bir Collection(T): `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="96c7a-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="96c7a-173">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="96c7a-173">**Return Value**</span></span>

<span data-ttu-id="96c7a-174">Türünü `expression`.</span><span class="sxs-lookup"><span data-stu-id="96c7a-174">The type of `expression`.</span></span>

<span data-ttu-id="96c7a-175">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="96c7a-175">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="96c7a-176">VAR(Expression)</span><span class="sxs-lookup"><span data-stu-id="96c7a-176">VAR(expression)</span></span>

<span data-ttu-id="96c7a-177">Belirtilen ifadedeki istatistiksel tüm değerlerin varyansını döndürür.</span><span class="sxs-lookup"><span data-stu-id="96c7a-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="96c7a-178">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="96c7a-178">**Arguments**</span></span>

<span data-ttu-id="96c7a-179">Bir koleksiyon (`Double`).</span><span class="sxs-lookup"><span data-stu-id="96c7a-179">A Collection(`Double`).</span></span>

<span data-ttu-id="96c7a-180">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="96c7a-180">**Return Value**</span></span>

<span data-ttu-id="96c7a-181">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="96c7a-181">A `Double`.</span></span>

<span data-ttu-id="96c7a-182">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="96c7a-182">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="96c7a-183">VarP(Expression)</span><span class="sxs-lookup"><span data-stu-id="96c7a-183">VARP(expression)</span></span>

<span data-ttu-id="96c7a-184">Belirtilen ifadedeki istatistiksel tüm değerlerin popülasyon varyansını verir.</span><span class="sxs-lookup"><span data-stu-id="96c7a-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="96c7a-185">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="96c7a-185">**Arguments**</span></span>

<span data-ttu-id="96c7a-186">Bir koleksiyon (`Double`).</span><span class="sxs-lookup"><span data-stu-id="96c7a-186">A Collection(`Double`).</span></span>

<span data-ttu-id="96c7a-187">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="96c7a-187">**Return Value**</span></span>

<span data-ttu-id="96c7a-188">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="96c7a-188">A `Double`.</span></span>

<span data-ttu-id="96c7a-189">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="96c7a-189">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="96c7a-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96c7a-190">See also</span></span>

<span data-ttu-id="96c7a-191">SqlClient destekleyen toplama işlevleri hakkında daha fazla bilgi için SqlClient sağlayıcı bildiriminde belirtilen SQL Server sürümü için belgelere bakın:</span><span class="sxs-lookup"><span data-stu-id="96c7a-191">For more information about the aggregate functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  
  
<span data-ttu-id="96c7a-192">**SQL Server 2005'te**: [toplama işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="96c7a-192">**SQL Server 2005**: [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span></span>  
<span data-ttu-id="96c7a-193">**SQL Server 2008 ve üzeri**: [toplama işlevleri (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="96c7a-193">**SQL Server 2008 and later**:  [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span></span>  
[<span data-ttu-id="96c7a-194">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="96c7a-194">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
[<span data-ttu-id="96c7a-195">Toplu Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="96c7a-195">Aggregate Canonical Functions</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
