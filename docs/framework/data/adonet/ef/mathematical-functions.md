---
title: Matematik İşlevleri
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: b6f248382f069df59a55e85e9a764b0df700fb26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780321"
---
# <a name="mathematical-functions"></a><span data-ttu-id="5a183-102">Matematik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5a183-102">Mathematical Functions</span></span>

<span data-ttu-id="5a183-103">SQL Server (SqlClient) için .NET Framework veri sağlayıcısı, bağımsız değişken olarak sağlanır ve bir sayısal değer sonuç giriş değerleri üzerinde hesaplamalar matematik işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a183-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="5a183-104">Bu işlevler SqlServer ad alanında SqlClient kullanırken, kullanılabilir bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="5a183-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="5a183-105">Bir sağlayıcının ad özelliği, hangi önekin türleri ve işlevleri gibi belirli yapılar için bu sağlayıcı tarafından kullanılan bulmak Entity Framework sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a183-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="5a183-106">Aşağıdaki tabloda SqlClient matematik işlevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5a183-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="5a183-107">ABS(expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-107">ABS(expression)</span></span>

<span data-ttu-id="5a183-108">Mutlak değeri işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="5a183-108">Performs the absolute value function.</span></span>

<span data-ttu-id="5a183-109">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-109">**Arguments**</span></span>

<span data-ttu-id="5a183-110">`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="5a183-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="5a183-111">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-111">**Return Value**</span></span>

<span data-ttu-id="5a183-112">Belirtilen ifadenin mutlak değeri.</span><span class="sxs-lookup"><span data-stu-id="5a183-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="5a183-113">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="5a183-114">ACOS(Expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-114">ACOS(expression)</span></span>

<span data-ttu-id="5a183-115">Belirtilen ifade arkkosinüsünü değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5a183-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="5a183-116">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-116">**Arguments**</span></span>

<span data-ttu-id="5a183-117">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="5a183-118">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-118">**Return Value**</span></span>

<span data-ttu-id="5a183-119">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-119">A `Double`.</span></span>

<span data-ttu-id="5a183-120">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="5a183-121">ASIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-121">ASIN(expression)</span></span>

<span data-ttu-id="5a183-122">Belirtilen ifade arksinüsünü değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5a183-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="5a183-123">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-123">**Arguments**</span></span>

<span data-ttu-id="5a183-124">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="5a183-125">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-125">**Return Value**</span></span>

<span data-ttu-id="5a183-126">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-126">A `Double`.</span></span>

<span data-ttu-id="5a183-127">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="5a183-128">ATAN(expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-128">ATAN(expression)</span></span>

<span data-ttu-id="5a183-129">Belirtilen sayısal ifade arktanjantını değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5a183-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="5a183-130">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-130">**Arguments**</span></span>

<span data-ttu-id="5a183-131">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="5a183-132">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-132">**Return Value**</span></span>

<span data-ttu-id="5a183-133">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-133">A `Double`.</span></span>

<span data-ttu-id="5a183-134">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="5a183-135">ATN2(Expression, Expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="5a183-136">Radyan cinsinden tanjantı iki belirli sayısal ifade olan açıyı döndürür.</span><span class="sxs-lookup"><span data-stu-id="5a183-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="5a183-137">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-137">**Arguments**</span></span>

<span data-ttu-id="5a183-138">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="5a183-139">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-139">**Return Value**</span></span>

<span data-ttu-id="5a183-140">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-140">A `Double`.</span></span>

<span data-ttu-id="5a183-141">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="5a183-142">CEILING(Expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-142">CEILING(expression)</span></span>

<span data-ttu-id="5a183-143">Belirtilen ifade değerinden büyük veya ona eşit olan en küçük tamsayı dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5a183-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="5a183-144">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-144">**Arguments**</span></span>

<span data-ttu-id="5a183-145">`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="5a183-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="5a183-146">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-146">**Return Value**</span></span>

