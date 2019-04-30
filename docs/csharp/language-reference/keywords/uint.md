---
title: uint anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords:
- uint keyword [C#]
ms.openlocfilehash: e22468eea63ce082f2e9842e6ec307aba1888964
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660443"
---
# <a name="uint-c-reference"></a>uint (C# Başvurusu)

`uint` Anahtar sözcüğü, boyutu ve aşağıdaki tabloda gösterilen aralığı göre değerler depolayan bir tamsayı türü belirtir.

|Tür|Aralık|Boyut|.NET türü|
|----------|-----------|----------|-------------------------|
|`uint`|0 için 4.294.967.295'e|32-bit işaretsiz tamsayı|<xref:System.UInt32?displayProperty=nameWithType>|

**Not** `uint` türü CLS uyumlu değil. Kullanım `int` mümkün olduğunda.

## <a name="literals"></a>Sabit değerler

Bildirmek ve başlatmak bir `uint` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak). Tamsayı sabit değeri aralığının dışında ise `uint` (diğer bir deyişle, bu ise kısa <xref:System.UInt32.MinValue?displayProperty=nameWithType> veya ondan <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 3,000,000,000 eşit ve ikili sabit değerler atanır `uint` değerleri.

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]

> [!NOTE]
> Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır.

İle başlayarak C# 7.0, birkaç özellik eklenmiştir okunabilirliği artırmak için:

- C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.
- C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak. Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.

Aşağıda bazı örnekler gösterilmektedir.

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]

Tamsayı sabit değerleri türü gösteren bir son eki de içerebilir. Sonek `U` veya 'u' gösterir ya da bir `uint` veya `ulong`sayısal değerine bağlı olarak. Aşağıdaki örnekte `u` sonek işaretsiz bir tamsayı her iki türdeki belirtmek için. İlk değişmez değer olduğunu unutmayın bir `uint` değeri olduğundan küçüktür <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, ikinci olmakla birlikte bir `ulong` değeri büyük olduğundan <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.

[!code-csharp[usuffix](~/samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]

Değişmez değer bir tamsayı sonek varsa, ilk değerini gösterilebilir aşağıdaki türlerde türünü verilmiştir:

1. [int](int.md)
2. `uint`
3. [long](long.md)
4. [ulong](ulong.md)

## <a name="conversions"></a>Dönüşümler

Önceden tanımlanmış bir örtük dönüştürme vardır `uint` için [uzun](long.md), [ulong](ulong.md), [float](float.md), [çift](double.md), veya [ ondalık](decimal.md). Örneğin:

```csharp
float myFloat = 4294967290;   // OK: implicit conversion to float
```

Önceden tanımlanmış bir örtük dönüştürme vardır [bayt](byte.md), [ushort](ushort.md), veya [char](char.md) için `uint`. Aksi takdirde, bir dönüştürme kullanmanız gerekir. Örneğin, aşağıdaki atama deyimi, bir yayın olmadan bir derleme hatasına neden olur:

```csharp
long aLong = 22;
// Error -- no implicit conversion from long:
uint uInt1 = aLong;
// OK -- explicit conversion:
uint uInt2 = (uint)aLong;
```

Ayrıca örtülü dönüştürme için kayan nokta türlerinden fark `uint`. Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:

```csharp
// Error -- no implicit conversion from double:
uint x = 3.0;
// OK -- explicit conversion:
uint y = (uint)3.0;
```

Karma kayan nokta türleri ve tamsayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](float.md) ve [çift](double.md).

Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [Integral türleri](~/_csharplang/spec/types.md#integral-types) içinde [ C# dil belirtimi](../language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.UInt32>
- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Tam Sayı Türleri Tablosu](integral-types-table.md)
- [Yerleşik Türler Tablosu](built-in-types-table.md)
- [Örtük Sayısal Dönüştürmeler Tablosu](implicit-numeric-conversions-table.md)
- [Açık Sayısal Dönüştürmeler Tablosu](explicit-numeric-conversions-table.md)