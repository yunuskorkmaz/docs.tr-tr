---
title: Matematik işlevleri
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: e6c58d781d7138f8295f2d0a2f0db110ad4b1dd6
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48793467"
---
# <a name="mathematical-functions"></a><span data-ttu-id="764e1-102">Matematik işlevleri</span><span class="sxs-lookup"><span data-stu-id="764e1-102">Mathematical Functions</span></span>

<span data-ttu-id="764e1-103">SQL Server (SqlClient) için .NET Framework veri sağlayıcısı, bağımsız değişken olarak sağlanır ve bir sayısal değer sonuç giriş değerleri üzerinde hesaplamalar matematik işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="764e1-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="764e1-104">Bu işlevler SqlServer ad alanında SqlClient kullanırken, kullanılabilir bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="764e1-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="764e1-105">Bir sağlayıcının ad özelliği, hangi önekin türleri ve işlevleri gibi belirli yapılar için bu sağlayıcı tarafından kullanılan bulmak Entity Framework sağlar. Aşağıdaki tabloda SqlClient matematik işlevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="764e1-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="764e1-106">Abs(Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-106">ABS(expression)</span></span>

<span data-ttu-id="764e1-107">Mutlak değeri işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="764e1-107">Performs the absolute value function.</span></span>

<span data-ttu-id="764e1-108">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-108">**Arguments**</span></span>

<span data-ttu-id="764e1-109">`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="764e1-109">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="764e1-110">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-110">**Return Value**</span></span>

<span data-ttu-id="764e1-111">Belirtilen ifadenin mutlak değeri.</span><span class="sxs-lookup"><span data-stu-id="764e1-111">The absolute value of the specified expression.</span></span>

<span data-ttu-id="764e1-112">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-112">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="764e1-113">ACOS(Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-113">ACOS(expression)</span></span>

<span data-ttu-id="764e1-114">Belirtilen ifade arkkosinüsünü değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="764e1-114">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="764e1-115">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-115">**Arguments**</span></span>

<span data-ttu-id="764e1-116">`expression`: BİR `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-116">`expression`: A `Double`.</span></span>

<span data-ttu-id="764e1-117">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-117">**Return Value**</span></span>

<span data-ttu-id="764e1-118">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-118">A `Double`.</span></span>

<span data-ttu-id="764e1-119">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-119">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="764e1-120">ASIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-120">ASIN(expression)</span></span>

<span data-ttu-id="764e1-121">Belirtilen ifade arksinüsünü değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="764e1-121">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="764e1-122">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-122">**Arguments**</span></span>

<span data-ttu-id="764e1-123">`expression`: BİR `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-123">`expression`: A `Double`.</span></span>

<span data-ttu-id="764e1-124">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-124">**Return Value**</span></span>

<span data-ttu-id="764e1-125">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-125">A `Double`.</span></span>

<span data-ttu-id="764e1-126">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-126">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="764e1-127">ATAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-127">ATAN(expression)</span></span>

<span data-ttu-id="764e1-128">Belirtilen sayısal ifade arktanjantını değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="764e1-128">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="764e1-129">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-129">**Arguments**</span></span>

<span data-ttu-id="764e1-130">`expression`: BİR `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-130">`expression`: A `Double`.</span></span>

<span data-ttu-id="764e1-131">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-131">**Return Value**</span></span>

<span data-ttu-id="764e1-132">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-132">A `Double`.</span></span>

<span data-ttu-id="764e1-133">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-133">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="764e1-134">ATN2(Expression, Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-134">ATN2(expression, expression)</span></span>

<span data-ttu-id="764e1-135">Radyan cinsinden tanjantı iki belirli sayısal ifade olan açıyı döndürür.</span><span class="sxs-lookup"><span data-stu-id="764e1-135">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="764e1-136">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-136">**Arguments**</span></span>

<span data-ttu-id="764e1-137">`expression`: BİR `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-137">`expression`: A `Double`.</span></span>

<span data-ttu-id="764e1-138">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-138">**Return Value**</span></span>

<span data-ttu-id="764e1-139">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-139">A `Double`.</span></span>

<span data-ttu-id="764e1-140">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-140">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="764e1-141">CEILING(Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-141">CEILING(expression)</span></span>

<span data-ttu-id="764e1-142">Belirtilen ifade değerinden büyük veya ona eşit olan en küçük tamsayı dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="764e1-142">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="764e1-143">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-143">**Arguments**</span></span>

<span data-ttu-id="764e1-144">`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="764e1-144">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="764e1-145">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-145">**Return Value**</span></span>

