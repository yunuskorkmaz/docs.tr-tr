---
title: Matematik İşlevleri
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 664d1a4f67ecced6713f83bf3dd11931c9b4dc18
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699994"
---
# <a name="mathematical-functions"></a><span data-ttu-id="f6792-102">Matematik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f6792-102">Mathematical Functions</span></span>

<span data-ttu-id="f6792-103">SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı, bağımsız değişken olarak sağlanan giriş değerlerinde hesaplamalar gerçekleştiren ve sayısal bir değer sonucu döndüren matematik işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6792-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="f6792-104">Bu işlevler, SqlClient kullandığınızda kullanılabilir olan SqlServer ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="f6792-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="f6792-105">Bir sağlayıcının ad alanı özelliği Entity Framework, bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan öneki bulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6792-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="f6792-106">Aşağıdaki tabloda, SqlClient matematik işlevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f6792-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="f6792-107">ABS (ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-107">ABS(expression)</span></span>

<span data-ttu-id="f6792-108">Mutlak değer işlevini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f6792-108">Performs the absolute value function.</span></span>

<span data-ttu-id="f6792-109">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-109">**Arguments**</span></span>

<span data-ttu-id="f6792-110">`expression`: bir `Int32`, `Int64`, `Double`veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f6792-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="f6792-111">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-111">**Return Value**</span></span>

<span data-ttu-id="f6792-112">Belirtilen ifadenin mutlak değeri.</span><span class="sxs-lookup"><span data-stu-id="f6792-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="f6792-113">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="f6792-114">ACOS (ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-114">ACOS(expression)</span></span>

<span data-ttu-id="f6792-115">Belirtilen ifadenin Arkkosinüs değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6792-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="f6792-116">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-116">**Arguments**</span></span>

<span data-ttu-id="f6792-117">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="f6792-118">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-118">**Return Value**</span></span>

<span data-ttu-id="f6792-119">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-119">A `Double`.</span></span>

