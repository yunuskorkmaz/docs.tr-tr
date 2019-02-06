---
title: Matematik işlevleri
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: b6f248382f069df59a55e85e9a764b0df700fb26
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759385"
---
# <a name="mathematical-functions"></a><span data-ttu-id="dc359-102">Matematik işlevleri</span><span class="sxs-lookup"><span data-stu-id="dc359-102">Mathematical Functions</span></span>

<span data-ttu-id="dc359-103">SQL Server (SqlClient) için .NET Framework veri sağlayıcısı, bağımsız değişken olarak sağlanır ve bir sayısal değer sonuç giriş değerleri üzerinde hesaplamalar matematik işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc359-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="dc359-104">Bu işlevler SqlServer ad alanında SqlClient kullanırken, kullanılabilir bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="dc359-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="dc359-105">Bir sağlayıcının ad özelliği, hangi önekin türleri ve işlevleri gibi belirli yapılar için bu sağlayıcı tarafından kullanılan bulmak Entity Framework sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc359-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="dc359-106">Aşağıdaki tabloda SqlClient matematik işlevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dc359-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="dc359-107">ABS(expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-107">ABS(expression)</span></span>

<span data-ttu-id="dc359-108">Mutlak değeri işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="dc359-108">Performs the absolute value function.</span></span>

<span data-ttu-id="dc359-109">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-109">**Arguments**</span></span>

<span data-ttu-id="dc359-110">`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc359-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="dc359-111">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-111">**Return Value**</span></span>

<span data-ttu-id="dc359-112">Belirtilen ifadenin mutlak değeri.</span><span class="sxs-lookup"><span data-stu-id="dc359-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="dc359-113">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="dc359-114">ACOS(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-114">ACOS(expression)</span></span>

<span data-ttu-id="dc359-115">Belirtilen ifade arkkosinüsünü değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc359-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="dc359-116">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-116">**Arguments**</span></span>

<span data-ttu-id="dc359-117">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="dc359-118">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-118">**Return Value**</span></span>

<span data-ttu-id="dc359-119">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-119">A `Double`.</span></span>

<span data-ttu-id="dc359-120">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="dc359-121">ASIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-121">ASIN(expression)</span></span>

<span data-ttu-id="dc359-122">Belirtilen ifade arksinüsünü değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc359-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="dc359-123">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-123">**Arguments**</span></span>

<span data-ttu-id="dc359-124">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="dc359-125">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-125">**Return Value**</span></span>

<span data-ttu-id="dc359-126">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-126">A `Double`.</span></span>

<span data-ttu-id="dc359-127">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="dc359-128">ATAN(expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-128">ATAN(expression)</span></span>

<span data-ttu-id="dc359-129">Belirtilen sayısal ifade arktanjantını değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc359-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="dc359-130">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-130">**Arguments**</span></span>

<span data-ttu-id="dc359-131">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="dc359-132">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-132">**Return Value**</span></span>

<span data-ttu-id="dc359-133">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-133">A `Double`.</span></span>

<span data-ttu-id="dc359-134">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="dc359-135">ATN2(Expression, Expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="dc359-136">Radyan cinsinden tanjantı iki belirli sayısal ifade olan açıyı döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc359-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="dc359-137">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-137">**Arguments**</span></span>

<span data-ttu-id="dc359-138">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="dc359-139">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-139">**Return Value**</span></span>

<span data-ttu-id="dc359-140">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-140">A `Double`.</span></span>

<span data-ttu-id="dc359-141">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="dc359-142">CEILING(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-142">CEILING(expression)</span></span>

<span data-ttu-id="dc359-143">Belirtilen ifade değerinden büyük veya ona eşit olan en küçük tamsayı dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="dc359-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="dc359-144">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-144">**Arguments**</span></span>

<span data-ttu-id="dc359-145">`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc359-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="dc359-146">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-146">**Return Value**</span></span>

<span data-ttu-id="dc359-147">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc359-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="dc359-148">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-148">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="dc359-149">COS(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-149">COS(expression)</span></span>

<span data-ttu-id="dc359-150">Trigonometrik radyan cinsinden belirtilen bir açının kosinüsünü hesaplar.</span><span class="sxs-lookup"><span data-stu-id="dc359-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="dc359-151">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-151">**Arguments**</span></span> 

<span data-ttu-id="dc359-152">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-152">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc359-153">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-153">**Return Value**</span></span> 

<span data-ttu-id="dc359-154">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-154">A `Double`.</span></span> 

<span data-ttu-id="dc359-155">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-155">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="dc359-156">COT(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-156">COT(expression)</span></span>

<span data-ttu-id="dc359-157">Trigonometrik radyan cinsinden belirtilen bir açının kotanjantını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="dc359-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="dc359-158">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-158">**Arguments**</span></span> 

<span data-ttu-id="dc359-159">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-159">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc359-160">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-160">**Return Value**</span></span> 

<span data-ttu-id="dc359-161">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-161">A `Double`.</span></span> 

<span data-ttu-id="dc359-162">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-162">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="dc359-163">DEGREES(radians)</span><span class="sxs-lookup"><span data-stu-id="dc359-163">DEGREES(radians)</span></span>

