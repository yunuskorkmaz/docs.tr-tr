---
title: Matematik İşlevleri
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 4512aaa2eeb3e715a1d6f7a8655912eb15162124
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149771"
---
# <a name="mathematical-functions"></a><span data-ttu-id="1868f-102">Matematik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1868f-102">Mathematical Functions</span></span>

<span data-ttu-id="1868f-103">SQL Server için .NET Framework Data Provider (SqlClient), bağımsız değişken olarak sağlanan giriş değerleri üzerinde hesaplamalar gerçekleştiren ve sayısal bir değer sonucu döndüren matematik işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1868f-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="1868f-104">Bu işlevler, SqlClient'ı kullandığınızda kullanılabilen SqlServer ad alanındadır.</span><span class="sxs-lookup"><span data-stu-id="1868f-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="1868f-105">Sağlayıcının ad alanı özelliği, Varlık Çerçevesi'nin bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için hangi önek kullanıldığını keşfetmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1868f-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="1868f-106">Aşağıdaki tabloda SqlClient matematik işlevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1868f-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="1868f-107">ABS(ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-107">ABS(expression)</span></span>

<span data-ttu-id="1868f-108">Mutlak değer işlevini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1868f-108">Performs the absolute value function.</span></span>

<span data-ttu-id="1868f-109">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-109">**Arguments**</span></span>

<span data-ttu-id="1868f-110">`expression`: `Int32`Bir `Int64` `Double`, `Decimal`, veya .</span><span class="sxs-lookup"><span data-stu-id="1868f-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="1868f-111">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-111">**Return Value**</span></span>

<span data-ttu-id="1868f-112">Belirtilen ifadenin mutlak değeri.</span><span class="sxs-lookup"><span data-stu-id="1868f-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="1868f-113">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="1868f-114">ACOS(ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-114">ACOS(expression)</span></span>

<span data-ttu-id="1868f-115">Belirtilen ifadenin arccosine değerini verir.</span><span class="sxs-lookup"><span data-stu-id="1868f-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="1868f-116">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-116">**Arguments**</span></span>

<span data-ttu-id="1868f-117">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1868f-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="1868f-118">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-118">**Return Value**</span></span>

<span data-ttu-id="1868f-119">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="1868f-119">A `Double`.</span></span>

<span data-ttu-id="1868f-120">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="1868f-121">ASIN(ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-121">ASIN(expression)</span></span>

<span data-ttu-id="1868f-122">Belirtilen ifadenin arcsine değerini verir.</span><span class="sxs-lookup"><span data-stu-id="1868f-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="1868f-123">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-123">**Arguments**</span></span>

<span data-ttu-id="1868f-124">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1868f-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="1868f-125">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-125">**Return Value**</span></span>

<span data-ttu-id="1868f-126">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="1868f-126">A `Double`.</span></span>

<span data-ttu-id="1868f-127">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="1868f-128">ATAN(ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-128">ATAN(expression)</span></span>

<span data-ttu-id="1868f-129">Belirtilen sayısal ifadenin arctanjant değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1868f-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="1868f-130">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-130">**Arguments**</span></span>

<span data-ttu-id="1868f-131">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1868f-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="1868f-132">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-132">**Return Value**</span></span>

<span data-ttu-id="1868f-133">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="1868f-133">A `Double`.</span></span>

<span data-ttu-id="1868f-134">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="1868f-135">ATN2(ifade, ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="1868f-136">Radyanlarda, teğet olarak belirtilen iki sayısal ifade arasında olan açıyı döndürür.</span><span class="sxs-lookup"><span data-stu-id="1868f-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="1868f-137">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-137">**Arguments**</span></span>

<span data-ttu-id="1868f-138">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1868f-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="1868f-139">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-139">**Return Value**</span></span>

<span data-ttu-id="1868f-140">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="1868f-140">A `Double`.</span></span>

<span data-ttu-id="1868f-141">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`

## <a name="ceilingexpression"></a><span data-ttu-id="1868f-142">TAVAN(ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-142">CEILING(expression)</span></span>

<span data-ttu-id="1868f-143">Belirtilen ifadeyi kendisinden büyük veya eşit olan en küçük karşıcıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1868f-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="1868f-144">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-144">**Arguments**</span></span>

<span data-ttu-id="1868f-145">`expression`: `Int32`Bir `Int64` `Double`, `Decimal`, veya .</span><span class="sxs-lookup"><span data-stu-id="1868f-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="1868f-146">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-146">**Return Value**</span></span>

<span data-ttu-id="1868f-147">Bir `Int32` `Int64`, `Double`, `Decimal`veya .</span><span class="sxs-lookup"><span data-stu-id="1868f-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="1868f-148">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-148">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="1868f-149">COS(ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-149">COS(expression)</span></span>

<span data-ttu-id="1868f-150">Radyanlarda belirtilen açının trigonometrik kosinüsünü hesaplar.</span><span class="sxs-lookup"><span data-stu-id="1868f-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span>

<span data-ttu-id="1868f-151">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-151">**Arguments**</span></span>

<span data-ttu-id="1868f-152">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1868f-152">`expression`: A `Double`.</span></span>

<span data-ttu-id="1868f-153">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-153">**Return Value**</span></span>

<span data-ttu-id="1868f-154">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="1868f-154">A `Double`.</span></span>

<span data-ttu-id="1868f-155">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-155">**Example**</span></span>

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="1868f-156">COT(ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-156">COT(expression)</span></span>

<span data-ttu-id="1868f-157">Radyanlarda belirtilen açının trigonometrik kotanjantını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="1868f-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span>

<span data-ttu-id="1868f-158">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-158">**Arguments**</span></span>

<span data-ttu-id="1868f-159">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1868f-159">`expression`: A `Double`.</span></span>

<span data-ttu-id="1868f-160">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-160">**Return Value**</span></span>

<span data-ttu-id="1868f-161">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="1868f-161">A `Double`.</span></span>

<span data-ttu-id="1868f-162">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-162">**Example**</span></span>

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="1868f-163">DERECELER(radyanlar)</span><span class="sxs-lookup"><span data-stu-id="1868f-163">DEGREES(radians)</span></span>

<span data-ttu-id="1868f-164">Derece olarak karşılık gelen açıyı döndürür.</span><span class="sxs-lookup"><span data-stu-id="1868f-164">Returns the corresponding angle in degrees.</span></span>

<span data-ttu-id="1868f-165">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-165">**Arguments**</span></span>

<span data-ttu-id="1868f-166">`expression`: `Int32`Bir `Int64` `Double`, `Decimal`, veya .</span><span class="sxs-lookup"><span data-stu-id="1868f-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="1868f-167">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-167">**Return Value**</span></span>

<span data-ttu-id="1868f-168">Bir `Int32` `Int64`, `Double`, `Decimal`veya .</span><span class="sxs-lookup"><span data-stu-id="1868f-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="1868f-169">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-169">**Example**</span></span>

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="1868f-170">EXP(ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-170">EXP(expression)</span></span>

<span data-ttu-id="1868f-171">Belirtilen sayısal ifadenin üstel değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="1868f-171">Calculates the exponential value of a specified numeric expression.</span></span>

<span data-ttu-id="1868f-172">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-172">**Arguments**</span></span>

<span data-ttu-id="1868f-173">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1868f-173">`expression`: A `Double`.</span></span>

<span data-ttu-id="1868f-174">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-174">**Return Value**</span></span>

<span data-ttu-id="1868f-175">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="1868f-175">A `Double`.</span></span>

<span data-ttu-id="1868f-176">**Örnek**`SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="1868f-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="1868f-177">KAT(ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-177">FLOOR(expression)</span></span>

<span data-ttu-id="1868f-178">Belirtilen ifadeyi, kendisinden daha az veya eşit olan en büyük tümseciye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1868f-178">Converts the specified expression to the largest integer less than or equal to it.</span></span>

<span data-ttu-id="1868f-179">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-179">**Arguments**</span></span>

<span data-ttu-id="1868f-180">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1868f-180">`expression`: A `Double`.</span></span>

<span data-ttu-id="1868f-181">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-181">**Return Value**</span></span>

<span data-ttu-id="1868f-182">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="1868f-182">A `Double`.</span></span>

<span data-ttu-id="1868f-183">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-183">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="1868f-184">LOG(ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-184">LOG(expression)</span></span>

<span data-ttu-id="1868f-185">Belirtilen `float` ifadenin doğal logaritmasını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="1868f-185">Calculates the natural logarithm of the specified `float` expression.</span></span>

<span data-ttu-id="1868f-186">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-186">**Arguments**</span></span>

<span data-ttu-id="1868f-187">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1868f-187">`expression`: A `Double`.</span></span>

<span data-ttu-id="1868f-188">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-188">**Return Value**</span></span>

<span data-ttu-id="1868f-189">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="1868f-189">A `Double`.</span></span>

<span data-ttu-id="1868f-190">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-190">**Example**</span></span>

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="1868f-191">LOG10(ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-191">LOG10(expression)</span></span>

<span data-ttu-id="1868f-192">Belirtilen ifadenin base-10 logarythm döndürür. `Double`</span><span class="sxs-lookup"><span data-stu-id="1868f-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span>

<span data-ttu-id="1868f-193">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-193">**Arguments**</span></span>

<span data-ttu-id="1868f-194">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1868f-194">`expression`: A `Double`.</span></span>

<span data-ttu-id="1868f-195">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-195">**Return Value**</span></span>

<span data-ttu-id="1868f-196">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="1868f-196">A `Double`.</span></span>

<span data-ttu-id="1868f-197">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-197">**Example**</span></span>

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="1868f-198">PI()</span><span class="sxs-lookup"><span data-stu-id="1868f-198">PI()</span></span>

<span data-ttu-id="1868f-199">Pi'nin sabit değerini `Double`bir . olarak verir</span><span class="sxs-lookup"><span data-stu-id="1868f-199">Returns the constant value of pi as a `Double`.</span></span>

<span data-ttu-id="1868f-200">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-200">**Return Value**</span></span>

<span data-ttu-id="1868f-201">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="1868f-201">A `Double`.</span></span>

<span data-ttu-id="1868f-202">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-202">**Example**</span></span>

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a><span data-ttu-id="1868f-203">GÜÇ(numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="1868f-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="1868f-204">Belirtilen bir ifadenin değerini belirli bir güce hesaplar.</span><span class="sxs-lookup"><span data-stu-id="1868f-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="1868f-205">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-205">**Arguments**</span></span>

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="1868f-206">Bir `Int32` `Int64`, `Double`, `Decimal`veya .</span><span class="sxs-lookup"><span data-stu-id="1868f-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="1868f-207">Bir `Double` yükseltmek için güç temsil `numeric_expression`eder.</span><span class="sxs-lookup"><span data-stu-id="1868f-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>|

<span data-ttu-id="1868f-208">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-208">**Return Value**</span></span>

<span data-ttu-id="1868f-209">Belirtilen değeri belirtilir. `numeric_expression` `power_expression`</span><span class="sxs-lookup"><span data-stu-id="1868f-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="1868f-210">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-210">**Example**</span></span>

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="1868f-211">RADYANS(ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-211">RADIANS(expression)</span></span>

<span data-ttu-id="1868f-212">Dereceyi radyana dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1868f-212">Converts degrees to radians.</span></span>

<span data-ttu-id="1868f-213">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-213">**Arguments**</span></span>

<span data-ttu-id="1868f-214">`expression`: `Int32`Bir `Int64` `Double`, `Decimal`, veya .</span><span class="sxs-lookup"><span data-stu-id="1868f-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="1868f-215">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-215">**Return Value**</span></span>

<span data-ttu-id="1868f-216">Bir `Int32` `Int64`, `Double`, `Decimal`veya .</span><span class="sxs-lookup"><span data-stu-id="1868f-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="1868f-217">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-217">**Example**</span></span>

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="1868f-218">RAND([tohum])</span><span class="sxs-lookup"><span data-stu-id="1868f-218">RAND([seed])</span></span>

<span data-ttu-id="1868f-219">0'dan 1'e rastgele bir değer verir.</span><span class="sxs-lookup"><span data-stu-id="1868f-219">Returns a random value from 0 through 1.</span></span>

<span data-ttu-id="1868f-220">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-220">**Arguments**</span></span>

<span data-ttu-id="1868f-221">Tohum değeri olarak `Int32`bir .</span><span class="sxs-lookup"><span data-stu-id="1868f-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="1868f-222">Tohum belirtilmemişse, SQL Server Veritabanı Altyapısı rasgele bir tohum değeri atar.</span><span class="sxs-lookup"><span data-stu-id="1868f-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="1868f-223">Belirli bir tohum değeri için döndürülen sonuç her zaman aynıdır.</span><span class="sxs-lookup"><span data-stu-id="1868f-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="1868f-224">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-224">**Return Value**</span></span>

<span data-ttu-id="1868f-225">0'dan 1'e rastgele `Double` bir değer.</span><span class="sxs-lookup"><span data-stu-id="1868f-225">A random `Double` value from 0 through 1.</span></span>

<span data-ttu-id="1868f-226">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-226">**Example**</span></span>

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a><span data-ttu-id="1868f-227">ROUND(numeric_expression, uzunluk[,fonksiyon])</span><span class="sxs-lookup"><span data-stu-id="1868f-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="1868f-228">Belirtilen uzunluğa veya duyarlıka yuvarlatılmış sayısal bir ifade verir.</span><span class="sxs-lookup"><span data-stu-id="1868f-228">Returns a numeric expression, rounded to the specified length or precision.</span></span>

<span data-ttu-id="1868f-229">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-229">**Arguments**</span></span>

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="1868f-230">Bir `Int32` `Int64`, `Double`, `Decimal`veya .</span><span class="sxs-lookup"><span data-stu-id="1868f-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>
|`length`| <span data-ttu-id="1868f-231">`Int32` Yuvarlanmak için hassas `numeric_expression` temsil eden bir.</span><span class="sxs-lookup"><span data-stu-id="1868f-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="1868f-232">Pozitif `length` bir sayı `numeric_expression` olduğunda, `length`ondalık basamak sayısına yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="1868f-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="1868f-233">Negatif `length` bir sayı `numeric_expression` olduğunda, ondalık noktanın sol tarafında, 'de `length`belirtildiği gibi yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="1868f-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="1868f-234">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1868f-234">Optional.</span></span> <span data-ttu-id="1868f-235">Gerçekleştirecek `Int32` işlem türünü temsil eden bir işlem.</span><span class="sxs-lookup"><span data-stu-id="1868f-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="1868f-236">İşlev atlandığında veya 0 (varsayılan) `numeric_expression` değeri olduğunda yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="1868f-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="1868f-237">0'dan başka bir değer `numeric_expression` belirtildiğinde kesilir.</span><span class="sxs-lookup"><span data-stu-id="1868f-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="1868f-238">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-238">**Return Value**</span></span>

<span data-ttu-id="1868f-239">Belirtilen değeri belirtilir. `numeric_expression` `power_expression`</span><span class="sxs-lookup"><span data-stu-id="1868f-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="1868f-240">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-240">**Example**</span></span>

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="1868f-241">SIGN(ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-241">SIGN(expression)</span></span>

<span data-ttu-id="1868f-242">Belirtilen ifadenin pozitif (+1), sıfır (0) veya negatif (-1) işaretini verir.</span><span class="sxs-lookup"><span data-stu-id="1868f-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span>

<span data-ttu-id="1868f-243">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-243">**Arguments**</span></span>

<span data-ttu-id="1868f-244">`expression`: `Int32` `Int64`, `Double`, veya`Decimal`</span><span class="sxs-lookup"><span data-stu-id="1868f-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span>

<span data-ttu-id="1868f-245">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-245">**Return Value**</span></span>

<span data-ttu-id="1868f-246">Bir `Int32` `Int64`, `Double`, `Decimal`veya .</span><span class="sxs-lookup"><span data-stu-id="1868f-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="1868f-247">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-247">**Example**</span></span>

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="1868f-248">SIN(ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-248">SIN(expression)</span></span>

<span data-ttu-id="1868f-249">Radyanlarda belirtilen açının trigonometrik sinüsünü hesaplar ve `Double` bir ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="1868f-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span>

<span data-ttu-id="1868f-250">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-250">**Arguments**</span></span>

<span data-ttu-id="1868f-251">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1868f-251">`expression`: A `Double`.</span></span>

<span data-ttu-id="1868f-252">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-252">**Return Value**</span></span>

<span data-ttu-id="1868f-253">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="1868f-253">A `Double`.</span></span>

<span data-ttu-id="1868f-254">**Örnek**`SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="1868f-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="1868f-255">SQRT(ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-255">SQRT(expression)</span></span>

<span data-ttu-id="1868f-256">Belirtilen ifadenin kare kökünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="1868f-256">Returns the square root of the specified expression.</span></span>

<span data-ttu-id="1868f-257">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-257">**Arguments**</span></span>

<span data-ttu-id="1868f-258">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1868f-258">`expression`: A `Double`.</span></span>

<span data-ttu-id="1868f-259">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-259">**Return Value**</span></span>

<span data-ttu-id="1868f-260">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="1868f-260">A `Double`.</span></span>

<span data-ttu-id="1868f-261">**Örnek**`SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="1868f-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="1868f-262">KARE(ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-262">SQUARE(expression)</span></span>

<span data-ttu-id="1868f-263">Belirtilen ifadenin karesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1868f-263">Returns the square of the specified expression.</span></span>

<span data-ttu-id="1868f-264">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-264">**Arguments**</span></span>

<span data-ttu-id="1868f-265">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1868f-265">`expression`: A `Double`.</span></span>

<span data-ttu-id="1868f-266">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-266">**Return Value**</span></span>

<span data-ttu-id="1868f-267">Bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="1868f-267">A `Double`.</span></span>

<span data-ttu-id="1868f-268">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-268">**Example**</span></span>

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="1868f-269">TAN(ifade)</span><span class="sxs-lookup"><span data-stu-id="1868f-269">TAN(expression)</span></span>

<span data-ttu-id="1868f-270">Belirtilen ifadenin teğetini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="1868f-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="1868f-271">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="1868f-271">**Arguments**</span></span>

<span data-ttu-id="1868f-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="1868f-272">`expression`: `Double`</span></span>

<span data-ttu-id="1868f-273">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="1868f-273">**Return Value**</span></span>

`Double`

<span data-ttu-id="1868f-274">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="1868f-274">**Example**</span></span>

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="1868f-275">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1868f-275">See also</span></span>

- [<span data-ttu-id="1868f-276">Matematiksel Fonksiyonlar (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1868f-276">Mathematical Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [<span data-ttu-id="1868f-277">Entity Framework için SqlClient İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1868f-277">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
