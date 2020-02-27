---
title: Yapı türleri- C# başvuru
ms.date: 02/24/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 6113912f176d2d7b68c77ff2e78a361b373ca31a
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634871"
---
# <a name="structure-types-c-reference"></a>Yapı türleri (C# başvuru)

*Yapı türü* (veya *Yapı türü*), verileri ve ilgili işlevleri kapsüllemek için bir [değer türüdür](value-types.md) . `struct` anahtar sözcüğünü kullanarak bir yapı türü tanımlayabilirsiniz:

[!code-csharp[struct example](~/samples/csharp/language-reference/builtin-types/StructType.cs#StructExample)]

Yapı türlerinde *değer semantiği*vardır. Diğer bir deyişle, yapı türünün bir değişkeni türünün bir örneğini içerir. Varsayılan olarak, değişken değerleri atamaya kopyalanır, bir yönteme bağımsız değişken geçirme ve bir yöntem sonucu döndürüyor. Yapı türü değişkeni söz konusu olduğunda, türün bir örneği kopyalanır. Daha fazla bilgi için bkz. [değer türleri](value-types.md).

Genellikle, çok az davranış sağlayan küçük veri merkezli türler tasarlamak için yapı türlerini kullanırsınız. Örneğin, .NET bir sayıyı (hem [tamsayı](integral-numeric-types.md) hem de [gerçek](floating-point-numeric-types.md)), bir [Boole değerini](bool.md), bir [Unicode karakteri](char.md), bir [zaman örneğini](xref:System.DateTime)temsil etmek için yapı türlerini kullanır. Bir türün davranışına odaklandıysanız bir [sınıf](../keywords/class.md)tanımlamayı düşünün. Sınıf türlerinde *başvuru semantiği*vardır. Diğer bir deyişle, bir sınıf türünün değişkeni, örneğin kendisi değil, türün bir örneğine bir başvuru içerir.

## <a name="limitations-with-the-design-of-a-structure-type"></a>Yapı türünün tasarımıyla ilgili sınırlamalar

Bir yapı türü tasarlarken, aşağıdaki özel durumlarla birlikte bir [sınıf](../keywords/class.md) türüyle aynı olanaklara sahip olursunuz:

- Parametresiz bir Oluşturucu bildiremezsiniz. Her yapı türü zaten türün [varsayılan değerini](default-values.md) üreten örtük parametresiz bir oluşturucu sağlar.

- Bildiriminde bir örnek alanı veya özelliği başlatamıyor. Ancak, bir [statik](../keywords/static.md) veya [const](../keywords/const.md) alanı veya bildiriminde statik bir özellik başlatabilirsiniz.

- Yapı türünde bir Oluşturucu, türün tüm örnek alanlarını başlatmalıdır.

- Yapı türü, diğer sınıf veya yapı türünden devralınabilir ve bir sınıfın temeli olamaz. Ancak, bir yapı türü [arabirimler](../keywords/interface.md)uygulayabilir.

- Bir yapı türü içinde [sonlandırıcıyı](../../programming-guide/classes-and-structs/destructors.md) bildiremezsiniz.

## <a name="instantiation-of-a-structure-type"></a>Yapı türünü örnekleme

' C#De, kullanılmadan önce, belirtilen bir değişkeni başlatmalısınız. Bir yapı türü değişkeni `null` olamaz ( [null yapılabilir değer türünde](nullable-value-types.md)bir değişken olmadığı takdirde), karşılık gelen türün bir örneğini örneklemelisiniz. Bunu yapmak için birkaç yol vardır.

Genellikle, [`new`](../operators/new-operator.md) işleçle uygun bir oluşturucuyu çağırarak bir yapı türü örnekleyebilirsiniz. Her yapı türünün en az bir Oluşturucusu vardır. Bu, türün [varsayılan değerini](default-values.md) üreten örtük parametresiz bir Oluşturucu. Bir türün varsayılan değerini oluşturmak için [varsayılan](../operators/default.md) işleci veya hazır değeri de kullanabilirsiniz.

Bir yapı türünün tüm örnek alanlarına erişilebiliyorsa, `new` işleci olmadan da örneğini oluşturabilirsiniz. Bu durumda, örneğin ilk kullanmadan önce tüm örnek alanlarını başlatmalısınız. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir:

[!code-csharp[without new](~/samples/csharp/language-reference/builtin-types/StructType.cs#WithoutNew)]

[Yerleşik değer türleri](value-types.md#built-in-value-types)söz konusu olduğunda, türü bir değer belirtmek için karşılık gelen değişmez değerleri kullanın.

## <a name="passing-structure-type-variables-by-reference"></a>Başvuruya göre yapı türü değişkenleri geçirme

Bir yapı türü değişkenini bir bağımsız değişken olarak bir yönteme geçirdiğinizde veya bir yöntemden yapı türü değer döndürmeniz durumunda, bir yapı türünün tüm örneği kopyalanır. Bu, büyük yapı türlerini içeren yüksek performanslı senaryolarda kodunuzun performansını etkileyebilir. Bir yapı türü değişkenini başvuruya göre geçirerek değer kopyalamaya engel olabilirsiniz. Bir bağımsız değişkenin başvuruya göre geçirilmesi gerektiğini göstermek için [`ref`](../keywords/ref.md#passing-an-argument-by-reference), [`out`](../keywords/out-parameter-modifier.md)veya [`in`](../keywords/in-parameter-modifier.md) Yöntem parametre değiştiricilerini kullanın. Başvuruya göre bir yöntem sonucu döndürmek için [ref dönüşleri](../../programming-guide/classes-and-structs/ref-returns.md) kullanın. Daha fazla bilgi için bkz. [yazma güvenli ve C# verimli kod](../../write-safe-efficient-code.md).

## <a name="conversions"></a>Dönüşümler

Herhangi bir yapı türü için, <xref:System.ValueType?displayProperty=nameWithType> ve <xref:System.Object?displayProperty=nameWithType> türlerine ve öğesinden, ve bu türlerden bir [paketleme ve kutudan](../../programming-guide/types/boxing-and-unboxing.md) çıkarma dönüştürmeleri mevcuttur. Ayrıca, yapı türü ve uyguladığı herhangi bir arabirim arasında kutulama ve kutudan çıkarma dönüştürmeleri de mevcuttur.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [yapılar](~/_csharplang/spec/structs.md) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [Tasarım yönergeleri-sınıf ve yapı arasında seçim yapma](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Tasarım yönergeleri-yapı tasarımı](../../../standard/design-guidelines/struct.md)
- [Sınıflar ve yapılar](../../programming-guide/classes-and-structs/index.md)
