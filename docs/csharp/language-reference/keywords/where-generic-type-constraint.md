---
title: WHERE (genel tür kısıtlaması)- C# başvuru
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: bccc22f5362b22540dadf08e6b21a07cbc578327
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433860"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (genel tür kısıtlaması) (C# Başvurusu)

Genel tanımda yer alan yantümce,genelbirtür,metot,temsilciveyayerelişlevdetürparametreleriiçinbağımsızdeğişkenolarakkullanılantürlerdekısıtlamalarbelirtir.`where` Kısıtlamalar, arabirimler, temel sınıflar veya bir genel türün bir başvuru, değer veya yönetilmeyen tür olmasını gerektirebilir. Bunlar, tür bağımsız değişkeninin sahip olması gereken özellikleri bildirir.

Örneğin, tür parametresi `MyGenericClass` `T` <xref:System.IComparable%601> arabirimini uygulayan genel bir sınıf bildirebilirsiniz:

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Bir sorgu ifadesindeki WHERE yan tümcesi hakkında daha fazla bilgi için bkz. [WHERE yan tümcesi](where-clause.md).

`where` Yan tümce bir temel sınıf kısıtlaması de içerebilir. Temel sınıf kısıtlaması, bu genel türün tür bağımsız değişkeni olarak kullanılacak bir türün, bu genel tür için bir tür bağımsız değişkeni olarak kullanılacak bir temel sınıf (veya temel sınıf) olarak belirtilen sınıfa sahip olduğunu belirtir. Temel sınıf kısıtlaması kullanılırsa, bu tür parametresindeki diğer kısıtlamaların önüne gelmelidir. Bir temel sınıf kısıtlaması olarak bazı türlere izin verilmez: <xref:System.Object>, <xref:System.Array>ve <xref:System.ValueType>. C# 7,3, <xref:System.Enum>, <xref:System.Delegate>ve 'denöncetemelsınıfkısıtlamalarıolarakdaizinverilmedi.<xref:System.MulticastDelegate> Aşağıdaki örnek, artık temel sınıf olarak belirtime türleri göstermektedir:

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

Yan tümce türün bir `class` veya bir `struct`olduğunu belirtebilir. `where` Kısıtlama, öğesinin `System.ValueType`temel sınıf kısıtlamasını belirtme gereksinimini ortadan kaldırır. `struct` Tür `System.ValueType` , temel sınıf kısıtlaması olarak kullanılamaz. Aşağıdaki örnek, `class` ve `struct` kısıtlamalarını göstermektedir:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

Yan tümce de bir `unmanaged` kısıtlama içerebilir. `where` Kısıtlama, tür parametresini [yönetilmeyen türler](../builtin-types/unmanaged-types.md)olarak bilinen türlerle sınırlandırır. `unmanaged` Kısıtlama `unmanaged` , içinde C#alt düzey birlikte çalışma kodu yazmayı kolaylaştırır. Bu kısıtlama, tüm yönetilmeyen türler arasında yeniden kullanılabilir yordamlar sunar. Kısıtlama, `class` veya`struct` kısıtlaması ile birleştirilemez. `unmanaged` Kısıtlama, türün bir `struct`olması için şunu uygular: `unmanaged`

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

Yan tümce bir Oluşturucu `new()`kısıtlaması de içerebilir. `where` Bu kısıtlama `new` işleci kullanarak bir tür parametresinin örneğini oluşturmayı mümkün kılar. [New () kısıtlaması](new-constraint.md) , derleyicinin sağlanan herhangi bir tür bağımsız değişkeninin erişilebilir bir parametresiz-veya varsayılan--oluşturucusu olması gerektiğini bilmesini sağlar. Örneğin:

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

`new()` Kısıtlama `where` yan tümcesinde en son görünür. `new()` `struct` Kısıtlama veya`unmanaged` kısıtlamalarıyla birleştirilemez. Bu kısıtlamaların karşılankarşılayan tüm türlerin erişilebilir bir parametresiz oluşturucusu olması gerekir ve `new()` kısıtlama gereksiz hale getirir.

Birden çok tür parametresiyle, her tür `where` parametresi için bir yan tümce kullanın, örneğin:

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Ayrıca, aşağıdaki örnekte gösterildiği gibi genel yöntemlerin tür parametrelerine kısıtlamalar ekleyebilirsiniz:

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Temsilcilerle ilgili tür parametresi kısıtlamalarını betimleyen sözdiziminin, metodların türüyle aynı olduğunu unutmayın:

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Genel Temsilciler hakkında daha fazla bilgi için bkz. [Genel Temsilciler](../../../csharp/programming-guide/generics/generic-delegates.md).

Kısıtlamaların sözdizimi ve kullanımı hakkında ayrıntılı bilgi için bkz. [tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>C# dili belirtimi

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Genel Türlere Giriş](../../../csharp/programming-guide/generics/index.md)
- [new Kısıtlaması](../../../csharp/language-reference/keywords/new-constraint.md)
- [Tür Parametrelerindeki Kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
