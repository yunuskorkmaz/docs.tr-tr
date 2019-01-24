---
title: Toplama işlevleri (Entity Framework için SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 55a10b82ffc189f5cf4118cb225a96963226256e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724193"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="6b902-102">Toplama işlevleri (Entity Framework için SqlClient)</span><span class="sxs-lookup"><span data-stu-id="6b902-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="6b902-103">SQL Server (SqlClient) için .NET Framework veri sağlayıcısı toplama işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b902-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="6b902-104">Toplama işlevleri, bir giriş değerleri kümesi üzerinde hesaplamalar ve bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b902-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="6b902-105">Bu işlevler SqlServer ad alanında SqlClient kullanırken, kullanılabilir bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="6b902-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="6b902-106">Bir sağlayıcının ad özelliği, hangi önekin türleri ve işlevleri gibi belirli yapılar için bu sağlayıcı tarafından kullanılan bulmak Entity Framework sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b902-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="6b902-107">SqlClient toplama işlevleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6b902-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="6b902-108">AVG(Expression)</span><span class="sxs-lookup"><span data-stu-id="6b902-108">AVG(expression)</span></span>

<span data-ttu-id="6b902-109">Bir koleksiyondaki değerlerin ortalamasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b902-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="6b902-110">Null değerler yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="6b902-110">Null values are ignored.</span></span>

<span data-ttu-id="6b902-111">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="6b902-111">**Arguments**</span></span>

<span data-ttu-id="6b902-112">Bir `Int32`, `Int64`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6b902-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="6b902-113">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="6b902-113">**Return Value**</span></span>

<span data-ttu-id="6b902-114">Türünü `expression`.</span><span class="sxs-lookup"><span data-stu-id="6b902-114">The type of `expression`.</span></span>

<span data-ttu-id="6b902-115">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="6b902-115">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksumaggcollection"></a><span data-ttu-id="6b902-116">CHECKSUM_AGG(Collection)</span><span class="sxs-lookup"><span data-stu-id="6b902-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="6b902-117">Sağlama toplamı değerleri, bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b902-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="6b902-118">Null değerler yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="6b902-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="6b902-119">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="6b902-119">**Arguments**</span></span>
 
 <span data-ttu-id="6b902-120">Bir koleksiyon (`Int32`).</span><span class="sxs-lookup"><span data-stu-id="6b902-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="6b902-121">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="6b902-121">**Return Value**</span></span>
 
 <span data-ttu-id="6b902-122">Bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="6b902-122">An `Int32`.</span></span>
 
 <span data-ttu-id="6b902-123">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="6b902-123">**Example**</span></span>
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="6b902-124">Count (deyim)</span><span class="sxs-lookup"><span data-stu-id="6b902-124">COUNT(expression)</span></span>

<span data-ttu-id="6b902-125">Bir koleksiyondaki öğe sayısını döndürür. bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="6b902-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="6b902-126">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="6b902-126">**Arguments**</span></span>

<span data-ttu-id="6b902-127">Bir koleksiyon\<T >, burada T aşağıdaki türlerden biridir:</span><span class="sxs-lookup"><span data-stu-id="6b902-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="6b902-128">`Guid` (SQL Server 2000'de döndürülmez)</span><span class="sxs-lookup"><span data-stu-id="6b902-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="6b902-129">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="6b902-129">**Return Value**</span></span>

<span data-ttu-id="6b902-130">Bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="6b902-130">An `Int32`.</span></span>

<span data-ttu-id="6b902-131">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="6b902-131">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
<span data-ttu-id="6b902-132">[! kod sql[#SQLSERVER_COUNT DP EntityServices kavramları](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span><span class="sxs-lookup"><span data-stu-id="6b902-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span></span>
 
## <a name="countbigexpression"></a><span data-ttu-id="6b902-133">COUNT_BIG(Expression)</span><span class="sxs-lookup"><span data-stu-id="6b902-133">COUNT_BIG(expression)</span></span>
 
 <span data-ttu-id="6b902-134">Bir koleksiyondaki öğe sayısını döndürür. bir `bigint`.</span><span class="sxs-lookup"><span data-stu-id="6b902-134">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="6b902-135">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="6b902-135">**Arguments**</span></span>
 
 <span data-ttu-id="6b902-136">Burada T aşağıdaki türlerden biri, bir Collection(T):</span><span class="sxs-lookup"><span data-stu-id="6b902-136">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="6b902-137">`Guid` (SQL Server 2000'de döndürülmez)</span><span class="sxs-lookup"><span data-stu-id="6b902-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="6b902-138">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="6b902-138">**Return Value**</span></span>

<span data-ttu-id="6b902-139">Bir `Int64`.</span><span class="sxs-lookup"><span data-stu-id="6b902-139">An `Int64`.</span></span>

<span data-ttu-id="6b902-140">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="6b902-140">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="6b902-141">MAX(expression)</span><span class="sxs-lookup"><span data-stu-id="6b902-141">MAX(expression)</span></span>

<span data-ttu-id="6b902-142">En yüksek değer koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b902-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="6b902-143">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="6b902-143">**Arguments**</span></span>

<span data-ttu-id="6b902-144">Burada T aşağıdaki türlerden biri, bir Collection(T):</span><span class="sxs-lookup"><span data-stu-id="6b902-144">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="6b902-145">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="6b902-145">**Return Value**</span></span>

<span data-ttu-id="6b902-146">Türünü `expression`.</span><span class="sxs-lookup"><span data-stu-id="6b902-146">The type of `expression`.</span></span>

<span data-ttu-id="6b902-147">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="6b902-147">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="6b902-148">MIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="6b902-148">MIN(expression)</span></span>

<span data-ttu-id="6b902-149">En düşük değer, bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b902-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="6b902-150">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="6b902-150">**Arguments**</span></span>

<span data-ttu-id="6b902-151">Burada T aşağıdaki türlerden biri, bir Collection(T):</span><span class="sxs-lookup"><span data-stu-id="6b902-151">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="6b902-152">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="6b902-152">**Return Value**</span></span>

<span data-ttu-id="6b902-153">Türünü `expression`.</span><span class="sxs-lookup"><span data-stu-id="6b902-153">The type of `expression`.</span></span>

<span data-ttu-id="6b902-154">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="6b902-154">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="6b902-155">STDEV(Expression)</span><span class="sxs-lookup"><span data-stu-id="6b902-155">STDEV(expression)</span></span>

<span data-ttu-id="6b902-156">Belirtilen ifadedeki istatistiksel tüm değerlerin standart sapmasını verir.</span><span class="sxs-lookup"><span data-stu-id="6b902-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="6b902-157">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="6b902-157">**Arguments**</span></span>

<span data-ttu-id="6b902-158">Bir koleksiyon (`Double`).</span><span class="sxs-lookup"><span data-stu-id="6b902-158">A Collection(`Double`).</span></span>

<span data-ttu-id="6b902-159">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="6b902-159">**Return Value**</span></span>

<span data-ttu-id="6b902-160">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="6b902-160">A `Double`.</span></span>

<span data-ttu-id="6b902-161">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="6b902-161">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="6b902-162">StDevP(Expression)</span><span class="sxs-lookup"><span data-stu-id="6b902-162">STDEVP(expression)</span></span>

<span data-ttu-id="6b902-163">Belirtilen ifadedeki tüm değerlerin popülasyon için istatistiksel standart sapma döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b902-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="6b902-164">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="6b902-164">**Arguments**</span></span>

<span data-ttu-id="6b902-165">Bir koleksiyon (`Double`).</span><span class="sxs-lookup"><span data-stu-id="6b902-165">A Collection(`Double`).</span></span>

<span data-ttu-id="6b902-166">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="6b902-166">**Return Value**</span></span>

<span data-ttu-id="6b902-167">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="6b902-167">A `Double`.</span></span>

<span data-ttu-id="6b902-168">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="6b902-168">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="6b902-169">SUM(Expression)</span><span class="sxs-lookup"><span data-stu-id="6b902-169">SUM(expression)</span></span>

<span data-ttu-id="6b902-170">Koleksiyondaki tüm değerlerin toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b902-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="6b902-171">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="6b902-171">**Arguments**</span></span>

<span data-ttu-id="6b902-172">Burada T, şu türlerden birinde bir Collection(T): `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6b902-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="6b902-173">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="6b902-173">**Return Value**</span></span>

<span data-ttu-id="6b902-174">Türünü `expression`.</span><span class="sxs-lookup"><span data-stu-id="6b902-174">The type of `expression`.</span></span>

<span data-ttu-id="6b902-175">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="6b902-175">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="6b902-176">VAR(Expression)</span><span class="sxs-lookup"><span data-stu-id="6b902-176">VAR(expression)</span></span>

<span data-ttu-id="6b902-177">Belirtilen ifadedeki istatistiksel tüm değerlerin varyansını döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b902-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="6b902-178">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="6b902-178">**Arguments**</span></span>

<span data-ttu-id="6b902-179">Bir koleksiyon (`Double`).</span><span class="sxs-lookup"><span data-stu-id="6b902-179">A Collection(`Double`).</span></span>

<span data-ttu-id="6b902-180">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="6b902-180">**Return Value**</span></span>

<span data-ttu-id="6b902-181">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="6b902-181">A `Double`.</span></span>

<span data-ttu-id="6b902-182">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="6b902-182">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="6b902-183">VarP(Expression)</span><span class="sxs-lookup"><span data-stu-id="6b902-183">VARP(expression)</span></span>

<span data-ttu-id="6b902-184">Belirtilen ifadedeki istatistiksel tüm değerlerin popülasyon varyansını verir.</span><span class="sxs-lookup"><span data-stu-id="6b902-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="6b902-185">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="6b902-185">**Arguments**</span></span>

<span data-ttu-id="6b902-186">Bir koleksiyon (`Double`).</span><span class="sxs-lookup"><span data-stu-id="6b902-186">A Collection(`Double`).</span></span>

<span data-ttu-id="6b902-187">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="6b902-187">**Return Value**</span></span>

<span data-ttu-id="6b902-188">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="6b902-188">A `Double`.</span></span>

<span data-ttu-id="6b902-189">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="6b902-189">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="6b902-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b902-190">See also</span></span>

<span data-ttu-id="6b902-191">SqlClient destekleyen toplama işlevleri hakkında daha fazla bilgi için SqlClient sağlayıcı bildiriminde belirtilen SQL Server sürümü için belgelere bakın:</span><span class="sxs-lookup"><span data-stu-id="6b902-191">For more information about the aggregate functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  

<span data-ttu-id="6b902-192">**SQL Server 2005**: [Toplama işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="6b902-192">**SQL Server 2005**: [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span></span>  
<span data-ttu-id="6b902-193">**SQL Server 2008 ve üzeri**:  [Toplama işlevleri (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="6b902-193">**SQL Server 2008 and later**:  [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span></span>  
- [<span data-ttu-id="6b902-194">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="6b902-194">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [<span data-ttu-id="6b902-195">Toplu Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="6b902-195">Aggregate Canonical Functions</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
