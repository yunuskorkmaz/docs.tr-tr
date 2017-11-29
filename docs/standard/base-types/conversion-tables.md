---
title: ".NET tür dönüştürme tabloları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- widening conversions
- narrowing conversions
- type conversion, table
- converting types, narrowing conversions
- converting types, widening conversions
- base types, converting
- tables [.NET Framework], type conversions
- data types [.NET Framework], converting
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 327469f9a151b6ef7e1c42f6669c0a9dae7016fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="type-conversion-tables-in-net"></a><span data-ttu-id="b5403-102">.NET tür dönüştürme tabloları</span><span class="sxs-lookup"><span data-stu-id="b5403-102">Type Conversion Tables in .NET</span></span>
<span data-ttu-id="b5403-103">Bir türde bir değer eşit veya daha büyük boyutta başka bir türüne dönüştürülürken dönüştürme genişletme oluşur.</span><span class="sxs-lookup"><span data-stu-id="b5403-103">Widening conversion occurs when a value of one type is converted to another type that is of equal or greater size.</span></span> <span data-ttu-id="b5403-104">Bir türde bir değer daha küçük bir boyuta sahiptir başka bir türdeki bir değere dönüştürüldüğünde daraltma dönüşümü gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="b5403-104">A narrowing conversion occurs when a value of one type is converted to a value of another type that is of a smaller size.</span></span> <span data-ttu-id="b5403-105">Bu konuda tablolarda her iki tür dönüşümleri tarafından sergilenen davranışları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b5403-105">The tables in this topic illustrate the behaviors exhibited by both types of conversions.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="b5403-106">Dönüştürmeleri Genişletme</span><span class="sxs-lookup"><span data-stu-id="b5403-106">Widening Conversions</span></span>  
 <span data-ttu-id="b5403-107">Aşağıdaki tabloda bilgi kaybı olmadan gerçekleştirilebilir genişletme dönüşümleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b5403-107">The following table describes the widening conversions that can be performed without the loss of information.</span></span>  
  
|<span data-ttu-id="b5403-108">Tür</span><span class="sxs-lookup"><span data-stu-id="b5403-108">Type</span></span>|<span data-ttu-id="b5403-109">Veri kaybı olmadan dönüştürülebilir</span><span class="sxs-lookup"><span data-stu-id="b5403-109">Can be converted without data loss to</span></span>|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<span data-ttu-id="b5403-110"><xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="b5403-110"><xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.SByte>|<span data-ttu-id="b5403-111"><xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="b5403-111"><xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="b5403-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="b5403-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="b5403-113"><xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="b5403-113"><xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Char>|<span data-ttu-id="b5403-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="b5403-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="b5403-115"><xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="b5403-115"><xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="b5403-116"><xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="b5403-116"><xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 <span data-ttu-id="b5403-117">Bazı dönüşümleri <xref:System.Single> veya <xref:System.Double> duyarlık kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5403-117">Some widening conversions to <xref:System.Single> or <xref:System.Double> can cause a loss of precision.</span></span> <span data-ttu-id="b5403-118">Aşağıdaki tabloda, bazen bilgi kaybına neden genişletme dönüşümleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b5403-118">The following table describes the widening conversions that sometimes result in a loss of information.</span></span>  
  
