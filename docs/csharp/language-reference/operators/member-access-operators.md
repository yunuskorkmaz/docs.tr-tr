---
title: Üye erişim işleçleri - C# başvurusu
description: Hakkında bilgi edinin C# tür üyelerine erişmek için kullanabileceğiniz işleçler.
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
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
ms.openlocfilehash: 2c5f569b0ad68132e07b009ec9968c766bb965f5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633509"
---
# <a name="member-access-operators"></a>Üye erişimi işleçleri

Bir tür üyesi erişirken aşağıdaki işleçleri kullanabilirsiniz:

- [`.` (üye erişimi) ](#member-access-operator-): bir ad alanı veya tür üyesi erişmek için
- [`[]` (diziyi öğe veya dizin oluşturucu erişimi) ](#indexer-operator-): bir dizi öğesine ya da türü bir dizin oluşturucu erişmek için
- [`?.` ve `?[]` (null koşullu işleçleri)](#null-conditional-operators--and-): yalnızca bir işlenen null olmayan ise bir üyesi veya öğenin erişim işlemi gerçekleştirmek için
- [`()` (çağırma) ](#invocation-operator-): erişilen bir yöntemi çağırabilir veya bir temsilci çağırmak için

## <a name="member-access-operator-"></a>Üye erişimi işleci.

Kullandığınız `.` aşağıdaki örneklerde gösterildiği gibi bir ad alanı veya tür, üye erişim belirteci:

- Kullanım `.` iç içe geçmiş ad alanı içinde bir ad alanı, aşağıdaki örnek olarak erişmek için bir [ `using` yönergesi](../keywords/using-directive.md) gösterir:

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- Kullanım `.` forma bir *tam adı* aşağıdaki kodun gösterdiği gibi bir ad alanı içinde bir tür erişmek için:

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  Kullanan bir [ `using` yönergesi](../keywords/using-directive.md) nitelenmiş adlar kullanımı isteğe bağlı yapmak için.

- Kullanım `.` erişimi [üyelerini türü](../../programming-guide/classes-and-structs/index.md#members), statik ve statik olmayan, aşağıdaki kodun gösterdiği olarak:

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

Ayrıca `.` erişmek için bir [genişletme yöntemi](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="indexer-operator-"></a>Dizin Oluşturucu [] işleci

Köşeli ayraçlar `[]`, genellikle dizi, dizin oluşturucu veya işaretçiyi öğe erişimi için kullanılır.

### <a name="array-access"></a>Dizi erişimi

Aşağıdaki örnekte, dizi öğelerinin nasıl erişileceğini gösteren:

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

Bir dizi dizini karşılık gelen boyutuna bir dizinin sınırları dışında ise bir <xref:System.IndexOutOfRangeException> oluşturulur.

Yukarıdaki örnekte gösterildiği gibi bir dizi türü bildirin veya bir dizi örneği de köşeli ayraç kullanabilirsiniz.

Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Dizinleyici erişimi

Aşağıdaki örnek, .NET kullanır <xref:System.Collections.Generic.Dictionary%602> dizinleyici erişimi göstermek için türü:

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

Dizin oluşturucular dizi dizini oluşturma olarak benzer şekilde, kullanıcı tanımlı bir tür dizin örneğini olanak tanır. Dizin oluşturucu bağımsız değişken tamsayı olması gerekir, dizi dizinleri, herhangi bir türde olması bildirilir.

Dizin oluşturucular hakkında daha fazla bilgi için bkz: [dizin oluşturucular](../../programming-guide/indexers/index.md).

### <a name="other-usages-of-"></a>[] İfadesinin diğer kullanımları

İşaretçi öğe erişimi hakkında daha fazla bilgi için bkz. [nasıl yapılır: işaretçiyle bir dizi öğesine erişme](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).

Köşeli ayraçlar belirtmek için de [öznitelikleri](../../programming-guide/concepts/attributes/index.md):

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Null koşullu işleçleri? ve? []

Kullanılabilir C# 6 ve üzeri, bir null koşullu işleci bir üye erişimi geçerlidir `?.`, ya da öğe erişimi, `?[]`, işlem için yalnızca işlenen null olmayan olarak değerlendirilirse, işleneni. İşlenen değerlendirilirse `null`, işlecin sonucu olan `null`.

Null koşullu işleçleri short-circuiting. Diğer bir deyişle, işlemler zinciri tek bir işlemde koşullu üyesi veya bir öğenin erişim verir `null`, rest zincirinin yürütülmez. Aşağıdaki örnekte, `B` uygulanamıyorsa değerlendirilmez `A` değerlendiren `null` ve `C` uygulanamıyorsa değerlendirilmez `A` veya `B` değerlendiren `null`:

```csharp
A?.B?.Do(C);
A?.B?[C];
```

Aşağıdaki örnek, kullanımını gösterir. `?.` ve `?[]` işleçleri:

[!code-csharp-interactive[null-conditional operators](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

Yukarıdaki örnekte ayrıca kullanımını gösterir [null birleşim işleci](null-coalescing-operator.md). Null koşullu işleminin sonucu olması durumunda değerlendirmek için alternatif bir ifade sağlamak için null birleşim işleci kullanabilir `null`.

### <a name="thread-safe-delegate-invocation"></a>İş parçacığı açısından güvenli temsilci çağrısı

Kullanım `?.` işleci, null olmayan bir temsilci olup olmadığını kontrol edin ve bir iş parçacığı açısından güvenli şekilde çağırmak için (örneğin, [bir olayı](../../../standard/events/how-to-raise-and-consume-events.md)) aşağıdaki kodda gösterildiği gibi:

```csharp
PropertyChanged?.Invoke(…)
```

Kod içinde kullanacağınız aşağıdaki koda denk olduğuna C# 5 veya daha önceki:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a>Çağırma işleci (.)

Parantez kullanın `()`çağırmak için bir [yöntemi](../../programming-guide/classes-and-structs/methods.md) veya çağırma bir [temsilci](../../programming-guide/delegates/index.md).

Aşağıdaki örnek, olan veya olmayan bağımsız değişkenler, bir yöntem çağrısı ve temsilci çağırma gösterilmektedir:

[!code-csharp-interactive[invocation with ()](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

Çağırdığınızda parantez de kullanmak bir [Oluşturucusu](../../programming-guide/classes-and-structs/constructors.md) ile bir [ `new` ](../keywords/new-operator.md) işleci.

### <a name="other-usages-of-"></a>()'nin diğer kullanımları

Ayrıca bir ifade işlemlerinde değerlendirilecek sırayı belirtmek için parantez kullanın. Daha fazla bilgi için [ayraç ekleme](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) bölümünü [işleçleri](../../programming-guide/statements-expressions-operators/operators.md) makalesi. İşleçler, öncelik düzeyine göre sıralı listesi için bkz. [ C# işleçleri](index.md).

[Cast ifadeleri](invocation-operator.md#cast-expression), çağırmak bir dönüşüm işleci, parantez de kullanabilirsiniz.

## <a name="operator-overloadability"></a>İşleç overloadability

`.` Ve `()` işleçleri aşırı yüklenemez. `[]` İşleci aşırı yüklenebilir olmayan bir işleç ayrıca değerlendirilir. Kullanım [dizin oluşturucular](../../programming-guide/indexers/index.md) için kullanıcı tanımlı türler ile dizin oluşturmayı destekler.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):

- [Üye erişimi](~/_csharplang/spec/expressions.md#member-access)
- [Öğe erişimi](~/_csharplang/spec/expressions.md#element-access)
- [Null koşullu işleci](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Çağrı ifadeleri](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [?? (null birleşim işleci)](null-coalescing-operator.md)
