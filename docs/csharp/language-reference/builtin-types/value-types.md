---
title: Değer türleri - C# referansı
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 406e5b8bbe0802146a65bb4b9a053e753a7827ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399583"
---
# <a name="value-types-c-reference"></a>Değer türleri (C# başvurusu)

*Değer türleri* ve [başvuru türleri](../keywords/reference-types.md) C# türlerinin iki ana kategorisidir. Değer türünden bir değişken, türün bir örneğini içerir. Bu, türünün bir örneğine başvuru içeren bir başvuru türünün değişkeninden farklıdır. Varsayılan olarak, [atama,](../operators/assignment-operator.md)bir yönteme bir argüman geçen ve bir yöntem sonucu döndürerek, değişken değerleri kopyalanır. Değer türü değişkenleri söz konusu olduğunda, karşılık gelen tür örnekleri kopyalanır. Aşağıdaki örnek, davranışı gösterir:

[!code-csharp[copy of values](snippets/ValueTypes.cs#ValueTypeCopied)]

Önceki örnekte de görüldüğü gibi, değer türündeki bir değişkendeki işlemler yalnızca değişkende depolanan değer türü örneğini etkiler.

Bir değer türü bir başvuru türünün veri üyesini içeriyorsa, değer türü örneği kopyalandığında yalnızca başvuru türü örneğine yapılan başvuru kopyalanır. Hem kopya hem de özgün değer türü örneği aynı başvuru türü örneğine erişebilir. Aşağıdaki örnek, davranışı gösterir:

[!code-csharp[shallow copy](snippets/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> Kodunuzu daha az hataya yatkın ve daha sağlam hale getirmek için değişmez değer türlerini tanımlayın ve kullanın. Bu makalede, yalnızca gösterim amacıyla mutable değer türleri kullanır.

## <a name="kinds-of-value-types"></a>Değer türleri türleri

Değer türü aşağıdaki iki türden biri olabilir:

- verileri ve ilgili işlevselliği kapsayan bir [yapı türü](struct.md)
- bir [numaralandırma türü](enum.md), adlı sabitler kümesi tarafından tanımlanan ve bir seçim veya seçenek bir arada temsil eden

[Nullable değer türü,](nullable-value-types.md) `T?` temel değer türünün `T` tüm değerlerini ve ek bir [null](../keywords/null.md) değerini temsil eder. Nullable değer `null` türü olmadığı sürece, değer türünden bir değişkene atayamazsınız.

## <a name="built-in-value-types"></a>Yerleşik değer türleri

C# *basit türleri*olarak da bilinen aşağıdaki yerleşik değer türlerini sağlar:

- [Tamsayı sayısal türler](integral-numeric-types.md)
- [Kayan nokta sayısal türleri](floating-point-numeric-types.md)
- boolean değerini temsil eden [bool](bool.md)
- unicode UTF-16 karakterini temsil eden [char](char.md)

Tüm basit türler yapı türleridir ve belirli ek işlemlere izin verdikleri için diğer yapı türlerinden farklıdır:

- Basit bir tür değeri sağlamak için literals kullanabilirsiniz. Örneğin, `'A'` `char` türünün bir harfidir `2001` ve türünün `int`bir harfidir.

- [Const](../keywords/const.md) anahtar sözcüğüyle basit türlerin sabitlerini bildirebilirsiniz. Diğer yapı türlerinin sabitlerinin olması mümkün değildir.

- Operandları basit türlerin tüm sabitleri olan sabit ifadeler derleme zamanında değerlendirilir.

C# 7.0 ile başlayarak, C# [değer tuples](../../tuples.md)destekler. Değer tuple bir değer türüdür, ancak basit bir tür değildir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Değer türleri](~/_csharplang/spec/types.md#value-types)
- [Basit türler](~/_csharplang/spec/types.md#simple-types)
- [Değişkenler](~/_csharplang/spec/variables.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [Başvuru türleri](../keywords/reference-types.md)
