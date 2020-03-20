---
title: Toplam Fonksiyonlar (Entity Framework için SqlClient)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 1fad25f2229b4fa810cf82a96dcb8c50a9de3070
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150655"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="9fc59-102">Toplam Fonksiyonlar (Entity Framework için SqlClient)</span><span class="sxs-lookup"><span data-stu-id="9fc59-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="9fc59-103">SQL Server için .NET Framework Data Provider (SqlClient) toplu işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fc59-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="9fc59-104">Toplam işlevler, giriş değerleri kümesi üzerinde hesaplamalar yapar ve bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="9fc59-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="9fc59-105">Bu işlevler, SqlClient'ı kullandığınızda kullanılabilen SqlServer ad alanındadır.</span><span class="sxs-lookup"><span data-stu-id="9fc59-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="9fc59-106">Sağlayıcının ad alanı özelliği, Varlık Çerçevesi'nin bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için hangi önek kullanıldığını keşfetmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9fc59-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="9fc59-107">Aşağıdaki sqlclient toplu işlevleri vardır.</span><span class="sxs-lookup"><span data-stu-id="9fc59-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="9fc59-108">AVG(ifade)</span><span class="sxs-lookup"><span data-stu-id="9fc59-108">AVG(expression)</span></span>

<span data-ttu-id="9fc59-109">Koleksiyondaki değerlerin ortalamasını verir.</span><span class="sxs-lookup"><span data-stu-id="9fc59-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="9fc59-110">Null değerleri yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="9fc59-110">Null values are ignored.</span></span>

<span data-ttu-id="9fc59-111">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="9fc59-111">**Arguments**</span></span>

<span data-ttu-id="9fc59-112">Bir `Int32` `Int64`, `Double`, `Decimal`ve .</span><span class="sxs-lookup"><span data-stu-id="9fc59-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="9fc59-113">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="9fc59-113">**Return Value**</span></span>

<span data-ttu-id="9fc59-114">Türü `expression`.</span><span class="sxs-lookup"><span data-stu-id="9fc59-114">The type of `expression`.</span></span>

<span data-ttu-id="9fc59-115">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="9fc59-115">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="9fc59-116">CHECKSUM_AGG(toplama)</span><span class="sxs-lookup"><span data-stu-id="9fc59-116">CHECKSUM_AGG(collection)</span></span>

 <span data-ttu-id="9fc59-117">Koleksiyondaki değerlerin denetimini verir.</span><span class="sxs-lookup"><span data-stu-id="9fc59-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="9fc59-118">Null değerleri yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="9fc59-118">Null values are ignored.</span></span>

 <span data-ttu-id="9fc59-119">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="9fc59-119">**Arguments**</span></span>

 <span data-ttu-id="9fc59-120">Bir Koleksiyon(`Int32`).</span><span class="sxs-lookup"><span data-stu-id="9fc59-120">A Collection(`Int32`).</span></span>

 <span data-ttu-id="9fc59-121">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="9fc59-121">**Return Value**</span></span>

 <span data-ttu-id="9fc59-122">Bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="9fc59-122">An `Int32`.</span></span>

 <span data-ttu-id="9fc59-123">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="9fc59-123">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a><span data-ttu-id="9fc59-124">COUNT(ifade)</span><span class="sxs-lookup"><span data-stu-id="9fc59-124">COUNT(expression)</span></span>

<span data-ttu-id="9fc59-125">Koleksiyondaki öğe sayısını ' `Int32`olarak verir.</span><span class="sxs-lookup"><span data-stu-id="9fc59-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="9fc59-126">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="9fc59-126">**Arguments**</span></span>

<span data-ttu-id="9fc59-127">T'nin aşağıdaki türlerden biri olduğu Bir Koleksiyon\<T>:</span><span class="sxs-lookup"><span data-stu-id="9fc59-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="9fc59-128">`Guid`(SQL Server 2000'de döndürülmez)</span><span class="sxs-lookup"><span data-stu-id="9fc59-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="9fc59-129">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="9fc59-129">**Return Value**</span></span>

