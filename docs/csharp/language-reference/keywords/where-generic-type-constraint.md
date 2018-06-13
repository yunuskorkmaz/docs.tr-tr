---
title: where (genel tür kısıtlaması) (C# Başvurusu)
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 94db10c81af55030dfcf6e210a86658c84868e42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288326"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (genel tür kısıtlaması) (C# Başvurusu)

`where` Yan tümcesi genel tanımında tür parametrelerinde genel tür, yöntem, temsilci veya yerel bir işlev bağımsız değişkenleri olarak kullanılan türleri kısıtlamaları belirtir. Kısıtlamaları arabirimleri, temel sınıflar belirtin veya bir başvuru, değeri veya yönetilmeyen tür genel bir tür gerektirir. Bunlar, tür bağımsız değişkeni sahip olması gerekir yetenekleri bildirin.

Örneğin, genel bir sınıf bildirebilir `MyGenericClass`gibi tür parametresi `T` uygulayan <xref:System.IComparable%601> arabirimi:

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Daha fazla bilgi için bir sorgu ifadesinde yan tümcesine bakın [burada yan tümcesi](where-clause.md).

`where` Yan tümcesi de bir taban sınıf kısıtlaması içerir. Taban sınıf kısıtlaması genel türü için tür bağımsız değişkeni olarak kullanılacak bir türü belirtilen sınıfın temel sınıf olarak olduğunu bildiren (veya temel sınıfı olan), genel tür için tür bağımsız değişkeni olarak kullanılacak. Taban sınıf kısıtlaması kullanılırsa, bu tür parametre diğer kısıtlamalar önce görünmelidir. Bazı türleri bir temel sınıf kısıtlaması izin verilmez: <xref:System.Object>, <xref:System.Array>, ve <xref:System.ValueType>. C# 7.3 önce <xref:System.Enum>, <xref:System.Delegate>, ve <xref:System.MulticastDelegate> da temel sınıf kısıtlamaları olarak izin verilmiyor. Aşağıdaki örnek, artık bir temel sınıf olarak belirttiğiniz türlerini gösterir:

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

`where` Yan tümcesi türü olduğunu belirtebilirsiniz bir `class` veya `struct`. `struct` Kısıtlamayı kaldırır bir temel sınıf kısıtlaması belirtme ihtiyacını `System.ValueType`. `System.ValueType` Türü bir temel sınıf kısıtlama olarak kullanılamaz. Aşağıdaki örnek, her ikisi de gösterir `class` ve `struct` kısıtlamalar:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

`where` Yan tümcesi de içerebilir bir `unmanaged` kısıtlaması. `unmanaged` Kısıtlaması sınırlar olarak bilinen türleri için tür parametre **yönetilmeyen türleri**. Bir **yönetilmeyen türü** bir başvuru türü değil ve tüm iç içe geçme düzeyini başvuru türü alanlarını içermiyor. bir tür. `unmanaged` Kısıtlaması alt düzey birlikte çalışma kod C# ' ta yazmayı kolaylaştırır. Bu sınırlama tüm yönetilmeyen türlerine yeniden kullanılabilir yordamlar sağlar. `unmanaged` Kısıtlaması ile ilişkilendirilemez `class` veya `struct` kısıtlaması. `unmanaged` Kısıtlamayı zorlar türü olmalıdır bir `struct`:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

`where` Yan tümcesi Oluşturucusu kısıtlaması de içerebilir `new()`. Kısıtlaması, bir tür parametresini kullanarak bir örneğini oluşturmak mümkün kılar, `new` işleci. [New() kısıtlaması](new-constraint.md) sağlanan herhangi bir tür bağımsız değişkeni bir erişilebilir olması gerektiğini biliyor derleyici sağlar parametresiz--veya varsayılan--oluşturucusu. Örneğin:

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

`new()` Kısıtlaması görünür içinde son `where` yan tümcesi. `new()` Kısıtlaması ile ilişkilendirilemez `struct` veya `unmanaged` kısıtlamaları. Bu kısıtlamalar erişilebilir bir parametresiz oluşturucuya sahip olmalıdır çağıran, yapmadan tüm türleri `new()` kısıtlaması gereksiz.

Birden çok tür parametreleri ile kullanmayı `where` yan tümcesi örneğin her tür parametresi için:

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Tür parametreleri genel yöntemlerin kısıtlamaları aşağıdaki örnekte gösterildiği gibi ekleyebilirsiniz:

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Temsilciler üzerinde türü parametresi kısıtlamaları tanımlamak üzere sözdizimini aynı yöntemleri olduğuna dikkat edin:

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Genel temsilciler hakkında daha fazla bilgi için bkz: [genel temsilciler](../../../csharp/programming-guide/generics/generic-delegates.md).

Söz dizimi ve kullanım kısıtlamaları hakkında daha fazla bilgi için bkz: [tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>C# dili belirtimi

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel Türlere Giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [new Kısıtlaması](../../../csharp/language-reference/keywords/new-constraint.md)  
 [Tür Parametrelerindeki Kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
