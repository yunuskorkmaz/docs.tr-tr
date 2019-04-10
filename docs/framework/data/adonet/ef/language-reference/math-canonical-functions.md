---
title: Kurallı Matematik İşlevleri
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: f575785bb198251ef50ba3563e736946253c9526
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228776"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="66e76-102">Kurallı Matematik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="66e76-102">Math Canonical Functions</span></span>

<span data-ttu-id="66e76-103">Entity SQL aşağıdaki kurallı matematik işlevleri içerir:</span><span class="sxs-lookup"><span data-stu-id="66e76-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="66e76-104">Abs(Value)</span><span class="sxs-lookup"><span data-stu-id="66e76-104">Abs(value)</span></span>

<span data-ttu-id="66e76-105">Mutlak değerini döndürür `value`.</span><span class="sxs-lookup"><span data-stu-id="66e76-105">Returns the absolute value of `value`.</span></span>

**<span data-ttu-id="66e76-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="66e76-106">Arguments</span></span>**

<span data-ttu-id="66e76-107">Bir `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="66e76-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

**<span data-ttu-id="66e76-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="66e76-108">Return Value</span></span>**

<span data-ttu-id="66e76-109">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="66e76-109">The type of `value`.</span></span>

**<span data-ttu-id="66e76-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="66e76-110">Example</span></span>**

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="66e76-111">Ceiling(Value)</span><span class="sxs-lookup"><span data-stu-id="66e76-111">Ceiling(value)</span></span>

<span data-ttu-id="66e76-112">Küçük olmayan en küçük tamsayı döndürür daha `value`.</span><span class="sxs-lookup"><span data-stu-id="66e76-112">Returns the smallest integer that is not less than `value`.</span></span>

**<span data-ttu-id="66e76-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="66e76-113">Arguments</span></span>**

<span data-ttu-id="66e76-114">A `Single`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="66e76-114">A `Single`, `Double`, and `Decimal`.</span></span>

**<span data-ttu-id="66e76-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="66e76-115">Return Value</span></span>**

<span data-ttu-id="66e76-116">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="66e76-116">The type of `value`.</span></span>

**<span data-ttu-id="66e76-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="66e76-117">Example</span></span>**

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="66e76-118">Floor(Value)</span><span class="sxs-lookup"><span data-stu-id="66e76-118">Floor(value)</span></span>

<span data-ttu-id="66e76-119">Değerinden büyük olmayan en büyük tamsayı döndürür `value`.</span><span class="sxs-lookup"><span data-stu-id="66e76-119">Returns the largest integer that is not greater than `value`.</span></span>

**<span data-ttu-id="66e76-120">Arguments</span><span class="sxs-lookup"><span data-stu-id="66e76-120">Arguments</span></span>**

<span data-ttu-id="66e76-121">A `Single`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="66e76-121">A `Single`, `Double`, and `Decimal`.</span></span>

**<span data-ttu-id="66e76-122">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="66e76-122">Return Value</span></span>**

<span data-ttu-id="66e76-123">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="66e76-123">The type of `value`.</span></span>

**<span data-ttu-id="66e76-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="66e76-124">Example</span></span>**

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="66e76-125">Güç (değeri, üs)</span><span class="sxs-lookup"><span data-stu-id="66e76-125">Power(value, exponent)</span></span>

<span data-ttu-id="66e76-126">Belirtilen sonuç döndüren `value` belirtilen `exponent`.</span><span class="sxs-lookup"><span data-stu-id="66e76-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

**<span data-ttu-id="66e76-127">Arguments</span><span class="sxs-lookup"><span data-stu-id="66e76-127">Arguments</span></span>**

|  |  |
|--|--|
|`value` | <span data-ttu-id="66e76-128">Bir `Int32, Int64, Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="66e76-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="66e76-129">Bir `Int64`, `Double`, veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="66e76-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

**<span data-ttu-id="66e76-130">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="66e76-130">Return Value</span></span>**

