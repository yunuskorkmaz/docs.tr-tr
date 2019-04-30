---
title: Burada (genel tür kısıtlaması) - C# başvurusu
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 094358dea9054bf198ded77736dc45af1a436787
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660235"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (genel tür kısıtlaması) (C# Başvurusu)

`where` Yan tümcesinde genel bir tanımı bir genel tür, yöntem, temsilci veya yerel işlev parametrelerinde türü bağımsız değişkenleri olarak kullanılan türler kısıtlamaları belirtir. Kısıtlamaları, temel sınıfları, arabirimleri belirtin veya bir başvuru, değer veya yönetilmeyen tür için bir genel türü gerektirir. Bunlar, tür bağımsız değişkeni sahip olması gereken özellikleri bildirin.

Örneğin, genel bir sınıf bildirebilirsiniz `MyGenericClass`gibi tür parametresi `T` uygulayan <xref:System.IComparable%601> arabirimi:

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Nerede hakkında daha fazla bilgi için bkz yan tümcesi bir sorgu ifadesinde [burada yan tümcesi](where-clause.md).

`where` Yan tümcesi, bir temel sınıf kısıtlaması de içerebilir. Temel sınıf kısıtlaması bir tür, genel tür için bir tür bağımsız değişkeni olarak kullanılacak bir temel sınıf olarak belirtilen sınıf olduğunu belirtir (veya temel sınıf olan), genel tür için bir tür bağımsız değişkeni olarak kullanılacak. Temel sınıf kısıtlaması kullandıysanız, bu tür parametresi üzerinde diğer kısıtlamalardan önce yer almalıdır. Bazı türleri temel sınıf kısıtlama olarak izin verilmez: <xref:System.Object>, <xref:System.Array>, ve <xref:System.ValueType>. C# 7.3 önce <xref:System.Enum>, <xref:System.Delegate>, ve <xref:System.MulticastDelegate> ayrıca temel sınıf kısıtlama olarak izin verilmiyor. Aşağıdaki örnek, artık temel sınıf olarak belirttiğiniz türlerini gösterir:

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

`where` Yan tümcesi, türü olduğunu belirtebilirsiniz bir `class` veya `struct`. `struct` Sınırlama bir temel sınıfı kısıtlamasını belirtmek için gereken kaldırır `System.ValueType`. `System.ValueType` Türü temel sınıf kısıtlama olarak kullanılamaz. Aşağıdaki örnek her ikisini de gösteren `class` ve `struct` kısıtlamaları:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

`where` Yan tümcesi de içerebilir bir `unmanaged` kısıtlaması. `unmanaged` Sınırlar olarak bilinen türler için tür parametresi kısıtlaması **yönetilmeyen türleri**. Bir **yönetilmeyen tür** , bir başvuru türü değil ve başvuru türü alanları iç içe geçme herhangi bir düzeyde içermeyen bir türdür. `unmanaged` Kısıtlaması alt düzey birlikte çalışma kodu C# ' ta yazmak kolaylaştırır. Bu kısıtlama, yönetilmeyen tüm türleri arasında yeniden kullanılabilir yordamları sağlar. `unmanaged` Kısıtlaması ile birleştirilemez `class` veya `struct` kısıtlaması. `unmanaged` Kısıtlamayı zorlar türü olmalıdır bir `struct`:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

`where` Yan tümcesi bir oluşturucu kısıtlaması de içerebilir `new()`. Kısıtlaması, bir tür parametresini kullanarak bir örneğini oluşturmak mümkün kılar, `new` işleci. [New() kısıtlaması](new-constraint.md) sağlanan herhangi bir tür bağımsız değişkeni bir erişilebilir olması gerektiğini bilmeniz derleyici sağlar parametresiz--ya da varsayılan--oluşturucu. Örneğin:

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

`new()` Kısıtlaması, son görüntülenen `where` yan tümcesi. `new()` Kısıtlaması ile birleştirilemez `struct` veya `unmanaged` kısıtlamaları. Kısıtlamalar, erişilebilir bir parametresiz oluşturucusu olmalıdır çağıran, yapmadan tüm türleri `new()` yedekli kısıtlaması.

Birden çok tür parametreleriyle kullanın `where` yan tümcesi, örneğin her tür parametresi için:

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Aşağıdaki örnekte gösterildiği gibi bazı sınırlamalar genel yöntemlerin parametreleri ekleyebilirsiniz:

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Temsilciler üzerinde tür parametresi kısıtlamaları tanımlamak için sözdizimi, yöntemlerin aynı olduğuna dikkat edin:

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Genel temsilciler hakkında daha fazla bilgi için bkz: [genel temsilciler](../../../csharp/programming-guide/generics/generic-delegates.md).

Söz dizimi ve kullanım kısıtlamaları hakkında daha fazla bilgi için bkz: [tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>C# dili belirtimi

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Genel Türlere Giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)
- [new Kısıtlaması](../../../csharp/language-reference/keywords/new-constraint.md)
- [Tür Parametrelerindeki Kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)