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
ms.openlocfilehash: 87faa623f5b145eec8b88e350fce4171125324dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="derived-math-functions-visual-basic"></a>Türetilen Matematik İşlevleri (Visual Basic)
Aşağıdaki tabloda iç matematik işlevlerden türetilebilir iç olmayan matematik işlevleri gösterilmektedir <xref:System.Math?displayProperty=nameWithType> nesnesi. İç matematik işlevleri ekleyerek erişebilirsiniz `Imports System.Math` dosya veya projesi.  
  
|İşlev|Türetilen eşdeğerleri|  
|--------------|-------------------------|  
|Secant (Sec(x))|1 / Cos(x)|  
|Cosecant (Csc(x))|1 / Sin(x)|  
|Kotanjant (Ctan(x))|1 / Tan(x)|  
|Ters sinüsünü (Asin(x))|Atan (x / Sqrt (-x * x + 1))|  
|Ters kosinüsünü (Acos(x))|Atan (-x / Sqrt (-x * x + 1)) + 2 \* Atan(1)|  
|Ters secant (Asec(x))|2 * Atan(1) – Atan(Sign(x) / Sqrt (x \* x-1))|  
|Ters cosecant (Acsc(x))|Atan(Sign(x) / Sqrt (x * x-1))|  
|Ters Kotanjant (Acot(x))|2 * Atan(1) - Atan(x)|  
|Hiperbolik sinüsü (Sinh(x))|(Exp(x) – Exp(-x)) / 2|  
|Hiperbolik kosinüsünü (Cosh(x))|(Exp(x) + Exp(-x)) / 2|  
|Hiperbolik tanjantı (Tanh(x))|(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))|  
|Hiperbolik secant (Sech(x))|2 / (Exp(x) + Exp(-x))|  
|Hiperbolik cosecant (Csch(x))|2 / (Exp(x) – Exp(-x))|  
|Hiperbolik kotanjantını (Coth(x))|(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))|  
|Ters hiperbolik sinüs (Asinh(x))|Günlük (x + Sqrt (x * x + 1))|  
|Ters hiperbolik Kosinüs (Acosh(x))|Günlük (x + Sqrt (x * x-1))|  
|Ters hiperbolik tanjant (Atanh(x))|Günlük ((1 + x) / (1-x)) / 2|  
|Ters hiperbolik secant (AsecH(x))|Günlük ((Sqrt (-x * x + 1) + 1) / x)|  
|Ters hiperbolik cosecant (Acsch(x))|Log((Sign(x) * Sqrtsqrt (x \* x + 1) + 1) / x)|  
|Ters hiperbolik kotanjantını (Acoth(x))|Günlük ((x + 1) / (x-1)) / 2|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Matematik İşlevleri](../../../visual-basic/language-reference/functions/math-functions.md)
