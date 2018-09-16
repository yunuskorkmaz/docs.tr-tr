---
title: Matematik İşlevleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
ms.openlocfilehash: da0b612feb5b9a479d50f52cf65e38007ab3b196
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45675723"
---
# <a name="math-functions-visual-basic"></a>Matematik İşlevleri (Visual Basic)
Yöntemlerinin <xref:System.Math?displayProperty=nameWithType> sınıfı trigonometrik Logaritmik ve diğer yaygın matematiksel işlevler sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda yöntemlerini listeler <xref:System.Math?displayProperty=nameWithType> sınıfı. Bir Visual Basic programını kullanabilirsiniz.  
  
|.NET yöntemi|Açıklama|  
|---------------------------|-----------------|  
|<xref:System.Math.Abs%2A>|Bir sayının mutlak değerini döndürür.|  
|<xref:System.Math.Acos%2A>|Kosinüsü belirtilen sayı olan açıyı döndürür.|  
|<xref:System.Math.Asin%2A>|Sinüsü belirtilen sayı olan açıyı döndürür.|  
|<xref:System.Math.Atan%2A>|Tanjantı belirtilen sayı olan açıyı döndürür.|  
|<xref:System.Math.Atan2%2A>|Tanjantı belirtilen iki sayının bölümünü olan açıyı döndürür.|  
|<xref:System.Math.BigMul%2A>|İki 32-bit sayının tam çarpımını döndürür.|  
|<xref:System.Math.Ceiling%2A>|Büyüktür veya belirtilen değere eşit en küçük tamsayı değeri döndürür `Decimal` veya `Double`.|  
|<xref:System.Math.Cos%2A>|Belirtilen açının kosinüsünü döndürür.|  
|<xref:System.Math.Cosh%2A>|Belirtilen açının hiperbolik kosinüsünü döndürür.|  
|<xref:System.Math.DivRem%2A>|İki 32-bit veya 64-bit imzalı tamsayı bölümünü döndürür ve ayrıca bir output parametresi kalanı döndürür.|  
|<xref:System.Math.Exp%2A>|Belirtilen kuvvetini e (doğal logaritma tabanı) döndürür.|  
|<xref:System.Math.Floor%2A>|Değerden küçük veya eşit belirtilen en büyük tamsayı döndürür `Decimal` veya `Double` numarası.|  
|<xref:System.Math.IEEERemainder%2A>|Belirtilen numarası bir başkası tarafından belirtilen sayının bölmeden sonuçları kalanı döndürür.|  
|<xref:System.Math.Log%2A>|Belirtilen temel içinde belirtilen bir sayının doğal (e tabanında) logaritmasını veya belirtilen bir sayının logaritmasını döndürür.|  
|<xref:System.Math.Log10%2A>|Belirtilen sayının 10 tabanındaki logaritmasını döndürür.|  
|<xref:System.Math.Max%2A>|İki sayı daha büyük döndürür.|  
|<xref:System.Math.Min%2A>|İki sayı daha küçük döndürür.|  
|<xref:System.Math.Pow%2A>|Belirtilen sayının belirtilen kuvvetini döndürür.|  
|<xref:System.Math.Round%2A>|Döndürür bir `Decimal` veya `Double` değeri en yakın tam sayı değeri veya belirtilen bir kesirli bir basamak sayısına yuvarlanır.|  
|<xref:System.Math.Sign%2A>|Döndürür bir `Integer` bir sayının işaretini belirten değer.|  
|<xref:System.Math.Sin%2A>|Belirtilen açının sinüsünü döndürür.|  
|<xref:System.Math.Sinh%2A>|Belirtilen açının hiperbolik sinüsünü döndürür.|  
|<xref:System.Math.Sqrt%2A>|Belirtilen Sayının karekökünü döndürür.|  
|<xref:System.Math.Tan%2A>|Belirtilen açının tanjantını döndürür.|  
|<xref:System.Math.Tanh%2A>|Belirtilen açının hiperbolik tanjantını döndürür.|  
|<xref:System.Math.Truncate%2A>|Belirtilen bir tamsayı kısmını hesaplar `Decimal` veya `Double` numarası.|  
  
 Bu işlevlerin nitelik kullanmak için içeri aktarma <xref:System.Math?displayProperty=nameWithType> ad alanı, kaynak dosyasının en üstüne aşağıdaki kodu ekleyerek projenize:  
  
```vb
Imports System.Math  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Abs%2A> yöntemi <xref:System.Math> bir sayının mutlak değerini hesaplamak için sınıf.  
  
```vb
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Atan%2A> yöntemi <xref:System.Math> pi değerini hesaplamak için sınıf.  
  
```vb
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Cos%2A> yöntemi <xref:System.Math> sınıfının bir açının kosinüsünü döndürür.  
  
```vb
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Exp%2A> yöntemi <xref:System.Math> e üssü döndürülecek sınıfı.  
  
```vb
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Log%2A> yöntemi <xref:System.Math> sınıfının bir sayının doğal logaritmasını döndürür.  
  
```vb
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Round%2A> yöntemi <xref:System.Math> en yakın tamsayıya yuvarlamak için sınıf.  
  
```vb
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Sign%2A> yöntemi <xref:System.Math> bir sayının işaretini belirlemek için sınıf.  
  
```vb
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Sin%2A> yöntemi <xref:System.Math> sınıfının bir açının sinüsünü döndürür.  
  
```vb
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Math.Sqrt%2A> yöntemi <xref:System.Math> bir sayının karekökünü hesaplamak için sınıf.  
  
```vb
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
 Bu örnekte <xref:System.Math.Tan%2A> yöntemi <xref:System.Math> sınıfının bir açının tanjantını döndürür.  
  
```vb
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Sınıf:** <xref:System.Math>  
  
 **Namespace:** <xref:System>  
  
 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll içinde)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>  
 <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>  
 <xref:System.Double.NaN>  
 [Türetilen Matematik İşlevleri](../../../visual-basic/language-reference/keywords/derived-math-functions.md)  
 [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
