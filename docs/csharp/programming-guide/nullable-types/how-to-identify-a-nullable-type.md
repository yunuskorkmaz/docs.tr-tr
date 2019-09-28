---
title: 'Nasıl yapılır: null yapılabilir değer türü belirleme- C# Programlama Kılavuzu'
ms.custom: seodec18
description: Bir türün null yapılabilir bir değer türü mi yoksa bir örnek null yapılabilir bir değer türü mi olduğunu belirlemeyi öğrenin
ms.date: 09/26/2019
helpviewer_keywords:
- nullable value types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: 15b1ffedf57648955ee5a004514841a5d140292b
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392614"
---
# <a name="how-to-identify-a-nullable-value-type-c-programming-guide"></a>Nasıl yapılır: null yapılabilir değer türü belirleme (C# Programlama Kılavuzu)

Aşağıdaki örnek, <xref:System.Type?displayProperty=nameWithType> örneğinin kapalı bir genel null yapılabilir değer türünü temsil edip etmediğini gösterir, diğer bir deyişle, belirtilen tür parametresine sahip <xref:System.Nullable%601?displayProperty=nameWithType> türü `T`:

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

Örnekte gösterildiği gibi, <xref:System.Type?displayProperty=nameWithType> nesnesi oluşturmak için [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) işlecini kullanırsınız.

Bir örneğin, null yapılabilir bir değer türünde olup olmadığını anlamak istiyorsanız, yukarıdaki kodla test edilecek bir <xref:System.Type> örneğini almak için <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemini kullanmayın. Nullable değer türünün bir örneğinde <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemini çağırdığınızda, örnek <xref:System.Object> ' ye [kutulanır](using-nullable-types.md#boxing-and-unboxing) . Null olabilen bir değer türünün null olmayan bir örneğinin kutulenmesi, temel alınan türün bir değer kutulamasında eşdeğerdir, <xref:System.Object.GetType%2A>, null olabilen bir değer türünün temel alınan türünü temsil eden bir <xref:System.Type> nesnesi döndürür:

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

Bir örneğin Nullable değer türünde olup olmadığını anlamak için [,](../../language-reference/keywords/is.md) işleç kullanmayın. Aşağıdaki örnekte gösterildiği gibi, null olabilen bir değer türünün örnek türlerini ve `is` işlecini kullanarak temel alınan türünü ayırt edemezsiniz:

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

Bir örneğin null yapılabilir bir değer türünde olup olmadığını anlamak için aşağıdaki örnekte sunulan kodu kullanabilirsiniz:

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]

## <a name="see-also"></a>Ayrıca bkz.

- [Null yapılabilir değer türleri](index.md)
- [Nullable değer türlerini kullanma](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
