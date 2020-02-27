---
title: WHERE (genel tür kısıtlaması)- C# başvuru
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: d236420c5019f7529b729155b13df50807dc1dab
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626717"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (genel tür kısıtlaması) (C# Başvurusu)

Genel tanımda `where` yan tümcesi, genel bir tür, metot, temsilci veya yerel işlev içindeki tür parametreleri için bağımsız değişken olarak kullanılan türlerde kısıtlamalar belirtir. Kısıtlamalar, arabirimler, temel sınıflar veya bir genel türün bir başvuru, değer veya yönetilmeyen tür olmasını gerektirebilir. Bunlar, tür bağımsız değişkeninin sahip olması gereken özellikleri bildirir.

Örneğin, `T` tür parametresi <xref:System.IComparable%601> arabirimini uyguladığı için, `MyGenericClass`genel bir sınıf bildirebilirsiniz:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Bir sorgu ifadesindeki WHERE yan tümcesi hakkında daha fazla bilgi için bkz. [WHERE yan tümcesi](where-clause.md).

`where` yan tümcesi bir temel sınıf kısıtlaması de içerebilir. Temel sınıf kısıtlaması, bu genel türün tür bağımsız değişkeni olarak kullanılacak bir türün, bu genel tür için bir tür bağımsız değişkeni olarak kullanılacak bir temel sınıf (veya temel sınıf) olarak belirtilen sınıfa sahip olduğunu belirtir. Temel sınıf kısıtlaması kullanılırsa, bu tür parametresindeki diğer kısıtlamaların önüne gelmelidir. Bir temel sınıf kısıtlaması olarak bazı türlere izin verilmez: <xref:System.Object>, <xref:System.Array>ve <xref:System.ValueType>. C# 7,3 ' den önceki <xref:System.Enum>, <xref:System.Delegate>ve <xref:System.MulticastDelegate> de temel sınıf kısıtlamaları olarak izin verilmedi. Aşağıdaki örnek, artık temel sınıf olarak belirtime türleri göstermektedir:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

`where` yan tümcesi, türün bir `class` veya `struct`olduğunu belirtebilir. `struct` kısıtlaması, `System.ValueType`temel sınıf kısıtlaması belirtme gereksinimini ortadan kaldırır. `System.ValueType` türü, temel sınıf kısıtlaması olarak kullanılamaz. Aşağıdaki örnek hem `class` hem de `struct` kısıtlamalarını göstermektedir:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

`where` yan tümcesi `notnull` kısıtlaması içerebilir. `notnull` kısıtlaması, tür parametresini null yapılamayan türler ile sınırlandırır. Bu tür bir [değer türü](../builtin-types/value-types.md) veya null yapılamayan bir başvuru türü olabilir. `notnull` kısıtlaması, bir [`nullable enable` bağlamında](../../nullable-references.md#nullable-contexts)derlenen C# kod için 8,0 ' den başlayarak kullanılabilir. Diğer kısıtlamaların aksine, bir tür bağımsız değişkeni `notnull` kısıtlamasını ihlal ederse, derleyici hata yerine bir uyarı oluşturur. Uyarılar yalnızca bir `nullable enable` bağlamında oluşturulur.

> [!IMPORTANT]
> `notnull` kısıtlamasını içeren genel bildirimler null olabilir bir zorunluluvou bağlamında kullanılabilir, ancak derleyici kısıtlamayı zorlamaz.

[!code-csharp[using the nonnull constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#NotNull)]

`where` yan tümcesi Ayrıca bir `unmanaged` kısıtlaması içerebilir. `unmanaged` kısıtlaması, tür parametresini [yönetilmeyen türler](../builtin-types/unmanaged-types.md)olarak bilinen türlerle sınırlandırır. `unmanaged` kısıtlaması, ' de C#alt düzey birlikte çalışma kodu yazmayı kolaylaştırır. Bu kısıtlama, tüm yönetilmeyen türler arasında yeniden kullanılabilir yordamlar sunar. `unmanaged` kısıtlaması `class` veya `struct` kısıtlaması ile birleştirilemez. `unmanaged` kısıtlaması, türün bir `struct`olması için zorlar:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

`where` yan tümcesi Ayrıca, `new()`bir Oluşturucu kısıtlaması içerebilir. Bu kısıtlama, `new` işlecini kullanarak bir tür parametresinin örneğini oluşturmayı mümkün kılar. [New () kısıtlaması](new-constraint.md) , derleyicinin sağlanan herhangi bir tür bağımsız değişkeninin erişilebilir parametresiz bir oluşturucuya sahip olması gerektiğini bilmesini sağlar. Örnek:

[!code-csharp[using the new constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

`new()` kısıtlaması `where` yan tümcesinde son görünür. `new()` kısıtlaması `struct` veya `unmanaged` kısıtlamalarıyla birleştirilemez. Bu kısıtlamaların karşılankarşılayan tüm türlerin erişilebilir bir parametresiz oluşturucusu olması ve `new()` kısıtlamasının gereksiz hale getirilmesi gerekir.

Birden çok tür parametresiyle, her tür parametresi için bir `where` yan tümcesi kullanın, örneğin:

[!code-csharp[using multiple where constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Ayrıca, aşağıdaki örnekte gösterildiği gibi genel yöntemlerin tür parametrelerine kısıtlamalar ekleyebilirsiniz:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Temsilcilerle ilgili tür parametresi kısıtlamalarını betimleyen sözdiziminin, metodların türüyle aynı olduğunu unutmayın:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Genel Temsilciler hakkında daha fazla bilgi için bkz. [Genel Temsilciler](../../programming-guide/generics/generic-delegates.md).

Kısıtlamaların sözdizimi ve kullanımı hakkında ayrıntılı bilgi için bkz. [tür parametrelerindeki kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>C# dili belirtimi

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Genel Türlere Giriş](../../programming-guide/generics/index.md)
- [new Kısıtlaması](./new-constraint.md)
- [Tür Parametrelerindeki Kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md)
