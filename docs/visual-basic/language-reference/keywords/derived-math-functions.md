---
description: 'Daha fazla bilgi edinin: türetilmiş matematik Işlevleri (Visual Basic)'
title: Türetilen Matematik İşlevleri
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operations, derived math functions
- cosecant function
- arcsecant function
- arccotangent function
- functions [Visual Basic], derived math functions
- inverse functions
- math functions, derived
- derived math functions
- cotangent function
- angles
- secant function
- trigonometric functions
- logarithms
- arccosecant function
- hyperbolic functions
- arcsine function
- degrees
- arccosine function
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
ms.openlocfilehash: daaed1312f08cecc0c68af0e36d574424fc526a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730778"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="d0c04-103">Türetilen Matematik İşlevleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0c04-103">Derived Math Functions (Visual Basic)</span></span>

<span data-ttu-id="d0c04-104">Aşağıdaki tabloda, nesnenin iç matematik işlevlerinden türetilebilecek iç olmayan matematik işlevleri gösterilmektedir <xref:System.Math?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d0c04-104">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="d0c04-105">Dosyanıza veya projenize ekleyerek iç matematik işlevlerine erişebilirsiniz `Imports System.Math` .</span><span class="sxs-lookup"><span data-stu-id="d0c04-105">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="d0c04-106">İşlev</span><span class="sxs-lookup"><span data-stu-id="d0c04-106">Function</span></span>|<span data-ttu-id="d0c04-107">Türetilmiş eşdeğerleri</span><span class="sxs-lookup"><span data-stu-id="d0c04-107">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="d0c04-108">Sekant (sn (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-108">Secant (Sec(x))</span></span>|<span data-ttu-id="d0c04-109">1/cos (x)</span><span class="sxs-lookup"><span data-stu-id="d0c04-109">1 / Cos(x)</span></span>|  
|<span data-ttu-id="d0c04-110">Kosekant (CSC (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-110">Cosecant (Csc(x))</span></span>|<span data-ttu-id="d0c04-111">1/sin (x)</span><span class="sxs-lookup"><span data-stu-id="d0c04-111">1 / Sin(x)</span></span>|  
|<span data-ttu-id="d0c04-112">Kotanjant (Ctan (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-112">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="d0c04-113">1/tan (x)</span><span class="sxs-lookup"><span data-stu-id="d0c04-113">1 / Tan(x)</span></span>|  
|<span data-ttu-id="d0c04-114">Ters Sinüs (asin (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-114">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="d0c04-115">Atan (x/sqrt (-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="d0c04-115">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="d0c04-116">Ters kosinüs (ACOS (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-116">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="d0c04-117">Atan (-x/sqrt (-x \* x + 1)) + 2 \* atan (1)</span><span class="sxs-lookup"><span data-stu-id="d0c04-117">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="d0c04-118">Ters Sekant (ASEC (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-118">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="d0c04-119">2 \* atan (1) – atan (Imzala (x)/sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="d0c04-119">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="d0c04-120">Ters kosekant (ACSC (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-120">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="d0c04-121">Atan (x)/sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="d0c04-121">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="d0c04-122">Ters Kotanjant (ACOT (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-122">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="d0c04-123">2 \* atan (1)-atan (x)</span><span class="sxs-lookup"><span data-stu-id="d0c04-123">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="d0c04-124">Hiperbolik sinüs (sinh (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-124">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="d0c04-125">(EXP (x) – exp (-x))/2</span><span class="sxs-lookup"><span data-stu-id="d0c04-125">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="d0c04-126">Hiperbolik kosinüs (cosh (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-126">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="d0c04-127">(EXP (x) + exp (-x))/2</span><span class="sxs-lookup"><span data-stu-id="d0c04-127">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="d0c04-128">Hiperbolik tanjant (tanh (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-128">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="d0c04-129">(EXP (x) – exp (-x))/(EXP (x) + exp (-x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-129">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="d0c04-130">Hiperbolik Sekant (sech (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-130">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="d0c04-131">2/(EXP (x) + exp (-x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-131">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="d0c04-132">Hiperbolik kosekant (Csch (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-132">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="d0c04-133">2/(EXP (x) – exp (-x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-133">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="d0c04-134">Hiperbolik Kotanjant (Coth (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-134">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="d0c04-135">(EXP (x) + exp (-x))/(EXP (x) – exp (-x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-135">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="d0c04-136">Ters hiperbolik sinüs (ASİNH (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-136">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="d0c04-137">Günlük (x + sqrt (x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="d0c04-137">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="d0c04-138">Ters hiperbolik kosinüs (ACOSH (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-138">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="d0c04-139">Günlük (x + sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="d0c04-139">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="d0c04-140">Ters hiperbolik tanjant (ATANH (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-140">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="d0c04-141">Günlük ((1 + x)/(1 – x))/2</span><span class="sxs-lookup"><span data-stu-id="d0c04-141">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="d0c04-142">Ters Hiperbolik Sekant (AsecH (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-142">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="d0c04-143">Günlük ((sqrt (-x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="d0c04-143">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="d0c04-144">Ters hiperbolik kosekant (Acsch (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-144">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="d0c04-145">Log (((x) \* sqrt (x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="d0c04-145">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="d0c04-146">Ters hiperbolik Kotanjant (Acoth (x))</span><span class="sxs-lookup"><span data-stu-id="d0c04-146">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="d0c04-147">Günlük ((x + 1)/(x – 1))/2</span><span class="sxs-lookup"><span data-stu-id="d0c04-147">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0c04-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0c04-148">See also</span></span>

- [<span data-ttu-id="d0c04-149">Matematik Işlevleri</span><span class="sxs-lookup"><span data-stu-id="d0c04-149">Math Functions</span></span>](../functions/math-functions.md)
