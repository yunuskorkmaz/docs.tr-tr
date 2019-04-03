---
title: Türetilen Matematik İşlevleri (Visual Basic)
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
ms.openlocfilehash: 0d0606c52d1d50fcc2fd8eea3ad2851c95b18a69
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836590"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="ffcb2-102">Türetilen Matematik İşlevleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ffcb2-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="ffcb2-103">Aşağıdaki tablo iç matematik işlevleri türetilmiş iç olmayan matematik işlevleri gösterir <xref:System.Math?displayProperty=nameWithType> nesne.</span><span class="sxs-lookup"><span data-stu-id="ffcb2-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="ffcb2-104">Gerçek matematik işlevleri ekleyerek erişebileceğiniz `Imports System.Math` dosyası veya proje için.</span><span class="sxs-lookup"><span data-stu-id="ffcb2-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="ffcb2-105">İşlev</span><span class="sxs-lookup"><span data-stu-id="ffcb2-105">Function</span></span>|<span data-ttu-id="ffcb2-106">Türetilmiş eşdeğerleri</span><span class="sxs-lookup"><span data-stu-id="ffcb2-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="ffcb2-107">Secant (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-107">Secant (Sec(x))</span></span>|<span data-ttu-id="ffcb2-108">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="ffcb2-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="ffcb2-109">Cosecant (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="ffcb2-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="ffcb2-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="ffcb2-111">Kotanjantını (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="ffcb2-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="ffcb2-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="ffcb2-113">Ters sinüsünü (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="ffcb2-114">Atan(x / Sqrt(-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="ffcb2-115">Ters kosinüsünü (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="ffcb2-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="ffcb2-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="ffcb2-117">Ters secant (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="ffcb2-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="ffcb2-119">Ters cosecant (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="ffcb2-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="ffcb2-121">Ark kotanjantını (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="ffcb2-122">2 \* Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="ffcb2-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="ffcb2-123">Hiperbolik sinüs (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="ffcb2-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="ffcb2-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="ffcb2-125">Hiperbolik kosinüsü (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="ffcb2-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="ffcb2-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="ffcb2-127">Hiperbolik tanjantı (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="ffcb2-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="ffcb2-129">Hiperbolik secant (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="ffcb2-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="ffcb2-131">Hiperbolik cosecant (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="ffcb2-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="ffcb2-133">Hiperbolik kotanjantını (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="ffcb2-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="ffcb2-135">Ters hiperbolik sinüs (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="ffcb2-136">Log(x + Sqrt(x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="ffcb2-137">Ters hiperbolik kosinüsü (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="ffcb2-138">Log(x + Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="ffcb2-139">Ters hiperbolik tanjantı (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="ffcb2-140">Günlük ((1 + x) / (1: x)) / 2</span><span class="sxs-lookup"><span data-stu-id="ffcb2-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="ffcb2-141">Ters hiperbolik secant (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="ffcb2-142">Günlük ((Sqrt (-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="ffcb2-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="ffcb2-143">Ters hiperbolik cosecant (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="ffcb2-144">Log((Sign(x) \* Sqrt (x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="ffcb2-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="ffcb2-145">Ters hiperbolik kotanjantını (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="ffcb2-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="ffcb2-146">Günlük ((x + 1) / (x – 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="ffcb2-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ffcb2-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffcb2-147">See also</span></span>

- [<span data-ttu-id="ffcb2-148">Matematik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ffcb2-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
