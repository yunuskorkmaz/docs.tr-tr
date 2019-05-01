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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801900"
---
# <a name="derived-math-functions-visual-basic"></a>Türetilen Matematik İşlevleri (Visual Basic)
Aşağıdaki tablo iç matematik işlevleri türetilmiş iç olmayan matematik işlevleri gösterir <xref:System.Math?displayProperty=nameWithType> nesne. Gerçek matematik işlevleri ekleyerek erişebileceğiniz `Imports System.Math` dosyası veya proje için.  
  
|İşlev|Türetilmiş eşdeğerleri|  
|--------------|-------------------------|  
|Secant (Sec(x))|1 / Cos(x)|  
|Cosecant (Csc(x))|1 / Sin(x)|  
|Kotanjantını (Ctan(x))|1 / Tan(x)|  
|Ters sinüsünü (Asin(x))|Atan(x / Sqrt(-x * x + 1))|  
|Ters kosinüsünü (Acos(x))|Atan(-x / Sqrt(-x * x + 1)) + 2 \* Atan(1)|  
|Ters secant (Asec(x))|2 * Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))|  
|Ters cosecant (Acsc(x))|Atan(Sign(x) / Sqrt(x * x – 1))|  
|Ark kotanjantını (Acot(x))|2 * Atan(1) - Atan(x)|  
|Hiperbolik sinüs (Sinh(x))|(Exp(x) – Exp(-x)) / 2|  
|Hiperbolik kosinüsü (Cosh(x))|(Exp(x) + Exp(-x)) / 2|  
|Hiperbolik tanjantı (Tanh(x))|(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))|  
|Hiperbolik secant (Sech(x))|2 / (Exp(x) + Exp(-x))|  
|Hiperbolik cosecant (Csch(x))|2 / (Exp(x) – Exp(-x))|  
|Hiperbolik kotanjantını (Coth(x))|(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))|  
|Ters hiperbolik sinüs (Asinh(x))|Log(x + Sqrt(x * x + 1))|  
|Ters hiperbolik kosinüsü (Acosh(x))|Log(x + Sqrt(x * x – 1))|  
|Ters hiperbolik tanjantı (Atanh(x))|Günlük ((1 + x) / (1: x)) / 2|  
|Ters hiperbolik secant (AsecH(x))|Günlük ((Sqrt (-x * x + 1) + 1) / x)|  
|Ters hiperbolik cosecant (Acsch(x))|Log((Sign(x) * Sqrt (x \* x + 1) + 1) / x)|  
|Ters hiperbolik kotanjantını (Acoth(x))|Günlük ((x + 1) / (x – 1)) / 2|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Matematik İşlevleri](../../../visual-basic/language-reference/functions/math-functions.md)
