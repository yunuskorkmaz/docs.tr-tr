---
title: Matematik İşlevleri
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 5e5658e28c7d806f7fd38f941bfa7254e7806e11
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182489"
---
# <a name="mathematical-functions"></a><span data-ttu-id="5e60e-102">Matematik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5e60e-102">Mathematical Functions</span></span>

<span data-ttu-id="5e60e-103">SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı, bağımsız değişken olarak sağlanan giriş değerlerinde hesaplamalar gerçekleştiren ve sayısal bir değer sonucu döndüren matematik işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e60e-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="5e60e-104">Bu işlevler, SqlClient kullandığınızda kullanılabilir olan SqlServer ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="5e60e-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="5e60e-105">Bir sağlayıcının ad alanı özelliği Entity Framework, bu sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan öneki bulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e60e-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="5e60e-106">Aşağıdaki tabloda, SqlClient matematik işlevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e60e-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="5e60e-107">ABS (ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-107">ABS(expression)</span></span>

<span data-ttu-id="5e60e-108">Mutlak değer işlevini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="5e60e-108">Performs the absolute value function.</span></span>

<span data-ttu-id="5e60e-109">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-109">**Arguments**</span></span>

<span data-ttu-id="5e60e-110">`expression`: `Int32` ,`Int64`, Veya .`Decimal` `Double`</span><span class="sxs-lookup"><span data-stu-id="5e60e-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="5e60e-111">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-111">**Return Value**</span></span>

<span data-ttu-id="5e60e-112">Belirtilen ifadenin mutlak değeri.</span><span class="sxs-lookup"><span data-stu-id="5e60e-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="5e60e-113">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="5e60e-114">ACOS (ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-114">ACOS(expression)</span></span>

<span data-ttu-id="5e60e-115">Belirtilen ifadenin Arkkosinüs değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e60e-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="5e60e-116">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-116">**Arguments**</span></span>

<span data-ttu-id="5e60e-117">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="5e60e-118">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-118">**Return Value**</span></span>

<span data-ttu-id="5e60e-119">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-119">A `Double`.</span></span>

