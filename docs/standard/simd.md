---
title: .NET 'te SıMD-hızlandırılmış türler
description: Bu makalede, .NET 'teki SıMD-Enable türleri açıklanmakta ve C# ve .NET 'te Hardware SıMD işlemlerinin nasıl kullanılacağı gösterilir.
author: FIVIL
ms.author: tagoo
ms.date: 04/28/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 27263931ff0338e194c8fd3d9ec5ba59bfafd9fe
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507784"
---
# <a name="use-simd-accelerated-numeric-types"></a>SıMD hızlandırılmış sayısal türleri kullanma

SıMD (tek yönerge, birden çok veri), tek bir yönerge kullanılarak paralel olarak birden çok veri parçasına bir işlem gerçekleştirmeye yönelik donanım desteği sağlar. .NET ' te, <xref:System.Numerics> ad alanı altında SIMD hızlandırmalı türler kümesi vardır. SıMD işlemleri donanım düzeyinde paralelleştirilmiş olabilir. Bu, matematiksel, bilimsel ve grafik uygulamalarda ortak olan vektörleştirilmiş hesaplamaların verimini artırır.

## <a name="net-simd-accelerated-types"></a>.NET SIMD-hızlandırılmış türler

.NET SıMD-hızlandırılmış türleri aşağıdaki türleri içerir:

- 2 <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>3 ve <xref:System.Numerics.Vector4> 4 <xref:System.Single> değerli vektörleri temsil eden, ve türleri.

- Bir 3X2 matrisini <xref:System.Numerics.Matrix3x2>temsil eden iki matris türü ve <xref:System.Numerics.Matrix4x4>bir 4x4 <xref:System.Single> değer matrisini temsil eden.

- Değerler <xref:System.Numerics.Plane> kullanılarak <xref:System.Single> üç boyutlu alanda bir düzlemi temsil eden tür.

- Değer <xref:System.Numerics.Quaternion> kullanarak <xref:System.Single> üç boyutlu fiziksel döndürmeler kodlamak için kullanılan bir vektörü temsil eden tür.

- Belirtilen <xref:System.Numerics.Vector%601> bir sayısal türün vektörünü temsil eden ve SIMD desteğinden yararlanan geniş bir işleç kümesi sağlayan tür. Bir uygulamanın ömrü için <xref:System.Numerics.Vector%601> bir örneğin sayısı sabittir, ancak değeri <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> kodu çalıştıran makinenin CPU 'suna bağlıdır.

  > [!NOTE]
  > <xref:System.Numerics.Vector%601> Tür .NET Framework dahil değildir. Bu türe erişim sağlamak için [System. Numerics. vektörleri](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet paketini yüklemelisiniz.
  
SıMD hızlandırmalı türler, SıMD olmayan donanımla veya JıT derleyicilerle kullanılabilecek şekilde uygulanır. SıMD yönergelerinden faydalanmak için, 64 bitlik uygulamalarınızın **RyuJIT** derleyicisini kullanan çalışma zamanı tarafından çalıştırılması gerekir. **RyuJIT** derleyicisi, .NET Core 'a ve .NET Framework 4,6 ve üzeri bir sürüme dahildir. SıMD desteği yalnızca 64 bitlik işlemciler hedeflenirken sağlanır.

## <a name="how-to-use-simd"></a>SıMD nasıl kullanılır?

Özel SıMD algoritmalarını yürütmeden önce, konak makinenin kullanılarak <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType>SIMD 'yi destekleyip desteklemediğini denetlemek mümkündür. <xref:System.Boolean> Bu, SıMD hızlandırmasının belirli bir tür için etkinleştirildiğini garantilemez, ancak bazı türler tarafından desteklendiği bir göstergedir.

## <a name="simple-vectors"></a>Basit vektörler

.Net 'teki en basit SIMD- <xref:System.Numerics.Vector2>hızlandırılmış türler, <xref:System.Numerics.Vector3>ve <xref:System.Numerics.Vector4> , 2, 3 ve 4 <xref:System.Single> değerli vektörlerini temsil eden türlerdir. Aşağıdaki örnek, iki <xref:System.Numerics.Vector2> vektör eklemek için kullanır.

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResutl = v1 + v2;
```

Ayrıca `Dot product`, `Transform` `Clamp` ve gibi vektörin diğer matematik özelliklerini hesaplamak için .net vektörlerini kullanmak da mümkündür.

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResutl1 = Vector2.Dot(v1, v2);
var vResutl2 = Vector2.Distance(v1, v2);
var vResutl3 = Vector2.Clamp(v1, Vector2.Zero, Vector2.One);
```

## <a name="matrix"></a>Matrix

<xref:System.Numerics.Matrix3x2>bir 3X2 matrisini temsil eden ve <xref:System.Numerics.Matrix4x4>bir 4x4 matrisini temsil eden. , Matris ile ilgili hesaplamalar için kullanılabilir. Aşağıdaki örnekte, SıMD kullanarak bir matrisin çarpmayı bir matrisin çarpılacağını gösterir.

```csharp
var m1 = new Matrix4x4(
            1.1f, 1.2f, 1.3f, 1.4f,
            2.1f, 2.2f, 3.3f, 4.4f,
            3.1f, 3.2f, 3.3f, 3.4f,
            4.1f, 4.2f, 4.3f, 4.4f);

var m2 = Matrix4x4.Transpose(m1);
var mResult = Matrix4x4.Multiply(m1, m2);
```

## <a name="vectort"></a>Vektör\<T>

, <xref:System.Numerics.Vector%601> Daha uzun vektörlerini kullanma olanağı sunar. Bir <xref:System.Numerics.Vector%601> örneğin sayısı sabittir, ancak değeri <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> kodu çalıştıran makinenin CPU 'suna bağlıdır.

Aşağıdaki örnekte kullanarak <xref:System.Numerics.Vector%601>uzun diziler öğeleri ekleme gösterilmektedir.

```csharp
double[] SimdVectorProd(double[] left, double[] right)
{
    var offset = Vector<double>.Count;
    double[] result = new double[left.Length];
    int i = 0;
    for (i = 0; i < left.Length; i += offset)
    {
        var v1 = new Vector<double>(left, i);
        var v2 = new Vector<double>(right, i);
        (v1 * v2).CopyTo(result, i);
    }

    //remaining items
    for (; i < left.Length; ++i)
    {
        result[i] = left[i] * right[i];
    }

    return result;
}
```

## <a name="remarks"></a>Açıklamalar

SıMD 'nin bir darboğazı kaldırmak ve bir sonraki performansı ortaya çıkarmak daha olasıdır. Genel olarak, SıMD kullanmanın performans avantajı, belirli senaryoya bağlı olarak farklılık gösterir ve bazı durumlarda, daha basit bir SıMD olmayan eşdeğer koddan daha kötüleşme de olabilir.
