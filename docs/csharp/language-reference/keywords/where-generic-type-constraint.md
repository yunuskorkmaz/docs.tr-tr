---
title: where (genel tür kısıtlaması) - C# Reference
ms.date: 04/15/2020
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 5a56b8058735d3ca786520a82424c79d1975bfc4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463008"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (genel tür kısıtlaması) (C# Başvurusu)

Genel `where` bir tanımdaki yan tümce, genel bir tür, yöntem, temsilci veya yerel işlevdeki tür parametreleri için bağımsız değişken olarak kullanılan türler üzerindeki kısıtlamaları belirtir. Kısıtlamalar arabirimleri, temel sınıfları belirtebilir veya başvuru, değer veya yönetilmeyen tür olması için genel bir tür gerektirebilir. Tür bağımsız değişkeninin sahip olması gereken yetenekleri bildirirler.

Örneğin, tür parametresi `MyGenericClass` `T` <xref:System.IComparable%601> arabirimi uygular gibi genel bir sınıf bildirebilirsiniz:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Sorgu ifadesinde yer yan tümcesi hakkında daha fazla bilgi için [bkz.](where-clause.md)

Yan `where` tümce, taban sınıf kısıtlaması da içerebilir. Taban sınıf kısıtlaması, bu genel tür için tür bağımsız değişkeni olarak kullanılacak bir türün taban sınıf olarak belirtilen sınıfa sahip olduğunu veya bu taban sınıf olduğunu belirtir. Taban sınıf kısıtlaması kullanılırsa, bu tür parametresindeki diğer kısıtlamalardan önce görünmesi gerekir. Bazı türler taban sınıf kısıtlaması olarak <xref:System.Object> <xref:System.Array>izin <xref:System.ValueType>verilmez: , ve . C# <xref:System.Enum>7.3'den <xref:System.Delegate>önce <xref:System.MulticastDelegate> ve taban sınıf kısıtlamaları olarak da izin verilmedi. Aşağıdaki örnek, şimdi taban sınıf olarak belirtilebilen türleri gösterir:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

C# 8.0 ve sonraki durumlarda, taban sınıf türünün nullable'ı zorlanır. Taban sınıf nullable (örneğin) `Base`ise, tür bağımsız değişkeni nullable olmalıdır. Taban sınıf nullable ise (örneğin), `Base?`tür bağımsız değişkeni nullable veya unnullable referans türü olabilir. Derleyici, taban sınıf nullable olmadığında tür bağımsız değişkeni nullable bir başvuru türü yse bir uyarı yayınlar.

Yan `where` tümce, türün `class` a `struct`veya bir . Kısıtlama, `struct` bir taban sınıf kısıtlaması belirtme `System.ValueType`gereksinimini ortadan kaldırır. Tür `System.ValueType` taban sınıf kısıtlaması olarak kullanılmayabilir. Aşağıdaki örnek, hem `class` `struct` kısıtlamaları hem de kısıtlamaları gösterir:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

C# 8.0 ve sonraki durumlarda, `class` kısıtlama bir tür geçersiz bir başvuru türü gerektirir. Nullable başvuru türlerine izin `class?` vermek için, hem nullable hem de nullable olmayan başvuru türlerine izin veren kısıtlamayı kullanın.

Yan `where` tümce `notnull` kısıtlamayı içerebilir. Kısıtlama, `notnull` tür parametresini nullable olmayan türlerle sınırlar. Bu tür bir [değer türü](../builtin-types/value-types.md) veya nullable olmayan bir başvuru türü olabilir. Kısıtlama, `notnull` bir [ `nullable enable` bağlamda](../../nullable-references.md#nullable-contexts)derlenen kod için C# 8.0'dan başlayarak kullanılabilir. Diğer kısıtlamaların aksine, bir tür `notnull` bağımsız değişkenkısıtlamayı ihlal ederse, derleyici hata yerine bir uyarı oluşturur. Uyarılar yalnızca bir `nullable enable` bağlamda oluşturulur.

> [!IMPORTANT]
> Kısıtlamayı `notnull` içeren genel bildirimler geçersiz bir ilgisiz bağlamda kullanılabilir, ancak derleyici kısıtlamayı zorlamaz.

[!code-csharp[using the nonnull constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#NotNull)]

Yan `where` tümce, `unmanaged` bir kısıtlama da içerebilir. Kısıtlama, `unmanaged` tür parametresini [yönetilmeyen türler](../builtin-types/unmanaged-types.md)olarak bilinen türlerle sınırlar. Kısıtlama, `unmanaged` c#'a düşük seviyeli interop kodu yazmayı kolaylaştırır. Bu kısıtlama, tüm yönetilmeyen türler arasında yeniden kullanılabilir yordamlar sağlar. Kısıtlama `unmanaged` `class` veya `struct` kısıtlama ile birleştirilemez. Kısıtlama, `unmanaged` türün aşağıdaki `struct`gibi olması gerektiğini zorlar:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

Yan `where` tümce, bir oluşturucu `new()`kısıtlama sıda içerebilir. Bu kısıtlama, işleci kullanarak bir tür parametresi örneği oluşturmayı `new` mümkün kılar. [Yeni() Kısıtlama,](new-constraint.md) derleyiciye, sağlanan herhangi bir tür bağımsız değişkeninin erişilebilir bir parametresiz oluşturucuya sahip olması gerektiğini bilmesini sağlar. Örneğin:

[!code-csharp[using the new constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

Kısıtlama `new()` `where` yan tümcede son görünür. Kısıtlama `new()` `struct` veya `unmanaged` kısıtlamalarla birleştirilemez. Bu kısıtlamaları karşılayan tüm türler, `new()` kısıtlamayı gereksiz hale getiren erişilebilir bir parametresiz oluşturucuya sahip olmalıdır.

Birden çok tür parametresi ile, örneğin, her tür parametresi için bir `where` yan tümce kullanın:

[!code-csharp[using multiple where constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Aşağıdaki örnekte gösterildiği gibi, genel yöntemlerin parametrelerini yazına kısıtlamalar da ekleyebilirsiniz:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Temsilciler üzerindeki tür parametre kısıtlamalarını açıklayan sözdiziminin yöntemlerle aynı olduğuna dikkat edin:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Genel temsilciler hakkında bilgi için [Genel Temsilciler'e](../../programming-guide/generics/generic-delegates.md)bakın.

Sözdizimi ve kısıtlamaların kullanımı yla ilgili ayrıntılar için, [Tür Parametreleri üzerindeki Kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md)bölümüne bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Genel Türlere Giriş](../../programming-guide/generics/index.md)
- [yeni Kısıtlama](./new-constraint.md)
- [Tür Parametrelerindeki Kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md)
