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
ms.openlocfilehash: f84b1ef18ef2a924bb2e47da85ecbb51f982873a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869023"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="d0609-102">Türetilen Matematik İşlevleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0609-102">Derived Math Functions (Visual Basic)</span></span>

<span data-ttu-id="d0609-103">Aşağıdaki tabloda, nesnenin iç matematik işlevlerinden türetilebilecek iç olmayan matematik işlevleri gösterilmektedir <xref:System.Math?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d0609-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="d0609-104">Dosyanıza veya projenize ekleyerek iç matematik işlevlerine erişebilirsiniz `Imports System.Math` .</span><span class="sxs-lookup"><span data-stu-id="d0609-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="d0609-105">İşlev</span><span class="sxs-lookup"><span data-stu-id="d0609-105">Function</span></span>|<span data-ttu-id="d0609-106">Türetilmiş eşdeğerleri</span><span class="sxs-lookup"><span data-stu-id="d0609-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="d0609-107">Sekant (sn (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-107">Secant (Sec(x))</span></span>|<span data-ttu-id="d0609-108">1/cos (x)</span><span class="sxs-lookup"><span data-stu-id="d0609-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="d0609-109">Kosekant (CSC (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="d0609-110">1/sin (x)</span><span class="sxs-lookup"><span data-stu-id="d0609-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="d0609-111">Kotanjant (Ctan (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="d0609-112">1/tan (x)</span><span class="sxs-lookup"><span data-stu-id="d0609-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="d0609-113">Ters Sinüs (asin (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="d0609-114">Atan (x/sqrt (-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="d0609-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="d0609-115">Ters kosinüs (ACOS (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="d0609-116">Atan (-x/sqrt (-x \* x + 1)) + 2 \* atan (1)</span><span class="sxs-lookup"><span data-stu-id="d0609-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="d0609-117">Ters Sekant (ASEC (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="d0609-118">2 \* atan (1) – atan (Imzala (x)/sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="d0609-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="d0609-119">Ters kosekant (ACSC (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="d0609-120">Atan (x)/sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="d0609-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="d0609-121">Ters Kotanjant (ACOT (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="d0609-122">2 \* atan (1)-atan (x)</span><span class="sxs-lookup"><span data-stu-id="d0609-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="d0609-123">Hiperbolik sinüs (sinh (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="d0609-124">(EXP (x) – exp (-x))/2</span><span class="sxs-lookup"><span data-stu-id="d0609-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="d0609-125">Hiperbolik kosinüs (cosh (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="d0609-126">(EXP (x) + exp (-x))/2</span><span class="sxs-lookup"><span data-stu-id="d0609-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="d0609-127">Hiperbolik tanjant (tanh (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="d0609-128">(EXP (x) – exp (-x))/(EXP (x) + exp (-x))</span><span class="sxs-lookup"><span data-stu-id="d0609-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="d0609-129">Hiperbolik Sekant (sech (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="d0609-130">2/(EXP (x) + exp (-x))</span><span class="sxs-lookup"><span data-stu-id="d0609-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="d0609-131">Hiperbolik kosekant (Csch (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="d0609-132">2/(EXP (x) – exp (-x))</span><span class="sxs-lookup"><span data-stu-id="d0609-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="d0609-133">Hiperbolik Kotanjant (Coth (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="d0609-134">(EXP (x) + exp (-x))/(EXP (x) – exp (-x))</span><span class="sxs-lookup"><span data-stu-id="d0609-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="d0609-135">Ters hiperbolik sinüs (ASİNH (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="d0609-136">Günlük (x + sqrt (x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="d0609-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="d0609-137">Ters hiperbolik kosinüs (ACOSH (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="d0609-138">Günlük (x + sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="d0609-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="d0609-139">Ters hiperbolik tanjant (ATANH (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="d0609-140">Günlük ((1 + x)/(1 – x))/2</span><span class="sxs-lookup"><span data-stu-id="d0609-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="d0609-141">Ters Hiperbolik Sekant (AsecH (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="d0609-142">Günlük ((sqrt (-x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="d0609-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="d0609-143">Ters hiperbolik kosekant (Acsch (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="d0609-144">Log (((x) \* sqrt (x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="d0609-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="d0609-145">Ters hiperbolik Kotanjant (Acoth (x))</span><span class="sxs-lookup"><span data-stu-id="d0609-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="d0609-146">Günlük ((x + 1)/(x – 1))/2</span><span class="sxs-lookup"><span data-stu-id="d0609-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0609-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0609-147">See also</span></span>

- [<span data-ttu-id="d0609-148">Matematik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d0609-148">Math Functions</span></span>](../functions/math-functions.md)