<span data-ttu-id="66e76-131">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="66e76-131">The type of `value`.</span></span>

**<span data-ttu-id="66e76-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="66e76-132">Example</span></span>**

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="66e76-133">Round(Value)</span><span class="sxs-lookup"><span data-stu-id="66e76-133">Round(value)</span></span>

<span data-ttu-id="66e76-134">Tamsayı bölümünü döndürür `value`, en yakın tamsayıya yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="66e76-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

**<span data-ttu-id="66e76-135">Arguments</span><span class="sxs-lookup"><span data-stu-id="66e76-135">Arguments</span></span>**

<span data-ttu-id="66e76-136">A `Single`, `Double`, ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="66e76-136">A `Single`, `Double`, and `Decimal`.</span></span>

**<span data-ttu-id="66e76-137">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="66e76-137">Return Value</span></span>**

<span data-ttu-id="66e76-138">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="66e76-138">The type of `value`.</span></span>

**<span data-ttu-id="66e76-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="66e76-139">Example</span></span>**

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="66e76-140">Round (değer, basamak)</span><span class="sxs-lookup"><span data-stu-id="66e76-140">Round(value, digits)</span></span>

<span data-ttu-id="66e76-141">Döndürür `value`, yuvarlanır yakın belirtilen `digits`.</span><span class="sxs-lookup"><span data-stu-id="66e76-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

**<span data-ttu-id="66e76-142">Arguments</span><span class="sxs-lookup"><span data-stu-id="66e76-142">Arguments</span></span>**

|  |  |
|--|--|
|`value`|`Double` <span data-ttu-id="66e76-143">veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="66e76-143">or `Decimal`.</span></span>|
|`digits`|`Int16` <span data-ttu-id="66e76-144">veya `Int32`.</span><span class="sxs-lookup"><span data-stu-id="66e76-144">or `Int32`.</span></span>|

**<span data-ttu-id="66e76-145">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="66e76-145">Return Value</span></span>**

<span data-ttu-id="66e76-146">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="66e76-146">The type of `value`.</span></span>

**<span data-ttu-id="66e76-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="66e76-147">Example</span></span>**

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="66e76-148">(Değer, basamak) Kes</span><span class="sxs-lookup"><span data-stu-id="66e76-148">Truncate(value, digits)</span></span>

<span data-ttu-id="66e76-149">Döndürür `value`, kesilmiş yakın belirtilen `digits`.</span><span class="sxs-lookup"><span data-stu-id="66e76-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

**<span data-ttu-id="66e76-150">Arguments</span><span class="sxs-lookup"><span data-stu-id="66e76-150">Arguments</span></span>**

|  |  |
|--|--|
|`value`|`Double` <span data-ttu-id="66e76-151">veya `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="66e76-151">or `Decimal`.</span></span>|
|`digits`|`Int16` <span data-ttu-id="66e76-152">veya `Int32`.</span><span class="sxs-lookup"><span data-stu-id="66e76-152">or `Int32`.</span></span>|

**<span data-ttu-id="66e76-153">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="66e76-153">Return Value</span></span>**

<span data-ttu-id="66e76-154">Türünü `value`.</span><span class="sxs-lookup"><span data-stu-id="66e76-154">The type of `value`.</span></span>

**<span data-ttu-id="66e76-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="66e76-155">Example</span></span>**

`Truncate(748.58,1)`  
  
 <span data-ttu-id="66e76-156">Bu işlevler döndüreceği `null` verildiyse `null` giriş.</span><span class="sxs-lookup"><span data-stu-id="66e76-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="66e76-157">Microsoft SQL istemci yönetilen sağlayıcısında eşdeğer bir işlevselliği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66e76-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="66e76-158">Daha fazla bilgi için [Entity Framework işlevleri için SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="66e76-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e76-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66e76-159">See also</span></span>

- [<span data-ttu-id="66e76-160">Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="66e76-160">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
