---
description: 'Daha fazla bilgi edinin: matematik Işlevleri (Visual Basic)'
title: Matematik işlevleri
ms.date: 01/27/2020
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
ms.openlocfilehash: d6ab82e45a17c0b1e1ee9f7df54936cd5420ef2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731168"
---
# <a name="math-functions-visual-basic"></a>Matematik İşlevleri (Visual Basic)

Sınıfının yöntemleri, <xref:System.Math?displayProperty=nameWithType> trigonometrik, logaritmik ve diğer yaygın matematik işlevleri sağlar.

## <a name="remarks"></a>Açıklamalar

Aşağıdaki tablo, sınıfının yöntemlerini listeler <xref:System.Math?displayProperty=nameWithType> . Bunları bir Visual Basic programında kullanabilirsiniz:
  
|.NET yöntemi|Description|
|---------------------------|-----------------|
|<xref:System.Math.Abs%2A>|Sayının mutlak değerini döndürür.|
|<xref:System.Math.Acos%2A>|Kosinüsü belirtilen sayı olan açıyı döndürür.|
|<xref:System.Math.Asin%2A>|Sinüsü belirtilen sayı olan açıyı döndürür.|
|<xref:System.Math.Atan%2A>|Tanjantı belirtilen sayı olan açıyı döndürür.|
|<xref:System.Math.Atan2%2A>|Tanjantı belirtilen iki sayının bölümü olan açıyı döndürür.|
|<xref:System.Math.BigMul%2A>|2 32 bitlik sayıların tam çarpımını döndürür.|
|<xref:System.Math.Ceiling%2A>|Belirtilen veya ondan büyük veya buna eşit en küçük integral değeri döndürür `Decimal` `Double` .|
|<xref:System.Math.Cos%2A>|Belirtilen açının kosinüsünü döndürür.|
|<xref:System.Math.Cosh%2A>|Belirtilen açının hiperbolik kosinüsünü döndürür.|
|<xref:System.Math.DivRem%2A>|2 32 bitlik veya 64 bit işaretli tamsayıların bölümünü döndürür ve ayrıca bir çıkış parametresindeki kalanı döndürür.|
|<xref:System.Math.Exp%2A>|Belirtilen üsle oluşturulan e (doğal logaritmalar tabanı) döndürür.|
|<xref:System.Math.Floor%2A>|Belirtilen veya sayıdan küçük veya eşit olan en büyük tamsayıyı döndürür `Decimal` `Double` .|
|<xref:System.Math.IEEERemainder%2A>|Belirtilen sayının bölümünün belirtilen başka bir sayı ile sonuçlanan kalanını döndürür.|
|<xref:System.Math.Log%2A>|Belirtilen bir tabandaki belirtilen bir sayının doğal (Taban e) logaritmasını veya belirtilen sayının logaritmasını döndürür.|
|<xref:System.Math.Log10%2A>|Belirtilen sayının 10 tabanında logaritmasını döndürür.|
|<xref:System.Math.Max%2A>|İki sayıdan daha büyük bir değer döndürür.|
|<xref:System.Math.Min%2A>|İki sayıdan daha küçük bir değer döndürür.|
|<xref:System.Math.Pow%2A>|Belirtilen üsle oluşturulan belirtilen sayıyı döndürür.|
|<xref:System.Math.Round%2A>|`Decimal` `Double` En yakın tamsayı değerine veya belirtilen sayıda kesirli basamağa yuvarlanmış bir veya değeri döndürür.|
|<xref:System.Math.Sign%2A>|`Integer`Bir sayının işaretini gösteren bir değer döndürür.|
|<xref:System.Math.Sin%2A>|Belirtilen açının sinüsünü döndürür.|
|<xref:System.Math.Sinh%2A>|Belirtilen açının hiperbolik sinüsünü döndürür.|
|<xref:System.Math.Sqrt%2A>|Belirtilen sayının kare kökünü döndürür.|
|<xref:System.Math.Tan%2A>|Belirtilen açının tanjantını döndürür.|
|<xref:System.Math.Tanh%2A>|Belirtilen açının hiperbolik tanjantını döndürür.|
|<xref:System.Math.Truncate%2A>|Belirtilen veya sayının integral bölümünü hesaplar `Decimal` `Double` .|

Aşağıdaki tabloda, <xref:System.Math?displayProperty=nameWithType> .NET Framework olmayan, ancak .NET Standard veya .NET Core 'a eklenen sınıfının yöntemleri listelenmiştir:

