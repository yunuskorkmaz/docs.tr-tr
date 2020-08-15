---
title: .NET 'te SıMD-hızlandırılmış türler
description: Bu makalede, .NET 'teki SıMD-Enable türleri açıklanmakta ve C# ve .NET 'te Hardware SıMD işlemlerinin nasıl kullanılacağı gösterilir.
author: FIVIL
ms.author: tagoo
ms.date: 04/28/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 5c1ad01ea15a9c4352cf7f87e5fba3bf74b4679c
ms.sourcegitcommit: 2987e241e2f76c9248d2146bf2761a33e2c7a882
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88228737"
---
# <a name="use-simd-accelerated-numeric-types"></a><span data-ttu-id="0d335-103">SıMD hızlandırılmış sayısal türleri kullanma</span><span class="sxs-lookup"><span data-stu-id="0d335-103">Use SIMD-accelerated numeric types</span></span>

<span data-ttu-id="0d335-104">SıMD (tek yönerge, birden çok veri), tek bir yönerge kullanılarak paralel olarak birden çok veri parçasına bir işlem gerçekleştirmeye yönelik donanım desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d335-104">SIMD (Single instruction, multiple data) provides hardware support for performing an operation on multiple pieces of data, in parallel, using a single instruction.</span></span> <span data-ttu-id="0d335-105">.NET ' te, ad alanı altında SıMD hızlandırmalı türler kümesi vardır <xref:System.Numerics> .</span><span class="sxs-lookup"><span data-stu-id="0d335-105">In .NET, there's set of SIMD-accelerated types under the <xref:System.Numerics> namespace.</span></span> <span data-ttu-id="0d335-106">SıMD işlemleri donanım düzeyinde paralelleştirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="0d335-106">SIMD operations can be parallelized at the hardware level.</span></span> <span data-ttu-id="0d335-107">Bu, matematiksel, bilimsel ve grafik uygulamalarda ortak olan vektörleştirilmiş hesaplamaların verimini artırır.</span><span class="sxs-lookup"><span data-stu-id="0d335-107">That increases the throughput of the vectorized computations, which are common in mathematical, scientific, and graphics apps.</span></span>

## <a name="net-simd-accelerated-types"></a><span data-ttu-id="0d335-108">.NET SIMD-hızlandırılmış türler</span><span class="sxs-lookup"><span data-stu-id="0d335-108">.NET SIMD-accelerated types</span></span>

<span data-ttu-id="0d335-109">.NET SıMD-hızlandırılmış türleri aşağıdaki türleri içerir:</span><span class="sxs-lookup"><span data-stu-id="0d335-109">The .NET SIMD-accelerated types include the following types:</span></span>

- <span data-ttu-id="0d335-110"><xref:System.Numerics.Vector2> <xref:System.Numerics.Vector3> <xref:System.Numerics.Vector4> 2, 3 ve 4 değerli vektörleri temsil eden, ve türleri <xref:System.Single> .</span><span class="sxs-lookup"><span data-stu-id="0d335-110">The <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4> types, which represent vectors with 2, 3, and 4 <xref:System.Single> values.</span></span>

- <span data-ttu-id="0d335-111"><xref:System.Numerics.Matrix3x2>Bir 3X2 matrisini temsil eden iki matris türü ve <xref:System.Numerics.Matrix4x4> bir 4x4 değer matrisini temsil eden <xref:System.Single> .</span><span class="sxs-lookup"><span data-stu-id="0d335-111">Two matrix types, <xref:System.Numerics.Matrix3x2>, which represents a 3x2 matrix, and <xref:System.Numerics.Matrix4x4>, which represents a 4x4 matrix of <xref:System.Single> values.</span></span>

- <span data-ttu-id="0d335-112"><xref:System.Numerics.Plane>Değerler kullanılarak üç boyutlu alanda bir düzlemi temsil eden tür <xref:System.Single> .</span><span class="sxs-lookup"><span data-stu-id="0d335-112">The <xref:System.Numerics.Plane> type, which represents a plane in three-dimensional space using <xref:System.Single> values.</span></span>

- <span data-ttu-id="0d335-113"><xref:System.Numerics.Quaternion>Değer kullanarak üç boyutlu fiziksel döndürmeler kodlamak için kullanılan bir vektörü temsil eden tür <xref:System.Single> .</span><span class="sxs-lookup"><span data-stu-id="0d335-113">The <xref:System.Numerics.Quaternion> type, which represents a vector that is used to encode three-dimensional physical rotations using <xref:System.Single> values.</span></span>

