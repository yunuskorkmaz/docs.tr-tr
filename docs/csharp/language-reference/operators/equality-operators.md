---
title: Eşitlik operatörleri - C# referansı
description: C# eşitlik karşılaştırma işleçleri ve C# türü eşitliği hakkında bilgi edinin.
ms.date: 06/26/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 7dd3e544dc03fb94577892b42aecd1a15a6621ac
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110925"
---
# <a name="equality-operators-c-reference"></a>Eşitlik operatörleri (C# başvurusu)

[ `==` (Eşitlik)](#equality-operator-) ve [ `!=` (eşitsizlik)](#inequality-operator-) işleçleri, operandlarının eşit olup olmadığını kontrol eder.

## <a name="equality-operator-"></a>Eşitlik işleci ==

Eşitlik `==` işleci, `true` operands eşitse, `false` aksi takdirde döner.

### <a name="value-types-equality"></a>Değer türleri eşitliği

[Yerleşik değer türlerinin](../builtin-types/value-types.md#built-in-value-types) operands değerleri eşit ise eşittir:

[!code-csharp-interactive[value types equality](snippets/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> Için `==` [ `<`, `>`, `<=`, `>=` , ve](comparison-operators.md) operatörler, herhangi bir operands bir sayı değilse (veya<xref:System.Double.NaN?displayProperty=nameWithType> <xref:System.Single.NaN?displayProperty=nameWithType>), operasyon sonucudur `false`. `NaN` Bu, değerin ne daha büyük, ne daha az, ne de dahil olmak üzere başka `double` bir (veya) `float`değere eşit olduğu anlamına `NaN`gelir. Daha fazla bilgi ve <xref:System.Double.NaN?displayProperty=nameWithType> örnekler <xref:System.Single.NaN?displayProperty=nameWithType> için, başvuru makalesine bakın.

Altta yatan integral türünün karşılık gelen değerleri eşitse, aynı [enum](../builtin-types/enum.md) türünden iki operand eşittir.

Kullanıcı tanımlı [yapı](../builtin-types/struct.md) türleri varsayılan olarak `==` işleci desteklemez. İşleciyi `==` desteklemek için, kullanıcı tarafından tanımlanan bir yapının [aşırı yüklenmesi](operator-overloading.md) gerekir.

C# 7.3 ile `==` başlayarak, ve `!=` işleçler C# [tuples](../../tuples.md)tarafından desteklenir. Daha fazla bilgi için [C# tuple türleri](../../tuples.md) makalesinin [Eşitlik ve tuples](../../tuples.md#equality-and-tuples) bölümüne bakın.

### <a name="reference-types-equality"></a>Referans türleri eşitliği

Varsayılan olarak, aynı nesneye başvururlarsa, iki başvuru tipi operand eşittir:

[!code-csharp[reference type equality](snippets/EqualityOperators.cs#ReferenceTypesEquality)]

Örnekte de görüldüğü gibi, kullanıcı `==` tanımlı başvuru türleri varsayılan olarak işleci destekler. Ancak, bir başvuru türü `==` işleci aşırı yükleyebilir. Bir başvuru türü `==` işleç aşırı <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> yüklerse, bu türiki başvurunun aynı nesneye başvurup başvurmadığını denetlemek için yöntemi kullanın.

### <a name="string-equality"></a>Dize eşitliği

İki [dize](../builtin-types/reference-types.md#the-string-type) operands her ikisi `null` de veya her iki dize örnekleri aynı uzunlukta ve her karakter konumunda aynı karakterlere sahip eşittir:

[!code-csharp-interactive[string equality](snippets/EqualityOperators.cs#StringEquality)]

Bu büyük/küçük harf duyarlı bir ordinal karşılaştırma. Dize karşılaştırması hakkında daha fazla bilgi için [C# dizelerini nasıl karşılaştırın.](../../how-to/compare-strings.md)

### <a name="delegate-equality"></a>Temsilci eşitliği

Her [delegate](../../programming-guide/delegates/index.md) ikisi de aynı uzunlukta olduğunda `null` ve her pozisyonda eşit girişlere sahip olduklarında, aynı çalışma zamanı türünden iki temsilci operandeşittir:

[!code-csharp-interactive[delegate equality](snippets/EqualityOperators.cs#DelegateEquality)]

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Temsilci eşitliği işleçleri](~/_csharplang/spec/expressions.md#delegate-equality-operators) bölümüne bakın.

Aşağıdaki örnekte görüldüğü gibi, anlamsal olarak özdeş [lambda ifadelerinin](../../programming-guide/statements-expressions-operators/lambda-expressions.md) değerlendirilmesinden elde edilen temsilciler eşit değildir:

[!code-csharp-interactive[from identical lambdas](snippets/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a>Eşitsizlik operatörü !=

Eşitsizlik işleci, `!=` `true` operands eşit değilse, `false` aksi takdirde döner. [Yerleşik türlerin](../builtin-types/built-in-types.md)operands için, ifade `x != y` ifade `!(x == y)`olarak aynı sonucu üretir. Tür eşitliği hakkında daha fazla bilgi için [Eşitlik işleci](#equality-operator-) bölümüne bakın.

Aşağıdaki örnek, işleç `!=` kullanımını gösterir:

[!code-csharp-interactive[non-equality examples](snippets/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a>Operatör aşırı yüklenebilirlik

Kullanıcı tanımlı bir tür `==` ve `!=` işleçler [aşırı yükleyebilir.](operator-overloading.md) Bir tür iki işleçten birini aşırı yüklenirse, diğerini de aşırı yüklemesi gerekir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [İlişkisel ve tür test işleçleri](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [Eşitlik karşılaştırmaları](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [Karşılaştırma işleçleri](comparison-operators.md)
