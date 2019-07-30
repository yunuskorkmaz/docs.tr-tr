---
title: Varsayılan değerler tablo- C# başvuru
ms.custom: seodec18
description: C# Türlerin varsayılan değerlerini öğrenin.
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 23fba8269670156000cb68b3aa07ae7c770eada1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627745"
---
# <a name="default-values-table-c-reference"></a>Varsayılan değerler tablosu (C# başvuru)

Aşağıdaki tabloda, C# türlerin varsayılan değerleri gösterilmektedir:

|Tür|Varsayılan değer|
|---------|------------------|
|Herhangi bir başvuru türü|`null`|
|Herhangi bir [yerleşik integral sayısal türü](../builtin-types/integral-numeric-types.md)|0 (sıfır)|
|Herhangi bir [yerleşik kayan nokta sayısal türü](../builtin-types/floating-point-numeric-types.md)|0 (sıfır)|
|[bool](bool.md)|`false`|
|[char](char.md)|`'\0'`(U + 0000)|
|[enum](enum.md)|İfade `(E)0`tarafından üretilen `E` , numaralandırma tanımlayıcısı olan değer.|
|[struct](struct.md)|Tüm değer türü alanları varsayılan değerlerine ve tüm başvuru türü alanlarına `null`ayarlanarak oluşturulan değer.|
|Herhangi bir [Nullable değer türü](../../programming-guide/nullable-types/index.md)|<xref:System.Nullable%601.HasValue%2A> Özelliği ve özelliği<xref:System.Nullable%601.Value%2A> tanımsız olan bir örnek. `false` Bu varsayılan değer null yapılabilir değer türünün *null* değeri olarak da bilinir.|

Aşağıdaki örnekte gösterildiği gibi, bir türün varsayılan değerini oluşturmak için [varsayılan değer ifadesini](../../programming-guide/statements-expressions-operators/default-value-expressions.md) kullanın:

```csharp
int a = default(int);
```

7,1 ' C# den başlayarak, bir değişkeni türünün varsayılan değeri ile başlatmak için [ `default` değişmez](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) değeri kullanabilirsiniz:

```csharp
int a = default;
```

Bir değer türü için, örtük parametresiz Oluşturucu, aşağıdaki örnekte gösterildiği gibi türün varsayılan değerini de üretir:

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Varsayılan değerler](~/_csharplang/spec/variables.md#default-values)
- [Varsayılan oluşturucular](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# anahtar sözcükleri](index.md)
- [Yerleşik türler tablosu](built-in-types-table.md)
- [Oluşturucular](../../programming-guide/classes-and-structs/constructors.md)
