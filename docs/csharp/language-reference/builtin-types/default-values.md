---
title: C# Türlerin varsayılan değerleri- C# başvuru
description: Bool, Char, int C# , float, Double ve daha fazlası gibi türlerin varsayılan değerlerini öğrenin.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 2447db25e837cdcd6d67847b8677d7d44da551a9
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964946"
---
# <a name="default-values-of-c-types-c-reference"></a>C# Türlerin varsayılan değerleri (C# başvuru)

Aşağıdaki tabloda, C# türlerin varsayılan değerleri gösterilmektedir:

|Tür|Varsayılan değer|
|---------|------------------|
|Herhangi bir başvuru türü|`null`|
|Herhangi bir [yerleşik integral sayısal türü](integral-numeric-types.md)|0 (sıfır)|
|Herhangi bir [yerleşik kayan nokta sayısal türü](floating-point-numeric-types.md)|0 (sıfır)|
|[bool](bool.md)|`false`|
|[char](char.md)|`'\0'` (U + 0000)|
|[enum](enum.md)|İfade tarafından üretilen değer `(E)0`, burada `E` enum tanımlayıcısıdır.|
|[struct](../keywords/struct.md)|Tüm değer türü alanları varsayılan değerlerine ve tüm başvuru türü alanlarına ayarlanarak oluşturulan değer `null`.|
|Herhangi bir [Nullable değer türü](nullable-value-types.md)|<xref:System.Nullable%601.HasValue%2A> özelliği `false` ve <xref:System.Nullable%601.Value%2A> özelliği tanımsız bir örnek. Bu varsayılan değer null olabilen bir değer türünün *null* değeri olarak da bilinir.|

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

Çalışma zamanında, <xref:System.Type?displayProperty=nameWithType> örneği bir değer türünü temsil ediyorsa, türün varsayılan değerini almak üzere parametresiz oluşturucuyu çağırmak için <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> yöntemini kullanabilirsiniz.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Varsayılan değerler](~/_csharplang/spec/variables.md#default-values)
- [Varsayılan oluşturucular](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [Oluşturucular](../../programming-guide/classes-and-structs/constructors.md)
