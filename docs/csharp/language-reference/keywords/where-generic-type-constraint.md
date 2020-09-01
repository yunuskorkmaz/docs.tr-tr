---
description: WHERE (genel tür kısıtlaması)-C# başvurusu
title: WHERE (genel tür kısıtlaması)-C# başvurusu
ms.date: 04/15/2020
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 78f784135c6bf01ea9724fcf92be234e6b86ff07
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141913"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (genel tür kısıtlaması) (C# Başvurusu)

`where`Genel tanımda yer alan yan tümce, genel bir tür, metot, temsilci veya yerel işlevde tür parametreleri için bağımsız değişken olarak kullanılan türlerde kısıtlamalar belirtir. Kısıtlamalar, arabirimler, temel sınıflar veya bir genel türün bir başvuru, değer veya yönetilmeyen tür olmasını gerektirebilir. Tür bağımsız değişkeninin sahip olması gereken özellikleri bildirir.

Örneğin, `MyGenericClass` tür parametresi arabirimini uygulayan genel bir sınıf bildirebilirsiniz `T` <xref:System.IComparable%601> :

[!code-csharp[using an interface constraint](snippets/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Bir sorgu ifadesindeki WHERE yan tümcesi hakkında daha fazla bilgi için bkz. [WHERE yan tümcesi](where-clause.md).

`where`Yan tümce bir temel sınıf kısıtlaması de içerebilir. Temel sınıf kısıtlaması, bu genel türün tür bağımsız değişkeni olarak kullanılacak bir türün, temel sınıf olarak belirtilen sınıfa sahip olduğunu veya temel sınıf olduğunu belirtir. Temel sınıf kısıtlaması kullanılırsa, bu tür parametresindeki diğer kısıtlamaların önüne gelmelidir. Bir temel sınıf kısıtlaması olarak bazı türlere izin verilmez: <xref:System.Object> , <xref:System.Array> ve <xref:System.ValueType> . C# 7,3,, ve ' den önce <xref:System.Enum> <xref:System.Delegate> <xref:System.MulticastDelegate> temel sınıf kısıtlamaları olarak da izin verilmedi. Aşağıdaki örnek, artık temel sınıf olarak belirtime türleri göstermektedir:

[!code-csharp[using an interface constraint](snippets/GenericWhereConstraints.cs#2)]

C# 8,0 ve sonraki sürümlerde null yapılabilir bir bağlamda, temel sınıf türünün null değer alabilme değeri zorlanır. Temel sınıf null atanamaz ise (örneğin `Base` ), tür bağımsız değişkeni null atanamaz olmalıdır. Temel sınıf null yapılabilir ise (örneğin `Base?` ), tür bağımsız değişkeni null yapılabilir veya null atanamaz bir başvuru türü olabilir. Temel sınıf null olamayan bir başvuru türünde ise derleyici bir uyarı verir.

`where`Yan tümce türün bir `class` veya bir olduğunu belirtebilir `struct` . `struct`Kısıtlama, öğesinin temel sınıf kısıtlamasını belirtme gereksinimini ortadan kaldırır `System.ValueType` . `System.ValueType`Tür, temel sınıf kısıtlaması olarak kullanılamaz. Aşağıdaki örnek, `class` ve `struct` kısıtlamalarını göstermektedir:

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#3)]

C# 8,0 ve sonraki sürümlerde null yapılabilir bir bağlamda kısıtlama, `class` bir türün null yapılamayan bir başvuru türü olmasını gerektirir. Null yapılabilir başvuru türlerine izin vermek için, `class?` hem null yapılabilir hem de null olamayan başvuru türlerine izin veren kısıtlamayı kullanın.

`where`Yan tümce `notnull` kısıtlaması içerebilir. `notnull`Kısıtlama, tür parametresini null yapılamayan türler ile sınırlandırır. Bu tür bir [değer türü](../builtin-types/value-types.md) veya null yapılamayan bir başvuru türü olabilir. `notnull`Kısıtlama, bir [ `nullable enable` bağlamda](../../nullable-references.md#nullable-contexts)derlenen kod için C# 8,0 ' den başlayarak kullanılabilir. Diğer kısıtlamaların aksine, bir tür bağımsız değişkeni kısıtlamayı ihlal ederse `notnull` , derleyici hata yerine bir uyarı oluşturur. Uyarılar yalnızca bir `nullable enable` bağlamda oluşturulur.

> [!IMPORTANT]
> Kısıtlamayı içeren genel bildirimler, `notnull` null yapılabilir bir zorunluluvou bağlamında kullanılabilir, ancak derleyici kısıtlamayı zorlamaz.

[!code-csharp[using the nonnull constraint](snippets/GenericWhereConstraints.cs#NotNull)]

`where`Yan tümce de bir kısıtlama içerebilir `unmanaged` . `unmanaged`Kısıtlama, tür parametresini [yönetilmeyen türler](../builtin-types/unmanaged-types.md)olarak bilinen türlerle sınırlandırır. `unmanaged`Kısıtlama, C# dilinde alt düzey birlikte çalışma kodu yazmayı kolaylaştırır. Bu kısıtlama, tüm yönetilmeyen türler arasında yeniden kullanılabilir yordamlar sunar. `unmanaged`Kısıtlama, `class` veya kısıtlaması ile birleştirilemez `struct` . `unmanaged`Kısıtlama, türün bir olması için şunu uygular `struct` :

[!code-csharp[using the unmanaged constraint](snippets/GenericWhereConstraints.cs#4)]

`where`Yan tümce bir Oluşturucu kısıtlaması de içerebilir `new()` . Bu kısıtlama işleci kullanarak bir tür parametresinin örneğini oluşturmayı mümkün kılar `new` . [New () kısıtlaması](new-constraint.md) , derleyicinin sağlanan herhangi bir tür bağımsız değişkeninin erişilebilir parametresiz bir oluşturucuya sahip olması gerektiğini bilmesini sağlar. Örneğin:

[!code-csharp[using the new constraint](snippets/GenericWhereConstraints.cs#5)]

`new()`Kısıtlama yan tümcesinde en son görünür `where` . `new()`Kısıtlama `struct` veya `unmanaged` kısıtlamalarıyla birleştirilemez. Bu kısıtlamaların karşılankarşılayan tüm türlerin erişilebilir bir parametresiz oluşturucusu olması gerekir ve `new()` kısıtlama gereksiz hale getirir.

Birden çok tür `where` parametresiyle, her tür parametresi için bir yan tümce kullanın, örneğin:

[!code-csharp[using multiple where constraints](snippets/GenericWhereConstraints.cs#6)]

Ayrıca, aşağıdaki örnekte gösterildiği gibi genel yöntemlerin tür parametrelerine kısıtlamalar ekleyebilirsiniz:

[!code-csharp[where constraints with generic methods](snippets/GenericWhereConstraints.cs#7)]

Temsilcilerle ilgili tür parametresi kısıtlamalarını betimleyen sözdiziminin, metodların türüyle aynı olduğunu unutmayın:

[!code-csharp[where constraints with generic methods](snippets/GenericWhereConstraints.cs#8)]

Genel Temsilciler hakkında daha fazla bilgi için bkz. [Genel Temsilciler](../../programming-guide/generics/generic-delegates.md).

Kısıtlamaların sözdizimi ve kullanımı hakkında ayrıntılı bilgi için bkz. [tür parametrelerindeki kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>C# dili belirtimi

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Genel Türlere Giriş](../../programming-guide/generics/index.md)
- [Yeni kısıtlama](./new-constraint.md)
- [Tür Parametrelerindeki Kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md)
