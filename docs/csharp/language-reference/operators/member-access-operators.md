---
title: Üye erişim işleçleri- C# başvuru
description: Tür üyelerine C# erişmek için kullanabileceğiniz işleçler hakkında bilgi edinin.
ms.date: 09/18/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: e69cc5a9634f0b5232562782557645894f94ce2e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345299"
---
# <a name="member-access-operators-c-reference"></a>Üye erişim işleçleri (C# başvuru)

Bir tür üyesine eriştiğinizde aşağıdaki işleçleri kullanabilirsiniz:

- [`.` (üye erişimi)](#member-access-operator-): bir ad alanının veya türün üyesine erişmek için
- [`[]` (dizi öğesi veya Dizin Oluşturucu erişimi)](#indexer-operator-): bir dizi öğesine veya bir tür dizin oluşturucusuna erişmek için
- [`?.` ve `?[]` (null-koşullu işleçler)](#null-conditional-operators--and-): yalnızca bir işlenen null değilse bir üye veya öğe erişim işlemi gerçekleştirmek için
- [`()` (çağırma)](#invocation-operator-): erişilen bir yöntemi çağırmak veya bir temsilciyi çağırmak için
- [`^` (uçtan dizin)](#index-from-end-operator-): öğe konumunun bir sıranın sonundan olduğunu göstermek için
- [`..` (Aralık)](#range-operator-): dizi öğeleri aralığını almak için kullanabileceğiniz bir dizin aralığı belirtmek için

## <a name="member-access-operator-"></a>Üye erişim işleci.

Aşağıdaki örneklerde gösterildiği gibi, bir ad alanı veya tür üyesine erişmek için `.` belirtecini kullanın:

- Bir [`using` yönergesinin](../keywords/using-directive.md) aşağıdaki örneğinde gösterildiği gibi, bir ad alanı içinde iç içe geçmiş bir ad alanına erişmek için `.` kullanın:

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- Aşağıdaki kodun gösterdiği gibi, bir ad alanı içindeki bir türe erişmek üzere *nitelenmiş bir ad* oluşturmak için `.` kullanın:

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  Nitelenmiş adların kullanımını isteğe bağlı yapmak için bir [`using` yönergesi](../keywords/using-directive.md) kullanın.

- Aşağıdaki kodda gösterildiği gibi, [tür üyelerine](../../programming-guide/classes-and-structs/index.md#members), statik ve statik olmayan erişim için `.` kullanın:

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

[Uzantı yöntemine](../../programming-guide/classes-and-structs/extension-methods.md)erişmek için `.` de kullanabilirsiniz.

## <a name="indexer-operator-"></a>Indexer işleci []

Köşeli ayraçlar `[]`, genellikle Array, Indexer veya pointer öğesi erişimi için kullanılır.

### <a name="array-access"></a>Dizi erişimi

Aşağıdaki örnek, dizi öğelerine nasıl erişileceğini göstermektedir:

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

Bir dizi dizini, bir dizi karşılık gelen boyutun sınırları dışındaysa bir <xref:System.IndexOutOfRangeException> oluşturulur.

Yukarıdaki örnekte gösterildiği gibi, bir dizi türü bildirdiğinizde veya bir dizi örneği örneklediğinizde köşeli parantezleri de kullanabilirsiniz.

Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Dizin Oluşturucu erişimi

Aşağıdaki örnek, Dizin Oluşturucu erişimini göstermek için .NET <xref:System.Collections.Generic.Dictionary%602> türünü kullanır:

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

Dizin oluşturucular, Kullanıcı tanımlı bir türün örneklerinin, dizi dizini oluşturma gibi benzer şekilde dizinlemesini sağlar. Tamsayı olması gereken dizi dizinlerinin aksine, Dizin Oluşturucu parametreleri herhangi bir türde olacak şekilde bildirilmelidir.

Dizin oluşturucular hakkında daha fazla bilgi için bkz. [Dizin oluşturucular](../../programming-guide/indexers/index.md).

### <a name="other-usages-of-"></a>[] Diğer kullanımları

İşaretçi öğesi erişimi hakkında daha fazla bilgi için, [işaretçi ilgili işleçler](pointer-related-operators.md) makalesinin [işaretçi öğesi erişim işleci []](pointer-related-operators.md#pointer-element-access-operator-) bölümüne bakın.

Ayrıca, [öznitelikleri](../../programming-guide/concepts/attributes/index.md)belirtmek için köşeli parantezleri de kullanabilirsiniz:

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Null koşullu işleçler?. '? []

C# 6 ve sonrasında kullanılabilir, null koşullu bir operatör, yalnızca bu işlenen null olmayan bir değer olarak değerlendiriliyorsa, bir [üye erişimi](#member-access-operator-), `?.`ya da [öğe erişimi](#indexer-operator-), `?[]`, işlem için uygular. Aksi takdirde, `null`döndürür. Yani

- `a` `null`değerlendirilirse, `a?.x` veya `a?[x]` sonucu `null`.
- `a` null olmayan olarak değerlendirilirse, `a?.x` veya `a?[x]` sonucu sırasıyla `a.x` veya `a[x]`sonucuyla aynıdır.

  > [!NOTE]
  > `a.x` veya `a[x]` bir özel durum oluşturursa, `a?.x` veya `a?[x]` null olmayan `a`için aynı özel durumu oluşturur. Örneğin, `a` null olmayan bir dizi örneğidir ve `x` `a`sınırlarının dışındaysa `a?[x]` <xref:System.IndexOutOfRangeException>oluşturur.

Null koşullu işleçler kısa devre dışı. Diğer bir deyişle, bir koşullu üye veya öğe erişim işlemleri zincirindeki bir işlem `null`döndürürse, zincirin geri kalanı yürütülmez. Aşağıdaki örnekte, `A` `null` değerlendirilirse `B` değerlendirilmez ve `A` veya `B` `null`olarak değerlendirilirse `C` değerlendirilmez:

```csharp
A?.B?.Do(C);
A?.B?[C];
```

Aşağıdaki örnek, `?.` ve `?[]` işleçlerinin kullanımını gösterir:

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

Yukarıdaki örnek ayrıca null [birleşim işlecini `??`](null-coalescing-operator.md) , null koşullu bir işlemin sonucu `null`sonucunu değerlendirmek üzere alternatif bir ifade belirtmek için kullanır.

Null koşullu üye erişim işleci `?.` ELVIS işleci olarak da bilinir.

### <a name="thread-safe-delegate-invocation"></a>İş parçacığı açısından güvenli temsilci çağırma

Bir temsilcinin null olup olmadığını denetlemek ve iş parçacığı güvenli bir şekilde (örneğin, [bir olay](../../../standard/events/how-to-raise-and-consume-events.md)yükselttiğinizde) aşağıdaki kodun gösterdiği gibi, bir temsilciyi çağırmak için `?.` işlecini kullanın:

```csharp
PropertyChanged?.Invoke(…)
```

Bu kod, C# 5 veya daha önceki sürümlerde kullanacağınız aşağıdaki koda eşdeğerdir:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a>Çağırma işleci ()

Bir [yöntemi](../../programming-guide/classes-and-structs/methods.md) çağırmak veya bir [temsilciyi](../../programming-guide/delegates/index.md)çağırmak için parantez, `()`kullanın.

Aşağıdaki örnek, bağımsız değişkenler içeren veya olmayan bir yöntemin nasıl çağrılacağını gösterir ve bir temsilciyi çağırır:

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

Ayrıca, [`new`](new-operator.md) işleçle bir [Oluşturucu](../../programming-guide/classes-and-structs/constructors.md) çağırdığınızda parantezleri de kullanabilirsiniz.

### <a name="other-usages-of-"></a>() Diğer kullanımları

Ayrıca, bir ifadede işlemlerin değerlendirileceği sırayı ayarlamak için parantez de kullanabilirsiniz. Daha fazla bilgi için bkz [ C# . işleçler](index.md).

Açık tür dönüştürmeleri gerçekleştiren [atama ifadeleri](type-testing-and-cast.md#cast-operator-), parantez de kullanır.

## <a name="index-from-end-operator-"></a>Bitiş işlecinden Dizin ^

C# 8,0 ve sonraki sürümlerde kullanılabilen `^` işleci, öğe konumunun sıranın sonundan itibaren olduğunu gösterir. `length`bir dizi Uzunluk için, `^n` bir sıranın başından itibaren `length - n` olan öğeye işaret eder. Örneğin `^1`, sıranın son öğesine işaret eder ve `^length` bir dizinin ilk öğesine işaret eder.

[!code-csharp[index from end](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#IndexFromEnd)]

Yukarıdaki örnekte gösterildiği gibi ifade `^e` <xref:System.Index?displayProperty=nameWithType> türüdür. İfade `^e`, `e` sonucu `int`örtülü olarak dönüştürülebilir olmalıdır.

Ayrıca, dizin aralığı oluşturmak için `^` işlecini [Aralık işleciyle](#range-operator-) de kullanabilirsiniz. Daha fazla bilgi için bkz. [Dizinler ve aralıklar](../../tutorials/ranges-indexes.md).

## <a name="range-operator-"></a>Aralık işleci..

C# 8,0 ve sonraki sürümlerde kullanılabilen `..` işleci, işlenen bir dizin aralığının başlangıcını ve sonunu belirtir. Sol işlenen bir aralığın *kapsamlı* bir başlangıcı olur. Sağ işlenen bir aralığın *dışlamalı* bir sonu. Her iki işlenen de, aşağıdaki örnekte gösterildiği gibi, bir sıranın başından veya sonundan bir dizin olabilir:

[!code-csharp[range examples](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Ranges)]

Yukarıdaki örnekte gösterildiği gibi ifade `a..b` <xref:System.Range?displayProperty=nameWithType> türüdür. İfade `a..b`, `a` ve `b` sonuçları `int` veya <xref:System.Index>örtülü olarak dönüştürülebilir olmalıdır.

Açık uçlu bir Aralık almak için `..` işlecinin herhangi bir işlenenini atlayabilirsiniz:

- `a..` `a..^0` eşdeğerdir
- `..b` `0..b` eşdeğerdir
- `..` `0..^0` eşdeğerdir

[!code-csharp[ranges with omitted operands](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#RangesOptional)]

Daha fazla bilgi için bkz. [Dizinler ve aralıklar](../../tutorials/ranges-indexes.md).

## <a name="operator-overloadability"></a>Operatör overloadability

`.`, `()`, `^`ve `..` işleçleri aşırı yüklenemez. `[]` işleci de aşırı yüklenebilir olmayan bir operatör olarak değerlendirilir. Kullanıcı tanımlı türlerle Dizin oluşturmayı desteklemek için [Dizin oluşturucular](../../programming-guide/indexers/index.md) kullanın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Üye erişimi](~/_csharplang/spec/expressions.md#member-access)
- [Öğe erişimi](~/_csharplang/spec/expressions.md#element-access)
- [Null-koşullu işleç](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Çağırma ifadeleri](~/_csharplang/spec/expressions.md#invocation-expressions)

Dizinler ve aralıklar hakkında daha fazla bilgi için bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-8.0/ranges.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [?? (null birleşim işleci)](null-coalescing-operator.md)
- [:: işleci](namespace-alias-qualifier.md)
