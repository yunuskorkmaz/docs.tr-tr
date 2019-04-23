---
title: Kurallı Matematik İşlevleri
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: f575785bb198251ef50ba3563e736946253c9526
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228776"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="83921-102">Kurallı Matematik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="83921-102">Math Canonical Functions</span></span>

<span data-ttu-id="83921-103">Entity SQL aşağıdaki kurallı matematik işlevleri içerir:</span><span class="sxs-lookup"><span data-stu-id="83921-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="83921-104">Abs(Value)</span><span class="sxs-lookup"><span data-stu-id="83921-104">Abs(value)</span></span>

<span data-ttu-id="83921-105">Mutlak değerini döndürür `value`.</span><span class="sxs-lookup"><span data-stu-id="83921-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="83921-106">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="83921-106">**Arguments**</span></span>

<span data-ttu-id="83921-107">Bir `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="83921-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="83921-108">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="83921-108">**Return Value**</span></span>

<span data-ttu-id="83921-109">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="83921-109">The type of `value`.</span></span>

<span data-ttu-id="83921-110">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="83921-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="83921-111">Ceiling(Value)</span><span class="sxs-lookup"><span data-stu-id="83921-111">Ceiling(value)</span></span>

<span data-ttu-id="83921-112">Küçük olmayan en küçük tamsayı döndürür daha `value`.</span><span class="sxs-lookup"><span data-stu-id="83921-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="83921-113">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="83921-113">**Arguments**</span></span>

<span data-ttu-id="83921-114">A `Single`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="83921-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="83921-115">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="83921-115">**Return Value**</span></span>

<span data-ttu-id="83921-116">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="83921-116">The type of `value`.</span></span>

<span data-ttu-id="83921-117">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="83921-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="83921-118">Floor(Value)</span><span class="sxs-lookup"><span data-stu-id="83921-118">Floor(value)</span></span>

<span data-ttu-id="83921-119">Değerinden büyük olmayan en büyük tamsayı döndürür `value`.</span><span class="sxs-lookup"><span data-stu-id="83921-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="83921-120">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="83921-120">**Arguments**</span></span>

<span data-ttu-id="83921-121">A `Single`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="83921-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="83921-122">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="83921-122">**Return Value**</span></span>

<span data-ttu-id="83921-123">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="83921-123">The type of `value`.</span></span>

<span data-ttu-id="83921-124">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="83921-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="83921-125">Güç (değeri, üs)</span><span class="sxs-lookup"><span data-stu-id="83921-125">Power(value, exponent)</span></span>

<span data-ttu-id="83921-126">Belirtilen sonuç döndüren `value` belirtilen `exponent`.</span><span class="sxs-lookup"><span data-stu-id="83921-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="83921-127">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="83921-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="83921-128">Bir `Int32, Int64, Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="83921-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="83921-129">Bir `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="83921-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="83921-130">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="83921-130">**Return Value**</span></span>

<span data-ttu-id="83921-131">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="83921-131">The type of `value`.</span></span>

<span data-ttu-id="83921-132">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="83921-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="83921-133">Round(Value)</span><span class="sxs-lookup"><span data-stu-id="83921-133">Round(value)</span></span>

<span data-ttu-id="83921-134">Tamsayı bölümünü döndürür `value`, en yakın tamsayıya yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="83921-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="83921-135">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="83921-135">**Arguments**</span></span>

<span data-ttu-id="83921-136">A `Single`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="83921-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="83921-137">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="83921-137">**Return Value**</span></span>

<span data-ttu-id="83921-138">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="83921-138">The type of `value`.</span></span>

<span data-ttu-id="83921-139">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="83921-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="83921-140">Round (değer, basamak)</span><span class="sxs-lookup"><span data-stu-id="83921-140">Round(value, digits)</span></span>

<span data-ttu-id="83921-141">Döndürür `value`, yuvarlanır yakın belirtilen `digits`.</span><span class="sxs-lookup"><span data-stu-id="83921-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="83921-142">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="83921-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="83921-143">`Double` veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="83921-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="83921-144">`Int16` veya `Int32`.</span><span class="sxs-lookup"><span data-stu-id="83921-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="83921-145">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="83921-145">**Return Value**</span></span>

<span data-ttu-id="83921-146">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="83921-146">The type of `value`.</span></span>

<span data-ttu-id="83921-147">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="83921-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="83921-148">(Değer, basamak) Kes</span><span class="sxs-lookup"><span data-stu-id="83921-148">Truncate(value, digits)</span></span>

<span data-ttu-id="83921-149">Döndürür `value`, kesilmiş yakın belirtilen `digits`.</span><span class="sxs-lookup"><span data-stu-id="83921-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="83921-150">**Bağımsız Değişkenler**</span><span class="sxs-lookup"><span data-stu-id="83921-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="83921-151">`Double` veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="83921-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="83921-152">`Int16` veya `Int32`.</span><span class="sxs-lookup"><span data-stu-id="83921-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="83921-153">**Dönüş değeri**</span><span class="sxs-lookup"><span data-stu-id="83921-153">**Return Value**</span></span>

<span data-ttu-id="83921-154">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="83921-154">The type of `value`.</span></span>

<span data-ttu-id="83921-155">**Örnek**</span><span class="sxs-lookup"><span data-stu-id="83921-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="83921-156">Bu işlevler döndüreceği `null` verildiyse `null` giriş.</span><span class="sxs-lookup"><span data-stu-id="83921-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="83921-157">Microsoft SQL istemci yönetilen sağlayıcısında eşdeğer bir işlevselliği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="83921-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="83921-158">Daha fazla bilgi için [Entity Framework işlevleri için SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="83921-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83921-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83921-159">See also</span></span>

- [<span data-ttu-id="83921-160">Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="83921-160">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
