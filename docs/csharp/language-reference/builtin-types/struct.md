---
title: Yapı türleri - C# başvurusu
ms.date: 04/21/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: dbe9b47625589de834b7a8021640885ca0920b96
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "82021267"
---
# <a name="structure-types-c-reference"></a>Yapı türleri (C# başvurusu)

*Yapı türü* (veya *yapı türü),* verileri ve ilgili işlevselliği kapsülleyebilen bir [değer türüdür.](value-types.md) Bir yapı `struct` türünü tanımlamak için anahtar sözcüğü kullanırsınız:

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

Yapı türleri *değer semantik*var. Diğer bir zamanda, bir yapı türü değişkeni türünün bir örneğini içerir. Varsayılan olarak, değişken değerleri atamada kopyalanır, bir bağımsız değişkeni bir yönteme geçirilir ve yöntem sonucunu döndürür. Yapı türünde bir değişken olması durumunda, türün bir örneği kopyalanır. Daha fazla bilgi için [Değer türlerine](value-types.md)bakın.

Genellikle, çok az veya hiç davranış sağlayan küçük veri merkezli türler tasarlamak için yapı türleri kullanırsınız. Örneğin, .NET bir sayıyı (hem [tamsayı](integral-numeric-types.md) hem de [gerçek),](floating-point-numeric-types.md) [Boolean değeri,](bool.md) [Unicode karakterini,](char.md)bir [zaman örneğini](xref:System.DateTime)temsil etmek için yapı türlerini kullanır. Bir türün davranışına odaklanmışsanız, bir [sınıf](../keywords/class.md)tanımlamayı düşünün. Sınıf türleri *referans semantik*var. Diğer bir zamanda, sınıf türünden bir değişken, örneğin kendisi değil, tür örneğinin bir örneğine başvuruda bulunun.

Yapı türlerinin değer semantikleri olduğundan, *değişmez* yapı türlerini tanımlamanızı öneririz.

## <a name="readonly-struct"></a>`readonly`Yapı

C# 7.2 ile başlayarak, bir yapı türünün değişmez olduğunu bildirmek için `readonly` değiştirici kullanırsınız:

[!code-csharp[readonly struct](snippets/StructType.cs#ReadonlyStruct)]

Bir `readonly` yapının tüm veri üyeleri aşağıdaki gibi salt okunur olmalıdır:

- Herhangi bir alan bildirimi [ `readonly` değiştirici olmalıdır](../keywords/readonly.md)
- Otomatik olarak uygulananlar da dahil olmak üzere herhangi bir özellik yalnızca okunmalıdır

Bu, bir `readonly` yapının hiçbir üyesinin yapının durumunu modiyi olmadığını garanti eder.

> [!NOTE]
> Bir `readonly` yapıda, mutable başvuru türündeki bir veri üyesi yine de kendi durumunu mutasyona uğrayabilir. Örneğin, bir <xref:System.Collections.Generic.List%601> örneği değiştiremezsiniz, ancak buna yeni öğeler ekleyebilirsiniz.

## <a name="readonly-instance-members"></a>`readonly`örnek üyeler

C# 8.0 ile başlayarak, `readonly` bir örnek üyenin yapının durumunu değiştirmediğini bildirmek için değiştiriciyi de kullanabilirsiniz. Tüm yapı türünü `readonly`, yapının durumunu değiştirmeyen örnek üyeleri işaretlemek için `readonly` değiştiriyi kullanın. Bir `readonly` yapıda, her örnek üye `readonly`örtülü olarak .

Bir `readonly` örnek üyeiçinde, yapının örnek alanlarına atayamazsınız. Ancak, `readonly` bir üye`readonly` üye olmayan bir araya gelebilir. Bu durumda derleyici yapı örneğinin bir kopyasını oluşturur ve`readonly` bu kopyada üye olmayanı çağırır. Sonuç olarak, özgün yapı örneği değiştirilmez.

Genellikle, `readonly` değiştiriciaşağıdaki örnek üye türlerine uygularsınız:

- Yöntemler:

  [!code-csharp[readonly method](snippets/StructType.cs#ReadonlyMethod)]

  `readonly` Ayrıca, aşağıdaki durumlarda <xref:System.Object?displayProperty=nameWithType>bildirilen yöntemleri geçersiz kılınan yöntemlere değiştirici uygulayabilirsiniz:

  [!code-csharp[readonly override](snippets/StructType.cs#ReadonlyOverride)]

- özellikleri ve dizinleyiciler:

  [!code-csharp[readonly property get](snippets/StructType.cs#ReadonlyProperty)]

  `readonly` Değiştiriciyi bir mülkün veya dizinleyicinin her iki erişimine de uygulamanız gerekiyorsa, bunu özellik veya dizinleyicinin bildirimine uygulayın.

  > [!NOTE]
  > Derleyici, bir `get` özellik bildiriminde `readonly` `readonly` değiştiricinin varlığından bağımsız olarak otomatik olarak uygulanan bir [özelliğin](../../programming-guide/classes-and-structs/auto-implemented-properties.md) erişimini bildirir.

`readonly` Değiştiriciyi bir yapı türünün statik üyelerine uygulayamazsınız.

Derleyici, performans optimizasyonları `readonly` için değiştiriciden yararlanabilir. Daha fazla bilgi için bkz: [Güvenli ve verimli C# kodu yaz.](../../write-safe-efficient-code.md)

## <a name="limitations-with-the-design-of-a-structure-type"></a>Bir yapı türünün tasarımıile sınırlamalar

Bir yapı türü tasarlarken, aşağıdaki özel durumlar dışında, [sınıf](../keywords/class.md) türüyle aynı özelliklere sahip olursunuz:

- Parametresiz bir oluşturucu bildiremezsiniz. Her yapı türü zaten türün [varsayılan değerini](default-values.md) üreten örtülü parametresiz bir oluşturucu sağlar.

- Bir örnek alanını veya özelliği beyannamesinde başharfe ait olamazsınız. Ancak, bir [statik](../keywords/static.md) veya [const](../keywords/const.md) alanı veya statik bir özelliği bildiriminde başharfe döndürebilirsiniz.

- Yapı türünden bir oluşturucu, türün tüm örnek alanlarını başlatmalıdır.

- Yapı türü diğer sınıf veya yapı türünden devralamaz ve bir sınıfın temeli olamaz. Ancak, bir yapı türü [arabirimleri](../keywords/interface.md)uygulayabilirsiniz.

- Bir yapı türü içinde [bir sonlandırıcı](../../programming-guide/classes-and-structs/destructors.md) bildiremezsiniz.

## <a name="instantiation-of-a-structure-type"></a>Bir yapı türünün anında

C#'da, kullanılmadan önce bildirilen bir değişkeni başlatmanız gerekir. Yapı türünde bir değişken `null` [(nullable değer türünde](nullable-value-types.md)bir değişken olmadığı sürece) olamaz, ilgili türdeki bir örneği anında alamalısınız. Bunu yapmanın birkaç yolu vardır.

Genellikle, [`new`](../operators/new-operator.md) işleç ile uygun bir yapıcı çağırarak bir yapı türü anında. Her yapı türünde en az bir oluşturucu vardır. Bu, türün [varsayılan değerini](default-values.md) üreten örtük bir parametresiz oluşturucu. Bir türün [varsayılan](../operators/default.md) değerini oluşturmak için varsayılan değer ifadesini de kullanabilirsiniz.

Yapı türünün tüm örnek alanlarına erişilebilirse, `new` operatör olmadan da anında ekleyebilirsiniz. Bu durumda, örneğin ilk kullanımından önce tüm örnek alanları başlatmanız gerekir. Aşağıdaki örnek, bunun nasıl yapılacağını gösterir:

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

[Yerleşik değer türleri](value-types.md#built-in-value-types)söz konusu olduğunda, türün bir değerini belirtmek için karşılık gelen literals kullanın.

## <a name="passing-structure-type-variables-by-reference"></a>Yapı tipi değişkenleri referansa göre geçirme

Bir yapı türü değişkenini bağımsız değişken olarak bir yönteme geçtiğinde veya bir yöntemden yapı türü değeri döndürdüğünde, yapı türünün tüm örneği kopyalanır. Bu, büyük yapı türleri içeren yüksek performanslı senaryolarda kodunuzu performansını etkileyebilir. Bir yapı türü değişkenini referans aylaaktararak değer kopyalamayı önleyebilirsiniz. Bir [`ref`](../keywords/ref.md#passing-an-argument-by-reference)bağımsız [`out`](../keywords/out-parameter-modifier.md)değişkenin başvuru yla geçirilmesi gerektiğini belirtmek için , veya [`in`](../keywords/in-parameter-modifier.md) yöntem parametre değiştiriciler kullanın. Referans bir yöntem sonucu döndürmek için [ref döner](../../programming-guide/classes-and-structs/ref-returns.md) kullanın. Daha fazla bilgi için bkz: [Güvenli ve verimli C# kodu yaz.](../../write-safe-efficient-code.md)

## <a name="ref-struct"></a>`ref`Yapı

C# 7.2 ile başlayarak, `ref` bir yapı türü bildiriminde değiştirici kullanabilirsiniz. Yapı türü `ref` örnekleri yığına ayrılır ve yönetilen yığına kaçamaz. Bunu sağlamak için derleyici yapı `ref` türlerinin kullanımını aşağıdaki gibi sınırlar:

- Bir `ref` yapı, bir dizinin öğe türü olamaz.
- Bir `ref` yapı, bir sınıfın veya yapı olmayan`ref` bir alanın beyan edilen türü olamaz.
- Bir `ref` yapı arabirimleri uygulayamaz.
- Bir `ref` yapı kutulanamaz <xref:System.ValueType?displayProperty=nameWithType> ya da. <xref:System.Object?displayProperty=nameWithType>
- Bir `ref` yapı tür bağımsız değişkeni olamaz.
- Bir `ref` yapı değişkeni [lambda ifadesi](../../programming-guide/statements-expressions-operators/lambda-expressions.md) veya yerel bir [işlev](../../programming-guide/classes-and-structs/local-functions.md)tarafından ele geçirilemez.
- Bir `ref` yapı değişkeni bir [`async`](../keywords/async.md) yöntemde kullanılamaz. Ancak, eşzamanlı `ref` yöntemlerde struct değişkenleri kullanabilirsiniz, örneğin, bu <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>döndürülen veya .
- Bir `ref` yapı [değişkeni yineleyicilerde](../../iterators.md)kullanılamaz.

Genellikle, `ref` `ref` yapı türlerinin veri üyelerini de içeren bir türe ihtiyacınız olduğunda bir yapı türü tanımlarsınız:

[!code-csharp[ref struct](snippets/StructType.cs#RefStruct)]

Bir `ref` [`readonly`](#readonly-struct)yapıyı , tür bildiriminde `readonly` ve `ref` değiştiricileri birleştirin `readonly` (değiştiricinin `ref` önce gelmesi gerekir):

[!code-csharp[readonly ref struct](snippets/StructType.cs#ReadonlyRef)]

.NET'te, `ref` bir yapı örnekleri <xref:System.Span%601?displayProperty=nameWithType> <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>ve .

## <a name="conversions"></a>Dönüşümler

Herhangi bir yapı türü için [ `ref` (yapı](#ref-struct) türleri hariç), [kutulama ve unboxing](../../programming-guide/types/boxing-and-unboxing.md) dönüşümleri <xref:System.ValueType?displayProperty=nameWithType> ve <xref:System.Object?displayProperty=nameWithType> türleri vardır. Ayrıca, bir yapı türü ve uyguladığı herhangi bir arabirim arasında kutulama ve unboxing dönüşümleri de vardır.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Structs](~/_csharplang/spec/structs.md) bölümüne bakın.

C# 7.2 ve sonraki özellikler hakkında daha fazla bilgi için aşağıdaki özellik teklif notlarına bakın:

- [Yalnızca okuma structs](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs)
- [Salt okunur örnek üyeleri](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)
- [Başvuru benzeri türler ile derleme zamanı güvenliği](~/_csharplang/proposals/csharp-7.2/span-safety.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Tasarım yönergeleri - Sınıf ve yapı arasında seçim](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Tasarım yönergeleri - Yapı tasarımı](../../../standard/design-guidelines/struct.md)
- [Sınıflar ve structs](../../programming-guide/classes-and-structs/index.md)