<span data-ttu-id="764e1-146">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="764e1-146">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="764e1-147">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-147">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="764e1-148">COS(Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-148">COS(expression)</span></span>

<span data-ttu-id="764e1-149">Trigonometrik radyan cinsinden belirtilen bir açının kosinüsünü hesaplar.</span><span class="sxs-lookup"><span data-stu-id="764e1-149">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="764e1-150">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-150">**Arguments**</span></span> 

<span data-ttu-id="764e1-151">`expression`: BİR `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-151">`expression`: A `Double`.</span></span> 

<span data-ttu-id="764e1-152">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-152">**Return Value**</span></span> 

<span data-ttu-id="764e1-153">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-153">A `Double`.</span></span> 

<span data-ttu-id="764e1-154">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-154">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="764e1-155">COT(Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-155">COT(expression)</span></span>

<span data-ttu-id="764e1-156">Trigonometrik radyan cinsinden belirtilen bir açının kotanjantını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="764e1-156">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="764e1-157">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-157">**Arguments**</span></span> 

<span data-ttu-id="764e1-158">`expression`: BİR `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-158">`expression`: A `Double`.</span></span> 

<span data-ttu-id="764e1-159">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-159">**Return Value**</span></span> 

<span data-ttu-id="764e1-160">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-160">A `Double`.</span></span> 

<span data-ttu-id="764e1-161">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-161">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="764e1-162">DEGREES(radians)</span><span class="sxs-lookup"><span data-stu-id="764e1-162">DEGREES(radians)</span></span>

<span data-ttu-id="764e1-163">Karşılık gelen açıyı derece cinsinden döndürür.</span><span class="sxs-lookup"><span data-stu-id="764e1-163">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="764e1-164">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-164">**Arguments**</span></span> 

<span data-ttu-id="764e1-165">`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="764e1-165">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="764e1-166">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-166">**Return Value**</span></span> 

<span data-ttu-id="764e1-167">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="764e1-167">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="764e1-168">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-168">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="764e1-169">EXP(Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-169">EXP(expression)</span></span>

<span data-ttu-id="764e1-170">Belirtilen bir sayısal ifade üs değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="764e1-170">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="764e1-171">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-171">**Arguments**</span></span> 

<span data-ttu-id="764e1-172">`expression`: BİR `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-172">`expression`: A `Double`.</span></span> 

<span data-ttu-id="764e1-173">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-173">**Return Value**</span></span> 

<span data-ttu-id="764e1-174">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-174">A `Double`.</span></span> 

