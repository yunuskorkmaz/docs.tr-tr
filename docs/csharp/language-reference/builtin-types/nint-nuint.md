---
description: "C 'de yerleşik nınt ve nuınt türleri hakkında bilgi edinin #"
title: nint ve nuınt türleri-C# başvurusu
ms.date: 03/15/2021
f1_keywords:
- nint_CSharpKeyword
- nuint_CSharpKeyword
helpviewer_keywords:
- nint data type [C#]
- nuint data type [C#]
ms.openlocfilehash: fc779731d7f67fd0239f095d1dd17217a56622f6
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760840"
---
# <a name="nint-and-nuint-types-c-reference"></a><span data-ttu-id="3b050-103">`nint` ve `nuint` türleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3b050-103">`nint` and `nuint` types (C# reference)</span></span>

<span data-ttu-id="3b050-104">C# 9,0 ' den başlayarak, `nint` ve `nuint` anahtar sözcüklerini kullanarak *Yerel boyutlu tamsayılar* tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b050-104">Starting in C# 9.0, you can use the `nint` and `nuint` keywords to define *native-sized integers*.</span></span> <span data-ttu-id="3b050-105">Bunlar, 32 bit işlemde çalışırken 32 bitlik tamsayılardır veya 64 bit süreçte çalışırken 64 bit tamsayılardır.</span><span class="sxs-lookup"><span data-stu-id="3b050-105">These are 32-bit integers when running in a 32-bit process, or 64-bit integers when running in a 64-bit process.</span></span> <span data-ttu-id="3b050-106">Bunlar, birlikte çalışma senaryoları, alt düzey kitaplıklar ve tamsayı matematiğinin yoğun kullanıldığı senaryolarda performansı iyileştirmek için kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="3b050-106">They can be used for interop scenarios, low-level libraries, and to optimize performance in scenarios where integer math is used extensively.</span></span>

<span data-ttu-id="3b050-107">Yerel boyutlu tamsayı türleri dahili olarak .NET türleri ve olarak temsil edilir <xref:System.IntPtr?displayProperty=nameWithType> <xref:System.UIntPtr?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3b050-107">The native-sized integer types are represented internally as the .NET types <xref:System.IntPtr?displayProperty=nameWithType> and <xref:System.UIntPtr?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3b050-108">Diğer sayısal türlerin aksine, anahtar sözcükler yalnızca türlerin diğer adları değildir.</span><span class="sxs-lookup"><span data-stu-id="3b050-108">Unlike other numeric types, the keywords are not simply aliases for the types.</span></span> <span data-ttu-id="3b050-109">Aşağıdaki deyimler eşdeğer değildir:</span><span class="sxs-lookup"><span data-stu-id="3b050-109">The following statements are not equivalent:</span></span>

```csharp
nint a = 1;
System.IntPtr a = 1;
```

<span data-ttu-id="3b050-110">Derleyici, için `nint` ve için `nuint` uygun olan ve tamsayı türleri için uygun olan işlemleri ve dönüştürmeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b050-110">The compiler provides operations and conversions for `nint` and `nuint` that are appropriate for integer types.</span></span>

## <a name="run-time-native-integer-size"></a><span data-ttu-id="3b050-111">Çalışma zamanı yerel tamsayı boyutu</span><span class="sxs-lookup"><span data-stu-id="3b050-111">Run-time native integer size</span></span>

<span data-ttu-id="3b050-112">Çalışma zamanında yerel boyutlu bir tamsayı boyutunu almak için kullanabilirsiniz `sizeof()` .</span><span class="sxs-lookup"><span data-stu-id="3b050-112">To get the size of a native-sized integer at run time, you can use `sizeof()`.</span></span> <span data-ttu-id="3b050-113">Ancak, kodun güvenli olmayan bir bağlamda derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b050-113">However, the code must be compiled in an unsafe context.</span></span> <span data-ttu-id="3b050-114">Örnek:</span><span class="sxs-lookup"><span data-stu-id="3b050-114">For example:</span></span>

:::code language="csharp" source="snippets/shared/NativeIntegerTypes.cs" id="SizeOf":::

<span data-ttu-id="3b050-115">Statik ve özelliklerden eşdeğer değeri de alabilirsiniz <xref:System.IntPtr.Size?displayProperty=nameWithType> <xref:System.UIntPtr.Size?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3b050-115">You can also get the equivalent value from the static <xref:System.IntPtr.Size?displayProperty=nameWithType> and <xref:System.UIntPtr.Size?displayProperty=nameWithType> properties.</span></span>

## <a name="minvalue-and-maxvalue"></a><span data-ttu-id="3b050-116">MinValue ve MaxValue</span><span class="sxs-lookup"><span data-stu-id="3b050-116">MinValue and MaxValue</span></span>

<span data-ttu-id="3b050-117">Çalışma zamanında yerel boyutlu tamsayıların en düşük ve en büyük değerlerini almak için, `MinValue` `MaxValue` `nint` `nuint` Aşağıdaki örnekte olduğu gibi, ve anahtar sözcükleriyle statik özellikler kullanın:</span><span class="sxs-lookup"><span data-stu-id="3b050-117">To get the minimum and maximum values of native-sized integers at run time, use `MinValue` and `MaxValue` as static properties with the `nint` and `nuint` keywords, as in the following example:</span></span>

:::code language="csharp" source="snippets/shared/NativeIntegerTypes.cs" id="MinMax":::

## <a name="constants"></a><span data-ttu-id="3b050-118">Sabitler</span><span class="sxs-lookup"><span data-stu-id="3b050-118">Constants</span></span>

<span data-ttu-id="3b050-119">Aşağıdaki aralıklardaki sabit değerleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3b050-119">You can use constant values in the following ranges:</span></span>

* <span data-ttu-id="3b050-120">İçin `nint` : <xref:System.Int32.MinValue?displayProperty=nameWithType> <xref:System.Int32.MaxValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3b050-120">For `nint`: <xref:System.Int32.MinValue?displayProperty=nameWithType> to <xref:System.Int32.MaxValue?displayProperty=nameWithType>.</span></span>
* <span data-ttu-id="3b050-121">İçin `nuint` : <xref:System.UInt32.MinValue?displayProperty=nameWithType> <xref:System.UInt32.MaxValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3b050-121">For `nuint`: <xref:System.UInt32.MinValue?displayProperty=nameWithType> to <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>

## <a name="conversions"></a><span data-ttu-id="3b050-122">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="3b050-122">Conversions</span></span>

<span data-ttu-id="3b050-123">Derleyici, diğer sayısal türlere örtük ve açık dönüştürmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b050-123">The compiler provides implicit and explicit conversions to other numeric types.</span></span> <span data-ttu-id="3b050-124">Daha fazla bilgi için bkz. [yerleşik sayısal dönüştürmeler](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="3b050-124">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="literals"></a><span data-ttu-id="3b050-125">Değişmez Değerler</span><span class="sxs-lookup"><span data-stu-id="3b050-125">Literals</span></span>

<span data-ttu-id="3b050-126">Yerel boyutlu tamsayı değişmez değerleri için doğrudan bir sözdizimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3b050-126">There's no direct syntax for native-sized integer literals.</span></span> <span data-ttu-id="3b050-127">Bir sabit değerin bir yerel boyutlu tamsayı olduğunu göstermek için bir sonek yoktur (örneğin,) `L` `long` .</span><span class="sxs-lookup"><span data-stu-id="3b050-127">There's no suffix to indicate that a literal is a native-sized integer, such as `L` to indicate a `long`.</span></span> <span data-ttu-id="3b050-128">Bunun yerine, diğer tamsayı değerlerinin örtük veya açık kayıtlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b050-128">You can use implicit or explicit casts of other integer values instead.</span></span> <span data-ttu-id="3b050-129">Örnek:</span><span class="sxs-lookup"><span data-stu-id="3b050-129">For example:</span></span>

```csharp
nint a = 42
nint a = (nint)42;
```

## <a name="unsupported-intptruintptr-members"></a><span data-ttu-id="3b050-130">Desteklenmeyen IntPtr/UIntPtr üyeleri</span><span class="sxs-lookup"><span data-stu-id="3b050-130">Unsupported IntPtr/UIntPtr members</span></span>

<span data-ttu-id="3b050-131"><xref:System.IntPtr> <xref:System.UIntPtr> Ve türleri için aşağıdaki üyeleri desteklenmez `nint` `nuint` :</span><span class="sxs-lookup"><span data-stu-id="3b050-131">The following members of <xref:System.IntPtr> and <xref:System.UIntPtr> aren't supported for `nint` and `nuint` types:</span></span>

* <span data-ttu-id="3b050-132">Parametreli oluşturucular</span><span class="sxs-lookup"><span data-stu-id="3b050-132">Parameterized constructors</span></span>
* <xref:System.IntPtr.Add(System.IntPtr,System.Int32)>
* <xref:System.IntPtr.CompareTo%2A>
* <span data-ttu-id="3b050-133"><xref:System.IntPtr.Size> -Bunun yerine [sizeOf ()](#run-time-native-integer-size) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3b050-133"><xref:System.IntPtr.Size> - Use [sizeOf()](#run-time-native-integer-size) instead.</span></span> <span data-ttu-id="3b050-134">`nint.Size`, Desteklenmese de, `IntPtr.Size` eşdeğer bir değer almak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b050-134">Although `nint.Size` isn't supported, you can use `IntPtr.Size` to get an equivalent value.</span></span>
* <xref:System.IntPtr.Subtract(System.IntPtr,System.Int32)>
* <xref:System.IntPtr.ToInt32%2A>
* <xref:System.IntPtr.ToInt64%2A>
* <xref:System.IntPtr.ToPointer%2A>
* <span data-ttu-id="3b050-135"><xref:System.IntPtr.Zero> -Bunun yerine 0 kullanın.</span><span class="sxs-lookup"><span data-stu-id="3b050-135"><xref:System.IntPtr.Zero> - Use 0 instead.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3b050-136">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3b050-136">C# language specification</span></span>

<span data-ttu-id="3b050-137">Daha fazla bilgi için C# [dil belirtimi](~/_csharplang/spec/introduction.md) ve c# 9,0 özellik teklifi notlarındaki [Yerel boyutlu tamsayılar](~/_csharplang/proposals/csharp-9.0/native-integers.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3b050-137">For more information, see the [C# language specification](~/_csharplang/spec/introduction.md) and the [Native-sized integers](~/_csharplang/proposals/csharp-9.0/native-integers.md) section of the C# 9.0 feature proposal notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b050-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b050-138">See also</span></span>

- [<span data-ttu-id="3b050-139">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3b050-139">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3b050-140">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="3b050-140">Value types</span></span>](value-types.md)
- [<span data-ttu-id="3b050-141">Tamsayı sayısal türler</span><span class="sxs-lookup"><span data-stu-id="3b050-141">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="3b050-142">Yerleşik sayısal dönüşümler</span><span class="sxs-lookup"><span data-stu-id="3b050-142">Built-in numeric conversions</span></span>](numeric-conversions.md)
