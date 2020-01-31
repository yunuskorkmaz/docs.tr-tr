---
title: Matematik işlevleri
ms.date: 01/27/2020
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
ms.openlocfilehash: ea30ae3b30484c1a13d6d540f121c03afb30ba26
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794602"
---
# <a name="math-functions-visual-basic"></a>Matematik İşlevleri (Visual Basic)

<xref:System.Math?displayProperty=nameWithType> sınıfının yöntemleri, trigonometrik, logaritmik ve diğer yaygın matematik işlevlerini sağlar.

## <a name="remarks"></a>Açıklamalar

Aşağıdaki tablo <xref:System.Math?displayProperty=nameWithType> sınıfının yöntemlerini listeler. Bunları bir Visual Basic programında kullanabilirsiniz:
  
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

Aşağıdaki tabloda, .NET Framework mevcut olmayan ancak .NET Standard veya .NET Core 'a eklenen <xref:System.Math?displayProperty=nameWithType> sınıfının yöntemleri listelenmiştir:

|.NET yöntemi|Açıklama|Kullanılabilir|
|---------------------------|-----------------|-----------|
|<xref:System.Math.Acosh%2A>|Hiperbolik kosinüsü belirtilen sayı olan açıyı döndürür.|.NET Core 2,1 ve .NET Standard ile başlayarak 2,1|
|<xref:System.Math.Asinh%2A>|Hiperbolik sinüsü belirtilen sayı olan açıyı döndürür.|.NET Core 2,1 ve .NET Standard ile başlayarak 2,1|
|<xref:System.Math.Atanh%2A>|Hiperbolik tanjantı belirtilen sayı olan açıyı döndürür.|.NET Core 2,1 ve .NET Standard ile başlayarak 2,1|
|<xref:System.Math.BitDecrement%2A>|`x`' den daha az karşılaştıran bir sonraki en küçük değeri döndürür.|.NET Core 3,0 ile başlama|
|<xref:System.Math.BitIncrement%2A>|`x`kıyasla daha büyük bir sonraki en büyük değeri döndürür.|.NET Core 3,0 ile başlama|
|<xref:System.Math.Cbrt%2A>|Belirtilen sayının Küp kökünü döndürür.|.NET Core 2,1 ve .NET Standard ile başlayarak 2,1|
|<xref:System.Math.Clamp%2A>|`value` `min` ve `max`kapsamlı olarak döndürür.|.NET Core 2,0 ve .NET Standard ile başlayarak 2,1|
|<xref:System.Math.CopySign%2A>|`x` büyüklüğü ve `y`işareti olan bir değer döndürür.|.NET Core 3,0 ile başlama|
|<xref:System.Math.FusedMultiplyAdd%2A>|Tek üçlü işlem olarak yuvarlanmış (x \* y) + z döndürür.|.NET Core 3,0 ile başlama|
|<xref:System.Math.ILogB%2A>|Belirtilen sayının taban 2 tamsayı logaritmasını döndürür.|.NET Core 3,0 ile başlama|
|<xref:System.Math.Log2%2A>|Belirtilen sayının 2 tabanında logaritmasını döndürür.|.NET Core 3,0 ile başlama|
|<xref:System.Math.MaxMagnitude%2A>|İki çift duyarlıklı kayan noktalı sayıların daha büyük büyüklüğünü döndürür.|.NET Core 3,0 ile başlama|
|<xref:System.Math.MinMagnitude%2A>|İki çift duyarlıklı kayan noktalı sayıların daha küçük bir boyutunu döndürür.|.NET Core 3,0 ile başlama|
|<xref:System.Math.ScaleB%2A>|X \* 2 ^ n 'yi verimli bir şekilde döndürür.|.NET Core 3,0 ile başlama|

Bu işlevleri nitelik olmadan kullanmak için, kaynak dosyanızın en üstüne aşağıdaki kodu ekleyerek <xref:System.Math?displayProperty=nameWithType> ad alanını projenize aktarın:

```vb
Imports System.Math
```

## <a name="example---abs"></a>Örnek-ABS

Bu örnek, bir sayının mutlak değerini hesaplamak için <xref:System.Math> sınıfının <xref:System.Math.Abs%2A> yöntemini kullanır.

```vb
Dim x As Double = Math.Abs(50.3)
Dim y As Double = Math.Abs(-50.3)
Console.WriteLine(x)
Console.WriteLine(y)
' This example produces the following output:
' 50.3
' 50.3
```  

