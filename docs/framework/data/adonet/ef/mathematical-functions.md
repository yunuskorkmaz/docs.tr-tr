---
title: Matematik işlevleri
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 63f83532c399f77e268913da3198327345b9c2ee
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143681"
---
# <a name="mathematical-functions"></a><span data-ttu-id="d4dbc-102">Matematik işlevleri</span><span class="sxs-lookup"><span data-stu-id="d4dbc-102">Mathematical Functions</span></span>

<span data-ttu-id="d4dbc-103">SQL Server (SqlClient) için .NET Framework veri sağlayıcısı, bağımsız değişken olarak sağlanır ve bir sayısal değer sonuç giriş değerleri üzerinde hesaplamalar matematik işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="d4dbc-104">Bu işlevler SqlServer ad alanında SqlClient kullanırken, kullanılabilir bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="d4dbc-105">Bir sağlayıcının ad özelliği, hangi önekin türleri ve işlevleri gibi belirli yapılar için bu sağlayıcı tarafından kullanılan bulmak Entity Framework sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="d4dbc-106">Aşağıdaki tabloda SqlClient matematik işlevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="d4dbc-107">Abs(Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-107">ABS(expression)</span></span>

<span data-ttu-id="d4dbc-108">Mutlak değeri işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-108">Performs the absolute value function.</span></span>

<span data-ttu-id="d4dbc-109">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-109">**Arguments**</span></span>

<span data-ttu-id="d4dbc-110">`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="d4dbc-111">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-111">**Return Value**</span></span>

<span data-ttu-id="d4dbc-112">Belirtilen ifadenin mutlak değeri.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="d4dbc-113">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="d4dbc-114">ACOS(Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-114">ACOS(expression)</span></span>

<span data-ttu-id="d4dbc-115">Belirtilen ifade arkkosinüsünü değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="d4dbc-116">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-116">**Arguments**</span></span>

<span data-ttu-id="d4dbc-117">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="d4dbc-118">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-118">**Return Value**</span></span>

<span data-ttu-id="d4dbc-119">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-119">A `Double`.</span></span>

<span data-ttu-id="d4dbc-120">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="d4dbc-121">ASIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-121">ASIN(expression)</span></span>

<span data-ttu-id="d4dbc-122">Belirtilen ifade arksinüsünü değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="d4dbc-123">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-123">**Arguments**</span></span>

<span data-ttu-id="d4dbc-124">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="d4dbc-125">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-125">**Return Value**</span></span>

<span data-ttu-id="d4dbc-126">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-126">A `Double`.</span></span>

<span data-ttu-id="d4dbc-127">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="d4dbc-128">ATAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-128">ATAN(expression)</span></span>

<span data-ttu-id="d4dbc-129">Belirtilen sayısal ifade arktanjantını değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="d4dbc-130">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-130">**Arguments**</span></span>

<span data-ttu-id="d4dbc-131">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="d4dbc-132">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-132">**Return Value**</span></span>

<span data-ttu-id="d4dbc-133">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-133">A `Double`.</span></span>

<span data-ttu-id="d4dbc-134">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="d4dbc-135">ATN2(Expression, Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="d4dbc-136">Radyan cinsinden tanjantı iki belirli sayısal ifade olan açıyı döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="d4dbc-137">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-137">**Arguments**</span></span>

<span data-ttu-id="d4dbc-138">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="d4dbc-139">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-139">**Return Value**</span></span>

<span data-ttu-id="d4dbc-140">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-140">A `Double`.</span></span>

<span data-ttu-id="d4dbc-141">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="d4dbc-142">CEILING(Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-142">CEILING(expression)</span></span>

<span data-ttu-id="d4dbc-143">Belirtilen ifade değerinden büyük veya ona eşit olan en küçük tamsayı dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="d4dbc-144">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-144">**Arguments**</span></span>

<span data-ttu-id="d4dbc-145">`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="d4dbc-146">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-146">**Return Value**</span></span>

<span data-ttu-id="d4dbc-147">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="d4dbc-148">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-148">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="d4dbc-149">COS(Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-149">COS(expression)</span></span>

<span data-ttu-id="d4dbc-150">Trigonometrik radyan cinsinden belirtilen bir açının kosinüsünü hesaplar.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="d4dbc-151">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-151">**Arguments**</span></span> 

<span data-ttu-id="d4dbc-152">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-152">`expression`: A `Double`.</span></span> 

<span data-ttu-id="d4dbc-153">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-153">**Return Value**</span></span> 

<span data-ttu-id="d4dbc-154">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-154">A `Double`.</span></span> 

<span data-ttu-id="d4dbc-155">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-155">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="d4dbc-156">COT(Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-156">COT(expression)</span></span>

<span data-ttu-id="d4dbc-157">Trigonometrik radyan cinsinden belirtilen bir açının kotanjantını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="d4dbc-158">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-158">**Arguments**</span></span> 

<span data-ttu-id="d4dbc-159">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-159">`expression`: A `Double`.</span></span> 

<span data-ttu-id="d4dbc-160">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-160">**Return Value**</span></span> 

<span data-ttu-id="d4dbc-161">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-161">A `Double`.</span></span> 

<span data-ttu-id="d4dbc-162">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-162">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="d4dbc-163">DEGREES(radians)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-163">DEGREES(radians)</span></span>

<span data-ttu-id="d4dbc-164">Karşılık gelen açıyı derece cinsinden döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-164">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="d4dbc-165">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-165">**Arguments**</span></span> 

<span data-ttu-id="d4dbc-166">`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="d4dbc-167">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-167">**Return Value**</span></span> 

<span data-ttu-id="d4dbc-168">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="d4dbc-169">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-169">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="d4dbc-170">EXP(Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-170">EXP(expression)</span></span>

<span data-ttu-id="d4dbc-171">Belirtilen bir sayısal ifade üs değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-171">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="d4dbc-172">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-172">**Arguments**</span></span> 

<span data-ttu-id="d4dbc-173">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-173">`expression`: A `Double`.</span></span> 

<span data-ttu-id="d4dbc-174">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-174">**Return Value**</span></span> 

<span data-ttu-id="d4dbc-175">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-175">A `Double`.</span></span> 

<span data-ttu-id="d4dbc-176">**Örnek** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="d4dbc-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="d4dbc-177">FLOOR(Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-177">FLOOR(expression)</span></span>

<span data-ttu-id="d4dbc-178">Belirtilen ifadedeki en büyük tamsayı daha az veya eşit ona dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-178">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="d4dbc-179">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-179">**Arguments**</span></span> 

<span data-ttu-id="d4dbc-180">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-180">`expression`: A `Double`.</span></span> 

<span data-ttu-id="d4dbc-181">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-181">**Return Value**</span></span> 

<span data-ttu-id="d4dbc-182">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-182">A `Double`.</span></span> 

<span data-ttu-id="d4dbc-183">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-183">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="d4dbc-184">LOG(Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-184">LOG(expression)</span></span>

<span data-ttu-id="d4dbc-185">Belirtilen doğal logaritmasını hesaplar `float` ifade.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-185">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="d4dbc-186">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-186">**Arguments**</span></span> 

<span data-ttu-id="d4dbc-187">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-187">`expression`: A `Double`.</span></span> 

<span data-ttu-id="d4dbc-188">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-188">**Return Value**</span></span> 

<span data-ttu-id="d4dbc-189">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-189">A `Double`.</span></span> 

<span data-ttu-id="d4dbc-190">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-190">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="d4dbc-191">Log10(Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-191">LOG10(expression)</span></span>

<span data-ttu-id="d4dbc-192">Belirtilen 10 tabanında logaritmasını döndürür `Double` ifade.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="d4dbc-193">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-193">**Arguments**</span></span> 

<span data-ttu-id="d4dbc-194">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-194">`expression`: A `Double`.</span></span> 

<span data-ttu-id="d4dbc-195">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-195">**Return Value**</span></span> 

<span data-ttu-id="d4dbc-196">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-196">A `Double`.</span></span> 

<span data-ttu-id="d4dbc-197">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-197">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="d4dbc-198">PI()</span><span class="sxs-lookup"><span data-stu-id="d4dbc-198">PI()</span></span>

<span data-ttu-id="d4dbc-199">Sabit değer pi'nin döndürür bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-199">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="d4dbc-200">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-200">**Return Value**</span></span> 

<span data-ttu-id="d4dbc-201">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-201">A `Double`.</span></span> 

<span data-ttu-id="d4dbc-202">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-202">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a><span data-ttu-id="d4dbc-203">GÜÇ (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="d4dbc-204">Belirtilen bir ifadenin belirtilen bir kuvvete değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="d4dbc-205">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-205">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="d4dbc-206">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="d4dbc-207">A `Double` yükseltmek istediğiniz gücünü temsil eden `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="d4dbc-208">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-208">**Return Value**</span></span> 

<span data-ttu-id="d4dbc-209">Belirtilen değeri `numeric_expression` belirtilen `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="d4dbc-210">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-210">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="d4dbc-211">RADIANS(Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-211">RADIANS(expression)</span></span>

<span data-ttu-id="d4dbc-212">Dereceyi radyana dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-212">Converts degrees to radians.</span></span> 

<span data-ttu-id="d4dbc-213">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-213">**Arguments**</span></span> 

<span data-ttu-id="d4dbc-214">`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="d4dbc-215">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-215">**Return Value**</span></span> 

<span data-ttu-id="d4dbc-216">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="d4dbc-217">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-217">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="d4dbc-218">RAND([seed])</span><span class="sxs-lookup"><span data-stu-id="d4dbc-218">RAND([seed])</span></span>

<span data-ttu-id="d4dbc-219">0 ile 1 arasında rastgele bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-219">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="d4dbc-220">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-220">**Arguments**</span></span> 

<span data-ttu-id="d4dbc-221">Çekirdek değeri olarak bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="d4dbc-222">Çekirdek değer belirtilmemişse, SQL Server veritabanı altyapısı rastgele bir tohum değeri atar.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="d4dbc-223">Belirtilen çekirdek değeri için döndürülen sonuç her zaman aynıdır.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="d4dbc-224">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-224">**Return Value**</span></span> 

<span data-ttu-id="d4dbc-225">Rastgele bir sıra `Double` 0 ile 1 arasında bir değer.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-225">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="d4dbc-226">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-226">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a><span data-ttu-id="d4dbc-227">ROUND(numeric_expression, length[,Function])</span><span class="sxs-lookup"><span data-stu-id="d4dbc-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="d4dbc-228">Belirtilen uzunluk veya duyarlık yuvarlak bir sayısal ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-228">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="d4dbc-229">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-229">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="d4dbc-230">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="d4dbc-231">Bir `Int32` duyarlık olduğu temsil eden `numeric_expression` yuvarlanmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="d4dbc-232">Zaman `length` pozitif bir sayı `numeric_expression` tarafından belirtilen ondalık basamak sayısına yuvarlanır `length`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="d4dbc-233">Zaman `length` negatif bir sayı `numeric_expression` belirtildiği gibi Ondalık ayırıcının sol tarafındaki yuvarlanır `length`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="d4dbc-234">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-234">Optional.</span></span> <span data-ttu-id="d4dbc-235">Bir `Int32` gerçekleştirilecek işlem türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="d4dbc-236">İşlev atlanırsa veya 0 (varsayılan), değeri `numeric_expression` yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="d4dbc-237">0 dışında bir değer belirtilirse, `numeric_expression` kesilir.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="d4dbc-238">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-238">**Return Value**</span></span> 

<span data-ttu-id="d4dbc-239">Belirtilen değeri `numeric_expression` belirtilen `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="d4dbc-240">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-240">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="d4dbc-241">SIGN(Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-241">SIGN(expression)</span></span> 

<span data-ttu-id="d4dbc-242">(+ 1) pozitif, sıfır (0) veya eksi (-1) belirtilen ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="d4dbc-243">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-243">**Arguments**</span></span> 

<span data-ttu-id="d4dbc-244">`expression`: `Int32`, `Int64`, `Double`, veya `Decimal`</span><span class="sxs-lookup"><span data-stu-id="d4dbc-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="d4dbc-245">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-245">**Return Value**</span></span> 

<span data-ttu-id="d4dbc-246">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="d4dbc-247">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-247">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="d4dbc-248">SIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-248">SIN(expression)</span></span>

<span data-ttu-id="d4dbc-249">Trigonometrik radyan cinsinden belirtilen bir açının sinüsünü hesaplar ve döndürür bir `Double` ifade.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="d4dbc-250">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-250">**Arguments**</span></span> 

<span data-ttu-id="d4dbc-251">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-251">`expression`: A `Double`.</span></span> 

<span data-ttu-id="d4dbc-252">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-252">**Return Value**</span></span> 

<span data-ttu-id="d4dbc-253">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-253">A `Double`.</span></span> 

<span data-ttu-id="d4dbc-254">**Örnek** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="d4dbc-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="d4dbc-255">Sqrt(Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-255">SQRT(expression)</span></span>

<span data-ttu-id="d4dbc-256">Belirtilen ifadenin kare kökünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-256">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="d4dbc-257">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-257">**Arguments**</span></span> 

<span data-ttu-id="d4dbc-258">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-258">`expression`: A `Double`.</span></span> 

<span data-ttu-id="d4dbc-259">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-259">**Return Value**</span></span> 

<span data-ttu-id="d4dbc-260">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-260">A `Double`.</span></span> 

<span data-ttu-id="d4dbc-261">**Örnek** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="d4dbc-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="d4dbc-262">SQUARE(Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-262">SQUARE(expression)</span></span>

<span data-ttu-id="d4dbc-263">Belirtilen ifade karesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-263">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="d4dbc-264">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-264">**Arguments**</span></span> 

<span data-ttu-id="d4dbc-265">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-265">`expression`: A `Double`.</span></span> 

<span data-ttu-id="d4dbc-266">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-266">**Return Value**</span></span> 

<span data-ttu-id="d4dbc-267">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-267">A `Double`.</span></span> 

<span data-ttu-id="d4dbc-268">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-268">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="d4dbc-269">TAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-269">TAN(expression)</span></span>

<span data-ttu-id="d4dbc-270">Belirtilen bir ifade tanjantını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="d4dbc-271">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-271">**Arguments**</span></span> 

<span data-ttu-id="d4dbc-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="d4dbc-272">`expression`: `Double`</span></span> 

<span data-ttu-id="d4dbc-273">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-273">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="d4dbc-274">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="d4dbc-274">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="d4dbc-275">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4dbc-275">See also</span></span>

<span data-ttu-id="d4dbc-276">SqlClient destekleyen matematiksel işlevler hakkında daha fazla bilgi için SqlClient sağlayıcı bildiriminde belirtilen SQL Server sürümü için belgelere bakın:</span><span class="sxs-lookup"><span data-stu-id="d4dbc-276">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  
  
<span data-ttu-id="d4dbc-277">**SQL Server 2005'te:** [Matematik işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="d4dbc-277">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>  
<span data-ttu-id="d4dbc-278">**SQL Server 2008:** [Matematik işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="d4dbc-278">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>  
<span data-ttu-id="d4dbc-279">**SQL Server 2012 ve sonraki sürümler:** [Matematik işlevleri (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span><span class="sxs-lookup"><span data-stu-id="d4dbc-279">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span></span>   

 [<span data-ttu-id="d4dbc-280">Entity Framework için SqlClient İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d4dbc-280">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
