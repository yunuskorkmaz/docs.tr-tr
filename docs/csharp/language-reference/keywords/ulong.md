---
title: ulong anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
ms.openlocfilehash: 97db22612e900658746f40cd117ff941135027a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660430"
---
# <a name="ulong-c-reference"></a>ulong (C# Başvurusu)

`ulong` Anahtar değerlere göre boyutunu ve aşağıdaki tabloda gösterilen aralığı depolayan bir tamsayı türü gösterir.

|Tür|Aralık|Boyut|.NET türü|
|----------|-----------|----------|-------------------------|
|`ulong`|0 için 18,446,744,073,709,551,615|64-bit işaretsiz tamsayı|<xref:System.UInt64?displayProperty=nameWithType>|

## <a name="literals"></a>Sabit değerler

Bildirmek ve başlatmak bir `ulong` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak).  Tamsayı sabit değeri aralığının dışında ise `ulong` (diğer bir deyişle, bu ise kısa <xref:System.UInt64.MinValue?displayProperty=nameWithType> veya ondan <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 7,934,076,125 eşit ve ikili sabit değerler atanır `ulong` değerleri.

[!code-csharp[ulong](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]

> [!NOTE]
> Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır.

İle başlayarak C# 7.0, birkaç özellik eklenmiştir okunabilirliği artırmak için:

- C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.
- C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak. Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.

Aşağıda bazı örnekler gösterilmektedir.

[!code-csharp[long](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]

Tamsayı sabit değerleri türü gösteren bir son eki de içerebilir. Sonek `UL` veya `ul` sayısal bir değişmez değer olarak kesin bir şekilde tanımlayan bir `ulong` değeri. `L` Soneki gösterir bir `ulong` değişmez değer aşarsa <xref:System.Int64.MaxValue?displayProperty=nameWithType>. Ve `U` veya `u` soneki gösterir bir `ulong` değişmez değer aşarsa <xref:System.UInt32.MaxValue?displayProperty=nameWithType>. Aşağıdaki örnekte `ul` sonek uzun tamsayı belirtmek için:

[!code-csharp[ulsuffix](~/samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]

Değişmez değer bir tamsayı sonek varsa, ilk değerini gösterilebilir aşağıdaki türlerde türünü verilmiştir:

1. [int](int.md)
2. [uint](uint.md)
3. [long](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a>Derleyici aşırı yükleme çözümlemesi

Bir ortak soneki aşırı yüklenmiş yöntem çağırma işleviyle kullanılır. Örneğin, aşağıdaki aşırı yüklenmiş yöntem düşünün `ulong` ve [int](int.md) parametreleri:

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(ulong l) {}
```

Bir sonek ile kullanarak `ulong` parametresi doğru türde, örneğin çağrıldığını güvence altına alır:

```csharp
SampleMethod(5);    // Calling the method with the int parameter
SampleMethod(5UL);  // Calling the method with the ulong parameter
```

## <a name="conversions"></a>Dönüşümler

Önceden tanımlanmış bir örtük dönüştürme vardır `ulong` için [float](float.md), [çift](double.md), veya [ondalık](decimal.md).

Örtülü dönüştürme olmaz yoktur `ulong` için herhangi bir tamsayı türü. Örneğin, aşağıdaki deyim, açık atama olmadan bir derleme hatasına neden olur:

```csharp
long long1 = 8UL;   // Error: no implicit conversion from ulong
```

Önceden tanımlanmış bir örtük dönüştürme vardır [bayt](byte.md), [ushort](ushort.md), [uint](uint.md), veya [char](char.md) için `ulong`.

Ayrıca, kayan nokta türlerinden örtük dönüştürme vardır `ulong`. Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:

```csharp
// Error -- no implicit conversion from double:
ulong x = 3.0;
// OK -- explicit conversion:
ulong y = (ulong)3.0;
```

Karma kayan nokta türleri ve tamsayı türleri aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](float.md) ve [çift](double.md).

Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [Integral türleri](~/_csharplang/spec/types.md#integral-types) içinde [ C# dil belirtimi](../language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.UInt64>
- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Tam Sayı Türleri Tablosu](integral-types-table.md)
- [Yerleşik Türler Tablosu](built-in-types-table.md)
- [Örtük Sayısal Dönüştürmeler Tablosu](implicit-numeric-conversions-table.md)
- [Açık Sayısal Dönüştürmeler Tablosu](explicit-numeric-conversions-table.md)