<span data-ttu-id="f6792-120">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="f6792-121">ASIN (ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-121">ASIN(expression)</span></span>

<span data-ttu-id="f6792-122">Belirtilen ifadenin arksinüs değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6792-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="f6792-123">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-123">**Arguments**</span></span>

<span data-ttu-id="f6792-124">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="f6792-125">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-125">**Return Value**</span></span>

<span data-ttu-id="f6792-126">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-126">A `Double`.</span></span>

<span data-ttu-id="f6792-127">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="f6792-128">ATAN (ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-128">ATAN(expression)</span></span>

<span data-ttu-id="f6792-129">Belirtilen sayısal ifadenin arktanjant değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6792-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="f6792-130">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-130">**Arguments**</span></span>

<span data-ttu-id="f6792-131">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="f6792-132">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-132">**Return Value**</span></span>

<span data-ttu-id="f6792-133">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-133">A `Double`.</span></span>

<span data-ttu-id="f6792-134">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="f6792-135">ATN2 (ifade, ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="f6792-136">Tanjantı belirtilen iki sayısal ifade arasında olan radyan cinsinden açıyı döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6792-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="f6792-137">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-137">**Arguments**</span></span>

<span data-ttu-id="f6792-138">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="f6792-139">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-139">**Return Value**</span></span>

<span data-ttu-id="f6792-140">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-140">A `Double`.</span></span>

<span data-ttu-id="f6792-141">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="f6792-142">TAVAN (ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-142">CEILING(expression)</span></span>

<span data-ttu-id="f6792-143">Belirtilen ifadeyi, bu değerden büyük veya ona eşit en küçük tamsayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f6792-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="f6792-144">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-144">**Arguments**</span></span>

<span data-ttu-id="f6792-145">`expression`: bir `Int32`, `Int64`, `Double`veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f6792-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="f6792-146">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-146">**Return Value**</span></span>

<span data-ttu-id="f6792-147">`Int32`, `Int64`, `Double`veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f6792-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="f6792-148">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-148">**Example**</span></span> 

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="f6792-149">COS (ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-149">COS(expression)</span></span>

<span data-ttu-id="f6792-150">Radyan cinsinden belirtilen açının trigonometrik kosinüsünü hesaplar.</span><span class="sxs-lookup"><span data-stu-id="f6792-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="f6792-151">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-151">**Arguments**</span></span> 

<span data-ttu-id="f6792-152">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-152">`expression`: A `Double`.</span></span> 

<span data-ttu-id="f6792-153">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-153">**Return Value**</span></span> 

<span data-ttu-id="f6792-154">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-154">A `Double`.</span></span> 

<span data-ttu-id="f6792-155">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-155">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="f6792-156">COT (ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-156">COT(expression)</span></span>

<span data-ttu-id="f6792-157">Radyan cinsinden belirtilen açıdaki trigonometrik kovaryansı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="f6792-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="f6792-158">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-158">**Arguments**</span></span> 

<span data-ttu-id="f6792-159">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-159">`expression`: A `Double`.</span></span> 

<span data-ttu-id="f6792-160">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-160">**Return Value**</span></span> 

<span data-ttu-id="f6792-161">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-161">A `Double`.</span></span> 

<span data-ttu-id="f6792-162">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-162">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="f6792-163">DERECE (radyan)</span><span class="sxs-lookup"><span data-stu-id="f6792-163">DEGREES(radians)</span></span>

<span data-ttu-id="f6792-164">Karşılık gelen açıyı derece cinsinden döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6792-164">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="f6792-165">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-165">**Arguments**</span></span> 

<span data-ttu-id="f6792-166">`expression`: bir `Int32`, `Int64`, `Double`veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f6792-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="f6792-167">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-167">**Return Value**</span></span> 

<span data-ttu-id="f6792-168">`Int32`, `Int64`, `Double`veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f6792-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="f6792-169">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-169">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="f6792-170">EXP (ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-170">EXP(expression)</span></span>

<span data-ttu-id="f6792-171">Belirtilen bir sayısal ifadenin üstel değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="f6792-171">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="f6792-172">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-172">**Arguments**</span></span> 

<span data-ttu-id="f6792-173">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-173">`expression`: A `Double`.</span></span> 

<span data-ttu-id="f6792-174">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-174">**Return Value**</span></span> 

<span data-ttu-id="f6792-175">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-175">A `Double`.</span></span> 

<span data-ttu-id="f6792-176">**Örnek** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="f6792-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="f6792-177">FLOOR (ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-177">FLOOR(expression)</span></span>

<span data-ttu-id="f6792-178">Belirtilen ifadeyi ona eşit veya ondan küçük olan en büyük tamsayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f6792-178">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="f6792-179">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-179">**Arguments**</span></span> 

<span data-ttu-id="f6792-180">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-180">`expression`: A `Double`.</span></span> 

<span data-ttu-id="f6792-181">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-181">**Return Value**</span></span> 

<span data-ttu-id="f6792-182">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-182">A `Double`.</span></span> 

<span data-ttu-id="f6792-183">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-183">**Example**</span></span> 

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="f6792-184">GÜNLÜK (ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-184">LOG(expression)</span></span>

<span data-ttu-id="f6792-185">Belirtilen `float` ifadesinin doğal logaritmasını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="f6792-185">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="f6792-186">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-186">**Arguments**</span></span> 

<span data-ttu-id="f6792-187">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-187">`expression`: A `Double`.</span></span> 

<span data-ttu-id="f6792-188">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-188">**Return Value**</span></span> 

<span data-ttu-id="f6792-189">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-189">A `Double`.</span></span> 

<span data-ttu-id="f6792-190">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-190">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="f6792-191">LOG10 (ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-191">LOG10(expression)</span></span>

<span data-ttu-id="f6792-192">Belirtilen `Double` ifadesinin 10 tabanında logaritmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6792-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="f6792-193">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-193">**Arguments**</span></span> 

<span data-ttu-id="f6792-194">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-194">`expression`: A `Double`.</span></span> 

<span data-ttu-id="f6792-195">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-195">**Return Value**</span></span> 

<span data-ttu-id="f6792-196">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-196">A `Double`.</span></span> 

<span data-ttu-id="f6792-197">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-197">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="f6792-198">PI ()</span><span class="sxs-lookup"><span data-stu-id="f6792-198">PI()</span></span>

<span data-ttu-id="f6792-199">`Double`olarak Pi 'nin sabit değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6792-199">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="f6792-200">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-200">**Return Value**</span></span> 

<span data-ttu-id="f6792-201">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-201">A `Double`.</span></span> 

<span data-ttu-id="f6792-202">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-202">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a><span data-ttu-id="f6792-203">Güç (numeric_expression power_expression)</span><span class="sxs-lookup"><span data-stu-id="f6792-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="f6792-204">Belirtilen bir ifadenin değerini belirtilen bir kuvvet olarak hesaplar.</span><span class="sxs-lookup"><span data-stu-id="f6792-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="f6792-205">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-205">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="f6792-206">`Int32`, `Int64`, `Double`veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f6792-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="f6792-207">`numeric_expression`yükseltebileceği kuvveti temsil eden bir `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="f6792-208">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-208">**Return Value**</span></span> 

<span data-ttu-id="f6792-209">Belirtilen `power_expression`belirtilen `numeric_expression` değeri.</span><span class="sxs-lookup"><span data-stu-id="f6792-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="f6792-210">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-210">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="f6792-211">RADYAN (ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-211">RADIANS(expression)</span></span>

<span data-ttu-id="f6792-212">Dereceyi radyana dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f6792-212">Converts degrees to radians.</span></span> 

<span data-ttu-id="f6792-213">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-213">**Arguments**</span></span> 

<span data-ttu-id="f6792-214">`expression`: bir `Int32`, `Int64`, `Double`veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f6792-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="f6792-215">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-215">**Return Value**</span></span> 

<span data-ttu-id="f6792-216">`Int32`, `Int64`, `Double`veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f6792-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="f6792-217">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-217">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="f6792-218">S_SAYI_ÜRET ([çekirdek])</span><span class="sxs-lookup"><span data-stu-id="f6792-218">RAND([seed])</span></span>

<span data-ttu-id="f6792-219">0 ile 1 arasında rastgele bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6792-219">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="f6792-220">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-220">**Arguments**</span></span> 

<span data-ttu-id="f6792-221">`Int32`olarak çekirdek değeri.</span><span class="sxs-lookup"><span data-stu-id="f6792-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="f6792-222">Çekirdek belirtilmemişse, SQL Server veritabanı altyapısı rastgele bir çekirdek değeri atar.</span><span class="sxs-lookup"><span data-stu-id="f6792-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="f6792-223">Belirtilen bir çekirdek değeri için döndürülen sonuç her zaman aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f6792-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="f6792-224">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-224">**Return Value**</span></span> 

<span data-ttu-id="f6792-225">0 ile 1 arasında rastgele bir `Double` değeri.</span><span class="sxs-lookup"><span data-stu-id="f6792-225">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="f6792-226">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-226">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a><span data-ttu-id="f6792-227">ROUND (numeric_expression, Uzunluk [, işlev])</span><span class="sxs-lookup"><span data-stu-id="f6792-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="f6792-228">Belirtilen uzunluğa veya duyarlığa yuvarlanmış bir sayısal ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6792-228">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="f6792-229">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-229">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="f6792-230">`Int32`, `Int64`, `Double`veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f6792-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="f6792-231">`numeric_expression` yuvarlanacak duyarlılığı temsil eden bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="f6792-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="f6792-232">`length` pozitif bir sayı olduğunda, `numeric_expression` `length`tarafından belirtilen ondalık konum sayısına yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="f6792-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="f6792-233">`length` negatif bir sayı olduğunda, `numeric_expression` `length`tarafından belirtildiği gibi ondalık noktanın sol tarafında yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="f6792-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="f6792-234">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f6792-234">Optional.</span></span> <span data-ttu-id="f6792-235">Gerçekleştirilecek işlemin türünü temsil eden bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="f6792-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="f6792-236">İşlev atlandığında veya 0 değerine (varsayılan) sahip olduğunda `numeric_expression` yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="f6792-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="f6792-237">0 dışında bir değer belirtildiğinde `numeric_expression` kesilir.</span><span class="sxs-lookup"><span data-stu-id="f6792-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="f6792-238">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-238">**Return Value**</span></span> 

<span data-ttu-id="f6792-239">Belirtilen `power_expression`belirtilen `numeric_expression` değeri.</span><span class="sxs-lookup"><span data-stu-id="f6792-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="f6792-240">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-240">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="f6792-241">IŞARETI (ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-241">SIGN(expression)</span></span> 

<span data-ttu-id="f6792-242">Belirtilen ifadenin pozitif (+ 1), sıfır (0) veya negatif (-1) işaretini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6792-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="f6792-243">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-243">**Arguments**</span></span> 

<span data-ttu-id="f6792-244">`expression`: `Int32`, `Int64`, `Double`veya `Decimal`</span><span class="sxs-lookup"><span data-stu-id="f6792-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="f6792-245">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-245">**Return Value**</span></span> 

<span data-ttu-id="f6792-246">`Int32`, `Int64`, `Double`veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f6792-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="f6792-247">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-247">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="f6792-248">SIN (ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-248">SIN(expression)</span></span>

<span data-ttu-id="f6792-249">Radyan cinsinden belirtilen açının trigonometrik sinüsünü hesaplar ve `Double` bir ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6792-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="f6792-250">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-250">**Arguments**</span></span> 

<span data-ttu-id="f6792-251">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-251">`expression`: A `Double`.</span></span> 

<span data-ttu-id="f6792-252">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-252">**Return Value**</span></span> 

<span data-ttu-id="f6792-253">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-253">A `Double`.</span></span> 

<span data-ttu-id="f6792-254">**Örnek** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="f6792-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="f6792-255">SQRT (ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-255">SQRT(expression)</span></span>

<span data-ttu-id="f6792-256">Belirtilen ifadenin kare kökünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6792-256">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="f6792-257">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-257">**Arguments**</span></span> 

<span data-ttu-id="f6792-258">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-258">`expression`: A `Double`.</span></span> 

<span data-ttu-id="f6792-259">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-259">**Return Value**</span></span> 

<span data-ttu-id="f6792-260">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-260">A `Double`.</span></span> 

<span data-ttu-id="f6792-261">**Örnek** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="f6792-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="f6792-262">KARE (ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-262">SQUARE(expression)</span></span>

<span data-ttu-id="f6792-263">Belirtilen ifadenin karesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6792-263">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="f6792-264">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-264">**Arguments**</span></span> 

<span data-ttu-id="f6792-265">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-265">`expression`: A `Double`.</span></span> 

<span data-ttu-id="f6792-266">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-266">**Return Value**</span></span> 

<span data-ttu-id="f6792-267">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="f6792-267">A `Double`.</span></span> 

<span data-ttu-id="f6792-268">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-268">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="f6792-269">TAN (ifade)</span><span class="sxs-lookup"><span data-stu-id="f6792-269">TAN(expression)</span></span>

<span data-ttu-id="f6792-270">Belirtilen bir ifadenin tanjantını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="f6792-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="f6792-271">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="f6792-271">**Arguments**</span></span> 

<span data-ttu-id="f6792-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="f6792-272">`expression`: `Double`</span></span> 

<span data-ttu-id="f6792-273">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="f6792-273">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="f6792-274">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="f6792-274">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="f6792-275">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6792-275">See also</span></span>

- [<span data-ttu-id="f6792-276">Matematik Işlevleri (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f6792-276">Mathematical Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [<span data-ttu-id="f6792-277">Entity Framework için SqlClient İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f6792-277">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
