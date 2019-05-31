---
title: Varsayılan değerler tablosu - C# başvurusu
ms.custom: seodec18
description: C# değer türleri için varsayılan değerleri ne olduğunu öğrenin.
ms.date: 08/23/2018
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- parameterless constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], parameterless constructor
- types [C#], parameterless constructor return values
ms.openlocfilehash: 4fc9a35f69540e047a97c21788015ca8e54068a0
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422035"
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

Aşağıdaki örnekte gösterildiği gibi bir değer türünün varsayılan değeri üretmek için parametresiz bir oluşturucu ya da örtük parametresiz oluşturucu kullanabilirsiniz. Oluşturucular hakkında daha fazla bilgi için bkz. [oluşturucular](../../programming-guide/classes-and-structs/constructors.md) makalesi.

```csharp
int a = new int();
```

Varsayılan değer aşağıdakilerden [başvuru türüne](reference-types.md) olduğu `null`. Varsayılan değer olan bir [boş değer atanabilir tür](../../programming-guide/nullable-types/index.md) bir örneği olduğu <xref:System.Nullable%601.HasValue%2A> özelliği `false` ve <xref:System.Nullable%601.Value%2A> özelliği tanımsız.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Değer türleri](value-types.md)
- [Değer türleri tablosu](value-types-table.md)
- [Yerleşik türler tablosu](built-in-types-table.md)
