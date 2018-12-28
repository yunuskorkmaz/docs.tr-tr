---
title: ushort anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
ms.openlocfilehash: 934e25576a8a24c176a54ec6af984459b513fe5a
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614470"
---
# <a name="ushort-c-reference"></a>ushort (C# Başvurusu)

`ushort` Anahtar değerlere göre boyutunu ve aşağıdaki tabloda gösterilen aralığı depolayan bir tam sayı veri türü belirtir.

|Tür|Aralık|Boyut|.NET türü|
|----------|-----------|----------|-------------------------|
|`ushort`|0 ile 65.535 arasındaki|16 bit işaretsiz tamsayı|<xref:System.UInt16?displayProperty=nameWithType>|

## <a name="literals"></a>Sabit değerler

Bildirmek ve başlatmak bir `ushort` değişkenini değişmez değer ondalık, onaltılık bir sabit değer atama veya (C# 7.0 ile için sabit bir ikili başlayarak). Tamsayı sabit değeri aralığının dışında ise `ushort` (diğer bir deyişle, bu ise kısa <xref:System.UInt16.MinValue?displayProperty=nameWithType> veya ondan <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), bir derleme hatası oluşur.

Aşağıdaki örnekte, tamsayılar ondalık, onaltılık, gösterilen 65,034 eşit ve ikili sabit dizeler öğesinden örtük olarak dönüştürülür [int](int.md) için `ushort` değerleri.

[!code-csharp[UShort](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]

> [!NOTE]
> Önek kullanın `0x` veya `0X` onaltılık bir sabit değer ve öneki belirtmek için `0b` veya `0B` ikili bir sabit belirtmek için. Ondalık değişmez değerler, önek vardır.

İle başlayarak C# 7.0, birkaç özellik eklenmiştir okunabilirliği artırmak için:

- C# 7.0, alt çizgi karakteri kullanımına izin verir `_`, basamak ayırıcı olarak.
- C# 7.2 sağlayan `_` sonra öneki için bir ikili veya onaltılık sabit basamak ayırıcı olarak kullanılacak. Ondalık bir sabit değer, bir alt çizgi olan izin verilen değil.

Aşağıda bazı örnekler gösterilmektedir.

[!code-csharp[UShort](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]

## <a name="compiler-overload-resolution"></a>Derleyici aşırı yükleme çözümlemesi

Aşırı yüklenmiş yöntemler çağırdığınızda, bir yayın kullanılmalıdır. Örneğin, aşağıdaki aşırı yüklenmiş yöntem düşünün `ushort` ve [int](int.md) parametreleri:

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(ushort s) {}
```

Kullanarak `ushort` atama doğru tür, örneğin çağrıldığını güvence altına alır:

```csharp
// Calls the method with the int parameter:
SampleMethod(5);
// Calls the method with the ushort parameter:
SampleMethod((ushort)5);
```

## <a name="conversions"></a>Dönüşümler

Önceden tanımlanmış bir örtük dönüştürme vardır `ushort` için [int](int.md), [uint](uint.md), [uzun](long.md), [ulong](ulong.md), [float ](float.md), [çift](double.md), veya [ondalık](decimal.md).

Önceden tanımlanmış bir örtük dönüştürme vardır [bayt](byte.md) veya [char](char.md) için `ushort`. Aksi halde bir tür dönüştürme açık bir dönüştürme gerçekleştirmek için kullanılması gerekir. Örneğin, aşağıdaki iki göz önünde bulundurun `ushort` değişkenleri `x` ve `y`:

```csharp
ushort x = 5, y = 12;
```

Atama işlecinin sağ tarafında aritmetik ifadenin değerlendirdiği çünkü aşağıdaki atama deyimi bir derleme hatası üretecektir `int` varsayılan olarak.

```csharp
ushort z = x + y;   // Error: conversion from int to ushort
```

Bu sorunu gidermek için bir tür dönüştürme kullanın:

```csharp
ushort z = (ushort)(x + y);   // OK: explicit conversion
```

Ancak hedef değişkeni aynı depolama boyutuna veya daha büyük bir depolama boyutu sahip olduğu aşağıdaki deyimleri kullanmak mümkündür:

```csharp
int m = x + y;
long n = x + y;
```

Ayrıca örtülü dönüştürme için kayan nokta türlerinden fark `ushort`. Örneğin, bir açık tür dönüştürme kullanılmadığı sürece aşağıdaki deyim, bir derleyici hatası oluşturur:

```csharp
// Error -- no implicit conversion from double:
ushort x = 3.0;
// OK -- explicit conversion:
ushort y = (ushort)3.0;
```

Karma kayan nokta türleri ve tamsayı türleri ile aritmetik ifadeler hakkında daha fazla bilgi için bkz: [float](float.md) ve [çift](double.md).

Örtük sayısal dönüştürme kuralları hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [Integral türleri](~/_csharplang/spec/types.md#integral-types) içinde [ C# dil belirtimi](../language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.UInt16>
- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Tam Sayı Türleri Tablosu](integral-types-table.md)
- [Yerleşik Türler Tablosu](built-in-types-table.md)
- [Örtük Sayısal Dönüştürmeler Tablosu](implicit-numeric-conversions-table.md)
- [Açık Sayısal Dönüştürmeler Tablosu](explicit-numeric-conversions-table.md)
