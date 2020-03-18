---
title: Yapı türleri - C# başvurusu
ms.date: 02/24/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: b85d0df086f3ca65ed995594dd374286e1c3ba5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847735"
---
# <a name="structure-types-c-reference"></a>Yapı türleri (C# başvurusu)

*Yapı türü* (veya *yapı türü),* verileri ve ilgili işlevselliği kapsülleyebilen bir [değer türüdür.](value-types.md) Bir yapı `struct` türünü tanımlamak için anahtar sözcüğü kullanırsınız:

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

Yapı türleri *değer semantik*var. Diğer bir zamanda, bir yapı türü değişkeni türünün bir örneğini içerir. Varsayılan olarak, değişken değerleri atamada kopyalanır, bir bağımsız değişkeni bir yönteme geçirilir ve yöntem sonucunu döndürür. Yapı türünde bir değişken olması durumunda, türün bir örneği kopyalanır. Daha fazla bilgi için [Değer türlerine](value-types.md)bakın.

Genellikle, çok az veya hiç davranış sağlayan küçük veri merkezli türler tasarlamak için yapı türleri kullanırsınız. Örneğin, .NET bir sayıyı (hem [tamsayı](integral-numeric-types.md) hem de [gerçek),](floating-point-numeric-types.md) [Boolean değeri,](bool.md) [Unicode karakterini,](char.md)bir [zaman örneğini](xref:System.DateTime)temsil etmek için yapı türlerini kullanır. Bir türün davranışına odaklanmışsanız, bir [sınıf](../keywords/class.md)tanımlamayı düşünün. Sınıf türleri *referans semantik*var. Diğer bir zamanda, sınıf türünden bir değişken, örneğin kendisi değil, tür örneğinin bir örneğine başvuruda bulunun.

## <a name="limitations-with-the-design-of-a-structure-type"></a>Bir yapı türünün tasarımıile sınırlamalar

Bir yapı türü tasarlarken, aşağıdaki özel durumlar dışında, [sınıf](../keywords/class.md) türüyle aynı özelliklere sahip olursunuz:

- Parametresiz bir oluşturucu bildiremezsiniz. Her yapı türü zaten türün [varsayılan değerini](default-values.md) üreten örtülü parametresiz bir oluşturucu sağlar.

- Bir örnek alanını veya özelliği beyannamesinde başharfe ait olamazsınız. Ancak, bir [statik](../keywords/static.md) veya [const](../keywords/const.md) alanı veya statik bir özelliği bildiriminde başharfe döndürebilirsiniz.

- Yapı türünden bir oluşturucu, türün tüm örnek alanlarını başlatmalıdır.

- Bir yapı türü diğer sınıf veya yapı türünden devralınamaz ve bir sınıfın temeli olamaz. Ancak, bir yapı türü [arabirimleri](../keywords/interface.md)uygulayabilirsiniz.

- Bir yapı türü içinde [bir sonlandırıcı](../../programming-guide/classes-and-structs/destructors.md) bildiremezsiniz.

## <a name="instantiation-of-a-structure-type"></a>Bir yapı türünün anında

C#'da, kullanılmadan önce bildirilen bir değişkeni başlatmanız gerekir. Yapı türünde bir değişken `null` olamayacağından [(nullable değer türünde](nullable-value-types.md)bir değişken olmadığı sürece), ilgili türdeki bir örneği anında alabilmeniz gerekir. Bunu yapmanın birkaç yolu vardır.

Genellikle, [`new`](../operators/new-operator.md) işleç ile uygun bir yapıcı çağırarak bir yapı türü anında. Her yapı türünde en az bir oluşturucu vardır. Bu, türün [varsayılan değerini](default-values.md) üreten örtük bir parametresiz oluşturucu. Bir türün [varsayılan](../operators/default.md) değerini üretmek için varsayılan işleci veya literal de kullanabilirsiniz.

Yapı türünün tüm örnek alanlarına erişilebilirse, `new` operatör olmadan da anında ekleyebilirsiniz. Bu durumda, örneğin ilk kullanımından önce tüm örnek alanları başlatmanız gerekir. Aşağıdaki örnek, bunun nasıl yapılacağını gösterir:

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

[Yerleşik değer türleri](value-types.md#built-in-value-types)söz konusu olduğunda, türün bir değerini belirtmek için karşılık gelen literals kullanın.

## <a name="passing-structure-type-variables-by-reference"></a>Yapı tipi değişkenleri referansa göre geçirme

Bir yapı türü değişkenini bağımsız değişken olarak bir yönteme geçtiğinde veya bir yöntemden yapı türü değeri döndürdüğünde, yapı türünün tüm örneği kopyalanır. Bu, büyük yapı türleri içeren yüksek performanslı senaryolarda kodunuzu performansını etkileyebilir. Bir yapı türü değişkenini referans aylaaktararak değer kopyalamayı önleyebilirsiniz. Bir [`ref`](../keywords/ref.md#passing-an-argument-by-reference)bağımsız [`out`](../keywords/out-parameter-modifier.md)değişkenin başvuru yla geçirilmesi gerektiğini belirtmek için , veya [`in`](../keywords/in-parameter-modifier.md) yöntem parametre değiştiriciler kullanın. Referans bir yöntem sonucu döndürmek için [ref döner](../../programming-guide/classes-and-structs/ref-returns.md) kullanın. Daha fazla bilgi için bkz: [Güvenli ve verimli C# kodu yaz.](../../write-safe-efficient-code.md)

## <a name="conversions"></a>Dönüşümler

Herhangi bir yapı türü için, [kutulama ve unboxing](../../programming-guide/types/boxing-and-unboxing.md) dönüşümleri var ve <xref:System.ValueType?displayProperty=nameWithType> ve <xref:System.Object?displayProperty=nameWithType> türleri. Ayrıca, bir yapı türü ve uyguladığı herhangi bir arabirim arasında kutulama ve unboxing dönüşümleri de vardır.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Structs](~/_csharplang/spec/structs.md) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Tasarım yönergeleri - Sınıf ve yapı arasında seçim](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Tasarım yönergeleri - Yapı tasarımı](../../../standard/design-guidelines/struct.md)
- [Sınıflar ve yapılar](../../programming-guide/classes-and-structs/index.md)
