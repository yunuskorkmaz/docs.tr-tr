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
# <a name="nint-and-nuint-types-c-reference"></a>`nint` ve `nuint` türleri (C# Başvurusu)

C# 9,0 ' den başlayarak, `nint` ve `nuint` anahtar sözcüklerini kullanarak *Yerel boyutlu tamsayılar* tanımlayabilirsiniz. Bunlar, 32 bit işlemde çalışırken 32 bitlik tamsayılardır veya 64 bit süreçte çalışırken 64 bit tamsayılardır. Bunlar, birlikte çalışma senaryoları, alt düzey kitaplıklar ve tamsayı matematiğinin yoğun kullanıldığı senaryolarda performansı iyileştirmek için kullanılabilirler.

Yerel boyutlu tamsayı türleri dahili olarak .NET türleri ve olarak temsil edilir <xref:System.IntPtr?displayProperty=nameWithType> <xref:System.UIntPtr?displayProperty=nameWithType> . Diğer sayısal türlerin aksine, anahtar sözcükler yalnızca türlerin diğer adları değildir. Aşağıdaki deyimler eşdeğer değildir:

```csharp
nint a = 1;
System.IntPtr a = 1;
```

Derleyici, için `nint` ve için `nuint` uygun olan ve tamsayı türleri için uygun olan işlemleri ve dönüştürmeleri sağlar.

## <a name="run-time-native-integer-size"></a>Çalışma zamanı yerel tamsayı boyutu

Çalışma zamanında yerel boyutlu bir tamsayı boyutunu almak için kullanabilirsiniz `sizeof()` . Ancak, kodun güvenli olmayan bir bağlamda derlenmesi gerekir. Örnek:

:::code language="csharp" source="snippets/shared/NativeIntegerTypes.cs" id="SizeOf":::

Statik ve özelliklerden eşdeğer değeri de alabilirsiniz <xref:System.IntPtr.Size?displayProperty=nameWithType> <xref:System.UIntPtr.Size?displayProperty=nameWithType> .

## <a name="minvalue-and-maxvalue"></a>MinValue ve MaxValue

Çalışma zamanında yerel boyutlu tamsayıların en düşük ve en büyük değerlerini almak için, `MinValue` `MaxValue` `nint` `nuint` Aşağıdaki örnekte olduğu gibi, ve anahtar sözcükleriyle statik özellikler kullanın:

:::code language="csharp" source="snippets/shared/NativeIntegerTypes.cs" id="MinMax":::

## <a name="constants"></a>Sabitler

Aşağıdaki aralıklardaki sabit değerleri kullanabilirsiniz:

* İçin `nint` : <xref:System.Int32.MinValue?displayProperty=nameWithType> <xref:System.Int32.MaxValue?displayProperty=nameWithType> .
* İçin `nuint` : <xref:System.UInt32.MinValue?displayProperty=nameWithType> <xref:System.UInt32.MaxValue?displayProperty=nameWithType> .

## <a name="conversions"></a>Dönüşümler

Derleyici, diğer sayısal türlere örtük ve açık dönüştürmeler sağlar. Daha fazla bilgi için bkz. [yerleşik sayısal dönüştürmeler](numeric-conversions.md).

## <a name="literals"></a>Değişmez Değerler

Yerel boyutlu tamsayı değişmez değerleri için doğrudan bir sözdizimi yoktur. Bir sabit değerin bir yerel boyutlu tamsayı olduğunu göstermek için bir sonek yoktur (örneğin,) `L` `long` . Bunun yerine, diğer tamsayı değerlerinin örtük veya açık kayıtlarını kullanabilirsiniz. Örnek:

```csharp
nint a = 42
nint a = (nint)42;
```

## <a name="unsupported-intptruintptr-members"></a>Desteklenmeyen IntPtr/UIntPtr üyeleri

<xref:System.IntPtr> <xref:System.UIntPtr> Ve türleri için aşağıdaki üyeleri desteklenmez `nint` `nuint` :

* Parametreli oluşturucular
* <xref:System.IntPtr.Add(System.IntPtr,System.Int32)>
* <xref:System.IntPtr.CompareTo%2A>
* <xref:System.IntPtr.Size> -Bunun yerine [sizeOf ()](#run-time-native-integer-size) kullanın. `nint.Size`, Desteklenmese de, `IntPtr.Size` eşdeğer bir değer almak için kullanabilirsiniz.
* <xref:System.IntPtr.Subtract(System.IntPtr,System.Int32)>
* <xref:System.IntPtr.ToInt32%2A>
* <xref:System.IntPtr.ToInt64%2A>
* <xref:System.IntPtr.ToPointer%2A>
* <xref:System.IntPtr.Zero> -Bunun yerine 0 kullanın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için C# [dil belirtimi](~/_csharplang/spec/introduction.md) ve c# 9,0 özellik teklifi notlarındaki [Yerel boyutlu tamsayılar](~/_csharplang/proposals/csharp-9.0/native-integers.md) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Değer türleri](value-types.md)
- [Tamsayı sayısal türler](integral-numeric-types.md)
- [Yerleşik sayısal dönüşümler](numeric-conversions.md)
