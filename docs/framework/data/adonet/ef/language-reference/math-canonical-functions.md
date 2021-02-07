---
description: 'Daha fazla bilgi edinin: matematik kurallı Işlevleri'
title: Kurallı Matematik İşlevleri
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 55072099f5766d48ea3067a2e9eaa187a8b3f111
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739371"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="e2698-103">Kurallı Matematik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e2698-103">Math Canonical Functions</span></span>

<span data-ttu-id="e2698-104">Entity SQL aşağıdaki matematik kurallı işlevlerini içerir:</span><span class="sxs-lookup"><span data-stu-id="e2698-104">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="e2698-105">ABS (değer)</span><span class="sxs-lookup"><span data-stu-id="e2698-105">Abs(value)</span></span>

<span data-ttu-id="e2698-106">`value` öğesinin mutlak değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e2698-106">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="e2698-107">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="e2698-107">**Arguments**</span></span>

<span data-ttu-id="e2698-108">,,,,, `Int16` `Int32` `Int64` `Byte` `Single` `Double` , Ve `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="e2698-108">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="e2698-109">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="e2698-109">**Return Value**</span></span>

<span data-ttu-id="e2698-110">Türü `value` .</span><span class="sxs-lookup"><span data-stu-id="e2698-110">The type of `value`.</span></span>

<span data-ttu-id="e2698-111">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="e2698-111">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="e2698-112">Tavan (değer)</span><span class="sxs-lookup"><span data-stu-id="e2698-112">Ceiling(value)</span></span>

<span data-ttu-id="e2698-113">Küçüktür olan en küçük tamsayıyı döndürür `value` .</span><span class="sxs-lookup"><span data-stu-id="e2698-113">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="e2698-114">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="e2698-114">**Arguments**</span></span>

<span data-ttu-id="e2698-115">`Single`, `Double` , Ve `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="e2698-115">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="e2698-116">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="e2698-116">**Return Value**</span></span>

<span data-ttu-id="e2698-117">Türü `value` .</span><span class="sxs-lookup"><span data-stu-id="e2698-117">The type of `value`.</span></span>

<span data-ttu-id="e2698-118">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="e2698-118">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="e2698-119">Floor (değer)</span><span class="sxs-lookup"><span data-stu-id="e2698-119">Floor(value)</span></span>

<span data-ttu-id="e2698-120">Değerinden büyük olmayan en büyük tamsayıyı döndürür `value` .</span><span class="sxs-lookup"><span data-stu-id="e2698-120">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="e2698-121">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="e2698-121">**Arguments**</span></span>

<span data-ttu-id="e2698-122">`Single`, `Double` , Ve `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="e2698-122">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="e2698-123">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="e2698-123">**Return Value**</span></span>

<span data-ttu-id="e2698-124">Türü `value` .</span><span class="sxs-lookup"><span data-stu-id="e2698-124">The type of `value`.</span></span>

<span data-ttu-id="e2698-125">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="e2698-125">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="e2698-126">Güç (değer, üs)</span><span class="sxs-lookup"><span data-stu-id="e2698-126">Power(value, exponent)</span></span>

<span data-ttu-id="e2698-127">Belirtilen öğesinin sonucunu `value` belirtilen şekilde döndürür `exponent` .</span><span class="sxs-lookup"><span data-stu-id="e2698-127">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="e2698-128">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="e2698-128">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="e2698-129">`Int32, Int64, Double`, Veya `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="e2698-129">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="e2698-130">Bir `Int64` , `Double` veya `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="e2698-130">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="e2698-131">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="e2698-131">**Return Value**</span></span>

<span data-ttu-id="e2698-132">Türü `value` .</span><span class="sxs-lookup"><span data-stu-id="e2698-132">The type of `value`.</span></span>

<span data-ttu-id="e2698-133">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="e2698-133">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="e2698-134">Round (değer)</span><span class="sxs-lookup"><span data-stu-id="e2698-134">Round(value)</span></span>

<span data-ttu-id="e2698-135">Öğesinin tamsayı bölümünü döndürür `value` , en yakın tamsayıya yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="e2698-135">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="e2698-136">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="e2698-136">**Arguments**</span></span>

<span data-ttu-id="e2698-137">`Single`, `Double` , Ve `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="e2698-137">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="e2698-138">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="e2698-138">**Return Value**</span></span>

<span data-ttu-id="e2698-139">Türü `value` .</span><span class="sxs-lookup"><span data-stu-id="e2698-139">The type of `value`.</span></span>

<span data-ttu-id="e2698-140">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="e2698-140">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="e2698-141">Round (değer, basamak)</span><span class="sxs-lookup"><span data-stu-id="e2698-141">Round(value, digits)</span></span>

<span data-ttu-id="e2698-142">`value`Belirtilen en yakın değere yuvarlanır ve döndürür `digits` .</span><span class="sxs-lookup"><span data-stu-id="e2698-142">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="e2698-143">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="e2698-143">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="e2698-144">`Double` veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e2698-144">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="e2698-145">`Int16` veya `Int32`.</span><span class="sxs-lookup"><span data-stu-id="e2698-145">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="e2698-146">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="e2698-146">**Return Value**</span></span>

<span data-ttu-id="e2698-147">Türü `value` .</span><span class="sxs-lookup"><span data-stu-id="e2698-147">The type of `value`.</span></span>

<span data-ttu-id="e2698-148">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="e2698-148">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="e2698-149">Kes (değer, basamak)</span><span class="sxs-lookup"><span data-stu-id="e2698-149">Truncate(value, digits)</span></span>

<span data-ttu-id="e2698-150">`value`Belirtilen en yakın değere kesilen öğesini döndürür `digits` .</span><span class="sxs-lookup"><span data-stu-id="e2698-150">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="e2698-151">**Bağımsız değişkenler**</span><span class="sxs-lookup"><span data-stu-id="e2698-151">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="e2698-152">`Double` veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e2698-152">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="e2698-153">`Int16` veya `Int32`.</span><span class="sxs-lookup"><span data-stu-id="e2698-153">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="e2698-154">**Dönüş Değeri**</span><span class="sxs-lookup"><span data-stu-id="e2698-154">**Return Value**</span></span>

<span data-ttu-id="e2698-155">Türü `value` .</span><span class="sxs-lookup"><span data-stu-id="e2698-155">The type of `value`.</span></span>

<span data-ttu-id="e2698-156">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="e2698-156">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="e2698-157">Bu işlevler, `null` verilen giriş durumunda döndürülür `null` .</span><span class="sxs-lookup"><span data-stu-id="e2698-157">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="e2698-158">Eşdeğer işlevsellik, Microsoft SQL Istemci tarafından yönetilen sağlayıcıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="e2698-158">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="e2698-159">Daha fazla bilgi için bkz. [Entity Framework işlevleri Için SqlClient](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="e2698-159">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2698-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2698-160">See also</span></span>

- [<span data-ttu-id="e2698-161">Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="e2698-161">Canonical Functions</span></span>](canonical-functions.md)