## <a name="example---atan"></a>Örnek-atan

Bu örnek, Pi değerini hesaplamak için <xref:System.Math> sınıfının <xref:System.Math.Atan%2A> yöntemini kullanır.

```vb
Public Function GetPi() As Double
    ' Calculate the value of pi.
    Return 4.0 * Math.Atan(1.0)
End Function
```

> [!NOTE]
> <xref:System.Math?displayProperty=nameWithType> sınıfı <xref:System.Math.PI?displayProperty=nameWithType> sabiti alanı içerir. Bunu, hesaplamak yerine kullanabilirsiniz.

## <a name="example---cos"></a>Örnek-Cos

Bu örnek, bir açının kosinüsünü döndürmek için <xref:System.Math> sınıfının <xref:System.Math.Cos%2A> yöntemini kullanır.

```vb
Public Function Sec(angle As Double) As Double
    ' Calculate the secant of angle, in radians.
    Return 1.0 / Math.Cos(angle)
End Function
```

## <a name="example---exp"></a>Örnek-Exp

Bu örnek, bir kuvvete yükseltilmiş e döndürmek için <xref:System.Math> sınıfının <xref:System.Math.Exp%2A> yöntemini kullanır.

```vb
Public Function Sinh(angle As Double) As Double
    ' Calculate hyperbolic sine of an angle, in radians.
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0
End Function
```

## <a name="example---log"></a>Örnek-günlük

Bu örnek, bir sayının doğal logaritmasını döndürmek için <xref:System.Math> sınıfının <xref:System.Math.Log%2A> yöntemini kullanır.

```vb
Public Function Asinh(value As Double) As Double
    ' Calculate inverse hyperbolic sine, in radians.
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))
End Function
```

## <a name="example---round"></a>Örnek-yuvarlak

Bu örnek, bir sayıyı en yakın tamsayıya yuvarlamak için <xref:System.Math> sınıfının <xref:System.Math.Round%2A> yöntemini kullanır.

```vb
Dim myVar2 As Double = Math.Round(2.8)
Console.WriteLine(myVar2)
' The code produces the following output:
' 3
```

## <a name="example---sign"></a>Örnek-Imzala

Bu örnek, bir sayının işaretini öğrenmek için <xref:System.Math> sınıfının <xref:System.Math.Sign%2A> yöntemini kullanır.

```vb
Dim mySign1 As Integer = Math.Sign(12)
Dim mySign2 As Integer = Math.Sign(-2.4)
Dim mySign3 As Integer = Math.Sign(0)
Console.WriteLine(mySign1)
Console.WriteLine(mySign2)
Console.WriteLine(mySign3)
' The code produces the following output:
' 1
' -1
' 0
```

## <a name="example---sin"></a>Örnek-sin

Bu örnek, bir açının sinüsünü döndürmek için <xref:System.Math> sınıfının <xref:System.Math.Sin%2A> yöntemini kullanır.

```vb
Public Function Csc(angle As Double) As Double
    ' Calculate cosecant of an angle, in radians.
    Return 1.0 / Math.Sin(angle)
End Function
```

## <a name="example---sqrt"></a>Örnek-sqrt

Bu örnek, bir sayının kare kökünü hesaplamak için <xref:System.Math> sınıfının <xref:System.Math.Sqrt%2A> yöntemini kullanır.

```vb
Dim mySqrt1 As Double = Math.Sqrt(4)
Dim mySqrt2 As Double = Math.Sqrt(23)
Dim mySqrt3 As Double = Math.Sqrt(0)
Dim mySqrt4 As Double = Math.Sqrt(-4)
Console.WriteLine(mySqrt1)
Console.WriteLine(mySqrt2)
Console.WriteLine(mySqrt3)
Console.WriteLine(mySqrt4)
' The code produces the following output:
' 2
' 4.79583152331272
' 0
' NaN
```

## <a name="example---tan"></a>Örnek-tan

Bu örnek, bir açının tanjantını döndürmek için <xref:System.Math> sınıfının <xref:System.Math.Tan%2A> yöntemini kullanır.

```vb
Public Function Ctan(angle As Double) As Double
    ' Calculate cotangent of an angle, in radians.
    Return 1.0 / Math.Tan(angle)
End Function
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>
- <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>
- <xref:System.Double.NaN>
- [Türetilen Matematik İşlevleri](../keywords/derived-math-functions.md)
- [Aritmetik İşleçler](../operators/arithmetic-operators.md)
