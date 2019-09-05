---
title: Kurallı Matematik İşlevleri
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 9417ff9836912017c9d88bb24a18849aaac2836a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250302"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="75fcc-102">Kurallı Matematik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="75fcc-102">Math Canonical Functions</span></span>

<span data-ttu-id="75fcc-103">Entity SQL aşağıdaki matematik kurallı işlevlerini içerir:</span><span class="sxs-lookup"><span data-stu-id="75fcc-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="75fcc-104">ABS (değer)</span><span class="sxs-lookup"><span data-stu-id="75fcc-104">Abs(value)</span></span>

<span data-ttu-id="75fcc-105">Öğesinin `value`mutlak değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="75fcc-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="75fcc-106">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="75fcc-106">**Arguments**</span></span>

<span data-ttu-id="75fcc-107">`Int16` ,`Byte` ,,`Decimal`,, ,Ve.`Double` `Int32` `Int64` `Single`</span><span class="sxs-lookup"><span data-stu-id="75fcc-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="75fcc-108">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="75fcc-108">**Return Value**</span></span>

<span data-ttu-id="75fcc-109">Türü `value`.</span><span class="sxs-lookup"><span data-stu-id="75fcc-109">The type of `value`.</span></span>

<span data-ttu-id="75fcc-110">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="75fcc-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="75fcc-111">Tavan (değer)</span><span class="sxs-lookup"><span data-stu-id="75fcc-111">Ceiling(value)</span></span>

<span data-ttu-id="75fcc-112">Küçüktür olan `value`en küçük tamsayıyı döndürür.</span><span class="sxs-lookup"><span data-stu-id="75fcc-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="75fcc-113">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="75fcc-113">**Arguments**</span></span>

<span data-ttu-id="75fcc-114">`Single`, ,`Double`Ve .`Decimal`</span><span class="sxs-lookup"><span data-stu-id="75fcc-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="75fcc-115">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="75fcc-115">**Return Value**</span></span>

<span data-ttu-id="75fcc-116">Türü `value`.</span><span class="sxs-lookup"><span data-stu-id="75fcc-116">The type of `value`.</span></span>

<span data-ttu-id="75fcc-117">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="75fcc-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="75fcc-118">Floor (değer)</span><span class="sxs-lookup"><span data-stu-id="75fcc-118">Floor(value)</span></span>

<span data-ttu-id="75fcc-119">Değerinden `value`büyük olmayan en büyük tamsayıyı döndürür.</span><span class="sxs-lookup"><span data-stu-id="75fcc-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="75fcc-120">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="75fcc-120">**Arguments**</span></span>

<span data-ttu-id="75fcc-121">`Single`, ,`Double`Ve .`Decimal`</span><span class="sxs-lookup"><span data-stu-id="75fcc-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="75fcc-122">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="75fcc-122">**Return Value**</span></span>

<span data-ttu-id="75fcc-123">Türü `value`.</span><span class="sxs-lookup"><span data-stu-id="75fcc-123">The type of `value`.</span></span>

<span data-ttu-id="75fcc-124">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="75fcc-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="75fcc-125">Güç (değer, üs)</span><span class="sxs-lookup"><span data-stu-id="75fcc-125">Power(value, exponent)</span></span>

<span data-ttu-id="75fcc-126">Belirtilen öğesinin `value` sonucunu belirtilen `exponent`şekilde döndürür.</span><span class="sxs-lookup"><span data-stu-id="75fcc-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="75fcc-127">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="75fcc-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="75fcc-128">`Int32, Int64, Double`, Veya`Decimal`.</span><span class="sxs-lookup"><span data-stu-id="75fcc-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="75fcc-129">Bir `Int64`, `Double`veya .`Decimal`</span><span class="sxs-lookup"><span data-stu-id="75fcc-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="75fcc-130">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="75fcc-130">**Return Value**</span></span>

<span data-ttu-id="75fcc-131">Türü `value`.</span><span class="sxs-lookup"><span data-stu-id="75fcc-131">The type of `value`.</span></span>

<span data-ttu-id="75fcc-132">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="75fcc-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="75fcc-133">Round (değer)</span><span class="sxs-lookup"><span data-stu-id="75fcc-133">Round(value)</span></span>

<span data-ttu-id="75fcc-134">Öğesinin `value`tamsayı bölümünü döndürür, en yakın tamsayıya yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="75fcc-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="75fcc-135">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="75fcc-135">**Arguments**</span></span>

<span data-ttu-id="75fcc-136">`Single`, ,`Double`Ve .`Decimal`</span><span class="sxs-lookup"><span data-stu-id="75fcc-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="75fcc-137">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="75fcc-137">**Return Value**</span></span>

<span data-ttu-id="75fcc-138">Türü `value`.</span><span class="sxs-lookup"><span data-stu-id="75fcc-138">The type of `value`.</span></span>

<span data-ttu-id="75fcc-139">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="75fcc-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="75fcc-140">Round (değer, basamak)</span><span class="sxs-lookup"><span data-stu-id="75fcc-140">Round(value, digits)</span></span>

<span data-ttu-id="75fcc-141">`value` Belirtilen`digits`en yakın değere yuvarlanır ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="75fcc-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="75fcc-142">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="75fcc-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="75fcc-143">`Double`veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="75fcc-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="75fcc-144">`Int16`veya `Int32`.</span><span class="sxs-lookup"><span data-stu-id="75fcc-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="75fcc-145">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="75fcc-145">**Return Value**</span></span>

<span data-ttu-id="75fcc-146">Türü `value`.</span><span class="sxs-lookup"><span data-stu-id="75fcc-146">The type of `value`.</span></span>

<span data-ttu-id="75fcc-147">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="75fcc-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="75fcc-148">Kes (değer, basamak)</span><span class="sxs-lookup"><span data-stu-id="75fcc-148">Truncate(value, digits)</span></span>

<span data-ttu-id="75fcc-149">`value` Belirtilen`digits`en yakın değere kesilen öğesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="75fcc-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="75fcc-150">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="75fcc-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="75fcc-151">`Double`veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="75fcc-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="75fcc-152">`Int16`veya `Int32`.</span><span class="sxs-lookup"><span data-stu-id="75fcc-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="75fcc-153">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="75fcc-153">**Return Value**</span></span>

<span data-ttu-id="75fcc-154">Türü `value`.</span><span class="sxs-lookup"><span data-stu-id="75fcc-154">The type of `value`.</span></span>

<span data-ttu-id="75fcc-155">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="75fcc-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="75fcc-156">Bu işlevler, verilen `null` `null` giriş durumunda döndürülür.</span><span class="sxs-lookup"><span data-stu-id="75fcc-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="75fcc-157">Eşdeğer işlevsellik, Microsoft SQL Istemci tarafından yönetilen sağlayıcıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="75fcc-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="75fcc-158">Daha fazla bilgi için bkz. [Entity Framework işlevleri Için SqlClient](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="75fcc-158">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75fcc-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75fcc-159">See also</span></span>

- [<span data-ttu-id="75fcc-160">Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="75fcc-160">Canonical Functions</span></span>](canonical-functions.md)
