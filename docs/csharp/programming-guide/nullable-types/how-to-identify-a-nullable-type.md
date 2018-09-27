---
title: 'Nasıl yapılır: boş değer atanabilir bir tür (C# programlama Kılavuzu) belirleme'
description: Boş değer atanabilir bir tür bir türdür örneği boş değer atanabilir bir tür olup olmadığını belirlemek hakkında bilgi edinin
ms.date: 09/24/2018
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: f9957568d3c68f60cc9286718be9f5a496f876e6
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47400549"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a><span data-ttu-id="15a47-103">Nasıl yapılır: boş değer atanabilir bir tür (C# programlama Kılavuzu) belirleme</span><span class="sxs-lookup"><span data-stu-id="15a47-103">How to: Identify a nullable type (C# Programming Guide)</span></span>

<span data-ttu-id="15a47-104">Aşağıdaki örnek nasıl belirleneceğini göstermektedir olup olmadığını bir <xref:System.Type?displayProperty=nameWithType> örneğini gösteren bir kapalı genel boş değer atanabilir tür diğer bir deyişle, <xref:System.Nullable%601?displayProperty=nameWithType> belirtilen türü parametre türüyle `T`:</span><span class="sxs-lookup"><span data-stu-id="15a47-104">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a closed generic nullable type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

<span data-ttu-id="15a47-105">Örnekte gösterildiği gibi kullandığınız [typeof](../../language-reference/keywords/typeof.md) oluşturmak için işleç bir <xref:System.Type?displayProperty=nameWithType> nesne.</span><span class="sxs-lookup"><span data-stu-id="15a47-105">As the example shows, you use the [typeof](../../language-reference/keywords/typeof.md) operator to create a <xref:System.Type?displayProperty=nameWithType> object.</span></span>  
  
<span data-ttu-id="15a47-106">Belirlemek istiyorsanız bir örnek olup boş değer atanabilir bir tür, kullanmayın <xref:System.Object.GetType%2A?displayProperty=nameWithType> almak için yöntemi bir <xref:System.Type> önceki kod ile test edilecek örneği.</span><span class="sxs-lookup"><span data-stu-id="15a47-106">If you want to determine whether an instance is of a nullable type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="15a47-107">Çağırdığınızda <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemi null yapılabilir bir tür örneği üzerinde örneğidir [Kutulu](using-nullable-types.md#boxing-and-unboxing) için <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="15a47-107">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable type, the instance is [boxed](using-nullable-types.md#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="15a47-108">Bir null olmayan boş değer atanabilir bir tür örneğinin kutulama temel türünde bir değer olarak kutulama için eşdeğer olarak <xref:System.Object.GetType%2A> döndürür bir <xref:System.Type> boş değer atanabilir bir tür temel alınan türünü temsil eden nesne:</span><span class="sxs-lookup"><span data-stu-id="15a47-108">As boxing of a non-null instance of a nullable type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> object that represents the underlying type of a nullable type:</span></span>

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

<span data-ttu-id="15a47-109">Kullanmayın [olduğu](../../language-reference/keywords/is.md) örneği boş değer atanabilir bir tür olup olmadığını belirlemek için işleci.</span><span class="sxs-lookup"><span data-stu-id="15a47-109">Don't use the [is](../../language-reference/keywords/is.md) operator to determine whether an instance is of a nullable type.</span></span> <span data-ttu-id="15a47-110">Aşağıdaki örnekte gösterildiği gibi boş değer atanabilir bir tür ve kullanarak, temelindeki türe örnekleri türlerini ayırt edemez `is` işleci:</span><span class="sxs-lookup"><span data-stu-id="15a47-110">As the following example shows, you cannot distinguish types of instances of a nullable type and its underlying type with using the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

<span data-ttu-id="15a47-111">Aşağıdaki örnekte gösterilen kod örneği boş değer atanabilir bir tür olup olmadığını belirlemek için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="15a47-111">You can use the code presented in the following example to determine whether an instance is of a nullable type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a><span data-ttu-id="15a47-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15a47-112">See also</span></span>

- [<span data-ttu-id="15a47-113">Boş değer atanabilir türler</span><span class="sxs-lookup"><span data-stu-id="15a47-113">Nullable types</span></span>](index.md)  
- [<span data-ttu-id="15a47-114">Boş değer atanabilir türleri kullanma</span><span class="sxs-lookup"><span data-stu-id="15a47-114">Using nullable types</span></span>](using-nullable-types.md)  
- <xref:System.Nullable.GetUnderlyingType%2A>  