<span data-ttu-id="dc359-164">Karşılık gelen açıyı derece cinsinden döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc359-164">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="dc359-165">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-165">**Arguments**</span></span> 

<span data-ttu-id="dc359-166">`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc359-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="dc359-167">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-167">**Return Value**</span></span> 

<span data-ttu-id="dc359-168">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc359-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="dc359-169">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-169">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="dc359-170">EXP(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-170">EXP(expression)</span></span>

<span data-ttu-id="dc359-171">Belirtilen bir sayısal ifade üs değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="dc359-171">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="dc359-172">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-172">**Arguments**</span></span> 

<span data-ttu-id="dc359-173">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-173">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc359-174">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-174">**Return Value**</span></span> 

<span data-ttu-id="dc359-175">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-175">A `Double`.</span></span> 

<span data-ttu-id="dc359-176">**Örnek** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="dc359-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="dc359-177">FLOOR(expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-177">FLOOR(expression)</span></span>

<span data-ttu-id="dc359-178">Belirtilen ifadedeki en büyük tamsayı daha az veya eşit ona dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="dc359-178">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="dc359-179">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-179">**Arguments**</span></span> 

<span data-ttu-id="dc359-180">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-180">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc359-181">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-181">**Return Value**</span></span> 

<span data-ttu-id="dc359-182">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-182">A `Double`.</span></span> 

<span data-ttu-id="dc359-183">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-183">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="dc359-184">LOG(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-184">LOG(expression)</span></span>

<span data-ttu-id="dc359-185">Belirtilen doğal logaritmasını hesaplar `float` ifade.</span><span class="sxs-lookup"><span data-stu-id="dc359-185">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="dc359-186">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-186">**Arguments**</span></span> 

<span data-ttu-id="dc359-187">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-187">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc359-188">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-188">**Return Value**</span></span> 

<span data-ttu-id="dc359-189">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-189">A `Double`.</span></span> 

<span data-ttu-id="dc359-190">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-190">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="dc359-191">Log10(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-191">LOG10(expression)</span></span>

<span data-ttu-id="dc359-192">Belirtilen 10 tabanında logaritmasını döndürür `Double` ifade.</span><span class="sxs-lookup"><span data-stu-id="dc359-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="dc359-193">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-193">**Arguments**</span></span> 

<span data-ttu-id="dc359-194">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-194">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc359-195">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-195">**Return Value**</span></span> 

<span data-ttu-id="dc359-196">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-196">A `Double`.</span></span> 

<span data-ttu-id="dc359-197">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-197">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="dc359-198">PI()</span><span class="sxs-lookup"><span data-stu-id="dc359-198">PI()</span></span>

<span data-ttu-id="dc359-199">Sabit değer pi'nin döndürür bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-199">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="dc359-200">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-200">**Return Value**</span></span> 

<span data-ttu-id="dc359-201">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-201">A `Double`.</span></span> 

<span data-ttu-id="dc359-202">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-202">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a><span data-ttu-id="dc359-203">POWER(numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="dc359-204">Belirtilen bir ifadenin belirtilen bir kuvvete değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="dc359-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="dc359-205">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-205">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="dc359-206">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc359-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="dc359-207">A `Double` yükseltmek istediğiniz gücünü temsil eden `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="dc359-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="dc359-208">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-208">**Return Value**</span></span> 

<span data-ttu-id="dc359-209">Belirtilen değeri `numeric_expression` belirtilen `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="dc359-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="dc359-210">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-210">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="dc359-211">RADIANS(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-211">RADIANS(expression)</span></span>

<span data-ttu-id="dc359-212">Dereceyi radyana dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="dc359-212">Converts degrees to radians.</span></span> 

<span data-ttu-id="dc359-213">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-213">**Arguments**</span></span> 

<span data-ttu-id="dc359-214">`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc359-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="dc359-215">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-215">**Return Value**</span></span> 

<span data-ttu-id="dc359-216">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc359-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="dc359-217">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-217">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="dc359-218">RAND([seed])</span><span class="sxs-lookup"><span data-stu-id="dc359-218">RAND([seed])</span></span>

<span data-ttu-id="dc359-219">0 ile 1 arasında rastgele bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc359-219">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="dc359-220">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-220">**Arguments**</span></span> 

<span data-ttu-id="dc359-221">Çekirdek değeri olarak bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="dc359-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="dc359-222">Çekirdek değer belirtilmemişse, SQL Server veritabanı altyapısı rastgele bir tohum değeri atar.</span><span class="sxs-lookup"><span data-stu-id="dc359-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="dc359-223">Belirtilen çekirdek değeri için döndürülen sonuç her zaman aynıdır.</span><span class="sxs-lookup"><span data-stu-id="dc359-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="dc359-224">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-224">**Return Value**</span></span> 

