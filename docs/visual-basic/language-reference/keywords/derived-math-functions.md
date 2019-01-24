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
ms.openlocfilehash: 1273871faf65afdd1a894c03f13a2c93507c1b13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505867"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="cd0f1-102">Türetilen Matematik İşlevleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd0f1-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="cd0f1-103">Aşağıdaki tablo iç matematik işlevleri türetilmiş iç olmayan matematik işlevleri gösterir <xref:System.Math?displayProperty=nameWithType> nesne.</span><span class="sxs-lookup"><span data-stu-id="cd0f1-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="cd0f1-104">Gerçek matematik işlevleri ekleyerek erişebileceğiniz `Imports System.Math` dosyası veya proje için.</span><span class="sxs-lookup"><span data-stu-id="cd0f1-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="cd0f1-105">İşlev</span><span class="sxs-lookup"><span data-stu-id="cd0f1-105">Function</span></span>|<span data-ttu-id="cd0f1-106">Türetilmiş eşdeğerleri</span><span class="sxs-lookup"><span data-stu-id="cd0f1-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="cd0f1-107">Secant (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-107">Secant (Sec(x))</span></span>|<span data-ttu-id="cd0f1-108">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="cd0f1-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="cd0f1-109">Cosecant (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="cd0f1-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="cd0f1-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="cd0f1-111">Kotanjantını (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="cd0f1-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="cd0f1-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="cd0f1-113">Ters sinüsünü (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="cd0f1-114">Atan(x / Sqrt(-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="cd0f1-115">Ters kosinüsünü (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="cd0f1-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="cd0f1-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="cd0f1-117">Ters secant (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="cd0f1-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="cd0f1-119">Ters cosecant (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="cd0f1-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="cd0f1-121">Ark kotanjantını (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="cd0f1-122">2 \* Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="cd0f1-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="cd0f1-123">Hiperbolik sinüs (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="cd0f1-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="cd0f1-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="cd0f1-125">Hiperbolik kosinüsü (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="cd0f1-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="cd0f1-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="cd0f1-127">Hiperbolik tanjantı (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="cd0f1-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="cd0f1-129">Hiperbolik secant (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="cd0f1-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="cd0f1-131">Hiperbolik cosecant (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="cd0f1-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="cd0f1-133">Hiperbolik kotanjantını (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="cd0f1-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="cd0f1-135">Ters hiperbolik sinüs (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="cd0f1-136">Log(x + Sqrt(x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="cd0f1-137">Ters hiperbolik kosinüsü (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="cd0f1-138">Log(x + Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="cd0f1-139">Ters hiperbolik tanjantı (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="cd0f1-140">Günlük ((1 + x) / (1: x)) / 2</span><span class="sxs-lookup"><span data-stu-id="cd0f1-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="cd0f1-141">Ters hiperbolik secant (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="cd0f1-142">Günlük ((Sqrt (-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="cd0f1-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="cd0f1-143">Ters hiperbolik cosecant (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="cd0f1-144">Log((Sign(x) \* Sqrt (x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="cd0f1-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="cd0f1-145">Ters hiperbolik kotanjantını (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="cd0f1-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="cd0f1-146">Günlük ((x + 1) / (x – 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="cd0f1-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd0f1-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd0f1-147">See also</span></span>
- [<span data-ttu-id="cd0f1-148">Matematik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="cd0f1-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
