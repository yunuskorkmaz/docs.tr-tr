---
title: C# türlerinin varsayılan değerleri - C# başvurusu
description: Bool, char, int, float, double ve daha fazlası gibi C# türlerinin varsayılan değerlerini öğrenin.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 93b6079b9a3bbf6d537094cab9dfb305ace7f6bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625871"
---
# <a name="default-values-of-c-types-c-reference"></a>C# türlerinin varsayılan değerleri (C# başvurusu)

Aşağıdaki tabloc# türlerinin varsayılan değerlerini gösterir:

|Tür|Varsayılan değer|
|---------|------------------|
|Herhangi bir başvuru türü|`null`|
|Herhangi bir [dahili integral sayısal tip](integral-numeric-types.md)|0 (sıfır)|
|Herhangi bir [yerleşik kayan nokta sayısal türü](floating-point-numeric-types.md)|0 (sıfır)|
|[bool](bool.md)|`false`|
|[char](char.md)|`'\0'`(U+0000)|
|[Enum](enum.md)|İfade `(E)0`tarafından üretilen değer `E` , enum tanımlayıcısı nerededir.|
|[Yapı](struct.md)|Tüm değer türü alanlarını varsayılan değerlerine ve tüm başvuru türü `null`alanlarının .'a ayarlanmasıyla üretilen değer.|
|Herhangi bir [nullable değer türü](nullable-value-types.md)|Özelliğin ve <xref:System.Nullable%601.HasValue%2A> özelliğin `false` <xref:System.Nullable%601.Value%2A> tanımsız olduğu bir örnek. Bu varsayılan değer, nullable değer türünün *null* değeri olarak da bilinir.|

Aşağıdaki örnekte görüldüğü gibi, bir türün varsayılan değerini üretmek için [varsayılan işleci](../operators/default.md) kullanın:

```csharp
int a = default(int);
```

C# 7.1 ile başlayarak, türünün varsayılan değerine sahip bir değişkeni başlatmak için [ `default` literal'ı](../operators/default.md#default-literal) kullanabilirsiniz:

```csharp
int a = default;
```

Bir değer türü için, örtük parametresiz oluşturucu da aşağıdaki örnekte görüldüğü gibi, türün varsayılan değerini üretir:

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

Çalışma zamanında, <xref:System.Type?displayProperty=nameWithType> örnek bir değer türünü temsil ederse, yöntem in türün varsayılan değerini elde etmek için parametresiz oluşturucuyu çağırmak için kullanabilirsiniz. <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType>

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Varsayılan değerler](~/_csharplang/spec/variables.md#default-values)
- [Varsayılan oluşturucular](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Oluşturucular](../../programming-guide/classes-and-structs/constructors.md)
