---
title: Üye erişim işleçleri- C# başvuru
description: Tür üyelerine C# erişmek için kullanabileceğiniz işleçler hakkında bilgi edinin.
ms.date: 05/09/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
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
ms.openlocfilehash: 5ff5e68fbce320076e6d18e9e139b418a15bba77
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924635"
---
# <a name="member-access-operators-c-reference"></a>Üye erişim işleçleri (C# başvuru)

Bir tür üyesine eriştiğinizde aşağıdaki işleçleri kullanabilirsiniz:

- (üye erişimi): bir ad alanının veya türün üyesine erişmek için [ `.` ](#member-access-operator-)
- [(dizi öğesi veya Dizin Oluşturucu erişimi): bir dizi öğesine veya bir tür dizin oluşturucusuna erişmek için `[]` ](#indexer-operator-)
- [ve (nullkoşulluişleçler):yalnızcabirişlenennulldeğilseüyeveyaöğeerişimişlemigerçekleştirmek`?[]`için `?.` ](#null-conditional-operators--and-)
- (çağırma): erişilen bir yöntemi çağırmak veya bir temsilciyi çağırmak için [ `()` ](#invocation-operator-)

## <a name="member-access-operator-"></a>Üye erişim işleci.

Aşağıdaki örneklerde gösterildiği `.` gibi, belirteci, bir ad uzayı veya bir tür üyesine erişmek için kullanabilirsiniz:

- Aşağıdaki `.` [bir yönerge`using` ](../keywords/using-directive.md) örneğinde gösterildiği gibi, bir ad alanı içinde iç içe geçmiş bir ad alanına erişmek için kullanın:

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- Aşağıdaki `.` kodun gösterdiği gibi, bir ad alanı içindeki bir türe erişmek üzere *nitelenmiş bir ad* oluşturmak için kullanın:

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  Nitelenmiş adların kullanımını isteğe bağlı yapmak için bir [ `using` yönergesi](../keywords/using-directive.md) kullanın.

- Aşağıdaki `.` kodda gösterildiği gibi, [tür üyelerine](../../programming-guide/classes-and-structs/index.md#members), statik ve statik olmayan erişim için kullanın:

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

Ayrıca, bir `.` [genişletme yöntemine](../../programming-guide/classes-and-structs/extension-methods.md)erişmek için kullanabilirsiniz.

## <a name="indexer-operator-"></a>Indexer işleci []

Köşeli parantezler `[]`, genellikle Array, Indexer veya pointer öğesi erişimi için kullanılır.

### <a name="array-access"></a>Dizi erişimi

Aşağıdaki örnek, dizi öğelerine nasıl erişileceğini göstermektedir:

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

Bir dizi dizini, bir dizi karşılık gelen boyutun sınırları dışındaysa, bir <xref:System.IndexOutOfRangeException> oluşturulur.

Yukarıdaki örnekte gösterildiği gibi, bir dizi türü bildirdiğinizde veya bir dizi örneği örneklediğinizde köşeli parantezleri de kullanabilirsiniz.

Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Dizin Oluşturucu erişimi

Aşağıdaki örnek, Dizin Oluşturucu <xref:System.Collections.Generic.Dictionary%602> erişimini göstermek için .NET türünü kullanır:

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

Dizin oluşturucular, Kullanıcı tanımlı bir türün örneklerinin, dizi dizini oluşturma gibi benzer şekilde dizinlemesini sağlar. Tamsayı olması gereken dizi dizinlerinin aksine, Dizin Oluşturucu bağımsız değişkenleri herhangi bir türde olacak şekilde bildirilmelidir.

Dizin oluşturucular hakkında daha fazla bilgi için bkz. [Dizin oluşturucular](../../programming-guide/indexers/index.md).

### <a name="other-usages-of-"></a>[] Diğer kullanımları

İşaretçi öğesi erişimi hakkında daha fazla bilgi için, [işaretçi ilgili işleçler](pointer-related-operators.md) makalesinin [işaretçi öğesi erişim işleci []](pointer-related-operators.md#pointer-element-access-operator-) bölümüne bakın.

Ayrıca, [öznitelikleri](../../programming-guide/concepts/attributes/index.md)belirtmek için köşeli parantezleri de kullanabilirsiniz:

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Null koşullu işleçler?. '? []

C# 6 ve sonraki sürümlerde kullanılabilir, null koşullu bir operatör, yalnızca o işlenen null olmayan `?.`bir değer olarak değerlendiriliyorsa `?[]`, bir üye erişimi, veya öğe erişimi, öğesini işleneninde uygular. İşlenen olarak `null`değerlendirilirse, işleci uygulamanın sonucu olur `null`. Null koşullu üye erişim işleci `?.` ELVIS işleci olarak da bilinir.

Null koşullu işleçler kısa devre dışı. Diğer bir deyişle, bir koşullu üye veya öğe erişim işlemleri zincirindeki bir işlem dönerse `null`, zincir geri kalanı yürütülmez. `B` Aşağıdaki örnekte, `A` olarak `null` değerlendirilirse ve`C`değerlendirmesi `A` durumundahesaplanmaz:`null` `B`

```csharp
A?.B?.Do(C);
A?.B?[C];
```

Aşağıdaki örnek, `?.` ve `?[]` işleçlerinin kullanımını gösterir:

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

Yukarıdaki örnek, [null birleşim işlecinin](null-coalescing-operator.md)kullanımını da gösterir. Null-koşullu işlemin `null`sonucu olarak değerlendirmek için alternatif bir ifade sağlamak üzere null birleşim işlecini kullanabilirsiniz.

### <a name="thread-safe-delegate-invocation"></a>İş parçacığı açısından güvenli temsilci çağırma

Bir temsilcinin null olup olmadığını denetlemek ve iş parçacığı güvenli bir şekilde (örneğin, [bir olay](../../../standard/events/how-to-raise-and-consume-events.md)yükselttiğinizde) aşağıdaki kodun gösterdiği gibi, bir temsilciyi çağırmak için işlecinikullanın:`?.`

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

Bir [yöntemi](../../programming-guide/classes-and-structs/methods.md) çağırmak `()`veya bir [temsilciyi](../../programming-guide/delegates/index.md)çağırmak için parantezleri kullanın.

Aşağıdaki örnek, bağımsız değişkenler içeren veya olmayan bir yöntemin nasıl çağrılacağını gösterir ve bir temsilciyi çağırır:

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

[`new`](new-operator.md) İşleci ile bir [Oluşturucu](../../programming-guide/classes-and-structs/constructors.md) çağırdığınızda parantezleri de kullanabilirsiniz.

### <a name="other-usages-of-"></a>() Diğer kullanımları

Ayrıca, bir ifadede işlemlerin değerlendirileceği sırayı ayarlamak için parantez de kullanabilirsiniz. Daha fazla bilgi için bkz [ C# . işleçler](index.md).

Açık tür dönüştürmeleri gerçekleştiren [atama ifadeleri](type-testing-and-cast.md#cast-operator-), parantez de kullanır.

## <a name="operator-overloadability"></a>Operatör overloadability

`.` Ve`()` işleçleri aşırı yüklenemez. İşleci `[]` , aşırı yüklenebilir olmayan bir işleç olarak kabul edilir. Kullanıcı tanımlı türlerle Dizin oluşturmayı desteklemek için [Dizin oluşturucular](../../programming-guide/indexers/index.md) kullanın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Üye erişimi](~/_csharplang/spec/expressions.md#member-access)
- [Öğe erişimi](~/_csharplang/spec/expressions.md#element-access)
- [Null-koşullu işleç](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Çağırma ifadeleri](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [?? (null birleşim işleci)](null-coalescing-operator.md)
- [:: işleci](namespace-alias-qualifier.md)