<span data-ttu-id="dc359-225">Rastgele bir sıra `Double` 0 ile 1 arasında bir değer.</span><span class="sxs-lookup"><span data-stu-id="dc359-225">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="dc359-226">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-226">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a><span data-ttu-id="dc359-227">ROUND(numeric_expression, length[,Function])</span><span class="sxs-lookup"><span data-stu-id="dc359-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="dc359-228">Belirtilen uzunluk veya duyarlık yuvarlak bir sayısal ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc359-228">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="dc359-229">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-229">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="dc359-230">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc359-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="dc359-231">Bir `Int32` duyarlık olduğu temsil eden `numeric_expression` yuvarlanmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="dc359-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="dc359-232">Zaman `length` pozitif bir sayı `numeric_expression` tarafından belirtilen ondalık basamak sayısına yuvarlanır `length`.</span><span class="sxs-lookup"><span data-stu-id="dc359-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="dc359-233">Zaman `length` negatif bir sayı `numeric_expression` belirtildiği gibi Ondalık ayırıcının sol tarafındaki yuvarlanır `length`.</span><span class="sxs-lookup"><span data-stu-id="dc359-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="dc359-234">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dc359-234">Optional.</span></span> <span data-ttu-id="dc359-235">Bir `Int32` gerçekleştirilecek işlem türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dc359-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="dc359-236">İşlev atlanırsa veya 0 (varsayılan), değeri `numeric_expression` yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="dc359-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="dc359-237">0 dışında bir değer belirtilirse, `numeric_expression` kesilir.</span><span class="sxs-lookup"><span data-stu-id="dc359-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="dc359-238">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-238">**Return Value**</span></span> 

<span data-ttu-id="dc359-239">Belirtilen değeri `numeric_expression` belirtilen `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="dc359-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="dc359-240">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-240">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="dc359-241">SIGN(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-241">SIGN(expression)</span></span> 

<span data-ttu-id="dc359-242">(+ 1) pozitif, sıfır (0) veya eksi (-1) belirtilen ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc359-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="dc359-243">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-243">**Arguments**</span></span> 

<span data-ttu-id="dc359-244">`expression`: `Int32`, `Int64`, `Double`, veya `Decimal`</span><span class="sxs-lookup"><span data-stu-id="dc359-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="dc359-245">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-245">**Return Value**</span></span> 

<span data-ttu-id="dc359-246">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="dc359-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="dc359-247">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-247">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="dc359-248">SIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-248">SIN(expression)</span></span>

<span data-ttu-id="dc359-249">Trigonometrik radyan cinsinden belirtilen bir açının sinüsünü hesaplar ve döndürür bir `Double` ifade.</span><span class="sxs-lookup"><span data-stu-id="dc359-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="dc359-250">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-250">**Arguments**</span></span> 

<span data-ttu-id="dc359-251">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-251">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc359-252">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-252">**Return Value**</span></span> 

<span data-ttu-id="dc359-253">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-253">A `Double`.</span></span> 

<span data-ttu-id="dc359-254">**Örnek** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="dc359-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="dc359-255">Sqrt(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-255">SQRT(expression)</span></span>

<span data-ttu-id="dc359-256">Belirtilen ifadenin kare kökünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc359-256">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="dc359-257">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-257">**Arguments**</span></span> 

<span data-ttu-id="dc359-258">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-258">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc359-259">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-259">**Return Value**</span></span> 

<span data-ttu-id="dc359-260">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-260">A `Double`.</span></span> 

<span data-ttu-id="dc359-261">**Örnek** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="dc359-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="dc359-262">SQUARE(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-262">SQUARE(expression)</span></span>

<span data-ttu-id="dc359-263">Belirtilen ifade karesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc359-263">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="dc359-264">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-264">**Arguments**</span></span> 

<span data-ttu-id="dc359-265">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-265">`expression`: A `Double`.</span></span> 

<span data-ttu-id="dc359-266">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-266">**Return Value**</span></span> 

<span data-ttu-id="dc359-267">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="dc359-267">A `Double`.</span></span> 

<span data-ttu-id="dc359-268">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-268">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="dc359-269">TAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="dc359-269">TAN(expression)</span></span>

<span data-ttu-id="dc359-270">Belirtilen bir ifade tanjantını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="dc359-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="dc359-271">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="dc359-271">**Arguments**</span></span> 

<span data-ttu-id="dc359-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="dc359-272">`expression`: `Double`</span></span> 

<span data-ttu-id="dc359-273">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="dc359-273">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="dc359-274">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="dc359-274">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="dc359-275">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc359-275">See also</span></span>

<span data-ttu-id="dc359-276">SqlClient destekleyen matematiksel işlevler hakkında daha fazla bilgi için SqlClient sağlayıcı bildiriminde belirtilen SQL Server sürümü için belgelere bakın:</span><span class="sxs-lookup"><span data-stu-id="dc359-276">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="dc359-277">**SQL Server 2005:** [Matematik işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="dc359-277">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>
- <span data-ttu-id="dc359-278">**SQL Server 2008:** [Matematik işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="dc359-278">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>
- <span data-ttu-id="dc359-279">**SQL Server 2012 ve sonraki sürümler:** [Matematik işlevleri (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span><span class="sxs-lookup"><span data-stu-id="dc359-279">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span></span>

- [<span data-ttu-id="dc359-280">Entity Framework için SqlClient İşlevleri</span><span class="sxs-lookup"><span data-stu-id="dc359-280">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
