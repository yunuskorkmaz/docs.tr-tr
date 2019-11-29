---
title: Varsayılan değerler tablo- C# başvuru
ms.custom: seodec18
description: C# Türlerin varsayılan değerlerini öğrenin.
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 48aa294fa9e37e2e138444e493faa5474011097e
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74551819"
---
# <a name="default-values-table-c-reference"></a>Varsayılan değerler tablosu (C# başvuru)

Aşağıdaki tabloda, C# türlerin varsayılan değerleri gösterilmektedir:

|Tür|Varsayılan değer|
|---------|------------------|
|Herhangi bir başvuru türü|`null`|
|Herhangi bir [yerleşik integral sayısal türü](../builtin-types/integral-numeric-types.md)|0 (sıfır)|
|Herhangi bir [yerleşik kayan nokta sayısal türü](../builtin-types/floating-point-numeric-types.md)|0 (sıfır)|
|[bool](../builtin-types/bool.md)|`false`|
|[char](../builtin-types/char.md)|`'\0'` (U + 0000)|
|[enum](enum.md)|İfade tarafından üretilen değer `(E)0`, burada `E` enum tanımlayıcısıdır.|
|[struct](struct.md)|Tüm değer türü alanları varsayılan değerlerine ve tüm başvuru türü alanlarına ayarlanarak oluşturulan değer `null`.|
|Herhangi bir [Nullable değer türü](../builtin-types/nullable-value-types.md)|<xref:System.Nullable%601.HasValue%2A> özelliği `false` ve <xref:System.Nullable%601.Value%2A> özelliği tanımsız bir örnek. Bu varsayılan değer null olabilen bir değer türünün *null* değeri olarak da bilinir.|

Aşağıdaki örnekte gösterildiği gibi, bir türün varsayılan değerini oluşturmak için [varsayılan işleci](../operators/default.md) kullanın:

```csharp
int a = default(int);
```

7,1 ' C# den başlayarak, türü varsayılan değeri olan bir değişkeni başlatmak için [`default` değişmez](../operators/default.md#default-literal) değerini kullanabilirsiniz:

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
