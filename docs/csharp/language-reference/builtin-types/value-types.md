---
title: Değer türleri- C# başvuru
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 76f4a3ed929e3ac8e3e6cc74158e75af7a6c8cf2
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625953"
---
# <a name="value-types-c-reference"></a>Değer türleri (C# başvuru)

*Değer türleri* ve [başvuru türleri](../keywords/reference-types.md) , C# türlerin iki ana kategorileridir. Değer türünde bir değişken türün bir örneğini içerir. Bu, bir tür örneğine başvuru içeren bir başvuru türü değişkeninden farklıdır. Varsayılan olarak, [atama](../operators/assignment-operator.md), bir yönteme bir bağımsız değişken geçirme ve bir yöntem sonucu döndürme, değişken değerleri kopyalanır. Değer türü değişkenler söz konusu olduğunda, karşılık gelen tür örnekleri kopyalanır. Aşağıdaki örnekte bu davranış gösterilmektedir:

[!code-csharp[copy of values](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ValueTypeCopied)]

Yukarıdaki örnekte gösterildiği gibi, bir değer türü değişkeni üzerindeki işlemler, değişkende depolanan yalnızca değer türü örneğini etkiler.

Değer türü bir başvuru türünün veri üyesini içeriyorsa, bir değer türü örneği kopyalandığında yalnızca başvuru türü örneğine başvuru kopyalanır. Hem Copy hem de orijinal değer türü örneğinin aynı başvuru türü örneğine erişimi vardır. Aşağıdaki örnekte bu davranış gösterilmektedir:

[!code-csharp[shallow copy](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> Kodunuzu daha az hataya açık ve daha sağlam hale getirmek için, değişmez değer türlerini tanımlayın ve kullanın. Bu makale yalnızca gösterim amacıyla kesilebilir değer türlerini kullanır.

## <a name="kinds-of-value-types"></a>Değer türü türleri

Değer türü aşağıdaki iki türden biri olabilir:

- veri ve ilgili işlevleri kapsülleyen bir [Yapı türü](struct.md)
- bir adlandırılmış sabitler kümesi tarafından tanımlanan ve bir seçimi veya seçenek bileşimini temsil eden bir [numaralandırma türü](enum.md)

[Null olabilen bir değer türü](nullable-value-types.md) `T?` temel alınan değer `T` türünün tüm değerlerini ve ek bir [null](../keywords/null.md) değeri temsil eder. Null atanabilir bir değer türü olmadığı takdirde, değer türü değişkenine `null` atayamazsınız.

## <a name="built-in-value-types"></a>Yerleşik değer türleri

C#, *basit türler*olarak da bilinen aşağıdaki yerleşik değer türlerini sağlar:

- [Integral sayısal türleri](integral-numeric-types.md)
- [Kayan nokta sayısal türleri](floating-point-numeric-types.md)
- Boole değeri temsil eden [bool](bool.md)
- Unicode UTF-16 karakterini temsil eden [karakter](char.md)

Tüm basit türler yapı türlerdir ve bazı ek işlemlere izin veren diğer yapı türlerinden farklıdır:

- Basit bir tür değeri sağlamak için sabit değerler kullanabilirsiniz. Örneğin, `'A'` türü `char` bir değişmez değerdir ve `2001` `int`türü bir değişmez değerdir.

- [Const](../keywords/const.md) anahtar sözcüğüyle basit türlerin sabitlerini bildirebilirsiniz. Diğer yapı türlerinde sabitler olması mümkün değildir.

- İşlenenleri basit türlerin tüm sabitleri olan sabit ifadeler, derleme zamanında değerlendirilir.

7,0 ' C# C# den başlayarak [değer tanımlama gruplarını](../../tuples.md)destekler. Değer tanımlama grubu bir değer türüdür, ancak basit bir tür değildir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Değer türleri](~/_csharplang/spec/types.md#value-types)
- [Basit türler](~/_csharplang/spec/types.md#simple-types)
- [Değişkenler](~/_csharplang/spec/variables.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [Başvuru türleri](../keywords/reference-types.md)
