---
title: Kurallı matematik işlevleri
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 0fc9f4942c3f76f139ab7e4400005f0bfe80204e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740360"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="a44ac-102">Kurallı matematik işlevleri</span><span class="sxs-lookup"><span data-stu-id="a44ac-102">Math Canonical Functions</span></span>

<span data-ttu-id="a44ac-103">Entity SQL aşağıdaki kurallı matematik işlevleri içerir:</span><span class="sxs-lookup"><span data-stu-id="a44ac-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="a44ac-104">Abs(Value)</span><span class="sxs-lookup"><span data-stu-id="a44ac-104">Abs(value)</span></span>

<span data-ttu-id="a44ac-105">Mutlak değerini döndürür `value`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="a44ac-106">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="a44ac-106">**Arguments**</span></span>

<span data-ttu-id="a44ac-107">Bir `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="a44ac-108">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="a44ac-108">**Return Value**</span></span>

<span data-ttu-id="a44ac-109">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-109">The type of `value`.</span></span>

<span data-ttu-id="a44ac-110">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="a44ac-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="a44ac-111">Ceiling(Value)</span><span class="sxs-lookup"><span data-stu-id="a44ac-111">Ceiling(value)</span></span>

<span data-ttu-id="a44ac-112">Küçük olmayan en küçük tamsayı döndürür daha `value`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="a44ac-113">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="a44ac-113">**Arguments**</span></span>

<span data-ttu-id="a44ac-114">A `Single`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="a44ac-115">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="a44ac-115">**Return Value**</span></span>

<span data-ttu-id="a44ac-116">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-116">The type of `value`.</span></span>

<span data-ttu-id="a44ac-117">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="a44ac-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="a44ac-118">Floor(Value)</span><span class="sxs-lookup"><span data-stu-id="a44ac-118">Floor(value)</span></span>

<span data-ttu-id="a44ac-119">Değerinden büyük olmayan en büyük tamsayı döndürür `value`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="a44ac-120">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="a44ac-120">**Arguments**</span></span>

<span data-ttu-id="a44ac-121">A `Single`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="a44ac-122">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="a44ac-122">**Return Value**</span></span>

<span data-ttu-id="a44ac-123">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-123">The type of `value`.</span></span>

<span data-ttu-id="a44ac-124">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="a44ac-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="a44ac-125">Güç (değeri, üs)</span><span class="sxs-lookup"><span data-stu-id="a44ac-125">Power(value, exponent)</span></span>

<span data-ttu-id="a44ac-126">Belirtilen sonuç döndüren `value` belirtilen `exponent`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="a44ac-127">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="a44ac-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="a44ac-128">Bir `Int32, Int64, Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="a44ac-129">Bir `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="a44ac-130">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="a44ac-130">**Return Value**</span></span>

<span data-ttu-id="a44ac-131">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-131">The type of `value`.</span></span>

<span data-ttu-id="a44ac-132">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="a44ac-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="a44ac-133">Round(Value)</span><span class="sxs-lookup"><span data-stu-id="a44ac-133">Round(value)</span></span>

<span data-ttu-id="a44ac-134">Tamsayı bölümünü döndürür `value`, en yakın tamsayıya yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="a44ac-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="a44ac-135">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="a44ac-135">**Arguments**</span></span>

<span data-ttu-id="a44ac-136">A `Single`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="a44ac-137">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="a44ac-137">**Return Value**</span></span>

<span data-ttu-id="a44ac-138">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-138">The type of `value`.</span></span>

<span data-ttu-id="a44ac-139">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="a44ac-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="a44ac-140">Round (değer, basamak)</span><span class="sxs-lookup"><span data-stu-id="a44ac-140">Round(value, digits)</span></span>

<span data-ttu-id="a44ac-141">Döndürür `value`, yuvarlanır yakın belirtilen `digits`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="a44ac-142">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="a44ac-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="a44ac-143">`Double` veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="a44ac-144">`Int16` veya `Int32`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="a44ac-145">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="a44ac-145">**Return Value**</span></span>

<span data-ttu-id="a44ac-146">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-146">The type of `value`.</span></span>

<span data-ttu-id="a44ac-147">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="a44ac-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="a44ac-148">(Değer, basamak) Kes</span><span class="sxs-lookup"><span data-stu-id="a44ac-148">Truncate(value, digits)</span></span>

<span data-ttu-id="a44ac-149">Döndürür `value`, kesilmiş yakın belirtilen `digits`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="a44ac-150">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="a44ac-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="a44ac-151">`Double` veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="a44ac-152">`Int16` veya `Int32`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="a44ac-153">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="a44ac-153">**Return Value**</span></span>

<span data-ttu-id="a44ac-154">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="a44ac-154">The type of `value`.</span></span>

<span data-ttu-id="a44ac-155">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="a44ac-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="a44ac-156">Bu işlevler döndüreceği `null` verildiyse `null` giriş.</span><span class="sxs-lookup"><span data-stu-id="a44ac-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="a44ac-157">Microsoft SQL istemci yönetilen sağlayıcısında eşdeğer bir işlevselliği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a44ac-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="a44ac-158">Daha fazla bilgi için [Entity Framework işlevleri için SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="a44ac-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a44ac-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a44ac-159">See Also</span></span>  
 [<span data-ttu-id="a44ac-160">Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="a44ac-160">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
