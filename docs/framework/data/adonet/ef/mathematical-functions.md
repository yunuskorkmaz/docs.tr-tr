---
description: 'Daha fazla bilgi edinin: matematik Işlevleri'
title: Matematik İşlevleri
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 6bf1f116d6d88a8a188dc31cab91fbf26bdaea36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795033"
---
# <a name="mathematical-functions"></a><span data-ttu-id="17532-103">Matematik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="17532-103">Mathematical Functions</span></span>

<span data-ttu-id="17532-104">SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı, bağımsız değişken olarak sağlanan giriş değerlerinde hesaplamalar gerçekleştiren ve sayısal bir değer sonucu döndüren matematik işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="17532-104">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="17532-105">Bu işlevler, SqlClient kullandığınızda kullanılabilir olan SqlServer ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="17532-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="17532-106">Bir sağlayıcının ad alanı özelliği Entity Framework, bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan öneki bulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="17532-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="17532-107">Aşağıdaki tabloda, SqlClient matematik işlevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="17532-107">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="17532-108">ABS (ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-108">ABS(expression)</span></span>

<span data-ttu-id="17532-109">Mutlak değer işlevini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="17532-109">Performs the absolute value function.</span></span>

<span data-ttu-id="17532-110">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-110">**Arguments**</span></span>

<span data-ttu-id="17532-111">`expression`: Bir `Int32` , `Int64` , `Double` veya `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="17532-111">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="17532-112">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-112">**Return Value**</span></span>

<span data-ttu-id="17532-113">Belirtilen ifadenin mutlak değeri.</span><span class="sxs-lookup"><span data-stu-id="17532-113">The absolute value of the specified expression.</span></span>

<span data-ttu-id="17532-114">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-114">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="17532-115">ACOS (ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-115">ACOS(expression)</span></span>

<span data-ttu-id="17532-116">Belirtilen ifadenin Arkkosinüs değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="17532-116">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="17532-117">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-117">**Arguments**</span></span>

<span data-ttu-id="17532-118">`expression`: A `Double` .</span><span class="sxs-lookup"><span data-stu-id="17532-118">`expression`: A `Double`.</span></span>

<span data-ttu-id="17532-119">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-119">**Return Value**</span></span>

<span data-ttu-id="17532-120">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="17532-120">A `Double`.</span></span>

<span data-ttu-id="17532-121">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-121">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="17532-122">ASIN (ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-122">ASIN(expression)</span></span>

<span data-ttu-id="17532-123">Belirtilen ifadenin arksinüs değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="17532-123">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="17532-124">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-124">**Arguments**</span></span>

<span data-ttu-id="17532-125">`expression`: A `Double` .</span><span class="sxs-lookup"><span data-stu-id="17532-125">`expression`: A `Double`.</span></span>

<span data-ttu-id="17532-126">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-126">**Return Value**</span></span>

<span data-ttu-id="17532-127">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="17532-127">A `Double`.</span></span>

<span data-ttu-id="17532-128">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-128">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="17532-129">ATAN (ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-129">ATAN(expression)</span></span>

<span data-ttu-id="17532-130">Belirtilen sayısal ifadenin arktanjant değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="17532-130">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="17532-131">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-131">**Arguments**</span></span>

<span data-ttu-id="17532-132">`expression`: A `Double` .</span><span class="sxs-lookup"><span data-stu-id="17532-132">`expression`: A `Double`.</span></span>

<span data-ttu-id="17532-133">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-133">**Return Value**</span></span>

<span data-ttu-id="17532-134">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="17532-134">A `Double`.</span></span>

<span data-ttu-id="17532-135">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-135">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="17532-136">ATN2 (ifade, ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-136">ATN2(expression, expression)</span></span>

<span data-ttu-id="17532-137">Tanjantı belirtilen iki sayısal ifade arasında olan radyan cinsinden açıyı döndürür.</span><span class="sxs-lookup"><span data-stu-id="17532-137">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="17532-138">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-138">**Arguments**</span></span>

<span data-ttu-id="17532-139">`expression`: A `Double` .</span><span class="sxs-lookup"><span data-stu-id="17532-139">`expression`: A `Double`.</span></span>

<span data-ttu-id="17532-140">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-140">**Return Value**</span></span>

<span data-ttu-id="17532-141">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="17532-141">A `Double`.</span></span>

<span data-ttu-id="17532-142">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-142">**Example**</span></span>

`SqlServer.ATN2(9, 8)`

## <a name="ceilingexpression"></a><span data-ttu-id="17532-143">TAVAN (ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-143">CEILING(expression)</span></span>

<span data-ttu-id="17532-144">Belirtilen ifadeyi, bu değerden büyük veya ona eşit en küçük tamsayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="17532-144">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="17532-145">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-145">**Arguments**</span></span>

<span data-ttu-id="17532-146">`expression`: Bir `Int32` , `Int64` , `Double` veya `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="17532-146">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="17532-147">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-147">**Return Value**</span></span>

<span data-ttu-id="17532-148">`Int32`,, `Int64` `Double` Veya `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="17532-148">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="17532-149">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-149">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="17532-150">COS (ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-150">COS(expression)</span></span>

<span data-ttu-id="17532-151">Radyan cinsinden belirtilen açının trigonometrik kosinüsünü hesaplar.</span><span class="sxs-lookup"><span data-stu-id="17532-151">Calculates the trigonometric cosine of the specified angle in radians.</span></span>

<span data-ttu-id="17532-152">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-152">**Arguments**</span></span>

<span data-ttu-id="17532-153">`expression`: A `Double` .</span><span class="sxs-lookup"><span data-stu-id="17532-153">`expression`: A `Double`.</span></span>

<span data-ttu-id="17532-154">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-154">**Return Value**</span></span>

<span data-ttu-id="17532-155">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="17532-155">A `Double`.</span></span>

<span data-ttu-id="17532-156">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-156">**Example**</span></span>

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="17532-157">COT (ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-157">COT(expression)</span></span>

<span data-ttu-id="17532-158">Radyan cinsinden belirtilen açıdaki trigonometrik kovaryansı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="17532-158">Calculates the trigonometric cotangent of the specified angle in radians.</span></span>

<span data-ttu-id="17532-159">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-159">**Arguments**</span></span>

<span data-ttu-id="17532-160">`expression`: A `Double` .</span><span class="sxs-lookup"><span data-stu-id="17532-160">`expression`: A `Double`.</span></span>

<span data-ttu-id="17532-161">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-161">**Return Value**</span></span>

<span data-ttu-id="17532-162">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="17532-162">A `Double`.</span></span>

<span data-ttu-id="17532-163">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-163">**Example**</span></span>

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="17532-164">DERECE (radyan)</span><span class="sxs-lookup"><span data-stu-id="17532-164">DEGREES(radians)</span></span>

<span data-ttu-id="17532-165">Karşılık gelen açıyı derece cinsinden döndürür.</span><span class="sxs-lookup"><span data-stu-id="17532-165">Returns the corresponding angle in degrees.</span></span>

<span data-ttu-id="17532-166">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-166">**Arguments**</span></span>

<span data-ttu-id="17532-167">`expression`: Bir `Int32` , `Int64` , `Double` veya `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="17532-167">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="17532-168">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-168">**Return Value**</span></span>

<span data-ttu-id="17532-169">`Int32`,, `Int64` `Double` Veya `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="17532-169">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="17532-170">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-170">**Example**</span></span>

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="17532-171">EXP (ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-171">EXP(expression)</span></span>

<span data-ttu-id="17532-172">Belirtilen bir sayısal ifadenin üstel değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="17532-172">Calculates the exponential value of a specified numeric expression.</span></span>

<span data-ttu-id="17532-173">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-173">**Arguments**</span></span>

<span data-ttu-id="17532-174">`expression`: A `Double` .</span><span class="sxs-lookup"><span data-stu-id="17532-174">`expression`: A `Double`.</span></span>

<span data-ttu-id="17532-175">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-175">**Return Value**</span></span>

<span data-ttu-id="17532-176">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="17532-176">A `Double`.</span></span>

<span data-ttu-id="17532-177">**Örnek**`SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="17532-177">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="17532-178">FLOOR (ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-178">FLOOR(expression)</span></span>

<span data-ttu-id="17532-179">Belirtilen ifadeyi ona eşit veya ondan küçük olan en büyük tamsayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="17532-179">Converts the specified expression to the largest integer less than or equal to it.</span></span>

<span data-ttu-id="17532-180">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-180">**Arguments**</span></span>

<span data-ttu-id="17532-181">`expression`: A `Double` .</span><span class="sxs-lookup"><span data-stu-id="17532-181">`expression`: A `Double`.</span></span>

<span data-ttu-id="17532-182">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-182">**Return Value**</span></span>

<span data-ttu-id="17532-183">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="17532-183">A `Double`.</span></span>

<span data-ttu-id="17532-184">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-184">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="17532-185">GÜNLÜK (ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-185">LOG(expression)</span></span>

<span data-ttu-id="17532-186">Belirtilen ifadenin doğal logaritmasını hesaplar `float` .</span><span class="sxs-lookup"><span data-stu-id="17532-186">Calculates the natural logarithm of the specified `float` expression.</span></span>

<span data-ttu-id="17532-187">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-187">**Arguments**</span></span>

<span data-ttu-id="17532-188">`expression`: A `Double` .</span><span class="sxs-lookup"><span data-stu-id="17532-188">`expression`: A `Double`.</span></span>

<span data-ttu-id="17532-189">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-189">**Return Value**</span></span>

<span data-ttu-id="17532-190">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="17532-190">A `Double`.</span></span>

<span data-ttu-id="17532-191">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-191">**Example**</span></span>

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="17532-192">LOG10 (ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-192">LOG10(expression)</span></span>

<span data-ttu-id="17532-193">Belirtilen ifadenin 10 tabanında logaritmasını döndürür `Double` .</span><span class="sxs-lookup"><span data-stu-id="17532-193">Returns the base-10 logarithm of the specified `Double` expression.</span></span>

<span data-ttu-id="17532-194">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-194">**Arguments**</span></span>

<span data-ttu-id="17532-195">`expression`: A `Double` .</span><span class="sxs-lookup"><span data-stu-id="17532-195">`expression`: A `Double`.</span></span>

<span data-ttu-id="17532-196">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-196">**Return Value**</span></span>

<span data-ttu-id="17532-197">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="17532-197">A `Double`.</span></span>

<span data-ttu-id="17532-198">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-198">**Example**</span></span>

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="17532-199">PI ()</span><span class="sxs-lookup"><span data-stu-id="17532-199">PI()</span></span>

<span data-ttu-id="17532-200">Pi değerinin sabit değerini bir olarak döndürür `Double` .</span><span class="sxs-lookup"><span data-stu-id="17532-200">Returns the constant value of pi as a `Double`.</span></span>

<span data-ttu-id="17532-201">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-201">**Return Value**</span></span>

<span data-ttu-id="17532-202">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="17532-202">A `Double`.</span></span>

<span data-ttu-id="17532-203">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-203">**Example**</span></span>

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a><span data-ttu-id="17532-204">Güç (numeric_expression power_expression)</span><span class="sxs-lookup"><span data-stu-id="17532-204">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="17532-205">Belirtilen bir ifadenin değerini belirtilen bir kuvvet olarak hesaplar.</span><span class="sxs-lookup"><span data-stu-id="17532-205">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="17532-206">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-206">**Arguments**</span></span>

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="17532-207">`Int32`,, `Int64` `Double` Veya `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="17532-207">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="17532-208">Öğesini `Double` , öğesini yükseltmek için gereken kuvveti temsil eder `numeric_expression` .</span><span class="sxs-lookup"><span data-stu-id="17532-208">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>|

<span data-ttu-id="17532-209">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-209">**Return Value**</span></span>

<span data-ttu-id="17532-210">Belirtilen değerinin `numeric_expression` belirtilen değeri `power_expression` .</span><span class="sxs-lookup"><span data-stu-id="17532-210">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="17532-211">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-211">**Example**</span></span>

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="17532-212">RADYAN (ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-212">RADIANS(expression)</span></span>

<span data-ttu-id="17532-213">Dereceyi radyana dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="17532-213">Converts degrees to radians.</span></span>

<span data-ttu-id="17532-214">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-214">**Arguments**</span></span>

<span data-ttu-id="17532-215">`expression`: Bir `Int32` , `Int64` , `Double` veya `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="17532-215">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="17532-216">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-216">**Return Value**</span></span>

<span data-ttu-id="17532-217">`Int32`,, `Int64` `Double` Veya `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="17532-217">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="17532-218">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-218">**Example**</span></span>

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="17532-219">S_SAYI_ÜRET ([çekirdek])</span><span class="sxs-lookup"><span data-stu-id="17532-219">RAND([seed])</span></span>

<span data-ttu-id="17532-220">0 ile 1 arasında rastgele bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="17532-220">Returns a random value from 0 through 1.</span></span>

<span data-ttu-id="17532-221">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-221">**Arguments**</span></span>

<span data-ttu-id="17532-222">Çekirdek değeri bir `Int32` .</span><span class="sxs-lookup"><span data-stu-id="17532-222">The seed value as an `Int32`.</span></span> <span data-ttu-id="17532-223">Çekirdek belirtilmemişse, SQL Server veritabanı altyapısı rastgele bir çekirdek değeri atar.</span><span class="sxs-lookup"><span data-stu-id="17532-223">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="17532-224">Belirtilen bir çekirdek değeri için döndürülen sonuç her zaman aynıdır.</span><span class="sxs-lookup"><span data-stu-id="17532-224">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="17532-225">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-225">**Return Value**</span></span>

<span data-ttu-id="17532-226">`Double`0 ile 1 arasında rastgele bir değer.</span><span class="sxs-lookup"><span data-stu-id="17532-226">A random `Double` value from 0 through 1.</span></span>

<span data-ttu-id="17532-227">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-227">**Example**</span></span>

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a><span data-ttu-id="17532-228">ROUND (numeric_expression, Uzunluk [, işlev])</span><span class="sxs-lookup"><span data-stu-id="17532-228">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="17532-229">Belirtilen uzunluğa veya duyarlığa yuvarlanmış bir sayısal ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="17532-229">Returns a numeric expression, rounded to the specified length or precision.</span></span>

<span data-ttu-id="17532-230">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-230">**Arguments**</span></span>

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="17532-231">`Int32`,, `Int64` `Double` Veya `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="17532-231">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>
|`length`| <span data-ttu-id="17532-232">`Int32`Bu, yuvarlanacak duyarlığı temsil eder `numeric_expression` .</span><span class="sxs-lookup"><span data-stu-id="17532-232">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="17532-233">`length`Pozitif bir sayı olduğunda, `numeric_expression` tarafından belirtilen ondalık konum sayısına yuvarlanır `length` .</span><span class="sxs-lookup"><span data-stu-id="17532-233">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="17532-234">`length`Negatif bir sayı olduğunda, `numeric_expression` ondalık noktanın sol tarafında tarafından belirtildiği gibi yuvarlanır `length` .</span><span class="sxs-lookup"><span data-stu-id="17532-234">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="17532-235">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="17532-235">Optional.</span></span> <span data-ttu-id="17532-236">`Int32`Gerçekleştirilecek işlemin türünü temsil eden bir.</span><span class="sxs-lookup"><span data-stu-id="17532-236">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="17532-237">İşlev atlandığında veya 0 değerine (varsayılan) sahip olduğunda, `numeric_expression` yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="17532-237">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="17532-238">0 dışında bir değer belirtildiğinde, `numeric_expression` atılır.</span><span class="sxs-lookup"><span data-stu-id="17532-238">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="17532-239">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-239">**Return Value**</span></span>

<span data-ttu-id="17532-240">Belirtilen değerinin `numeric_expression` belirtilen değeri `power_expression` .</span><span class="sxs-lookup"><span data-stu-id="17532-240">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="17532-241">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-241">**Example**</span></span>

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="17532-242">IŞARETI (ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-242">SIGN(expression)</span></span>

<span data-ttu-id="17532-243">Belirtilen ifadenin pozitif (+ 1), sıfır (0) veya negatif (-1) işaretini döndürür.</span><span class="sxs-lookup"><span data-stu-id="17532-243">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span>

<span data-ttu-id="17532-244">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-244">**Arguments**</span></span>

<span data-ttu-id="17532-245">`expression`: `Int32` , `Int64` , `Double` , veya `Decimal`</span><span class="sxs-lookup"><span data-stu-id="17532-245">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span>

<span data-ttu-id="17532-246">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-246">**Return Value**</span></span>

<span data-ttu-id="17532-247">`Int32`,, `Int64` `Double` Veya `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="17532-247">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="17532-248">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-248">**Example**</span></span>

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="17532-249">SIN (ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-249">SIN(expression)</span></span>

<span data-ttu-id="17532-250">Radyan cinsinden belirtilen açının trigonometrik sinüsünü hesaplar ve bir `Double` ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="17532-250">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span>

<span data-ttu-id="17532-251">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-251">**Arguments**</span></span>

<span data-ttu-id="17532-252">`expression`: A `Double` .</span><span class="sxs-lookup"><span data-stu-id="17532-252">`expression`: A `Double`.</span></span>

<span data-ttu-id="17532-253">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-253">**Return Value**</span></span>

<span data-ttu-id="17532-254">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="17532-254">A `Double`.</span></span>

<span data-ttu-id="17532-255">**Örnek**`SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="17532-255">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="17532-256">SQRT (ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-256">SQRT(expression)</span></span>

<span data-ttu-id="17532-257">Belirtilen ifadenin kare kökünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="17532-257">Returns the square root of the specified expression.</span></span>

<span data-ttu-id="17532-258">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-258">**Arguments**</span></span>

<span data-ttu-id="17532-259">`expression`: A `Double` .</span><span class="sxs-lookup"><span data-stu-id="17532-259">`expression`: A `Double`.</span></span>

<span data-ttu-id="17532-260">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-260">**Return Value**</span></span>

<span data-ttu-id="17532-261">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="17532-261">A `Double`.</span></span>

<span data-ttu-id="17532-262">**Örnek**`SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="17532-262">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="17532-263">KARE (ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-263">SQUARE(expression)</span></span>

<span data-ttu-id="17532-264">Belirtilen ifadenin karesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="17532-264">Returns the square of the specified expression.</span></span>

<span data-ttu-id="17532-265">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-265">**Arguments**</span></span>

<span data-ttu-id="17532-266">`expression`: A `Double` .</span><span class="sxs-lookup"><span data-stu-id="17532-266">`expression`: A `Double`.</span></span>

<span data-ttu-id="17532-267">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-267">**Return Value**</span></span>

<span data-ttu-id="17532-268">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="17532-268">A `Double`.</span></span>

<span data-ttu-id="17532-269">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-269">**Example**</span></span>

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="17532-270">TAN (ifade)</span><span class="sxs-lookup"><span data-stu-id="17532-270">TAN(expression)</span></span>

<span data-ttu-id="17532-271">Belirtilen bir ifadenin tanjantını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="17532-271">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="17532-272">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="17532-272">**Arguments**</span></span>

<span data-ttu-id="17532-273">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="17532-273">`expression`: `Double`</span></span>

<span data-ttu-id="17532-274">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="17532-274">**Return Value**</span></span>

`Double`

<span data-ttu-id="17532-275">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="17532-275">**Example**</span></span>

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="17532-276">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17532-276">See also</span></span>

- [<span data-ttu-id="17532-277">Matematik Işlevleri (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="17532-277">Mathematical Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [<span data-ttu-id="17532-278">Entity Framework için SqlClient İşlevleri</span><span class="sxs-lookup"><span data-stu-id="17532-278">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