- <span data-ttu-id="0d335-114"><xref:System.Numerics.Vector%601>Belirtilen bir sayısal türün vektörünü temsil eden ve SıMD desteğinden yararlanan geniş bir işleç kümesi sağlayan tür.</span><span class="sxs-lookup"><span data-stu-id="0d335-114">The <xref:System.Numerics.Vector%601> type, which represents a vector of a specified numeric type and provides a broad set of operators that benefit from SIMD support.</span></span> <span data-ttu-id="0d335-115">Bir <xref:System.Numerics.Vector%601> uygulamanın ömrü için bir örneğin sayısı sabittir, ancak değeri <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> kodu çalıştıran makinenin CPU 'suna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0d335-115">The count of a <xref:System.Numerics.Vector%601> instance is fixed for the lifetime of an application, but its value <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> depends on the CPU of the machine running the code.</span></span>

  > [!NOTE]
  > <span data-ttu-id="0d335-116"><xref:System.Numerics.Vector%601>Tür .NET Framework dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="0d335-116">The <xref:System.Numerics.Vector%601> type is not included in the .NET Framework.</span></span> <span data-ttu-id="0d335-117">Bu türe erişim sağlamak için [System. Numerics. vektörleri](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet paketini yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="0d335-117">You must install the [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet package to get access to this type.</span></span>
  
<span data-ttu-id="0d335-118">SıMD hızlandırmalı türler, SıMD olmayan donanımla veya JıT derleyicilerle kullanılabilecek şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0d335-118">The SIMD-accelerated types are implemented in such a way that they can be used with non-SIMD-accelerated hardware or JIT compilers.</span></span> <span data-ttu-id="0d335-119">SıMD yönergelerinden faydalanmak için, 64 bitlik uygulamalarınızın **RyuJIT** derleyicisini kullanan çalışma zamanı tarafından çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d335-119">To take advantage of SIMD instructions, your 64-bit apps must be run by the runtime that uses the **RyuJIT** compiler.</span></span> <span data-ttu-id="0d335-120">**RyuJIT** derleyicisi, .NET Core 'a ve .NET Framework 4,6 ve üzeri bir sürüme dahildir.</span><span class="sxs-lookup"><span data-stu-id="0d335-120">A **RyuJIT** compiler is included in .NET Core and in .NET Framework 4.6 and later.</span></span> <span data-ttu-id="0d335-121">SıMD desteği yalnızca 64 bitlik işlemciler hedeflenirken sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0d335-121">SIMD support is only provided when targeting 64-bit processors.</span></span>

## <a name="how-to-use-simd"></a><span data-ttu-id="0d335-122">SıMD nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="0d335-122">How to use SIMD?</span></span>

<span data-ttu-id="0d335-123">Özel SıMD algoritmalarını yürütmeden önce, konak makinenin kullanılarak SıMD 'yi destekleyip desteklemediğini denetlemek mümkündür <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType> <xref:System.Boolean> .</span><span class="sxs-lookup"><span data-stu-id="0d335-123">Before executing custom SIMD algorithms, it's possible to check if the host machine supports SIMD by using <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType>, which returns a <xref:System.Boolean>.</span></span> <span data-ttu-id="0d335-124">Bu, SıMD hızlandırmasının belirli bir tür için etkinleştirildiğini garantilemez, ancak bazı türler tarafından desteklendiği bir göstergedir.</span><span class="sxs-lookup"><span data-stu-id="0d335-124">This doesn't guarantee that SIMD-acceleration is enabled for a specific type, but is an indicator that it's supported by some types.</span></span>

## <a name="simple-vectors"></a><span data-ttu-id="0d335-125">Basit vektörler</span><span class="sxs-lookup"><span data-stu-id="0d335-125">Simple Vectors</span></span>

<span data-ttu-id="0d335-126">.NET 'teki en basit SıMD-hızlandırılmış türler <xref:System.Numerics.Vector2> , ve, <xref:System.Numerics.Vector3> <xref:System.Numerics.Vector4> 2, 3 ve 4 değerli vektörlerini temsil eden türlerdir <xref:System.Single> .</span><span class="sxs-lookup"><span data-stu-id="0d335-126">The most primitive SIMD-accelerated types in .NET are <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4> types, which represent vectors with 2, 3, and 4 <xref:System.Single> values.</span></span> <span data-ttu-id="0d335-127">Aşağıdaki örnek, <xref:System.Numerics.Vector2> iki vektör eklemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d335-127">The example below uses <xref:System.Numerics.Vector2> to add two vectors.</span></span>

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResult = v1 + v2;
```

<span data-ttu-id="0d335-128">Ayrıca, ve gibi vektörin diğer matematik özelliklerini hesaplamak için .net vektörlerini kullanmak da mümkündür `Dot product` `Transform` `Clamp` .</span><span class="sxs-lookup"><span data-stu-id="0d335-128">It's also possible to use .NET vectors to calculate other mathematical properties of vectors such as `Dot product`, `Transform`, `Clamp` and so on.</span></span>

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResult1 = Vector2.Dot(v1, v2);
var vResult2 = Vector2.Distance(v1, v2);
var vResult3 = Vector2.Clamp(v1, Vector2.Zero, Vector2.One);
```

## <a name="matrix"></a><span data-ttu-id="0d335-129">Matris</span><span class="sxs-lookup"><span data-stu-id="0d335-129">Matrix</span></span>

<span data-ttu-id="0d335-130"><xref:System.Numerics.Matrix3x2>bir 3X2 matrisini temsil eden ve <xref:System.Numerics.Matrix4x4> bir 4x4 matrisini temsil eden.</span><span class="sxs-lookup"><span data-stu-id="0d335-130"><xref:System.Numerics.Matrix3x2>, which represents a 3x2 matrix, and <xref:System.Numerics.Matrix4x4>, which represents a 4x4 matrix.</span></span> <span data-ttu-id="0d335-131">, Matris ile ilgili hesaplamalar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0d335-131">Can be used for matrix-related calculations.</span></span> <span data-ttu-id="0d335-132">Aşağıdaki örnekte, SıMD kullanarak bir matrisin çarpmayı bir matrisin çarpılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d335-132">The example below demonstrates multiplication of a matrix to its correspondent transpose matrix using SIMD.</span></span>

```csharp
var m1 = new Matrix4x4(
            1.1f, 1.2f, 1.3f, 1.4f,
            2.1f, 2.2f, 3.3f, 4.4f,
            3.1f, 3.2f, 3.3f, 3.4f,
            4.1f, 4.2f, 4.3f, 4.4f);

var m2 = Matrix4x4.Transpose(m1);
var mResult = Matrix4x4.Multiply(m1, m2);
```

## <a name="vectort"></a><span data-ttu-id="0d335-133">Vektör\<T></span><span class="sxs-lookup"><span data-stu-id="0d335-133">Vector\<T></span></span>

<span data-ttu-id="0d335-134">, <xref:System.Numerics.Vector%601> Daha uzun vektörlerini kullanma olanağı sunar.</span><span class="sxs-lookup"><span data-stu-id="0d335-134">The <xref:System.Numerics.Vector%601> gives the ability to use longer vectors.</span></span> <span data-ttu-id="0d335-135">Bir <xref:System.Numerics.Vector%601> Örneğin sayısı sabittir, ancak değeri <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> kodu çalıştıran makinenin CPU 'suna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0d335-135">The count of a <xref:System.Numerics.Vector%601> instance is fixed, but its value <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> depends on the CPU of the machine running the code.</span></span>

<span data-ttu-id="0d335-136">Aşağıdaki örnekte kullanarak uzun diziler öğeleri ekleme gösterilmektedir <xref:System.Numerics.Vector%601> .</span><span class="sxs-lookup"><span data-stu-id="0d335-136">The example below demonstrates adding long arrays elements using <xref:System.Numerics.Vector%601>.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="0d335-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d335-137">Remarks</span></span>

<span data-ttu-id="0d335-138">SıMD 'nin bir darboğazı kaldırmak ve bir sonraki performansı ortaya çıkarmak daha olasıdır.</span><span class="sxs-lookup"><span data-stu-id="0d335-138">SIMD is more likely to remove one bottleneck and expose the next, for example memory throughput.</span></span> <span data-ttu-id="0d335-139">Genel olarak, SıMD kullanmanın performans avantajı, belirli senaryoya bağlı olarak farklılık gösterir ve bazı durumlarda, daha basit bir SıMD olmayan eşdeğer koddan daha kötüleşme de olabilir.</span><span class="sxs-lookup"><span data-stu-id="0d335-139">In general the performance benefit of using SIMD varies depending on the specific scenario, and in some cases it can even perform worse than simpler non-SIMD equivalent code.</span></span>