<span data-ttu-id="764e1-175">**Örnek** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="764e1-175">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="764e1-176">FLOOR(Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-176">FLOOR(expression)</span></span>

<span data-ttu-id="764e1-177">Belirtilen ifadedeki en büyük tamsayı daha az veya eşit ona dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="764e1-177">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="764e1-178">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-178">**Arguments**</span></span> 

<span data-ttu-id="764e1-179">`expression`: BİR `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-179">`expression`: A `Double`.</span></span> 

<span data-ttu-id="764e1-180">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-180">**Return Value**</span></span> 

<span data-ttu-id="764e1-181">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-181">A `Double`.</span></span> 

<span data-ttu-id="764e1-182">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-182">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="764e1-183">LOG(Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-183">LOG(expression)</span></span>

<span data-ttu-id="764e1-184">Belirtilen doğal logaritmasını hesaplar `float` ifade.</span><span class="sxs-lookup"><span data-stu-id="764e1-184">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="764e1-185">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-185">**Arguments**</span></span> 

<span data-ttu-id="764e1-186">`expression`: BİR `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-186">`expression`: A `Double`.</span></span> 

<span data-ttu-id="764e1-187">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-187">**Return Value**</span></span> 

<span data-ttu-id="764e1-188">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-188">A `Double`.</span></span> 

<span data-ttu-id="764e1-189">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-189">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="764e1-190">Log10(Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-190">LOG10(expression)</span></span>

<span data-ttu-id="764e1-191">Belirtilen 10 tabanında logaritmasını döndürür `Double` ifade.</span><span class="sxs-lookup"><span data-stu-id="764e1-191">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="764e1-192">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-192">**Arguments**</span></span> 

<span data-ttu-id="764e1-193">`expression`: BİR `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-193">`expression`: A `Double`.</span></span> 

<span data-ttu-id="764e1-194">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-194">**Return Value**</span></span> 

<span data-ttu-id="764e1-195">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-195">A `Double`.</span></span> 

<span data-ttu-id="764e1-196">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-196">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="764e1-197">PI()</span><span class="sxs-lookup"><span data-stu-id="764e1-197">PI()</span></span>

<span data-ttu-id="764e1-198">Sabit değer pi'nin döndürür bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-198">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="764e1-199">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-199">**Return Value**</span></span> 

<span data-ttu-id="764e1-200">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-200">A `Double`.</span></span> 

<span data-ttu-id="764e1-201">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-201">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a><span data-ttu-id="764e1-202">GÜÇ (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-202">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="764e1-203">Belirtilen bir ifadenin belirtilen bir kuvvete değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="764e1-203">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="764e1-204">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-204">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="764e1-205">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="764e1-205">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="764e1-206">A `Double` yükseltmek istediğiniz gücünü temsil eden `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="764e1-206">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="764e1-207">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-207">**Return Value**</span></span> 

<span data-ttu-id="764e1-208">Belirtilen değeri `numeric_expression` belirtilen `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="764e1-208">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="764e1-209">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-209">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="764e1-210">RADIANS(Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-210">RADIANS(expression)</span></span>

<span data-ttu-id="764e1-211">Dereceyi radyana dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="764e1-211">Converts degrees to radians.</span></span> 

<span data-ttu-id="764e1-212">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-212">**Arguments**</span></span> 

<span data-ttu-id="764e1-213">`expression`: Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="764e1-213">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="764e1-214">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-214">**Return Value**</span></span> 

<span data-ttu-id="764e1-215">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="764e1-215">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="764e1-216">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-216">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="764e1-217">RAND([seed])</span><span class="sxs-lookup"><span data-stu-id="764e1-217">RAND([seed])</span></span>

<span data-ttu-id="764e1-218">0 ile 1 arasında rastgele bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="764e1-218">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="764e1-219">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-219">**Arguments**</span></span> 

<span data-ttu-id="764e1-220">Çekirdek değeri olarak bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="764e1-220">The seed value as an `Int32`.</span></span> <span data-ttu-id="764e1-221">Çekirdek değer belirtilmemişse, SQL Server veritabanı altyapısı rastgele bir tohum değeri atar.</span><span class="sxs-lookup"><span data-stu-id="764e1-221">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="764e1-222">Belirtilen çekirdek değeri için döndürülen sonuç her zaman aynıdır.</span><span class="sxs-lookup"><span data-stu-id="764e1-222">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="764e1-223">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-223">**Return Value**</span></span> 

<span data-ttu-id="764e1-224">Rastgele bir sıra `Double` 0 ile 1 arasında bir değer.</span><span class="sxs-lookup"><span data-stu-id="764e1-224">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="764e1-225">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-225">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a><span data-ttu-id="764e1-226">ROUND(numeric_expression, length[,Function])</span><span class="sxs-lookup"><span data-stu-id="764e1-226">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="764e1-227">Belirtilen uzunluk veya duyarlık yuvarlak bir sayısal ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="764e1-227">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="764e1-228">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-228">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="764e1-229">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="764e1-229">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="764e1-230">Bir `Int32` duyarlık olduğu temsil eden `numeric_expression` yuvarlanmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="764e1-230">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="764e1-231">Zaman `length` pozitif bir sayı `numeric_expression` tarafından belirtilen ondalık basamak sayısına yuvarlanır `length`.</span><span class="sxs-lookup"><span data-stu-id="764e1-231">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="764e1-232">Zaman `length` negatif bir sayı `numeric_expression` belirtildiği gibi Ondalık ayırıcının sol tarafındaki yuvarlanır `length`.</span><span class="sxs-lookup"><span data-stu-id="764e1-232">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="764e1-233">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="764e1-233">Optional.</span></span> <span data-ttu-id="764e1-234">Bir `Int32` gerçekleştirilecek işlem türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="764e1-234">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="764e1-235">İşlev atlanırsa veya 0 (varsayılan), değeri `numeric_expression` yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="764e1-235">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="764e1-236">0 dışında bir değer belirtilirse, `numeric_expression` kesilir.</span><span class="sxs-lookup"><span data-stu-id="764e1-236">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="764e1-237">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-237">**Return Value**</span></span> 

<span data-ttu-id="764e1-238">Belirtilen değeri `numeric_expression` belirtilen `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="764e1-238">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="764e1-239">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-239">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="764e1-240">SIGN(Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-240">SIGN(expression)</span></span> 

<span data-ttu-id="764e1-241">(+ 1) pozitif, sıfır (0) veya eksi (-1) belirtilen ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="764e1-241">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="764e1-242">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-242">**Arguments**</span></span> 

<span data-ttu-id="764e1-243">`expression`: `Int32`, `Int64`, `Double`, veya `Decimal`</span><span class="sxs-lookup"><span data-stu-id="764e1-243">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="764e1-244">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-244">**Return Value**</span></span> 

<span data-ttu-id="764e1-245">Bir `Int32`, `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="764e1-245">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="764e1-246">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-246">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="764e1-247">SIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-247">SIN(expression)</span></span>

<span data-ttu-id="764e1-248">Trigonometrik radyan cinsinden belirtilen bir açının sinüsünü hesaplar ve döndürür bir `Double` ifade.</span><span class="sxs-lookup"><span data-stu-id="764e1-248">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="764e1-249">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-249">**Arguments**</span></span> 

<span data-ttu-id="764e1-250">`expression`: BİR `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-250">`expression`: A `Double`.</span></span> 

<span data-ttu-id="764e1-251">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-251">**Return Value**</span></span> 

<span data-ttu-id="764e1-252">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-252">A `Double`.</span></span> 

<span data-ttu-id="764e1-253">**Örnek** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="764e1-253">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="764e1-254">Sqrt(Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-254">SQRT(expression)</span></span>

<span data-ttu-id="764e1-255">Belirtilen ifadenin kare kökünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="764e1-255">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="764e1-256">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-256">**Arguments**</span></span> 

<span data-ttu-id="764e1-257">`expression`: BİR `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-257">`expression`: A `Double`.</span></span> 

<span data-ttu-id="764e1-258">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-258">**Return Value**</span></span> 

<span data-ttu-id="764e1-259">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-259">A `Double`.</span></span> 

<span data-ttu-id="764e1-260">**Örnek** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="764e1-260">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="764e1-261">SQUARE(Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-261">SQUARE(expression)</span></span>

<span data-ttu-id="764e1-262">Belirtilen ifade karesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="764e1-262">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="764e1-263">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-263">**Arguments**</span></span> 

<span data-ttu-id="764e1-264">`expression`: BİR `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-264">`expression`: A `Double`.</span></span> 

<span data-ttu-id="764e1-265">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-265">**Return Value**</span></span> 

<span data-ttu-id="764e1-266">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="764e1-266">A `Double`.</span></span> 

<span data-ttu-id="764e1-267">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-267">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="764e1-268">TAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="764e1-268">TAN(expression)</span></span>

<span data-ttu-id="764e1-269">Belirtilen bir ifade tanjantını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="764e1-269">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="764e1-270">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="764e1-270">**Arguments**</span></span> 

<span data-ttu-id="764e1-271">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="764e1-271">`expression`: `Double`</span></span> 

<span data-ttu-id="764e1-272">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="764e1-272">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="764e1-273">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="764e1-273">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="764e1-274">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="764e1-274">See also</span></span>

<span data-ttu-id="764e1-275">SqlClient destekleyen matematiksel işlevler hakkında daha fazla bilgi için SqlClient sağlayıcı bildiriminde belirtilen SQL Server sürümü için belgelere bakın:</span><span class="sxs-lookup"><span data-stu-id="764e1-275">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  
  
<span data-ttu-id="764e1-276">**SQL Server 2005:** [matematik işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="764e1-276">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>  
<span data-ttu-id="764e1-277">**SQL Server 2008:** [matematik işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="764e1-277">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>  
<span data-ttu-id="764e1-278">**SQL Server 2012 ve sonraki sürümler:** [matematik işlevleri (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span><span class="sxs-lookup"><span data-stu-id="764e1-278">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span></span>   

 [<span data-ttu-id="764e1-279">Entity Framework için SqlClient İşlevleri</span><span class="sxs-lookup"><span data-stu-id="764e1-279">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
