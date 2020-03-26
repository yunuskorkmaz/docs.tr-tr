---
title: Üye erişim işleçleri ve ifadeleri - C# başvurusu
description: Tür üyelerine erişmek için kullanabileceğiniz C# işleçleri hakkında bilgi edinin.
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
ms.openlocfilehash: da2ca4517bd007678d74ae9b76e10cad4c2696b4
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546646"
---
# <a name="member-access-operators-and-expressions-c-reference"></a>Üye erişim işleçleri ve ifadeleri (C# başvurusu)

Bir tür üyesine erişirken aşağıdaki işleçleri ve ifadeleri kullanabilirsiniz:

- (üye erişimi) : bir ad alanı nın veya bir türün üyesine erişmek için [ `.` ](#member-access-expression-)
- [(dizi öğesi veya dizinleyici erişimi) : bir dizi öğesi veya bir tür dizinleyici erişmek için `[]` ](#indexer-operator-)
- ve (null-conditional operators) : bir üye veya eleman erişim işlemi gerçekleştirmek için sadece bir operand null olmayan [ `?.` `?[]` ](#null-conditional-operators--and-)
- (çağırma) : erişilen bir yöntemi çağırmak veya bir temsilci çağırmak [ `()` ](#invocation-expression-)
- (dizini sona) : eleman konumunun bir dizinin sonundan geldiğini belirtmek için [ `^` ](#index-from-end-operator-)
- (aralık) : dizi öğeleri aralığı elde etmek için kullanabileceğiniz bir dizi endeks belirtmek için [ `..` ](#range-operator-)

## <a name="member-access-expression-"></a>Üye erişim ifadesi .

Aşağıdaki örneklerde gösterildiği gibi, bir ad alanı nın veya bir türün üyesine erişmek için `.` belirteci kullanırsınız:

- Bir `.` [ `using` yönergeörneğinin](../keywords/using-directive.md) aşağıdaki örneğinde görüldüğü gibi, ad alanı içinde iç içe bir ad alanına erişmek için kullanın:

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- Aşağıdaki `.` kodun gösterdiği gibi, ad alanı içindeki bir türe erişmek için nitelikli bir *ad* oluşturmak için kullanın:

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  Nitelikli adlardan isteğe bağlı olarak yararlanmak için bir [ `using` yönerge](../keywords/using-directive.md) kullanın.

- Aşağıdaki `.` kodun gösterdiği gibi, statik ve statik olmayan [tür üyelerine](../../programming-guide/classes-and-structs/index.md#members)erişmek için kullanın:

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

Ayrıca bir `.` [uzantı yöntemine](../../programming-guide/classes-and-structs/extension-methods.md)erişmek için kullanabilirsiniz.

## <a name="indexer-operator-"></a>Dizinleyici operatörü []

Kare ayraçlar, `[]`genellikle dizi, dizinleyici veya işaretçi öğesi erişimi için kullanılır.

### <a name="array-access"></a>Dizi erişimi

Aşağıdaki örnek, dizi öğelerine nasıl erişilenleri gösterir:

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

Bir dizi dizi dizi dizinin ilgili boyutunun sınırları <xref:System.IndexOutOfRangeException> dışında ysa, bir atılır.

Önceki örnekte de görüldüğü gibi, bir dizi türünü beyan ettiğinizde veya bir dizi örneğini anında yaptığınızda kare ayraçlar da kullanırsınız.

Diziler hakkında daha fazla bilgi için [Diziler'e](../../programming-guide/arrays/index.md)bakın.

### <a name="indexer-access"></a>Dizinleyici erişimi

Aşağıdaki örnek, dizinleyici erişimini göstermek için .NET <xref:System.Collections.Generic.Dictionary%602> türünü kullanır:

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

Dizin leyiciler, kullanıcı tanımlı bir türün örneklerini dizi dizilimi gibi benzer şekilde dizilmesine izin verir. İntesayı olması gereken dizi dizinlerinin aksine, dizinleyici parametreleri herhangi bir türde olarak bildirilebilir.

Dizinleyiciler hakkında daha fazla bilgi için [bkz.](../../programming-guide/indexers/index.md)

### <a name="other-usages-of-"></a>Diğer kullanımları []

İşaretçi öğesi erişimi hakkında bilgi için, Pointer ilgili [işleçler](pointer-related-operators.md) makalesinin [Pointer öğesi erişim işleci []](pointer-related-operators.md#pointer-element-access-operator-) bölümüne bakın.

[Ayrıca öznitelikleri](../../programming-guide/concepts/attributes/index.md)belirtmek için kare ayraçlar kullanın:

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Null-koşullu operatörler ?. Ve? []

C# 6 ve sonraki durumlarda, null-koşullu bir işleç [üye erişimi](#member-access-expression-), `?.`veya [eleman erişimi](#indexer-operator-), `?[]`, operand non-null değerlendirir sadece operand için işlem uygular; aksi takdirde, `null`döner . Yani

- Eğer `a` `null`değerlendirirse , `a?.x` sonucu `a?[x]` `null`veya .
- Null `a` olmayan olarak değerlendirilirse, `a?.x` sonucu `a?[x]` veya sonucu `a.x` olarak aynıdır `a[x]`veya , sırasıyla.

  > [!NOTE]
  > Bir `a.x` `a[x]` özel durum atarsa `a?.x` veya bir özel durum atarsa veya `a?[x]` null `a`olmayanlar için aynı özel durumu atar. Örneğin, null `a` olmayan bir dizi örneği `x` ise ve sınırları `a` `a?[x]` dışında ise <xref:System.IndexOutOfRangeException>, bir .

Null-conditional operatörler kısa devre vardır. Diğer bir deyişle, koşullu üye veya öğe erişim `null`işlemleri zincirindeki bir işlem döndürürse, zincirin geri kalanı çalışmaz. Aşağıdaki örnekte, `B` `A` aşağıdaki durumlarda `null` `C` `A` değerlendirilmiyorsa ve `B` değerlendirilmiyorsa: `null`

```csharp
A?.B?.Do(C);
A?.B?[C];
```

Aşağıdaki örnek, `?.` `?[]` işleçlerin ve işleçlerin kullanımını göstermektedir:

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

Önceki örnek, null-koşullu bir işlemin sonucu durumunda değerlendirmek için alternatif bir ifade belirtmek için [null-coalescing işleci `??` ](null-coalescing-operator.md) `null`kullanır.

Null-koşullu üye erişim `?.` operatörü elvis operatörü olarak da bilinir.

### <a name="thread-safe-delegate-invocation"></a>İş parçacığı güvenli temsilci çağırma

Bir `?.` temsilcinin geçersiz olup olmadığını denetlemek için işleci kullanın ve aşağıdaki kodun gösterdiği gibi iş parçacığı güvenli bir şekilde (örneğin, [bir olay yükselttiğinde)](../../../standard/events/how-to-raise-and-consume-events.md)çağırın:

```csharp
PropertyChanged?.Invoke(…)
```

Bu kod, C# 5 veya daha önce kullanacağınız aşağıdaki koda eşdeğerdir:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-expression-"></a>Çağırma ifadesi ()

Bir yöntemi çağırmak `()`veya bir [method](../../programming-guide/classes-and-structs/methods.md) [temsilci](../../programming-guide/delegates/index.md)çağırmak için parantez kullanın.

Aşağıdaki örnek, bağımsız değişkenli veya bağımsız bir yöntemin nasıl çağrılmasını ve bir temsilci çağırmanın nasıl yapılacağını gösterir:

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

İşleç ile bir oluşturucu çağırırken de parantez kullanırsınız. [constructor](../../programming-guide/classes-and-structs/constructors.md) [`new`](new-operator.md)

### <a name="other-usages-of-"></a>Diğer kullanımları ()

İşlemleri bir ifadede değerlendirmek için sırasını ayarlamak için parantez ler de kullanırsınız. Daha fazla bilgi için [C# işleçleri'ne](index.md)bakın.

Açık tür [dönüşümleri](type-testing-and-cast.md#cast-operator-)gerçekleştiren cast ifadeleri de parantez kullanır.

## <a name="index-from-end-operator-"></a>Son işleç ^ dan Dizin

C# 8.0 ve daha `^` sonra kullanılabilir, işleç bir dizinin sonundan öğe konumunu gösterir. Uzunluk dizisi `length`için, `^n` bir dizinin başlangıcından itibaren ofset `length - n` ile eleman işaret eder. Örneğin, `^1` bir dizinin son öğesini `^length` ve bir dizinin ilk öğesini işaret eder.

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

Yukarıdaki örnekte de görüldüğü `^e` gibi, <xref:System.Index?displayProperty=nameWithType> ifade türündendir. İfadede `^e`, sonucu `e` örtülü olarak dönüştürülebilir `int`olmalıdır.

Ayrıca, bir `^` dizi endeks oluşturmak için [aralık işleciyle](#range-operator-) birlikte işleci de kullanabilirsiniz. Daha fazla bilgi için [Endeksler ve aralıklar'a](../../tutorials/ranges-indexes.md)bakın.

## <a name="range-operator-"></a>Menzil operatörü ...

C# 8.0 ve daha `..` sonra mevcuttur, operatör operands olarak endeksleri bir dizi başlangıç ve bitiş belirtir. Sol operand bir dizi *kapsayıcı* bir başlangıçtır. Sağ operand bir aralığın *özel* bir sonudur. Aşağıdaki örnekte görüldüğü gibi, operandlardan biri bir dizinin başından veya sonundan itibaren olabilir:

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

Yukarıdaki örnekte de görüldüğü `a..b` gibi, <xref:System.Range?displayProperty=nameWithType> ifade türündendir. İfadede `a..b`, sonuçları `a` `b` ve örtülü olarak dönüştürülebilir olmalıdır `int` ya da <xref:System.Index>.

Açık uçlu bir aralık elde etmek için `..` operatörün operands herhangi birini atlayabilirsiniz:

- `a..`eşdeğerdir`a..^0`
- `..b`eşdeğerdir`0..b`
- `..`eşdeğerdir`0..^0`

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

Daha fazla bilgi için [Endeksler ve aralıklar'a](../../tutorials/ranges-indexes.md)bakın.

## <a name="operator-overloadability"></a>Operatör aşırı yüklenebilirlik

`.`, `()`, `^`ve `..` işleçler aşırı yüklenemez. Operatör `[]` ayrıca aşırı yüklenebilir olmayan bir işleç olarak kabul edilir. Dizin oluşturmayı kullanıcı tanımlı türlerle desteklemek için [dizin oluşturmayı](../../programming-guide/indexers/index.md) kullanın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Üye erişimi](~/_csharplang/spec/expressions.md#member-access)
- [Öğe erişimi](~/_csharplang/spec/expressions.md#element-access)
- [Null koşullu işleç](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Çağırma ifadeleri](~/_csharplang/spec/expressions.md#invocation-expressions)

Endeksler ve aralıklar hakkında daha fazla bilgi için [özellik teklif notuna](~/_csharplang/proposals/csharp-8.0/ranges.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [?? (null-coalescing operatörü)](null-coalescing-operator.md)
- [:: operatör](namespace-alias-qualifier.md)