|.NET yöntemi|Description|Kullanılabilir|
|---------------------------|-----------------|-----------|
|<xref:System.Math.Acosh%2A>|Hiperbolik kosinüsü belirtilen sayı olan açıyı döndürür.|.NET Core 2,1 ve .NET Standard ile başlayarak 2,1|
|<xref:System.Math.Asinh%2A>|Hiperbolik sinüsü belirtilen sayı olan açıyı döndürür.|.NET Core 2,1 ve .NET Standard ile başlayarak 2,1|
|<xref:System.Math.Atanh%2A>|Hiperbolik tanjantı belirtilen sayı olan açıyı döndürür.|.NET Core 2,1 ve .NET Standard ile başlayarak 2,1|
|<xref:System.Math.BitDecrement%2A>|Küçüktür değerini karşılaştıran bir sonraki en küçük değeri döndürür `x` .|.NET Core 3,0 ile başlama|
|<xref:System.Math.BitIncrement%2A>|Şundan büyüktür karşılaştıran bir sonraki en büyük değeri döndürür `x` .|.NET Core 3,0 ile başlama|
|<xref:System.Math.Cbrt%2A>|Belirtilen sayının Küp kökünü döndürür.|.NET Core 2,1 ve .NET Standard ile başlayarak 2,1|
|<xref:System.Math.Clamp%2A>|, `value` Ve ' nin dahil olduğu aralığa döner `min` `max` .|.NET Core 2,0 ve .NET Standard ile başlayarak 2,1|
|<xref:System.Math.CopySign%2A>|Büyüklüğü ve işareti olan bir değer döndürür `x` `y` .|.NET Core 3,0 ile başlama|
|<xref:System.Math.FusedMultiplyAdd%2A>|\*Tek üçlü işlem olarak yuvarlanmış (x y) + z döndürür.|.NET Core 3,0 ile başlama|
|<xref:System.Math.ILogB%2A>|Belirtilen sayının taban 2 tamsayı logaritmasını döndürür.|.NET Core 3,0 ile başlama|
|<xref:System.Math.Log2%2A>|Belirtilen sayının 2 tabanında logaritmasını döndürür.|.NET Core 3,0 ile başlama|
|<xref:System.Math.MaxMagnitude%2A>|İki çift duyarlıklı kayan noktalı sayıların daha büyük büyüklüğünü döndürür.|.NET Core 3,0 ile başlama|
|<xref:System.Math.MinMagnitude%2A>|İki çift duyarlıklı kayan noktalı sayıların daha küçük bir boyutunu döndürür.|.NET Core 3,0 ile başlama|
|<xref:System.Math.ScaleB%2A>|X \* 2 ^ n öğesini verimli bir şekilde döndürür.|.NET Core 3,0 ile başlama|

Bu işlevleri nitelik olmadan kullanmak için, <xref:System.Math?displayProperty=nameWithType> kaynak dosyanızın en üstüne aşağıdaki kodu ekleyerek ad alanını projenize aktarın:

```vb
Imports System.Math
```

## <a name="example---abs"></a>Örnek-ABS

Bu örnek, <xref:System.Math.Abs%2A> <xref:System.Math> bir sayının mutlak değerini hesaplamak için sınıfının yöntemini kullanır.

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

Bu örnek, <xref:System.Math.Atan%2A> <xref:System.Math> Pi değerini hesaplamak için sınıfının yöntemini kullanır.

```vb
Public Function GetPi() As Double
    ' Calculate the value of pi.
    Return 4.0 * Math.Atan(1.0)
End Function
```

> [!NOTE]
> <xref:System.Math?displayProperty=nameWithType>Sınıf <xref:System.Math.PI?displayProperty=nameWithType> sabit alanı içerir. Bunu, hesaplamak yerine kullanabilirsiniz.

## <a name="example---cos"></a>Örnek-Cos

Bu örnek, <xref:System.Math.Cos%2A> <xref:System.Math> Bir açının kosinüsünü döndürmek için sınıfının yöntemini kullanır.

```vb
Public Function Sec(angle As Double) As Double
    ' Calculate the secant of angle, in radians.
    Return 1.0 / Math.Cos(angle)
End Function
```

## <a name="example---exp"></a>Örnek-Exp

Bu örnek, <xref:System.Math.Exp%2A> <xref:System.Math> bir kuvvete yükseltilmiş e döndürmek için sınıfının yöntemini kullanır.

```vb
Public Function Sinh(angle As Double) As Double
    ' Calculate hyperbolic sine of an angle, in radians.
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0
End Function
```

## <a name="example---log"></a>Örnek-günlük

Bu örnek, <xref:System.Math.Log%2A> <xref:System.Math> bir sayının doğal logaritmasını döndürmek için sınıfının yöntemini kullanır.

```vb
Public Function Asinh(value As Double) As Double
    ' Calculate inverse hyperbolic sine, in radians.
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))
End Function
```

## <a name="example---round"></a>Örnek-yuvarlak

Bu örnek, <xref:System.Math.Round%2A> <xref:System.Math> bir sayıyı en yakın tamsayıya yuvarlamak için sınıfının yöntemini kullanır.

```vb
Dim myVar2 As Double = Math.Round(2.8)
Console.WriteLine(myVar2)
' The code produces the following output:
' 3
```

## <a name="example---sign"></a>Örnek-Imzala

Bu örnek, <xref:System.Math.Sign%2A> <xref:System.Math> bir sayının işaretini belirlemekte kullanılan sınıfının yöntemini kullanır.

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

Bu örnek, <xref:System.Math.Sin%2A> <xref:System.Math> Bir açının sinüsünü döndürmek için sınıfının yöntemini kullanır.

```vb
Public Function Csc(angle As Double) As Double
    ' Calculate cosecant of an angle, in radians.
    Return 1.0 / Math.Sin(angle)
End Function
```

## <a name="example---sqrt"></a>Örnek-sqrt

Bu örnek, <xref:System.Math.Sqrt%2A> <xref:System.Math> bir sayının kare kökünü hesaplamak için sınıfının yöntemini kullanır.

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

Bu örnek, <xref:System.Math.Tan%2A> <xref:System.Math> Bir açının tanjantını döndürmek için sınıfının yöntemini kullanır.

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
- [Aritmetik Işleçler](../operators/arithmetic-operators.md)
