---
title: Kurallı matematik işlevleri
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 0fc9f4942c3f76f139ab7e4400005f0bfe80204e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43442791"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="7c392-102">Kurallı matematik işlevleri</span><span class="sxs-lookup"><span data-stu-id="7c392-102">Math Canonical Functions</span></span>

<span data-ttu-id="7c392-103">Entity SQL aşağıdaki kurallı matematik işlevleri içerir:</span><span class="sxs-lookup"><span data-stu-id="7c392-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="7c392-104">Abs(Value)</span><span class="sxs-lookup"><span data-stu-id="7c392-104">Abs(value)</span></span>

<span data-ttu-id="7c392-105">Mutlak değerini döndürür `value`.</span><span class="sxs-lookup"><span data-stu-id="7c392-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="7c392-106">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="7c392-106">**Arguments**</span></span>

<span data-ttu-id="7c392-107">Bir `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="7c392-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="7c392-108">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="7c392-108">**Return Value**</span></span>

<span data-ttu-id="7c392-109">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="7c392-109">The type of `value`.</span></span>

<span data-ttu-id="7c392-110">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="7c392-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="7c392-111">Ceiling(Value)</span><span class="sxs-lookup"><span data-stu-id="7c392-111">Ceiling(value)</span></span>

<span data-ttu-id="7c392-112">Küçük olmayan en küçük tamsayı döndürür daha `value`.</span><span class="sxs-lookup"><span data-stu-id="7c392-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="7c392-113">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="7c392-113">**Arguments**</span></span>

<span data-ttu-id="7c392-114">A `Single`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="7c392-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="7c392-115">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="7c392-115">**Return Value**</span></span>

<span data-ttu-id="7c392-116">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="7c392-116">The type of `value`.</span></span>

<span data-ttu-id="7c392-117">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="7c392-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="7c392-118">Floor(Value)</span><span class="sxs-lookup"><span data-stu-id="7c392-118">Floor(value)</span></span>

<span data-ttu-id="7c392-119">Değerinden büyük olmayan en büyük tamsayı döndürür `value`.</span><span class="sxs-lookup"><span data-stu-id="7c392-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="7c392-120">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="7c392-120">**Arguments**</span></span>

<span data-ttu-id="7c392-121">A `Single`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="7c392-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="7c392-122">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="7c392-122">**Return Value**</span></span>

<span data-ttu-id="7c392-123">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="7c392-123">The type of `value`.</span></span>

<span data-ttu-id="7c392-124">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="7c392-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="7c392-125">Güç (değeri, üs)</span><span class="sxs-lookup"><span data-stu-id="7c392-125">Power(value, exponent)</span></span>

<span data-ttu-id="7c392-126">Belirtilen sonuç döndüren `value` belirtilen `exponent`.</span><span class="sxs-lookup"><span data-stu-id="7c392-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="7c392-127">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="7c392-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="7c392-128">Bir `Int32, Int64, Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="7c392-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="7c392-129">Bir `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="7c392-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="7c392-130">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="7c392-130">**Return Value**</span></span>

<span data-ttu-id="7c392-131">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="7c392-131">The type of `value`.</span></span>

<span data-ttu-id="7c392-132">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="7c392-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="7c392-133">Round(Value)</span><span class="sxs-lookup"><span data-stu-id="7c392-133">Round(value)</span></span>

<span data-ttu-id="7c392-134">Tamsayı bölümünü döndürür `value`, en yakın tamsayıya yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="7c392-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="7c392-135">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="7c392-135">**Arguments**</span></span>

<span data-ttu-id="7c392-136">A `Single`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="7c392-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="7c392-137">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="7c392-137">**Return Value**</span></span>

<span data-ttu-id="7c392-138">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="7c392-138">The type of `value`.</span></span>

<span data-ttu-id="7c392-139">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="7c392-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="7c392-140">Round (değer, basamak)</span><span class="sxs-lookup"><span data-stu-id="7c392-140">Round(value, digits)</span></span>

<span data-ttu-id="7c392-141">Döndürür `value`, yuvarlanır yakın belirtilen `digits`.</span><span class="sxs-lookup"><span data-stu-id="7c392-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="7c392-142">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="7c392-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="7c392-143">`Double` veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="7c392-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="7c392-144">`Int16` veya `Int32`.</span><span class="sxs-lookup"><span data-stu-id="7c392-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="7c392-145">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="7c392-145">**Return Value**</span></span>

<span data-ttu-id="7c392-146">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="7c392-146">The type of `value`.</span></span>

<span data-ttu-id="7c392-147">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="7c392-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="7c392-148">(Değer, basamak) Kes</span><span class="sxs-lookup"><span data-stu-id="7c392-148">Truncate(value, digits)</span></span>

<span data-ttu-id="7c392-149">Döndürür `value`, kesilmiş yakın belirtilen `digits`.</span><span class="sxs-lookup"><span data-stu-id="7c392-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="7c392-150">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="7c392-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="7c392-151">`Double` veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="7c392-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="7c392-152">`Int16` veya `Int32`.</span><span class="sxs-lookup"><span data-stu-id="7c392-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="7c392-153">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="7c392-153">**Return Value**</span></span>

<span data-ttu-id="7c392-154">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="7c392-154">The type of `value`.</span></span>

<span data-ttu-id="7c392-155">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="7c392-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="7c392-156">Bu işlevler döndüreceği `null` verildiyse `null` giriş.</span><span class="sxs-lookup"><span data-stu-id="7c392-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="7c392-157">Microsoft SQL istemci yönetilen sağlayıcısında eşdeğer bir işlevselliği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7c392-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="7c392-158">Daha fazla bilgi için [Entity Framework işlevleri için SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="7c392-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c392-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c392-159">See Also</span></span>  
 [<span data-ttu-id="7c392-160">Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="7c392-160">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
