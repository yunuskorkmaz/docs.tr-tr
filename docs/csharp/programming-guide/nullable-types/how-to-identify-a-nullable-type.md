---
title: 'Nasıl yapılır: Null yapılabilir bir tür- C# Programlama Kılavuzu belirler'
ms.custom: seodec18
description: Bir türün null yapılabilir bir tür mi yoksa bir örnek null yapılabilir türde mi olduğunu belirlemeyi öğrenin
ms.date: 09/24/2018
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: 43a35874b8c9f52c4b98a93e1217994980e1b223
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567372"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a>Nasıl yapılır: Null yapılabilir bir tür (C# Programlama Kılavuzu) tanımla

Aşağıdaki örnek, bir örneğin bir <xref:System.Type?displayProperty=nameWithType> kapalı genel null yapılabilir türü, diğer bir deyişle <xref:System.Nullable%601?displayProperty=nameWithType> belirtilen tür parametresine `T`sahip türü temsil edip etmediğini nasıl belirleyeceğini gösterir:

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

Örnekte gösterildiği gibi, bir <xref:System.Type?displayProperty=nameWithType> nesnesi oluşturmak için [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) işlecini kullanırsınız.  
  
Bir örneğin null yapılabilir türde olup olmadığını anlamak istiyorsanız, önceki kodla test edilecek bir <xref:System.Object.GetType%2A?displayProperty=nameWithType> <xref:System.Type> örnek almak için yöntemini kullanmayın. Yöntemini null yapılabilir bir türdeki bir örnekte çağırdığınızda [](using-nullable-types.md#boxing-and-unboxing) <xref:System.Object>, örnek olarak öğesine ayarlanır. <xref:System.Object.GetType%2A?displayProperty=nameWithType> Null olabilen bir türün null olmayan bir örneğinin kutulenmesi, temel alınan türün bir değer kutulamasında eşdeğer olduğundan, <xref:System.Object.GetType%2A> null yapılabilir bir türün temel alınan türünü temsil eden bir <xref:System.Type> nesne döndürür:

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

Bir örneğin null yapılabilir türde olup olmadığını anlamak için [,](../../language-reference/keywords/is.md) işleç kullanmayın. Aşağıdaki örnekte gösterildiği gibi, null yapılabilir bir türün örnek türlerini ve `is` işlecini kullanarak temel alınan türünü ayırt edemezsiniz:

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

Bir örneğin null yapılabilir bir türde olup olmadığını anlamak için aşağıdaki örnekte sunulan kodu kullanabilirsiniz:

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [Null yapılabilir türler](index.md)
- [Null yapılabilir türler kullanma](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