<span data-ttu-id="5e60e-120">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="5e60e-121">ASIN (ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-121">ASIN(expression)</span></span>

<span data-ttu-id="5e60e-122">Belirtilen ifadenin arksinüs değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e60e-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="5e60e-123">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-123">**Arguments**</span></span>

<span data-ttu-id="5e60e-124">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="5e60e-125">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-125">**Return Value**</span></span>

<span data-ttu-id="5e60e-126">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-126">A `Double`.</span></span>

<span data-ttu-id="5e60e-127">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="5e60e-128">ATAN (ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-128">ATAN(expression)</span></span>

<span data-ttu-id="5e60e-129">Belirtilen sayısal ifadenin arktanjant değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e60e-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="5e60e-130">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-130">**Arguments**</span></span>

<span data-ttu-id="5e60e-131">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="5e60e-132">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-132">**Return Value**</span></span>

<span data-ttu-id="5e60e-133">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-133">A `Double`.</span></span>

<span data-ttu-id="5e60e-134">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="5e60e-135">ATN2 (ifade, ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="5e60e-136">Tanjantı belirtilen iki sayısal ifade arasında olan radyan cinsinden açıyı döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e60e-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="5e60e-137">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-137">**Arguments**</span></span>

<span data-ttu-id="5e60e-138">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="5e60e-139">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-139">**Return Value**</span></span>

<span data-ttu-id="5e60e-140">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-140">A `Double`.</span></span>

<span data-ttu-id="5e60e-141">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="5e60e-142">TAVAN (ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-142">CEILING(expression)</span></span>

<span data-ttu-id="5e60e-143">Belirtilen ifadeyi, bu değerden büyük veya ona eşit en küçük tamsayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5e60e-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="5e60e-144">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-144">**Arguments**</span></span>

<span data-ttu-id="5e60e-145">`expression`: `Int32` ,`Int64`, Veya .`Decimal` `Double`</span><span class="sxs-lookup"><span data-stu-id="5e60e-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="5e60e-146">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-146">**Return Value**</span></span>

<span data-ttu-id="5e60e-147">`Int32` ,`Int64`, Veya .`Decimal` `Double`</span><span class="sxs-lookup"><span data-stu-id="5e60e-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="5e60e-148">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-148">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="5e60e-149">COS (ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-149">COS(expression)</span></span>

<span data-ttu-id="5e60e-150">Radyan cinsinden belirtilen açının trigonometrik kosinüsünü hesaplar.</span><span class="sxs-lookup"><span data-stu-id="5e60e-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="5e60e-151">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-151">**Arguments**</span></span> 

<span data-ttu-id="5e60e-152">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-152">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5e60e-153">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-153">**Return Value**</span></span> 

<span data-ttu-id="5e60e-154">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-154">A `Double`.</span></span> 

<span data-ttu-id="5e60e-155">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-155">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="5e60e-156">COT (ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-156">COT(expression)</span></span>

<span data-ttu-id="5e60e-157">Radyan cinsinden belirtilen açıdaki trigonometrik kovaryansı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="5e60e-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="5e60e-158">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-158">**Arguments**</span></span> 

<span data-ttu-id="5e60e-159">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-159">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5e60e-160">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-160">**Return Value**</span></span> 

<span data-ttu-id="5e60e-161">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-161">A `Double`.</span></span> 

<span data-ttu-id="5e60e-162">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-162">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="5e60e-163">DERECE (radyan)</span><span class="sxs-lookup"><span data-stu-id="5e60e-163">DEGREES(radians)</span></span>

<span data-ttu-id="5e60e-164">Karşılık gelen açıyı derece cinsinden döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e60e-164">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="5e60e-165">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-165">**Arguments**</span></span> 

<span data-ttu-id="5e60e-166">`expression`: `Int32` ,`Int64`, Veya .`Decimal` `Double`</span><span class="sxs-lookup"><span data-stu-id="5e60e-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="5e60e-167">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-167">**Return Value**</span></span> 

<span data-ttu-id="5e60e-168">`Int32` ,`Int64`, Veya .`Decimal` `Double`</span><span class="sxs-lookup"><span data-stu-id="5e60e-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="5e60e-169">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-169">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="5e60e-170">EXP (ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-170">EXP(expression)</span></span>

<span data-ttu-id="5e60e-171">Belirtilen bir sayısal ifadenin üstel değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="5e60e-171">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="5e60e-172">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-172">**Arguments**</span></span> 

<span data-ttu-id="5e60e-173">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-173">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5e60e-174">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-174">**Return Value**</span></span> 

<span data-ttu-id="5e60e-175">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-175">A `Double`.</span></span> 

<span data-ttu-id="5e60e-176">**Örnek**`SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="5e60e-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="5e60e-177">FLOOR (ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-177">FLOOR(expression)</span></span>

<span data-ttu-id="5e60e-178">Belirtilen ifadeyi ona eşit veya ondan küçük olan en büyük tamsayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5e60e-178">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="5e60e-179">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-179">**Arguments**</span></span> 

<span data-ttu-id="5e60e-180">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-180">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5e60e-181">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-181">**Return Value**</span></span> 

<span data-ttu-id="5e60e-182">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-182">A `Double`.</span></span> 

<span data-ttu-id="5e60e-183">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-183">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="5e60e-184">GÜNLÜK (ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-184">LOG(expression)</span></span>

<span data-ttu-id="5e60e-185">Belirtilen `float` ifadenin doğal logaritmasını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="5e60e-185">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="5e60e-186">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-186">**Arguments**</span></span> 

<span data-ttu-id="5e60e-187">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-187">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5e60e-188">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-188">**Return Value**</span></span> 

<span data-ttu-id="5e60e-189">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-189">A `Double`.</span></span> 

<span data-ttu-id="5e60e-190">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-190">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="5e60e-191">LOG10 (ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-191">LOG10(expression)</span></span>

<span data-ttu-id="5e60e-192">Belirtilen `Double` ifadenin 10 tabanında logaritmasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e60e-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="5e60e-193">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-193">**Arguments**</span></span> 

<span data-ttu-id="5e60e-194">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-194">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5e60e-195">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-195">**Return Value**</span></span> 

<span data-ttu-id="5e60e-196">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-196">A `Double`.</span></span> 

<span data-ttu-id="5e60e-197">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-197">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="5e60e-198">PI ()</span><span class="sxs-lookup"><span data-stu-id="5e60e-198">PI()</span></span>

<span data-ttu-id="5e60e-199">Pi değerinin sabit değerini bir `Double`olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e60e-199">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="5e60e-200">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-200">**Return Value**</span></span> 

<span data-ttu-id="5e60e-201">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-201">A `Double`.</span></span> 

<span data-ttu-id="5e60e-202">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-202">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a><span data-ttu-id="5e60e-203">Güç (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="5e60e-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="5e60e-204">Belirtilen bir ifadenin değerini belirtilen bir kuvvet olarak hesaplar.</span><span class="sxs-lookup"><span data-stu-id="5e60e-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="5e60e-205">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-205">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="5e60e-206">`Int32` ,`Int64`, Veya .`Decimal` `Double`</span><span class="sxs-lookup"><span data-stu-id="5e60e-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="5e60e-207">`Double` Öğesini ,`numeric_expression`öğesini yükseltmek için gereken kuvveti temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5e60e-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="5e60e-208">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-208">**Return Value**</span></span> 

<span data-ttu-id="5e60e-209">Belirtilen değerinin belirtilen `numeric_expression` `power_expression`değeri.</span><span class="sxs-lookup"><span data-stu-id="5e60e-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="5e60e-210">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-210">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="5e60e-211">RADYAN (ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-211">RADIANS(expression)</span></span>

<span data-ttu-id="5e60e-212">Dereceyi radyana dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5e60e-212">Converts degrees to radians.</span></span> 

<span data-ttu-id="5e60e-213">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-213">**Arguments**</span></span> 

<span data-ttu-id="5e60e-214">`expression`: `Int32` ,`Int64`, Veya .`Decimal` `Double`</span><span class="sxs-lookup"><span data-stu-id="5e60e-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="5e60e-215">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-215">**Return Value**</span></span> 

<span data-ttu-id="5e60e-216">`Int32` ,`Int64`, Veya .`Decimal` `Double`</span><span class="sxs-lookup"><span data-stu-id="5e60e-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="5e60e-217">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-217">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="5e60e-218">S_SAYI_ÜRET ([çekirdek])</span><span class="sxs-lookup"><span data-stu-id="5e60e-218">RAND([seed])</span></span>

<span data-ttu-id="5e60e-219">0 ile 1 arasında rastgele bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e60e-219">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="5e60e-220">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-220">**Arguments**</span></span> 

<span data-ttu-id="5e60e-221">Çekirdek değeri bir `Int32`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="5e60e-222">Çekirdek belirtilmemişse, SQL Server veritabanı altyapısı rastgele bir çekirdek değeri atar.</span><span class="sxs-lookup"><span data-stu-id="5e60e-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="5e60e-223">Belirtilen bir çekirdek değeri için döndürülen sonuç her zaman aynıdır.</span><span class="sxs-lookup"><span data-stu-id="5e60e-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="5e60e-224">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-224">**Return Value**</span></span> 

<span data-ttu-id="5e60e-225">0 ile `Double` 1 arasında rastgele bir değer.</span><span class="sxs-lookup"><span data-stu-id="5e60e-225">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="5e60e-226">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-226">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a><span data-ttu-id="5e60e-227">ROUND (numeric_expression, length [, Function])</span><span class="sxs-lookup"><span data-stu-id="5e60e-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="5e60e-228">Belirtilen uzunluğa veya duyarlığa yuvarlanmış bir sayısal ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e60e-228">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="5e60e-229">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-229">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="5e60e-230">`Int32` ,`Int64`, Veya .`Decimal` `Double`</span><span class="sxs-lookup"><span data-stu-id="5e60e-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="5e60e-231">Bu, yuvarlanacak duyarlığı `numeric_expression` temsil eder. `Int32`</span><span class="sxs-lookup"><span data-stu-id="5e60e-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="5e60e-232">Pozitif `length` bir sayı olduğunda, `numeric_expression` tarafından `length`belirtilen ondalık konum sayısına yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="5e60e-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="5e60e-233">Negatif `length` bir sayı olduğunda, `numeric_expression` ondalık noktanın sol tarafında tarafından `length`belirtildiği gibi yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="5e60e-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="5e60e-234">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5e60e-234">Optional.</span></span> <span data-ttu-id="5e60e-235">Gerçekleştirilecek `Int32` işlemin türünü temsil eden bir.</span><span class="sxs-lookup"><span data-stu-id="5e60e-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="5e60e-236">İşlev atlandığında veya 0 değerine (varsayılan) sahip olduğunda, `numeric_expression` yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="5e60e-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="5e60e-237">0 dışında bir değer belirtildiğinde, `numeric_expression` atılır.</span><span class="sxs-lookup"><span data-stu-id="5e60e-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="5e60e-238">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-238">**Return Value**</span></span> 

<span data-ttu-id="5e60e-239">Belirtilen değerinin belirtilen `numeric_expression` `power_expression`değeri.</span><span class="sxs-lookup"><span data-stu-id="5e60e-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="5e60e-240">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-240">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="5e60e-241">IŞARETI (ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-241">SIGN(expression)</span></span> 

<span data-ttu-id="5e60e-242">Belirtilen ifadenin pozitif (+ 1), sıfır (0) veya negatif (-1) işaretini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e60e-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="5e60e-243">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-243">**Arguments**</span></span> 

<span data-ttu-id="5e60e-244">`expression`: `Int32`, `Int64` ,`Double`, veya`Decimal`</span><span class="sxs-lookup"><span data-stu-id="5e60e-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="5e60e-245">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-245">**Return Value**</span></span> 

<span data-ttu-id="5e60e-246">`Int32` ,`Int64`, Veya .`Decimal` `Double`</span><span class="sxs-lookup"><span data-stu-id="5e60e-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="5e60e-247">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-247">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="5e60e-248">SIN (ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-248">SIN(expression)</span></span>

<span data-ttu-id="5e60e-249">Radyan cinsinden belirtilen açının trigonometrik sinüsünü hesaplar ve bir `Double` ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e60e-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="5e60e-250">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-250">**Arguments**</span></span> 

<span data-ttu-id="5e60e-251">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-251">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5e60e-252">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-252">**Return Value**</span></span> 

<span data-ttu-id="5e60e-253">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-253">A `Double`.</span></span> 

<span data-ttu-id="5e60e-254">**Örnek**`SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="5e60e-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="5e60e-255">SQRT (ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-255">SQRT(expression)</span></span>

<span data-ttu-id="5e60e-256">Belirtilen ifadenin kare kökünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e60e-256">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="5e60e-257">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-257">**Arguments**</span></span> 

<span data-ttu-id="5e60e-258">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-258">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5e60e-259">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-259">**Return Value**</span></span> 

<span data-ttu-id="5e60e-260">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-260">A `Double`.</span></span> 

<span data-ttu-id="5e60e-261">**Örnek**`SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="5e60e-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="5e60e-262">KARE (ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-262">SQUARE(expression)</span></span>

<span data-ttu-id="5e60e-263">Belirtilen ifadenin karesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e60e-263">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="5e60e-264">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-264">**Arguments**</span></span> 

<span data-ttu-id="5e60e-265">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-265">`expression`: A `Double`.</span></span> 

<span data-ttu-id="5e60e-266">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-266">**Return Value**</span></span> 

<span data-ttu-id="5e60e-267">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5e60e-267">A `Double`.</span></span> 

<span data-ttu-id="5e60e-268">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-268">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="5e60e-269">TAN (ifade)</span><span class="sxs-lookup"><span data-stu-id="5e60e-269">TAN(expression)</span></span>

<span data-ttu-id="5e60e-270">Belirtilen bir ifadenin tanjantını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="5e60e-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="5e60e-271">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="5e60e-271">**Arguments**</span></span> 

<span data-ttu-id="5e60e-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="5e60e-272">`expression`: `Double`</span></span> 

<span data-ttu-id="5e60e-273">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="5e60e-273">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="5e60e-274">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="5e60e-274">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="5e60e-275">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e60e-275">See also</span></span>

<span data-ttu-id="5e60e-276">SqlClient tarafından desteklenen matematik işlevleri hakkında daha fazla bilgi için, SqlClient sağlayıcısı bildiriminde belirttiğiniz SQL Server sürümü için belgelere bakın:</span><span class="sxs-lookup"><span data-stu-id="5e60e-276">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="5e60e-277">**SQL Server 2005:** [Matematik Işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="5e60e-277">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>
- <span data-ttu-id="5e60e-278">**SQL Server 2008:** [Matematik Işlevleri (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="5e60e-278">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>
- <span data-ttu-id="5e60e-279">**SQL Server 2012 ve üzeri:** [Matematik Işlevleri (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="5e60e-279">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)</span></span>

- [<span data-ttu-id="5e60e-280">Entity Framework için SqlClient İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5e60e-280">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