<span data-ttu-id="5a183-147">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="5a183-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="5a183-148">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-148">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="5a183-149">COS(Expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-149">COS(expression)</span></span>

<span data-ttu-id="5a183-150">Trigonometrik radyan cinsinden belirtilen bir açının kosinüsünü hesaplar.</span><span class="sxs-lookup"><span data-stu-id="5a183-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="5a183-151">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-151">**Arguments**</span></span> 

<span data-ttu-id="5a183-152">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-152">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5a183-153">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-153">**Return Value**</span></span> 

<span data-ttu-id="5a183-154">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-154">A `Double`.</span></span> 

<span data-ttu-id="5a183-155">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-155">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="5a183-156">COT(Expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-156">COT(expression)</span></span>

<span data-ttu-id="5a183-157">Trigonometrik radyan cinsinden belirtilen bir açının kotanjantını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="5a183-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="5a183-158">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-158">**Arguments**</span></span> 

<span data-ttu-id="5a183-159">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-159">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5a183-160">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-160">**Return Value**</span></span> 

<span data-ttu-id="5a183-161">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-161">A `Double`.</span></span> 

<span data-ttu-id="5a183-162">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-162">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="5a183-163">DEGREES(radians)</span><span class="sxs-lookup"><span data-stu-id="5a183-163">DEGREES(radians)</span></span>

<span data-ttu-id="5a183-164">Karşılık gelen açıyı derece cinsinden döndürür.</span><span class="sxs-lookup"><span data-stu-id="5a183-164">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="5a183-165">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-165">**Arguments**</span></span> 

<span data-ttu-id="5a183-166">`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="5a183-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="5a183-167">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-167">**Return Value**</span></span> 

<span data-ttu-id="5a183-168">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="5a183-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="5a183-169">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-169">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="5a183-170">EXP(Expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-170">EXP(expression)</span></span>

<span data-ttu-id="5a183-171">Belirtilen bir sayısal ifade üs değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="5a183-171">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="5a183-172">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-172">**Arguments**</span></span> 

<span data-ttu-id="5a183-173">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-173">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5a183-174">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-174">**Return Value**</span></span> 

<span data-ttu-id="5a183-175">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-175">A `Double`.</span></span> 

<span data-ttu-id="5a183-176">**Örnek** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="5a183-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="5a183-177">FLOOR(expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-177">FLOOR(expression)</span></span>

<span data-ttu-id="5a183-178">Belirtilen ifadedeki en büyük tamsayı daha az veya eşit ona dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5a183-178">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="5a183-179">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-179">**Arguments**</span></span> 

<span data-ttu-id="5a183-180">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-180">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5a183-181">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-181">**Return Value**</span></span> 

<span data-ttu-id="5a183-182">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-182">A `Double`.</span></span> 

<span data-ttu-id="5a183-183">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-183">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="5a183-184">LOG(Expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-184">LOG(expression)</span></span>

<span data-ttu-id="5a183-185">Belirtilen doğal logaritmasını hesaplar `float` ifade.</span><span class="sxs-lookup"><span data-stu-id="5a183-185">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="5a183-186">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-186">**Arguments**</span></span> 

<span data-ttu-id="5a183-187">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-187">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5a183-188">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-188">**Return Value**</span></span> 

<span data-ttu-id="5a183-189">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-189">A `Double`.</span></span> 

<span data-ttu-id="5a183-190">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-190">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="5a183-191">Log10(Expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-191">LOG10(expression)</span></span>

<span data-ttu-id="5a183-192">Belirtilen 10 tabanında logaritmasını döndürür `Double` ifade.</span><span class="sxs-lookup"><span data-stu-id="5a183-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="5a183-193">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-193">**Arguments**</span></span> 

<span data-ttu-id="5a183-194">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-194">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5a183-195">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-195">**Return Value**</span></span> 

<span data-ttu-id="5a183-196">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-196">A `Double`.</span></span> 

<span data-ttu-id="5a183-197">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-197">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="5a183-198">PI()</span><span class="sxs-lookup"><span data-stu-id="5a183-198">PI()</span></span>

<span data-ttu-id="5a183-199">Sabit değer pi'nin döndürür bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-199">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="5a183-200">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-200">**Return Value**</span></span> 

<span data-ttu-id="5a183-201">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-201">A `Double`.</span></span> 

<span data-ttu-id="5a183-202">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-202">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a><span data-ttu-id="5a183-203">POWER(numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="5a183-204">Belirtilen bir ifadenin belirtilen bir kuvvete değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="5a183-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="5a183-205">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-205">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="5a183-206">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="5a183-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="5a183-207">A `Double` yükseltmek istediğiniz gücünü temsil eden `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="5a183-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="5a183-208">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-208">**Return Value**</span></span> 

<span data-ttu-id="5a183-209">Belirtilen değeri `numeric_expression` belirtilen `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="5a183-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="5a183-210">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-210">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="5a183-211">RADIANS(Expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-211">RADIANS(expression)</span></span>

<span data-ttu-id="5a183-212">Dereceyi radyana dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5a183-212">Converts degrees to radians.</span></span> 

<span data-ttu-id="5a183-213">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-213">**Arguments**</span></span> 

<span data-ttu-id="5a183-214">`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="5a183-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="5a183-215">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-215">**Return Value**</span></span> 

<span data-ttu-id="5a183-216">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="5a183-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="5a183-217">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-217">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="5a183-218">RAND([seed])</span><span class="sxs-lookup"><span data-stu-id="5a183-218">RAND([seed])</span></span>

<span data-ttu-id="5a183-219">0 ile 1 arasında rastgele bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="5a183-219">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="5a183-220">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-220">**Arguments**</span></span> 

<span data-ttu-id="5a183-221">Çekirdek değeri olarak bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="5a183-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="5a183-222">Çekirdek değer belirtilmemişse, SQL Server veritabanı altyapısı rastgele bir tohum değeri atar.</span><span class="sxs-lookup"><span data-stu-id="5a183-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="5a183-223">Belirtilen çekirdek değeri için döndürülen sonuç her zaman aynıdır.</span><span class="sxs-lookup"><span data-stu-id="5a183-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="5a183-224">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-224">**Return Value**</span></span> 

<span data-ttu-id="5a183-225">Rastgele bir sıra `Double` 0 ile 1 arasında bir değer.</span><span class="sxs-lookup"><span data-stu-id="5a183-225">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="5a183-226">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-226">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a><span data-ttu-id="5a183-227">ROUND(numeric_expression, length[,Function])</span><span class="sxs-lookup"><span data-stu-id="5a183-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="5a183-228">Belirtilen uzunluk veya duyarlık yuvarlak bir sayısal ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="5a183-228">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="5a183-229">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-229">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="5a183-230">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="5a183-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="5a183-231">Bir `Int32` duyarlık olduğu temsil eden `numeric_expression` yuvarlanmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="5a183-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="5a183-232">Zaman `length` pozitif bir sayı `numeric_expression` tarafından belirtilen ondalık basamak sayısına yuvarlanır `length`.</span><span class="sxs-lookup"><span data-stu-id="5a183-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="5a183-233">Zaman `length` negatif bir sayı `numeric_expression` belirtildiği gibi Ondalık ayırıcının sol tarafındaki yuvarlanır `length`.</span><span class="sxs-lookup"><span data-stu-id="5a183-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="5a183-234">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5a183-234">Optional.</span></span> <span data-ttu-id="5a183-235">Bir `Int32` gerçekleştirilecek işlem türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5a183-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="5a183-236">İşlev atlanırsa veya 0 (varsayılan), değeri `numeric_expression` yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="5a183-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="5a183-237">0 dışında bir değer belirtilirse, `numeric_expression` kesilir.</span><span class="sxs-lookup"><span data-stu-id="5a183-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="5a183-238">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-238">**Return Value**</span></span> 

<span data-ttu-id="5a183-239">Belirtilen değeri `numeric_expression` belirtilen `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="5a183-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="5a183-240">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-240">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="5a183-241">SIGN(Expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-241">SIGN(expression)</span></span> 

<span data-ttu-id="5a183-242">(+ 1) pozitif, sıfır (0) veya eksi (-1) belirtilen ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="5a183-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="5a183-243">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-243">**Arguments**</span></span> 

<span data-ttu-id="5a183-244">`expression`: `Int32`, `Int64`, `Double`, veya `Decimal`</span><span class="sxs-lookup"><span data-stu-id="5a183-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="5a183-245">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-245">**Return Value**</span></span> 

<span data-ttu-id="5a183-246">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="5a183-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="5a183-247">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-247">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="5a183-248">SIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-248">SIN(expression)</span></span>

<span data-ttu-id="5a183-249">Trigonometrik radyan cinsinden belirtilen bir açının sinüsünü hesaplar ve döndürür bir `Double` ifade.</span><span class="sxs-lookup"><span data-stu-id="5a183-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="5a183-250">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-250">**Arguments**</span></span> 

<span data-ttu-id="5a183-251">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-251">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5a183-252">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-252">**Return Value**</span></span> 

<span data-ttu-id="5a183-253">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-253">A `Double`.</span></span> 

<span data-ttu-id="5a183-254">**Örnek** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="5a183-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="5a183-255">Sqrt(Expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-255">SQRT(expression)</span></span>

<span data-ttu-id="5a183-256">Belirtilen ifadenin kare kökünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="5a183-256">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="5a183-257">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-257">**Arguments**</span></span> 

<span data-ttu-id="5a183-258">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-258">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5a183-259">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-259">**Return Value**</span></span> 

<span data-ttu-id="5a183-260">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-260">A `Double`.</span></span> 

<span data-ttu-id="5a183-261">**Örnek** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="5a183-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="5a183-262">SQUARE(Expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-262">SQUARE(expression)</span></span>

<span data-ttu-id="5a183-263">Belirtilen ifade karesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5a183-263">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="5a183-264">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-264">**Arguments**</span></span> 

<span data-ttu-id="5a183-265">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-265">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5a183-266">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-266">**Return Value**</span></span> 

<span data-ttu-id="5a183-267">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5a183-267">A `Double`.</span></span> 

<span data-ttu-id="5a183-268">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-268">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="5a183-269">TAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="5a183-269">TAN(expression)</span></span>

<span data-ttu-id="5a183-270">Belirtilen bir ifade tanjantını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="5a183-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="5a183-271">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5a183-271">**Arguments**</span></span> 

<span data-ttu-id="5a183-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="5a183-272">`expression`: `Double`</span></span> 

<span data-ttu-id="5a183-273">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5a183-273">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="5a183-274">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5a183-274">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="5a183-275">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a183-275">See also</span></span>

<span data-ttu-id="5a183-276">SqlClient destekleyen matematiksel işlevler hakkında daha fazla bilgi için SqlClient sağlayıcı bildiriminde belirtilen SQL Server sürümü için belgelere bakın:</span><span class="sxs-lookup"><span data-stu-id="5a183-276">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="5a183-277">**SQL Server 2005:** [Matematik işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="5a183-277">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>
- <span data-ttu-id="5a183-278">**SQL Server 2008:** [Matematik işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="5a183-278">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>
- <span data-ttu-id="5a183-279">**SQL Server 2012 ve sonraki sürümler:** [Matematik işlevleri (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span><span class="sxs-lookup"><span data-stu-id="5a183-279">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span></span>

- [<span data-ttu-id="5a183-280">Entity Framework için SqlClient İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5a183-280">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
