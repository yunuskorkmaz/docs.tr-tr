---
title: C# türlerinin varsayılan değerleri-C# başvurusu
description: Bool, Char, int, float, Double ve daha fazlası gibi C# türlerinin varsayılan değerlerini öğrenin.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 72d6249ed56ae6ae34a6f51102e1e7bbd3f64ab7
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104121"
---
# <a name="default-values-of-c-types-c-reference"></a>C# türlerinin varsayılan değerleri (C# Başvurusu)

Aşağıdaki tabloda C# türlerinin varsayılan değerleri gösterilmektedir:

|Tür|Varsayılan değer|
|---------|------------------|
|Herhangi bir [başvuru türü](../keywords/reference-types.md)|`null`|
|Herhangi bir [yerleşik integral sayısal türü](integral-numeric-types.md)|0 (sıfır)|
|Herhangi bir [yerleşik kayan nokta sayısal türü](floating-point-numeric-types.md)|0 (sıfır)|
|[bool](bool.md)|`false`|
|[char](char.md)|`'\0'` (U + 0000)|
|[yardımının](enum.md)|İfade tarafından üretilen `(E)0` , `E` numaralandırma tanımlayıcısı olan değer.|
|[sýný](struct.md)|Tüm değer türü alanları varsayılan değerlerine ve tüm başvuru türü alanlarına ayarlanarak oluşturulan değer `null` .|
|Herhangi bir [Nullable değer türü](nullable-value-types.md)|<xref:System.Nullable%601.HasValue%2A>Özelliği `false` ve özelliği tanımsız olan bir örnek <xref:System.Nullable%601.Value%2A> . Bu varsayılan değer null olabilen bir değer türünün *null* değeri olarak da bilinir.|

Aşağıdaki örnekte gösterildiği gibi, bir türün varsayılan değerini oluşturmak için [ `default` işlecini](../operators/default.md#default-operator) kullanın:

```csharp
int a = default(int);
```

C# 7,1 ' den başlayarak, bir değişkeni türünün varsayılan değeri ile başlatmak için [ `default` değişmez](../operators/default.md#default-literal) değeri kullanabilirsiniz:

```csharp
int a = default;
```

Bir değer türü için, örtük parametresiz Oluşturucu, aşağıdaki örnekte gösterildiği gibi türün varsayılan değerini de üretir:

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

Çalışma zamanında, <xref:System.Type?displayProperty=nameWithType> örnek bir değer türünü temsil ediyorsa, <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> türünün varsayılan değerini almak üzere parametresiz oluşturucuyu çağırmak için yöntemini kullanabilirsiniz.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Varsayılan değerler](~/_csharplang/spec/variables.md#default-values)
- [Varsayılan oluşturucular](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Oluşturucular](../../programming-guide/classes-and-structs/constructors.md)