|<span data-ttu-id="b5403-119">Tür</span><span class="sxs-lookup"><span data-stu-id="b5403-119">Type</span></span>|<span data-ttu-id="b5403-120">Dönüştürülebilir</span><span class="sxs-lookup"><span data-stu-id="b5403-120">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<span data-ttu-id="b5403-121"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="b5403-121"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="b5403-122"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="b5403-122"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="b5403-123"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="b5403-123"><xref:System.Single>, <xref:System.Double></span></span>|  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="b5403-124">Daraltma dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="b5403-124">Narrowing Conversions</span></span>  
 <span data-ttu-id="b5403-125">Daraltma dönüştürmeye <xref:System.Single> veya <xref:System.Double> bilgi kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5403-125">A narrowing conversion to <xref:System.Single> or <xref:System.Double> can cause a loss of information.</span></span> <span data-ttu-id="b5403-126">Hedef türü sorununun kaynağının düzgün bir şekilde express olamaz, elde edilen türü sabite ayarlanır `PositiveInfinity` veya `NegativeInfinity`.</span><span class="sxs-lookup"><span data-stu-id="b5403-126">If the target type cannot properly express the magnitude of the source, the resulting type is set to the constant `PositiveInfinity` or `NegativeInfinity`.</span></span> <span data-ttu-id="b5403-127">`PositiveInfinity`sonuçları sıfıra pozitif bir sayı bölen ve ne zaman da döndürülür değerini bir <xref:System.Single> veya <xref:System.Double> değerini aşıyor `MaxValue` alan.</span><span class="sxs-lookup"><span data-stu-id="b5403-127">`PositiveInfinity` results from dividing a positive number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> exceeds the value of the `MaxValue` field.</span></span> <span data-ttu-id="b5403-128">`NegativeInfinity`sonuçları sıfıra negatif bir sayı bölen ve ne zaman da döndürülür değerini bir <xref:System.Single> veya <xref:System.Double> değerin altına düşerse `MinValue` alan.</span><span class="sxs-lookup"><span data-stu-id="b5403-128">`NegativeInfinity` results from dividing a negative number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> falls below the value of the `MinValue` field.</span></span> <span data-ttu-id="b5403-129">Bir dönüştürme bir <xref:System.Double> için bir <xref:System.Single> sonuçlanabilir `PositiveInfinity` veya `NegativeInfinity`.</span><span class="sxs-lookup"><span data-stu-id="b5403-129">A conversion from a <xref:System.Double> to a <xref:System.Single> might result in `PositiveInfinity` or `NegativeInfinity`.</span></span>  
  
 <span data-ttu-id="b5403-130">Daraltma dönüşümü ayrıca diğer veri türleri için bilgi kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5403-130">A narrowing conversion can also result in a loss of information for other data types.</span></span> <span data-ttu-id="b5403-131">Ancak, bir <xref:System.OverflowException> dönüştürülecek bir türü değeri hedef tür tarafından belirtilen aralığın dışında kalırsa durum `MaxValue` ve `MinValue` alanları ve dönüştürme hedef değerini emin olmak için çalışma zamanı tarafından denetlenir aşmayan türü kendi `MaxValue` veya `MinValue`.</span><span class="sxs-lookup"><span data-stu-id="b5403-131">However, an <xref:System.OverflowException> is thrown if the value of a type that is being converted falls outside of the range specified by the target type's `MaxValue` and `MinValue` fields, and the conversion is checked by the runtime to ensure that the value of the target type does not exceed its `MaxValue` or `MinValue`.</span></span> <span data-ttu-id="b5403-132">İle gerçekleştirilen dönüşümleri <xref:System.Convert?displayProperty=nameWithType> sınıfı bu şekilde her zaman denetlenir.</span><span class="sxs-lookup"><span data-stu-id="b5403-132">Conversions that are performed with the <xref:System.Convert?displayProperty=nameWithType> class are always checked in this manner.</span></span>  
  
 <span data-ttu-id="b5403-133">Throw dönüşümleri aşağıdaki tabloda bir <xref:System.OverflowException> kullanarak <xref:System.Convert?displayProperty=nameWithType> veya dönüştürülecek türü değeri elde edilen türü tanımlı aralığın dışında ise herhangi bir dönüştürme denetledi.</span><span class="sxs-lookup"><span data-stu-id="b5403-133">The following table lists conversions that throw an <xref:System.OverflowException> using <xref:System.Convert?displayProperty=nameWithType> or any checked conversion if the value of the type being converted is outside the defined range of the resulting type.</span></span>  
  
|<span data-ttu-id="b5403-134">Tür</span><span class="sxs-lookup"><span data-stu-id="b5403-134">Type</span></span>|<span data-ttu-id="b5403-135">Dönüştürülebilir</span><span class="sxs-lookup"><span data-stu-id="b5403-135">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<span data-ttu-id="b5403-136"><xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="b5403-136"><xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="b5403-137"><xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16></span><span class="sxs-lookup"><span data-stu-id="b5403-137"><xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="b5403-138"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16></span><span class="sxs-lookup"><span data-stu-id="b5403-138"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="b5403-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span><span class="sxs-lookup"><span data-stu-id="b5403-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="b5403-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="b5403-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span></span>|  
|<xref:System.Int64>|<span data-ttu-id="b5403-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="b5403-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="b5403-142"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64></span><span class="sxs-lookup"><span data-stu-id="b5403-142"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="b5403-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="b5403-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Single>|<span data-ttu-id="b5403-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="b5403-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Double>|<span data-ttu-id="b5403-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="b5403-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5403-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5403-146">See Also</span></span>  
 <xref:System.Convert?displayProperty=nameWithType>  
 [<span data-ttu-id="b5403-147">.NET tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="b5403-147">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)
