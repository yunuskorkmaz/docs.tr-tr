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
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a><span data-ttu-id="a24fa-103">Nasıl yapılır: Null yapılabilir bir tür (C# Programlama Kılavuzu) tanımla</span><span class="sxs-lookup"><span data-stu-id="a24fa-103">How to: Identify a nullable type (C# Programming Guide)</span></span>

<span data-ttu-id="a24fa-104">Aşağıdaki örnek, bir örneğin bir <xref:System.Type?displayProperty=nameWithType> kapalı genel null yapılabilir türü, diğer bir deyişle <xref:System.Nullable%601?displayProperty=nameWithType> belirtilen tür parametresine `T`sahip türü temsil edip etmediğini nasıl belirleyeceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="a24fa-104">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a closed generic nullable type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

<span data-ttu-id="a24fa-105">Örnekte gösterildiği gibi, bir <xref:System.Type?displayProperty=nameWithType> nesnesi oluşturmak için [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) işlecini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="a24fa-105">As the example shows, you use the [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> object.</span></span>  
  
<span data-ttu-id="a24fa-106">Bir örneğin null yapılabilir türde olup olmadığını anlamak istiyorsanız, önceki kodla test edilecek bir <xref:System.Object.GetType%2A?displayProperty=nameWithType> <xref:System.Type> örnek almak için yöntemini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="a24fa-106">If you want to determine whether an instance is of a nullable type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="a24fa-107">Yöntemini null yapılabilir bir türdeki bir örnekte çağırdığınızda [](using-nullable-types.md#boxing-and-unboxing) <xref:System.Object>, örnek olarak öğesine ayarlanır. <xref:System.Object.GetType%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a24fa-107">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable type, the instance is [boxed](using-nullable-types.md#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="a24fa-108">Null olabilen bir türün null olmayan bir örneğinin kutulenmesi, temel alınan türün bir değer kutulamasında eşdeğer olduğundan, <xref:System.Object.GetType%2A> null yapılabilir bir türün temel alınan türünü temsil eden bir <xref:System.Type> nesne döndürür:</span><span class="sxs-lookup"><span data-stu-id="a24fa-108">As boxing of a non-null instance of a nullable type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> object that represents the underlying type of a nullable type:</span></span>

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

<span data-ttu-id="a24fa-109">Bir örneğin null yapılabilir türde olup olmadığını anlamak için [,](../../language-reference/keywords/is.md) işleç kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="a24fa-109">Don't use the [is](../../language-reference/keywords/is.md) operator to determine whether an instance is of a nullable type.</span></span> <span data-ttu-id="a24fa-110">Aşağıdaki örnekte gösterildiği gibi, null yapılabilir bir türün örnek türlerini ve `is` işlecini kullanarak temel alınan türünü ayırt edemezsiniz:</span><span class="sxs-lookup"><span data-stu-id="a24fa-110">As the following example shows, you cannot distinguish types of instances of a nullable type and its underlying type with using the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

<span data-ttu-id="a24fa-111">Bir örneğin null yapılabilir bir türde olup olmadığını anlamak için aşağıdaki örnekte sunulan kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a24fa-111">You can use the code presented in the following example to determine whether an instance is of a nullable type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a><span data-ttu-id="a24fa-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a24fa-112">See also</span></span>

- [<span data-ttu-id="a24fa-113">Null yapılabilir türler</span><span class="sxs-lookup"><span data-stu-id="a24fa-113">Nullable types</span></span>](index.md)
- [<span data-ttu-id="a24fa-114">Null yapılabilir türler kullanma</span><span class="sxs-lookup"><span data-stu-id="a24fa-114">Using nullable types</span></span>](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
