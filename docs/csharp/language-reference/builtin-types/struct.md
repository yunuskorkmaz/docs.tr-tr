---
title: Yapı türleri-C# başvurusu
ms.date: 04/21/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 515b8d9adc1359581625f0d822e254d2c1df3b58
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062502"
---
# <a name="structure-types-c-reference"></a>Yapı türleri (C# Başvurusu)

*Yapı türü* (veya *Yapı türü*), verileri ve ilgili işlevleri kapsüllemek için bir [değer türüdür](value-types.md) . `struct`Yapı türünü tanımlamak için anahtar sözcüğünü kullanırsınız:

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

Yapı türlerinde *değer semantiği*vardır. Diğer bir deyişle, yapı türünün bir değişkeni türünün bir örneğini içerir. Varsayılan olarak, değişken değerleri atamaya kopyalanır, bir yönteme bağımsız değişken geçirme ve bir yöntem sonucu döndürüyor. Yapı türü değişkeni söz konusu olduğunda, türün bir örneği kopyalanır. Daha fazla bilgi için bkz. [değer türleri](value-types.md).

Genellikle, çok az davranış sağlayan küçük veri merkezli türler tasarlamak için yapı türlerini kullanırsınız. Örneğin, .NET bir sayıyı (hem [tamsayı](integral-numeric-types.md) hem de [gerçek](floating-point-numeric-types.md)), bir [Boole değerini](bool.md), bir [Unicode karakteri](char.md), bir [zaman örneğini](xref:System.DateTime)temsil etmek için yapı türlerini kullanır. Bir türün davranışına odaklandıysanız bir [sınıf](../keywords/class.md)tanımlamayı düşünün. Sınıf türlerinde *başvuru semantiği*vardır. Diğer bir deyişle, bir sınıf türünün değişkeni, örneğin kendisi değil, türün bir örneğine bir başvuru içerir.

Yapı türlerinde değer semantiklerine sahip olduğundan, *değişmez* yapı türlerini tanımlamanızı öneririz.

## <a name="readonly-struct"></a>`readonly`sýný

C# 7,2 ' den başlayarak, `readonly` bir yapı türünün sabit olduğunu bildirmek için değiştiricisini kullanın:

[!code-csharp[readonly struct](snippets/StructType.cs#ReadonlyStruct)]

Bir yapının tüm veri üyeleri `readonly` aşağıdaki şekilde salt okunabilir olmalıdır:

- Herhangi bir alan bildirimi [ `readonly` değiştiriciye](../keywords/readonly.md) sahip olmalıdır
- Otomatik olarak uygulanan özellikler dahil olmak üzere herhangi bir özellik salt okunabilir olmalıdır

Bu, yapının hiçbir üyesinin `readonly` yapının durumunu değiştirdiğine garanti eder.

> [!NOTE]
> Bir `readonly` yapıda, kesilebilir başvuru türünün veri üyesi yine de kendi durumunu mukuz edebilir. Örneğin, bir <xref:System.Collections.Generic.List%601> örneği değiştiremezsiniz, ancak buna yeni öğeler ekleyebilirsiniz.

## <a name="readonly-instance-members"></a>`readonly`örnek üyeleri

C# 8,0 ' den başlayarak, `readonly` bir örnek üyesinin bir yapının durumunu değiştirmediğini bildirmek için değiştiricisini de kullanabilirsiniz. Tüm yapı türünü olarak bildiremezseniz `readonly` , `readonly` yapının durumunu değiştirmeyin örnek üyelerini işaretlemek için değiştiricisini kullanın. Bir `readonly` yapıda, her örnek üye örtük olarak olur `readonly` .

Bir `readonly` örnek üyesi içinde, yapının örnek alanlarına atayamazsınız. Ancak bir `readonly` üye üye olmayan bir öğesi çağırabilir `readonly` . Bu durumda, derleyici yapı örneğinin bir kopyasını oluşturur ve bu kopyada üye olmayan ' i çağırır `readonly` . Sonuç olarak, özgün yapı örneği değiştirilmez.

Genellikle, `readonly` değiştiricisini aşağıdaki örnek üye türlerine uygularsınız:

- Yöntem

  [!code-csharp[readonly method](snippets/StructType.cs#ReadonlyMethod)]

  Ayrıca, `readonly` içinde belirtilen yöntemleri geçersiz kılan yöntemlere değiştiricisini uygulayabilirsiniz <xref:System.Object?displayProperty=nameWithType> :

  [!code-csharp[readonly override](snippets/StructType.cs#ReadonlyOverride)]

- Özellikler ve Dizin oluşturucular:

  [!code-csharp[readonly property get](snippets/StructType.cs#ReadonlyProperty)]

  `readonly`Değiştirici ' i bir özelliğin veya dizin oluşturucunun her ikisine de uygulamanız gerekiyorsa, bunu özelliğin veya dizin oluşturucunun bildiriminde uygulayın.

  > [!NOTE]
  > Derleyici, `get` [auto-implemented property](../../programming-guide/classes-and-structs/auto-implemented-properties.md) `readonly` `readonly` bir özellik bildiriminde değiştiricinin varlığından bağımsız olarak otomatik uygulanan bir özelliğin erişimcisini bildirir.

`readonly`Bir yapı türünün statik üyelerine değiştiricisini uygulayamazsınız.

Derleyici, `readonly` performans iyileştirmeleri için değiştiriciyi kullanabilir. Daha fazla bilgi için bkz. [yazma güvenli ve verimli C# kodu](../../write-safe-efficient-code.md).

## <a name="limitations-with-the-design-of-a-structure-type"></a>Yapı türünün tasarımıyla ilgili sınırlamalar

Bir yapı türü tasarlarken, aşağıdaki özel durumlarla birlikte bir [sınıf](../keywords/class.md) türüyle aynı olanaklara sahip olursunuz:

- Parametresiz bir Oluşturucu bildiremezsiniz. Her yapı türü zaten türün [varsayılan değerini](default-values.md) üreten örtük parametresiz bir oluşturucu sağlar.

- Bildiriminde bir örnek alanı veya özelliği başlatamıyor. Ancak, bir [statik](../keywords/static.md) veya [const](../keywords/const.md) alanı veya bildiriminde statik bir özellik başlatabilirsiniz.

- Yapı türünde bir Oluşturucu, türün tüm örnek alanlarını başlatmalıdır.

- Yapı türü, diğer sınıf veya yapı türünden devralınabilir ve bir sınıfın temeli olamaz. Ancak, bir yapı türü [arabirimler](../keywords/interface.md)uygulayabilir.

- Bir yapı türü içinde [sonlandırıcıyı](../../programming-guide/classes-and-structs/destructors.md) bildiremezsiniz.

## <a name="instantiation-of-a-structure-type"></a>Yapı türünü örnekleme

C# dilinde, kullanılmadan önce, belirtilen bir değişkeni başlatmalısınız. Bir yapı türü değişkeni olamaz `null` ( [null yapılabilir değer türünde](nullable-value-types.md)bir değişken değilse), karşılık gelen türün bir örneğini örneklemelisiniz. Bunu yapmak için birkaç yol vardır.

Genellikle, işleçle uygun bir oluşturucuyu çağırarak bir yapı türü örnekleyebilirsiniz [`new`](../operators/new-operator.md) . Her yapı türünün en az bir Oluşturucusu vardır. Bu, türün [varsayılan değerini](default-values.md) üreten örtük parametresiz bir Oluşturucu. Bir türün varsayılan değerini oluşturmak için [varsayılan değer ifadesini](../operators/default.md) de kullanabilirsiniz.

Bir yapı türünün tüm örnek alanlarına erişilebiliyorsa, işleci olmadan da örneğini oluşturabilirsiniz `new` . Bu durumda, örneğin ilk kullanmadan önce tüm örnek alanlarını başlatmalısınız. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir:

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

[Yerleşik değer türleri](value-types.md#built-in-value-types)söz konusu olduğunda, türü bir değer belirtmek için karşılık gelen değişmez değerleri kullanın.

## <a name="passing-structure-type-variables-by-reference"></a>Başvuruya göre yapı türü değişkenleri geçirme

Bir yapı türü değişkenini bir bağımsız değişken olarak bir yönteme geçirdiğinizde veya bir yöntemden yapı türü değer döndürmeniz durumunda, bir yapı türünün tüm örneği kopyalanır. Bu, büyük yapı türlerini içeren yüksek performanslı senaryolarda kodunuzun performansını etkileyebilir. Bir yapı türü değişkenini başvuruya göre geçirerek değer kopyalamaya engel olabilirsiniz. [`ref`](../keywords/ref.md#passing-an-argument-by-reference) [`out`](../keywords/out-parameter-modifier.md) [`in`](../keywords/in-parameter-modifier.md) Bir bağımsız değişkenin başvuruya göre geçirilmesi gerektiğini göstermek için, veya yöntem parametre değiştiricilerini kullanın. Başvuruya göre bir yöntem sonucu döndürmek için [ref dönüşleri](../../programming-guide/classes-and-structs/ref-returns.md) kullanın. Daha fazla bilgi için bkz. [yazma güvenli ve verimli C# kodu](../../write-safe-efficient-code.md).

## <a name="ref-struct"></a>`ref`sýný

C# 7,2 ' den başlayarak, `ref` bir yapı türünün bildiriminde değiştiricisini kullanabilirsiniz. `ref`Yapı türünün örnekleri yığında ayrılır ve yönetilen yığına atlayabilir. Derleyicinin yapı türlerinin kullanımını şu şekilde sınırladığından emin olmak için `ref` :

- `ref`Struct bir dizinin öğe türü olamaz.
- Bir `ref` struct, bir sınıfın veya struct olmayan bir alanın tanımlı bir türü olamaz `ref` .
- Bir `ref` struct arabirimleri uygulayamaz.
- Bir `ref` struct veya olarak kutulanabilir <xref:System.ValueType?displayProperty=nameWithType> <xref:System.Object?displayProperty=nameWithType> .
- `ref`Struct bir tür bağımsız değişkeni olamaz.
- Bir `ref` struct değişkeni bir [lambda ifadesi](../operators/lambda-expressions.md) veya [yerel bir işlev](../../programming-guide/classes-and-structs/local-functions.md)tarafından yakalanamaz.
- Bir `ref` struct değişkeni bir [`async`](../keywords/async.md) yöntemde kullanılamaz. Ancak, `ref` Yapı değişkenlerini, örneğin veya döndüren zaman uyumlu yöntemlerle kullanabilirsiniz <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> .
- Bir `ref` struct değişkeni [yineleyiciler](../../iterators.md)içinde kullanılamaz.

Genellikle, `ref` Yapı türlerinin veri üyelerini de içeren bir türe ihtiyacınız olduğunda bir struct türü tanımlarsınız `ref` :

[!code-csharp[ref struct](snippets/StructType.cs#RefStruct)]

Bir yapıyı olarak bildirmek için, `ref` [`readonly`](#readonly-struct) `readonly` `ref` tür bildiriminde ve değiştiricilerini birleştirin (değiştiricinin `readonly` değiştiricisinden önce gelmesi gerekir `ref` ):

[!code-csharp[readonly ref struct](snippets/StructType.cs#ReadonlyRef)]

.NET ' te, bir `ref` struct örnekleri ve ' dir <xref:System.Span%601?displayProperty=nameWithType> <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> .

## <a name="conversions"></a>Dönüşümler

Herhangi bir yapı türü için ( [ `ref` Yapı](#ref-struct) türleri hariç), ve türlerinden ve türlerine bir [paketleme ve kutudan](../../programming-guide/types/boxing-and-unboxing.md) çıkarma dönüştürmeleri mevcuttur <xref:System.ValueType?displayProperty=nameWithType> <xref:System.Object?displayProperty=nameWithType> . Ayrıca, yapı türü ve uyguladığı herhangi bir arabirim arasında kutulama ve kutudan çıkarma dönüştürmeleri de mevcuttur.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [yapılar](~/_csharplang/spec/structs.md) bölümüne bakın.

C# 7,2 ve üzeri sürümlerde sunulan özellikler hakkında daha fazla bilgi için aşağıdaki özellik teklifi notlarına bakın:

- [ReadOnly yapılar](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs)
- [Salt okunur örnek üyeleri](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)
- [Başvuru benzeri türler ile derleme zamanı güvenliği](~/_csharplang/proposals/csharp-7.2/span-safety.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Tasarım yönergeleri-sınıf ve yapı arasında seçim yapma](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Tasarım yönergeleri-yapı tasarımı](../../../standard/design-guidelines/struct.md)
- [Sınıflar ve yapılar](../../programming-guide/classes-and-structs/index.md)