<span data-ttu-id="9fc59-130">Bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="9fc59-130">An `Int32`.</span></span>

<span data-ttu-id="9fc59-131">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="9fc59-131">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a><span data-ttu-id="9fc59-132">COUNT_BIG(ifade)</span><span class="sxs-lookup"><span data-stu-id="9fc59-132">COUNT_BIG(expression)</span></span>

<span data-ttu-id="9fc59-133">Koleksiyondaki madde sayısını ' `bigint`olarak verir.</span><span class="sxs-lookup"><span data-stu-id="9fc59-133">Returns the number of items in a collection as a `bigint`.</span></span>

 <span data-ttu-id="9fc59-134">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="9fc59-134">**Arguments**</span></span>

 <span data-ttu-id="9fc59-135">T'nin aşağıdaki türlerden biri olduğu Koleksiyon(T)</span><span class="sxs-lookup"><span data-stu-id="9fc59-135">A Collection(T), where T is one of the following types:</span></span>

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="9fc59-136">`Guid`(SQL Server 2000'de döndürülmez)</span><span class="sxs-lookup"><span data-stu-id="9fc59-136">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="9fc59-137">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="9fc59-137">**Return Value**</span></span>

<span data-ttu-id="9fc59-138">Bir `Int64`.</span><span class="sxs-lookup"><span data-stu-id="9fc59-138">An `Int64`.</span></span>

<span data-ttu-id="9fc59-139">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="9fc59-139">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="9fc59-140">MAX(ifade)</span><span class="sxs-lookup"><span data-stu-id="9fc59-140">MAX(expression)</span></span>

<span data-ttu-id="9fc59-141">Koleksiyonun en büyük değerini verir.</span><span class="sxs-lookup"><span data-stu-id="9fc59-141">Returns the maximum value the collection.</span></span>

<span data-ttu-id="9fc59-142">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="9fc59-142">**Arguments**</span></span>

<span data-ttu-id="9fc59-143">T'nin aşağıdaki türlerden biri olduğu Koleksiyon(T)</span><span class="sxs-lookup"><span data-stu-id="9fc59-143">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="9fc59-144">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="9fc59-144">**Return Value**</span></span>

<span data-ttu-id="9fc59-145">Türü `expression`.</span><span class="sxs-lookup"><span data-stu-id="9fc59-145">The type of `expression`.</span></span>

<span data-ttu-id="9fc59-146">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="9fc59-146">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="9fc59-147">MIN(ifade)</span><span class="sxs-lookup"><span data-stu-id="9fc59-147">MIN(expression)</span></span>

<span data-ttu-id="9fc59-148">Koleksiyondaki minimum değeri verir.</span><span class="sxs-lookup"><span data-stu-id="9fc59-148">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="9fc59-149">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="9fc59-149">**Arguments**</span></span>

<span data-ttu-id="9fc59-150">T'nin aşağıdaki türlerden biri olduğu Koleksiyon(T)</span><span class="sxs-lookup"><span data-stu-id="9fc59-150">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="9fc59-151">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="9fc59-151">**Return Value**</span></span>

<span data-ttu-id="9fc59-152">Türü `expression`.</span><span class="sxs-lookup"><span data-stu-id="9fc59-152">The type of `expression`.</span></span>

<span data-ttu-id="9fc59-153">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="9fc59-153">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="9fc59-154">STDSAPMA(ifade)</span><span class="sxs-lookup"><span data-stu-id="9fc59-154">STDEV(expression)</span></span>

<span data-ttu-id="9fc59-155">Belirtilen ifadedeki tüm değerlerin istatistiksel standart sapını verir.</span><span class="sxs-lookup"><span data-stu-id="9fc59-155">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="9fc59-156">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="9fc59-156">**Arguments**</span></span>

<span data-ttu-id="9fc59-157">Bir Koleksiyon(`Double`).</span><span class="sxs-lookup"><span data-stu-id="9fc59-157">A Collection(`Double`).</span></span>

<span data-ttu-id="9fc59-158">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="9fc59-158">**Return Value**</span></span>

<span data-ttu-id="9fc59-159">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="9fc59-159">A `Double`.</span></span>

<span data-ttu-id="9fc59-160">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="9fc59-160">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="9fc59-161">STDSAPMAS(ifade)</span><span class="sxs-lookup"><span data-stu-id="9fc59-161">STDEVP(expression)</span></span>

<span data-ttu-id="9fc59-162">Belirtilen ifadedeki tüm değerler için popülasyon için istatistiksel standart sapması verir.</span><span class="sxs-lookup"><span data-stu-id="9fc59-162">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="9fc59-163">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="9fc59-163">**Arguments**</span></span>

<span data-ttu-id="9fc59-164">Bir Koleksiyon(`Double`).</span><span class="sxs-lookup"><span data-stu-id="9fc59-164">A Collection(`Double`).</span></span>

<span data-ttu-id="9fc59-165">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="9fc59-165">**Return Value**</span></span>

<span data-ttu-id="9fc59-166">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="9fc59-166">A `Double`.</span></span>

<span data-ttu-id="9fc59-167">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="9fc59-167">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="9fc59-168">SUM(ifade)</span><span class="sxs-lookup"><span data-stu-id="9fc59-168">SUM(expression)</span></span>

<span data-ttu-id="9fc59-169">Koleksiyondaki tüm değerlerin toplamını verir.</span><span class="sxs-lookup"><span data-stu-id="9fc59-169">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="9fc59-170">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="9fc59-170">**Arguments**</span></span>

<span data-ttu-id="9fc59-171">T'nin aşağıdaki türlerden biri olduğu Bir `Int32` `Int64`Koleksiyon(T) : , , `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9fc59-171">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="9fc59-172">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="9fc59-172">**Return Value**</span></span>

<span data-ttu-id="9fc59-173">Türü `expression`.</span><span class="sxs-lookup"><span data-stu-id="9fc59-173">The type of `expression`.</span></span>

<span data-ttu-id="9fc59-174">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="9fc59-174">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="9fc59-175">VAR(ifade)</span><span class="sxs-lookup"><span data-stu-id="9fc59-175">VAR(expression)</span></span>

<span data-ttu-id="9fc59-176">Belirtilen ifadedeki tüm değerlerin istatistiksel değişkenini verir.</span><span class="sxs-lookup"><span data-stu-id="9fc59-176">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="9fc59-177">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="9fc59-177">**Arguments**</span></span>

<span data-ttu-id="9fc59-178">Bir Koleksiyon(`Double`).</span><span class="sxs-lookup"><span data-stu-id="9fc59-178">A Collection(`Double`).</span></span>

<span data-ttu-id="9fc59-179">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="9fc59-179">**Return Value**</span></span>

<span data-ttu-id="9fc59-180">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="9fc59-180">A `Double`.</span></span>

<span data-ttu-id="9fc59-181">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="9fc59-181">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="9fc59-182">VARP(ifade)</span><span class="sxs-lookup"><span data-stu-id="9fc59-182">VARP(expression)</span></span>

<span data-ttu-id="9fc59-183">Belirtilen ifadedeki tüm değerler için popülasyon için istatistiksel varyansı verir.</span><span class="sxs-lookup"><span data-stu-id="9fc59-183">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="9fc59-184">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="9fc59-184">**Arguments**</span></span>

<span data-ttu-id="9fc59-185">Bir Koleksiyon(`Double`).</span><span class="sxs-lookup"><span data-stu-id="9fc59-185">A Collection(`Double`).</span></span>

<span data-ttu-id="9fc59-186">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="9fc59-186">**Return Value**</span></span>

<span data-ttu-id="9fc59-187">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="9fc59-187">A `Double`.</span></span>

<span data-ttu-id="9fc59-188">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="9fc59-188">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a><span data-ttu-id="9fc59-189">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fc59-189">See also</span></span>

- [<span data-ttu-id="9fc59-190">Toplam Fonksiyonlar (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9fc59-190">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="9fc59-191">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="9fc59-191">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="9fc59-192">Toplu Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="9fc59-192">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
