---
title: Üye erişim işleçleri ve ifadeleri-C# başvurusu
description: Tür üyelerine erişmek için kullanabileceğiniz C# işleçleri hakkında bilgi edinin.
ms.date: 04/17/2020
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
ms.openlocfilehash: 37a6cb7cd32a9d60607aec51b1994e4717c5349a
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624871"
---
# <a name="member-access-operators-and-expressions-c-reference"></a>Üye erişim işleçleri ve ifadeleri (C# Başvurusu)

Bir tür üyesine eriştiğinizde aşağıdaki işleçleri ve ifadeleri kullanabilirsiniz:

- (üye erişimi): bir ad alanının veya türün üyesine erişmek için [ `.` ](#member-access-expression-)
- [(dizi öğesi veya Dizin Oluşturucu erişimi): bir dizi öğesine veya bir tür dizin oluşturucusuna erişmek için `[]` ](#indexer-operator-)
- [ve `?[]` null koşullu işleçler): yalnızca bir işlenen null değilse üye veya öğe erişim işlemi `?.` ](#null-conditional-operators--and-)gerçekleştirmek için
- (çağırma): erişilen bir yöntemi çağırmak veya bir temsilciyi çağırmak için [ `()` ](#invocation-expression-)
- (uçtan dizin): öğe konumunun bir sıranın sonundan olduğunu göstermek için [ `^` ](#index-from-end-operator-)
- (Aralık): dizi öğeleri aralığını almak için kullanabileceğiniz bir dizin aralığı belirtmek için [ `..` ](#range-operator-)

## <a name="member-access-expression-"></a>Üye erişim ifadesi.

Aşağıdaki örneklerde gösterildiği `.` gibi, belirteci, bir ad uzayı veya bir tür üyesine erişmek için kullanabilirsiniz:

- Aşağıdaki `.` bir [ `using` yönerge](../keywords/using-directive.md) örneğinde gösterildiği gibi, bir ad alanı içinde iç içe geçmiş bir ad alanına erişmek için kullanın:

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- Aşağıdaki `.` kodun gösterdiği gibi, bir ad alanı içindeki bir türe erişmek üzere *nitelenmiş bir ad* oluşturmak için kullanın:

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  Nitelenmiş adların kullanımını isteğe bağlı yapmak için bir [ `using` yönergesi](../keywords/using-directive.md) kullanın.

- Aşağıdaki `.` kodda gösterildiği gibi, [tür üyelerine](../../programming-guide/classes-and-structs/index.md#members), statik ve statik olmayan erişim için kullanın:

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

Ayrıca, bir `.` [genişletme yöntemine](../../programming-guide/classes-and-structs/extension-methods.md)erişmek için kullanabilirsiniz.

## <a name="indexer-operator-"></a>Indexer işleci []

Köşeli parantezler `[]`, genellikle Array, Indexer veya pointer öğesi erişimi için kullanılır.

### <a name="array-access"></a>Dizi erişimi

Aşağıdaki örnek, dizi öğelerine nasıl erişileceğini göstermektedir:

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

Bir dizi dizini, bir dizi karşılık gelen boyutun sınırları dışındaysa, bir <xref:System.IndexOutOfRangeException> oluşturulur.

Yukarıdaki örnekte gösterildiği gibi, bir dizi türü bildirdiğinizde veya bir dizi örneği örneklediğinizde köşeli parantezleri de kullanabilirsiniz.

Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Dizin Oluşturucu erişimi

Aşağıdaki örnek, Dizin Oluşturucu erişimini <xref:System.Collections.Generic.Dictionary%602> göstermek için .NET türünü kullanır:

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

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

C# 6 ve üzeri sürümlerde kullanılabilir, null koşullu bir operatör, yalnızca o işlenenin null olmayan `?.`olarak değerlendiriliyorsa işlenen için `?[]`bir [üye erişimi](#member-access-expression-), veya [öğe erişimi](#indexer-operator-)uygular; Aksi takdirde, döndürür `null`. Yani

- Olarak `a` `null`değerlendirilirse, `a?.x` veya `a?[x]` olur. `null`
- Null `a` olmayan `a?.x` olarak değerlendirilirse, `a?[x]` veya sonucu, sırasıyla `a.x` veya `a[x]`sonucu ile aynıdır.

  > [!NOTE]
  > `a.x` Ya `a[x]` da bir özel durum oluşturursa `a?.x` ya `a?[x]` da null `a`olmayan bir özel durum oluşturur. `a` Örneğin, null olmayan bir dizi örneğidir ve `x` sınırları `a` `a?[x]` dışındaysa bir <xref:System.IndexOutOfRangeException>oluşturur.

Null koşullu işleçler kısa devre dışı. Diğer bir deyişle, bir koşullu üye veya öğe erişim işlemleri zincirindeki bir işlem dönerse `null`, zincir geri kalanı yürütülmez. Aşağıdaki `B` örnekte, olarak `A` `null` değerlendirilirse ve `C` değerlendirmesi `A` `B` durumunda hesaplanmaz: `null`

```csharp
A?.B?.Do(C);
A?.B?[C];
```

Aşağıdaki örnek, `?.` ve `?[]` işleçlerinin kullanımını gösterir:

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

Yukarıdaki örnek, null-koşullu bir işlemin sonucu olarak değerlendirmek için alternatif bir ifade belirtmek üzere [null birleşim işlecini `??` ](null-coalescing-operator.md) de kullanır. `null`

`a.x` Ya `a[x]` `T`da null yapılamayan bir değer türü ise `a?.x` veya `a?[x]` buna karşılık gelen [null atanabilir değer türüdür](../builtin-types/nullable-value-types.md) `T?`. Türünde `T`bir ifadeye ihtiyacınız varsa, aşağıdaki örnekte gösterildiği gibi null birleşim işlecini `??` null koşullu ifadeye uygulayın:

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

`??` Önceki örnekte, işlecini kullanmıyorsanız, `numbers?.Length < 2` `false` ne zaman `numbers` olduğunu `null`değerlendirir.

Null koşullu üye erişim işleci `?.` ELVIS işleci olarak da bilinir.

> [!NOTE]
> C# 8 ' de, [null-forverme işleci](null-forgiving.md) önceki null koşullu işlemlerin listesini sonlandırır. Örneğin, ifadesi `x?.y!.z` olarak `(x?.y)!.z`ayrıştırılır. Bu yorum `z` nedeniyle,, olsa bile `x` değerlendirilir `null`, bu da bir <xref:System.NullReferenceException>ile sonuçlanabilir.

### <a name="thread-safe-delegate-invocation"></a>İş parçacığı açısından güvenli temsilci çağırma

Bir temsilcinin `?.` null olup olmadığını denetlemek ve iş parçacığı güvenli bir şekilde (örneğin, [bir olay](../../../standard/events/how-to-raise-and-consume-events.md)yükselttiğinizde) aşağıdaki kodun gösterdiği gibi, bir temsilciyi çağırmak için işlecini kullanın:

```csharp
PropertyChanged?.Invoke(…)
```

Bu kod, C# 5 veya daha önceki bir sürümünde kullanacağınız aşağıdaki koda eşdeğerdir:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

Bu, yalnızca null `handler` olmayan bir değer çağrılmasını sağlamak için iş parçacığı açısından güvenli bir yoldur. Temsilci örnekleri sabit olduğu için hiçbir iş parçacığı `handler` yerel değişken tarafından başvurulan değeri değiştiremez. Özellikle, başka bir iş parçacığı tarafından yürütülen `PropertyChanged` kod, olaydan abone olmaya devam eder ve `PropertyChanged` `null` `handler` çağrılır, tarafından `handler` başvurulan değer etkilenmemiştir. `?.` İşleci sol taraftaki işlenenini birden çok kez değerlendirir ve null olmayan olarak doğrulandıktan sonra olarak `null` değiştirilemez.

## <a name="invocation-expression-"></a>Çağırma ifadesi ()

Bir [yöntemi](../../programming-guide/classes-and-structs/methods.md) çağırmak `()`veya bir [temsilciyi](../../programming-guide/delegates/index.md)çağırmak için parantezleri kullanın.

Aşağıdaki örnek, bağımsız değişkenler içeren veya olmayan bir yöntemin nasıl çağrılacağını gösterir ve bir temsilciyi çağırır:

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

İşleci ile bir Oluşturucu çağırdığınızda parantezleri de kullanabilirsiniz. [constructor](../../programming-guide/classes-and-structs/constructors.md) [`new`](new-operator.md)

### <a name="other-usages-of-"></a>() Diğer kullanımları

Ayrıca, bir ifadede işlemlerin değerlendirileceği sırayı ayarlamak için parantez de kullanabilirsiniz. Daha fazla bilgi için bkz. [C# işleçleri](index.md).

Açık tür dönüştürmeleri gerçekleştiren [atama ifadeleri](type-testing-and-cast.md#cast-expression), parantez de kullanır.

## <a name="index-from-end-operator-"></a>Bitiş işlecinden Dizin ^

C# 8,0 ve üzeri sürümlerde kullanılabilen `^` işleç, öğe konumunun bir dizinin sonundan olduğunu gösterir. Bir uzunluk `length`sırası için, `^n` bir dizi başlangıcının sonuna `length - n` kadar olan öğesine işaret eder. Örneğin, `^1` bir sıranın son öğesine işaret eder ve `^length` dizinin ilk öğesine işaret eder.

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

Yukarıdaki örnekte gösterildiği gibi, ifadesi `^e` <xref:System.Index?displayProperty=nameWithType> türüdür. İfadesinde `^e`, sonucu örtük olarak dönüştürülebilir `e` olmalıdır `int`.

Ayrıca bir dizin aralığı oluşturmak `^` için işleci [Aralık işleciyle](#range-operator-) de kullanabilirsiniz. Daha fazla bilgi için bkz. [Dizinler ve aralıklar](../../tutorials/ranges-indexes.md).

## <a name="range-operator-"></a>Aralık işleci..

C# 8,0 ve üzeri sürümlerde kullanılabilen `..` işleç, işlenen bir dizin aralığının başlangıcını ve sonunu belirtir. Sol işlenen bir aralığın *kapsamlı* bir başlangıcı olur. Sağ işlenen bir aralığın *dışlamalı* bir sonu. Her iki işlenen de, aşağıdaki örnekte gösterildiği gibi, bir sıranın başından veya sonundan bir dizin olabilir:

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

Yukarıdaki örnekte gösterildiği gibi, ifadesi `a..b` <xref:System.Range?displayProperty=nameWithType> türüdür. `a..b`İfadesinde `a` , `b` ve sonuçları örtülü olarak veya `int` <xref:System.Index>olarak dönüştürülebilir olmalıdır.

Açık uçlu bir Aralık almak için `..` işlecin işlenenlerinden herhangi birini atlayabilirsiniz:

- `a..`eşdeğerdir`a..^0`
- `..b`eşdeğerdir`0..b`
- `..`eşdeğerdir`0..^0`

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

Daha fazla bilgi için bkz. [Dizinler ve aralıklar](../../tutorials/ranges-indexes.md).

## <a name="operator-overloadability"></a>Operatör overloadability

`.`, `()`, `^`, Ve `..` işleçleri aşırı yüklenemez. İşleci `[]` , aşırı yüklenebilir olmayan bir işleç olarak kabul edilir. Kullanıcı tanımlı türlerle Dizin oluşturmayı desteklemek için [Dizin oluşturucular](../../programming-guide/indexers/index.md) kullanın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Üye erişimi](~/_csharplang/spec/expressions.md#member-access)
- [Öğe erişimi](~/_csharplang/spec/expressions.md#element-access)
- [Null-koşullu işleç](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Çağırma ifadeleri](~/_csharplang/spec/expressions.md#invocation-expressions)

Dizinler ve aralıklar hakkında daha fazla bilgi için bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-8.0/ranges.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [?? (null birleşim işleci)](null-coalescing-operator.md)
- [:: işleci](namespace-alias-qualifier.md)
