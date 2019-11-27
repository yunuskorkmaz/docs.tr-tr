---
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
ms.openlocfilehash: 73cf56dd72f2baac0474d6f5c4e88228a1fe38cf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349847"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="3174c-102">Türetilen Matematik İşlevleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3174c-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="3174c-103">Aşağıdaki tabloda, <xref:System.Math?displayProperty=nameWithType> nesnesinin iç matematik işlevlerinden türetilebilecek iç olmayan matematik işlevleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3174c-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="3174c-104">Dosyanıza veya projenize `Imports System.Math` ekleyerek iç matematik işlevlerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3174c-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="3174c-105">İşlev</span><span class="sxs-lookup"><span data-stu-id="3174c-105">Function</span></span>|<span data-ttu-id="3174c-106">Türetilmiş eşdeğerleri</span><span class="sxs-lookup"><span data-stu-id="3174c-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="3174c-107">Sekant (sn (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-107">Secant (Sec(x))</span></span>|<span data-ttu-id="3174c-108">1/cos (x)</span><span class="sxs-lookup"><span data-stu-id="3174c-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="3174c-109">Kosekant (CSC (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="3174c-110">1/sin (x)</span><span class="sxs-lookup"><span data-stu-id="3174c-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="3174c-111">Kotanjant (Ctan (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="3174c-112">1/tan (x)</span><span class="sxs-lookup"><span data-stu-id="3174c-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="3174c-113">Ters Sinüs (asin (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="3174c-114">Atan (x/sqrt (-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="3174c-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="3174c-115">Ters kosinüs (ACOS (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="3174c-116">Atan (-x/sqrt (-x \* x + 1)) + 2 \* atan (1)</span><span class="sxs-lookup"><span data-stu-id="3174c-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="3174c-117">Ters Sekant (ASEC (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="3174c-118">2 \* atan (1) – atan (Imzala (x)/sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="3174c-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="3174c-119">Ters kosekant (ACSC (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="3174c-120">Atan (x)/sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="3174c-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="3174c-121">Ters Kotanjant (ACOT (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="3174c-122">2 \* atan (1)-atan (x)</span><span class="sxs-lookup"><span data-stu-id="3174c-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="3174c-123">Hiperbolik sinüs (sinh (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="3174c-124">(EXP (x) – exp (-x))/2</span><span class="sxs-lookup"><span data-stu-id="3174c-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="3174c-125">Hiperbolik kosinüs (cosh (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="3174c-126">(EXP (x) + exp (-x))/2</span><span class="sxs-lookup"><span data-stu-id="3174c-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="3174c-127">Hiperbolik tanjant (tanh (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="3174c-128">(EXP (x) – exp (-x))/(EXP (x) + exp (-x))</span><span class="sxs-lookup"><span data-stu-id="3174c-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="3174c-129">Hiperbolik Sekant (sech (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="3174c-130">2/(EXP (x) + exp (-x))</span><span class="sxs-lookup"><span data-stu-id="3174c-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="3174c-131">Hiperbolik kosekant (Csch (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="3174c-132">2/(EXP (x) – exp (-x))</span><span class="sxs-lookup"><span data-stu-id="3174c-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="3174c-133">Hiperbolik Kotanjant (Coth (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="3174c-134">(EXP (x) + exp (-x))/(EXP (x) – exp (-x))</span><span class="sxs-lookup"><span data-stu-id="3174c-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="3174c-135">Ters hiperbolik sinüs (ASİNH (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="3174c-136">Günlük (x + sqrt (x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="3174c-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="3174c-137">Ters hiperbolik kosinüs (ACOSH (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="3174c-138">Günlük (x + sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="3174c-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="3174c-139">Ters hiperbolik tanjant (ATANH (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="3174c-140">Günlük ((1 + x)/(1 – x))/2</span><span class="sxs-lookup"><span data-stu-id="3174c-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="3174c-141">Ters Hiperbolik Sekant (AsecH (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="3174c-142">Günlük ((sqrt (-x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="3174c-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="3174c-143">Ters hiperbolik kosekant (Acsch (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="3174c-144">Log (((x) \* sqrt (x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="3174c-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="3174c-145">Ters hiperbolik Kotanjant (Acoth (x))</span><span class="sxs-lookup"><span data-stu-id="3174c-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="3174c-146">Günlük ((x + 1)/(x – 1))/2</span><span class="sxs-lookup"><span data-stu-id="3174c-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3174c-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3174c-147">See also</span></span>

- [<span data-ttu-id="3174c-148">Matematik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3174c-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
