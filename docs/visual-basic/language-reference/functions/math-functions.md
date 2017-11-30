---
title: "Matematik İşlevleri (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4d67df44e5f4ea89475ea34e87fd5041ee6cb44f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="math-functions-visual-basic"></a>Matematik İşlevleri (Visual Basic)
Yöntemlerinin <xref:System.Math?displayProperty=nameWithType> sınıfı trigonometrik, logaritmik ve diğer ortak matematik işlevleri sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda yöntemlerini listeler <xref:System.Math?displayProperty=nameWithType> sınıfı. Bir Visual Basic programı kullanabilirsiniz.  
  
|.NET framework yöntemi|Açıklama|  
|---------------------------|-----------------|  
|<xref:System.Math.Abs%2A>|Bir sayının mutlak değerini döndürür.|  
|<xref:System.Math.Acos%2A>|Kosinüs, kosinüsü belirtilen sayı olan açıyı döndürür.|  
|<xref:System.Math.Asin%2A>|Sinüsü belirtilen sayı olan açıyı döndürür.|  
|<xref:System.Math.Atan%2A>|Tanjantı belirtilen sayı olan açıyı döndürür.|  
|<xref:System.Math.Atan2%2A>|İki sayının bölümünü belirtilen tanjantı olan açıyı döndürür.|  
|<xref:System.Math.BigMul%2A>|İki 32-bit sayının tam çarpımını döndürür.|  
|<xref:System.Math.Ceiling%2A>|Büyük veya eşit belirtilen en küçük tamsayı değeri döndürür `Decimal` veya `Double`.|  
|<xref:System.Math.Cos%2A>|Belirtilen açının kosinüsünü döndürür.|  
|<xref:System.Math.Cosh%2A>|Belirtilen açının hiperbolik kosinüsünü döndürür.|  
|<xref:System.Math.DivRem%2A>|İki 32 bit veya 64-bit işaretli tamsayının sayının verir ve ayrıca bir output parametresi kalanı döndürür.|  
|<xref:System.Math.Exp%2A>|Belirtilen üssünün e (Doğal logaritmanın tabanı) döndürür.|  
|<xref:System.Math.Floor%2A>|Küçük veya eşit belirtilen en büyük tamsayıyı döndürür `Decimal` veya `Double` numarası.|  
|<xref:System.Math.IEEERemainder%2A>|Belirtilen sayının bölmeden bir başkası tarafından sonuçları kalan numarası belirtilen döndürür.|  
|<xref:System.Math.Log%2A>|Belirtilen sayının doğal (e tabanında) logaritmasını veya belirtilen sayının logaritmasını içinde belirtilen bir taban döndürür.|  
|<xref:System.Math.Log10%2A>|Belirtilen sayının 10 tabanında logaritmasını döndürür.|  
|<xref:System.Math.Max%2A>|Büyük iki sayının döndürür.|  
|<xref:System.Math.Min%2A>|İki sayı daha küçük veya döndürür.|  
|<xref:System.Math.Pow%2A>|Belirtilen sayının belirtilen kuvvetini döndürür.|  
|<xref:System.Math.Round%2A>|Döndürür bir `Decimal` veya `Double` değeri en yakın tam sayı değeri veya belirtilen bir kesir basamakları sayısı yuvarlanır.|  
|<xref:System.Math.Sign%2A>|Döndürür bir `Integer` sayının işaretini gösteren değer.|  
|<xref:System.Math.Sin%2A>|Belirtilen açının sinüsünü döndürür.|  
|<xref:System.Math.Sinh%2A>|Belirtilen açının hiperbolik sinüsünü döndürür.|  
|<xref:System.Math.Sqrt%2A>|Belirtilen Sayının karekökünü döndürür.|  
|<xref:System.Math.Tan%2A>|Belirtilen açının tanjantını döndürür.|  
|<xref:System.Math.Tanh%2A>|Belirtilen açının hiperbolik tanjantını döndürür.|  
|<xref:System.Math.Truncate%2A>|Belirtilen'ın ayrılmaz bir parçası hesaplar `Decimal` veya `Double` numarası.|  
  
 Niteliğe olmadan bu işlevleri kullanmak için alma <xref:System.Math?displayProperty=nameWithType> kaynak dosyanızın en üstüne aşağıdaki kodu ekleyerek projenize ad alanı:  
  
```  
Imports System.Math  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Abs%2A> yöntemi <xref:System.Math> bir sayının mutlak değerini hesaplamak için sınıf.  
  
```  
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Atan%2A> yöntemi <xref:System.Math> pi değerini hesaplamak için sınıf.  
  
```  
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Cos%2A> yöntemi <xref:System.Math> sınıfı bir açının kosinüsünü döndürür.  
  
```  
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Exp%2A> yöntemi <xref:System.Math> üssü e dönmek için sınıf.  
  
```  
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Log%2A> yöntemi <xref:System.Math> sınıfı bir sayının doğal logaritmasını döndürür.  
  
```  
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Round%2A> yöntemi <xref:System.Math> sınıfı sayıyı en yakın tamsayıya yuvarlar.  
  
```  
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Sign%2A> yöntemi <xref:System.Math> sayının işaretini belirlemek için sınıf.  
  
```  
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Sin%2A> yöntemi <xref:System.Math> sınıfı bir açının sinüsünü döndürür.  
  
```  
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Sqrt%2A> yöntemi <xref:System.Math> bir sayının kare kökünü hesaplamak için sınıf.  
  
```  
' Returns 2.  
Dim MySqr1 As Double = Math.Sqrt(4)  
' Returns 4.79583152331272.  
Dim MySqr2 As Double = Math.Sqrt(23)  
' Returns 0.  
Dim MySqr3 As Double = Math.Sqrt(0)  
' Returns NaN (not a number).  
Dim MySqr4 As Double = Math.Sqrt(-4)  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Tan%2A> yöntemi <xref:System.Math> sınıfı bir açının tanjantını döndürür.  
  
```  
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Sınıfı:**<xref:System.Math>  
  
 **Namespace:**<xref:System>  
  
 **Derleme:** mscorlib (içinde mscorlib.dll)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>  
 <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>  
 <xref:System.Double.NaN>  
 [Türetilen matematik işlevleri](../../../visual-basic/language-reference/keywords/derived-math-functions.md)  
 [Aritmetik işleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
