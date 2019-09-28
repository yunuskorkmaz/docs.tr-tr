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
# <a name="how-to-identify-a-nullable-value-type-c-programming-guide"></a><span data-ttu-id="94087-103">Nasıl yapılır: null yapılabilir değer türü belirleme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="94087-103">How to: identify a nullable value type (C# Programming Guide)</span></span>

<span data-ttu-id="94087-104">Aşağıdaki örnek, <xref:System.Type?displayProperty=nameWithType> örneğinin kapalı bir genel null yapılabilir değer türünü temsil edip etmediğini gösterir, diğer bir deyişle, belirtilen tür parametresine sahip <xref:System.Nullable%601?displayProperty=nameWithType> türü `T`:</span><span class="sxs-lookup"><span data-stu-id="94087-104">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a closed generic nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

<span data-ttu-id="94087-105">Örnekte gösterildiği gibi, <xref:System.Type?displayProperty=nameWithType> nesnesi oluşturmak için [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) işlecini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="94087-105">As the example shows, you use the [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="94087-106">Bir örneğin, null yapılabilir bir değer türünde olup olmadığını anlamak istiyorsanız, yukarıdaki kodla test edilecek bir <xref:System.Type> örneğini almak için <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="94087-106">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="94087-107">Nullable değer türünün bir örneğinde <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemini çağırdığınızda, örnek <xref:System.Object> ' ye [kutulanır](using-nullable-types.md#boxing-and-unboxing) .</span><span class="sxs-lookup"><span data-stu-id="94087-107">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](using-nullable-types.md#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="94087-108">Null olabilen bir değer türünün null olmayan bir örneğinin kutulenmesi, temel alınan türün bir değer kutulamasında eşdeğerdir, <xref:System.Object.GetType%2A>, null olabilen bir değer türünün temel alınan türünü temsil eden bir <xref:System.Type> nesnesi döndürür:</span><span class="sxs-lookup"><span data-stu-id="94087-108">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> object that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

<span data-ttu-id="94087-109">Bir örneğin Nullable değer türünde olup olmadığını anlamak için [,](../../language-reference/keywords/is.md) işleç kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="94087-109">Don't use the [is](../../language-reference/keywords/is.md) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="94087-110">Aşağıdaki örnekte gösterildiği gibi, null olabilen bir değer türünün örnek türlerini ve `is` işlecini kullanarak temel alınan türünü ayırt edemezsiniz:</span><span class="sxs-lookup"><span data-stu-id="94087-110">As the following example shows, you cannot distinguish types of instances of a nullable value type and its underlying type with using the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

<span data-ttu-id="94087-111">Bir örneğin null yapılabilir bir değer türünde olup olmadığını anlamak için aşağıdaki örnekte sunulan kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="94087-111">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]

## <a name="see-also"></a><span data-ttu-id="94087-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94087-112">See also</span></span>

- [<span data-ttu-id="94087-113">Null yapılabilir değer türleri</span><span class="sxs-lookup"><span data-stu-id="94087-113">Nullable value types</span></span>](index.md)
- [<span data-ttu-id="94087-114">Nullable değer türlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="94087-114">Using nullable value types</span></span>](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
