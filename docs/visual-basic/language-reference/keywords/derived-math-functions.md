---
title: "Türetilen Matematik İşlevleri (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5816fa4c8c384eca116fa1512950a3588c6e3392
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="a2ba7-102">Türetilen Matematik İşlevleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2ba7-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="a2ba7-103">Aşağıdaki tabloda iç matematik işlevlerden türetilebilir iç olmayan matematik işlevleri gösterilmektedir <xref:System.Math?displayProperty=nameWithType> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a2ba7-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="a2ba7-104">İç matematik işlevleri ekleyerek erişebilirsiniz `Imports System.Math` dosya veya projesi.</span><span class="sxs-lookup"><span data-stu-id="a2ba7-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="a2ba7-105">İşlev</span><span class="sxs-lookup"><span data-stu-id="a2ba7-105">Function</span></span>|<span data-ttu-id="a2ba7-106">Türetilen eşdeğerleri</span><span class="sxs-lookup"><span data-stu-id="a2ba7-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="a2ba7-107">Secant (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-107">Secant (Sec(x))</span></span>|<span data-ttu-id="a2ba7-108">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="a2ba7-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="a2ba7-109">Cosecant (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="a2ba7-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="a2ba7-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="a2ba7-111">Kotanjant (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="a2ba7-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="a2ba7-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="a2ba7-113">Ters sinüsünü (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="a2ba7-114">Atan (x / Sqrt (-x * x + 1))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-114">Atan(x / Sqrt(-x * x + 1))</span></span>|  
|<span data-ttu-id="a2ba7-115">Ters kosinüsünü (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="a2ba7-116">Atan (-x / Sqrt (-x * x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="a2ba7-116">Atan(-x / Sqrt(-x * x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="a2ba7-117">Ters secant (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="a2ba7-118">2 * Atan(1) – Atan(Sign(x) / Sqrt (x \* x-1))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-118">2 * Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="a2ba7-119">Ters cosecant (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="a2ba7-120">Atan(Sign(x) / Sqrt (x * x-1))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-120">Atan(Sign(x) / Sqrt(x * x – 1))</span></span>|  
|<span data-ttu-id="a2ba7-121">Ters Kotanjant (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="a2ba7-122">2 * Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="a2ba7-122">2 * Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="a2ba7-123">Hiperbolik sinüsü (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="a2ba7-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="a2ba7-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="a2ba7-125">Hiperbolik kosinüsünü (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="a2ba7-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="a2ba7-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="a2ba7-127">Hiperbolik tanjantı (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="a2ba7-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="a2ba7-129">Hiperbolik secant (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="a2ba7-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="a2ba7-131">Hiperbolik cosecant (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="a2ba7-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="a2ba7-133">Hiperbolik kotanjantını (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="a2ba7-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="a2ba7-135">Ters hiperbolik sinüs (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="a2ba7-136">Günlük (x + Sqrt (x * x + 1))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-136">Log(x + Sqrt(x * x + 1))</span></span>|  
|<span data-ttu-id="a2ba7-137">Ters hiperbolik Kosinüs (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="a2ba7-138">Günlük (x + Sqrt (x * x-1))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-138">Log(x + Sqrt(x * x – 1))</span></span>|  
|<span data-ttu-id="a2ba7-139">Ters hiperbolik tanjant (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="a2ba7-140">Günlük ((1 + x) / (1-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="a2ba7-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="a2ba7-141">Ters hiperbolik secant (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="a2ba7-142">Günlük ((Sqrt (-x * x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="a2ba7-142">Log((Sqrt(-x * x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="a2ba7-143">Ters hiperbolik cosecant (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="a2ba7-144">Log((Sign(x) * Sqrtsqrt (x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="a2ba7-144">Log((Sign(x) * Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="a2ba7-145">Ters hiperbolik kotanjantını (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="a2ba7-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="a2ba7-146">Günlük ((x + 1) / (x-1)) / 2</span><span class="sxs-lookup"><span data-stu-id="a2ba7-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2ba7-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2ba7-147">See Also</span></span>  
 [<span data-ttu-id="a2ba7-148">Matematik işlevleri</span><span class="sxs-lookup"><span data-stu-id="a2ba7-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
