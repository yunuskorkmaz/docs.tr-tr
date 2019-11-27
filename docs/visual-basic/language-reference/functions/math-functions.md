---
title: Matematik İşlevleri
ms.date: 07/20/2015
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
ms.openlocfilehash: b1cd6a846a7dc1dddcf6bdb5eb99ebc1c57a012c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348069"
---
# <a name="math-functions-visual-basic"></a>Matematik İşlevleri (Visual Basic)
<xref:System.Math?displayProperty=nameWithType> sınıfının yöntemleri, trigonometrik, logaritmik ve diğer yaygın matematik işlevlerini sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tablo <xref:System.Math?displayProperty=nameWithType> sınıfının yöntemlerini listeler. Bunları bir Visual Basic programında kullanabilirsiniz.  
  
|.NET yöntemi|Açıklama|  
|---------------------------|-----------------|  
|<xref:System.Math.Abs%2A>|Bir sayının mutlak değerini döndürür.|  
|<xref:System.Math.Acos%2A>|Kosinüsü belirtilen sayı olan açıyı döndürür.|  
|<xref:System.Math.Asin%2A>|Sinüsü belirtilen sayı olan açıyı döndürür.|  
|<xref:System.Math.Atan%2A>|Tanjantı belirtilen sayı olan açıyı döndürür.|  
|<xref:System.Math.Atan2%2A>|Tanjantı belirtilen iki sayının bölümü olan açıyı döndürür.|  
|<xref:System.Math.BigMul%2A>|2 32 bitlik sayıların tam çarpımını döndürür.|  
|<xref:System.Math.Ceiling%2A>|Belirtilen `Decimal` veya `Double`büyük veya ona eşit olan en küçük integral değeri döndürür.|  
|<xref:System.Math.Cos%2A>|Belirtilen açının kosinüsünü döndürür.|  
|<xref:System.Math.Cosh%2A>|Belirtilen açının hiperbolik kosinüsünü döndürür.|  
|<xref:System.Math.DivRem%2A>|2 32 bitlik veya 64 bit işaretli tamsayıların bölümünü döndürür ve ayrıca bir çıkış parametresindeki kalanı döndürür.|  
|<xref:System.Math.Exp%2A>|Belirtilen üsle oluşturulan e (doğal logaritmalar tabanı) döndürür.|  
|<xref:System.Math.Floor%2A>|Belirtilen `Decimal` veya `Double` numarasına eşit veya daha küçük olan en büyük tamsayıyı döndürür.|  
|<xref:System.Math.IEEERemainder%2A>|Belirtilen sayının bölümünün belirtilen başka bir sayı ile sonuçlanan kalanını döndürür.|  
|<xref:System.Math.Log%2A>|Belirtilen bir tabandaki belirtilen bir sayının doğal (Taban e) logaritmasını veya belirtilen sayının logaritmasını döndürür.|  
|<xref:System.Math.Log10%2A>|Belirtilen sayının 10 tabanında logaritmasını döndürür.|  
|<xref:System.Math.Max%2A>|İki sayıdan daha büyük bir değer döndürür.|  
|<xref:System.Math.Min%2A>|İki sayıdan daha küçük bir değer döndürür.|  
|<xref:System.Math.Pow%2A>|Belirtilen üsle oluşturulan belirtilen sayıyı döndürür.|  
|<xref:System.Math.Round%2A>|En yakın tamsayı değerine veya belirtilen sayıda kesirli basamağa yuvarlanmış bir `Decimal` veya `Double` değeri döndürür.|  
|<xref:System.Math.Sign%2A>|Bir sayının işaretini gösteren bir `Integer` değeri döndürür.|  
|<xref:System.Math.Sin%2A>|Belirtilen açının sinüsünü döndürür.|  
|<xref:System.Math.Sinh%2A>|Belirtilen açının hiperbolik sinüsünü döndürür.|  
|<xref:System.Math.Sqrt%2A>|Belirtilen sayının kare kökünü döndürür.|  
|<xref:System.Math.Tan%2A>|Belirtilen açının tanjantını döndürür.|  
|<xref:System.Math.Tanh%2A>|Belirtilen açının hiperbolik tanjantını döndürür.|  
|<xref:System.Math.Truncate%2A>|Belirtilen bir `Decimal` veya `Double` sayının integral bölümünü hesaplar.|  
  
 Bu işlevleri nitelik olmadan kullanmak için, kaynak dosyanızın en üstüne aşağıdaki kodu ekleyerek <xref:System.Math?displayProperty=nameWithType> ad alanını projenize aktarın:  
  
```vb
Imports System.Math  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir sayının mutlak değerini hesaplamak için <xref:System.Math> sınıfının <xref:System.Math.Abs%2A> yöntemini kullanır.  
  
```vb
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, Pi değerini hesaplamak için <xref:System.Math> sınıfının <xref:System.Math.Atan%2A> yöntemini kullanır.  
  
```vb
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir açının kosinüsünü döndürmek için <xref:System.Math> sınıfının <xref:System.Math.Cos%2A> yöntemini kullanır.  
  
```vb
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir kuvvete yükseltilmiş e döndürmek için <xref:System.Math> sınıfının <xref:System.Math.Exp%2A> yöntemini kullanır.  
  
```vb
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir sayının doğal logaritmasını döndürmek için <xref:System.Math> sınıfının <xref:System.Math.Log%2A> yöntemini kullanır.  
  
```vb
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir sayıyı en yakın tamsayıya yuvarlamak için <xref:System.Math> sınıfının <xref:System.Math.Round%2A> yöntemini kullanır.  
  
```vb
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir sayının işaretini öğrenmek için <xref:System.Math> sınıfının <xref:System.Math.Sign%2A> yöntemini kullanır.  
  
```vb
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir açının sinüsünü döndürmek için <xref:System.Math> sınıfının <xref:System.Math.Sin%2A> yöntemini kullanır.  
  
```vb
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir sayının kare kökünü hesaplamak için <xref:System.Math> sınıfının <xref:System.Math.Sqrt%2A> yöntemini kullanır.  
  
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
 Bu örnek, bir açının tanjantını döndürmek için <xref:System.Math> sınıfının <xref:System.Math.Tan%2A> yöntemini kullanır.  
  
```vb
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Sınıf:** <xref:System.Math>  
  
 **Ad alanı:** <xref:System>  
  
 **Bütünleştirilmiş kod:** mscorlib (mscorlib. dll içinde)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>
- <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>
- <xref:System.Double.NaN>
- [Türetilen Matematik İşlevleri](../../../visual-basic/language-reference/keywords/derived-math-functions.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
