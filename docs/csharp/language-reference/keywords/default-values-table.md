---
title: Varsayılan değerler tablosu (C# Başvurusu)
description: C# değer türleri için varsayılan değerleri ne olduğunu öğrenin.
ms.date: 08/23/2018
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.openlocfilehash: 184a9f42ddd3654a81aef0b7ce35e404de2d4bb9
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935845"
---
# <a name="default-values-table-c-reference"></a>Varsayılan değerler tablosu (C# Başvurusu)

Varsayılan değerleri aşağıdaki tabloda gösterilmektedir [değer türleri](value-types.md).

|Değer türü|Varsayılan değer|
|----------------|-------------------|
|[bool](bool.md)|`false`|
|[byte](byte.md)|0|
|[char](char.md)|'\0'|
|[decimal](decimal.md)|0M|
|[double](double.md)|0,0 D|
|[enum](enum.md)|Değer ifade tarafından üretilen `(E)0`burada `E` numaralandırma tanımlayıcı.|
|[float](float.md)|0.0F|
|[int](int.md)|0|
|[long](long.md)|0 M|
|[sbyte](sbyte.md)|0|
|[short](short.md)|0|
|[struct](struct.md)|Değer üretilmediğini tüm değer tür alanları varsayılan değerlerine ve tüm başvuru türü alanları ayarlayarak `null`.|
|[uint](uint.md)|0|
|[ulong](ulong.md)|0|
|[ushort](ushort.md)|0|

## <a name="remarks"></a>Açıklamalar

C# dilinde başlatılmamış değişkenler kullanamazsınız. Varsayılan değer türüne sahip bir değişken başlatabilirsiniz. Bir yöntemin varsayılan değerini belirtmek için varsayılan değer olan bir türü kullanabilirsiniz [isteğe bağlı bağımsız değişkeni](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments).

Kullanım [varsayılan değer ifadesi](../../programming-guide/statements-expressions-operators/default-value-expressions.md) aşağıdaki örnekte gösterildiği gibi bir türü varsayılan değerini oluşturmak için:

```csharp
int a = default(int);
```

Kullanabileceğiniz C# 7.1 ile başlayarak, [ `default` değişmez değer](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) varsayılan değer türüne sahip bir değişken başlatmak için:

```csharp
int a = default;
```

Aşağıdaki örnekte gösterildiği gibi bir değer türünün varsayılan değeri üretmek için varsayılan oluşturucu veya örtülü varsayılan oluşturucu kullanabilirsiniz. Oluşturucular hakkında daha fazla bilgi için bkz. [oluşturucular](../../programming-guide/classes-and-structs/constructors.md) makalesi.

```csharp
int a = new int();
```

Varsayılan değer aşağıdakilerden [başvuru türüne](reference-types.md) olduğu `null`. Varsayılan değer olan bir [boş değer atanabilir tür](../../programming-guide/nullable-types/index.md) bir örneği olduğu <xref:System.Nullable%601.HasValue%2A> özelliği `false` ve <xref:System.Nullable%601.Value%2A> özelliği tanımsız.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Türler için başvuru tabloları](reference-tables-for-types.md)
- [Değer türleri](value-types.md)
- [Değer türleri tablosu](value-types-table.md)
- [Yerleşik türler tablosu](built-in-types-table.md)
