---
title: New işleci-C# başvurusu
ms.date: 06/25/2019
f1_keywords:
- new_CSharpKeyword
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 7e2f1a52f1681e0cc454da8cba324dd1b5995f11
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855107"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="84554-102">New işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="84554-102">new operator (C# reference)</span></span>

<span data-ttu-id="84554-103">`new`İşleci, bir türün yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="84554-103">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="84554-104">`new`Anahtar sözcüğünü [üye bildirim değiştiricisi](../keywords/new-modifier.md) veya [genel tür kısıtlaması](../keywords/new-constraint.md)olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84554-104">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="84554-105">Oluşturucu çağırma</span><span class="sxs-lookup"><span data-stu-id="84554-105">Constructor invocation</span></span>

<span data-ttu-id="84554-106">Bir türün yeni bir örneğini oluşturmak için, genellikle işlecini kullanarak bu türdeki [oluşturuculardan](../../programming-guide/classes-and-structs/constructors.md) birini çağırın `new` :</span><span class="sxs-lookup"><span data-stu-id="84554-106">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](snippets/NewOperator.cs#Constructor)]

<span data-ttu-id="84554-107">[object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) `new` Aşağıdaki örnekte gösterildiği gibi, bir ifadede bir nesne oluşturmak ve başlatmak için işleciyle bir nesne veya koleksiyon başlatıcısı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="84554-107">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](snippets/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a><span data-ttu-id="84554-108">Dizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="84554-108">Array creation</span></span>

<span data-ttu-id="84554-109">`new`Aşağıdaki örnekte gösterildiği gibi, bir dizi örneği oluşturmak için işlecini de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="84554-109">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](snippets/NewOperator.cs#Array)]

<span data-ttu-id="84554-110">Dizi başlatma söz dizimini kullanarak bir dizi örneği oluşturun ve tek bir deyimdeki öğelerle doldurun.</span><span class="sxs-lookup"><span data-stu-id="84554-110">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="84554-111">Aşağıdaki örnek, bunu nasıl yapabilmenizin çeşitli yollarını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="84554-111">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](snippets/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="84554-112">Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="84554-112">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="84554-113">Anonim türlerin örneklenmesi</span><span class="sxs-lookup"><span data-stu-id="84554-113">Instantiation of anonymous types</span></span>

<span data-ttu-id="84554-114">[Anonim türün](../../programming-guide/classes-and-structs/anonymous-types.md)bir örneğini oluşturmak için `new` işleç ve nesne Başlatıcısı söz dizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="84554-114">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](snippets/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="84554-115">Tür örneklerinin yok edilmesi</span><span class="sxs-lookup"><span data-stu-id="84554-115">Destruction of type instances</span></span>

<span data-ttu-id="84554-116">Önceden oluşturulmuş tür örneklerini yok etmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="84554-116">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="84554-117">Başvuru ve değer türlerinin örnekleri otomatik olarak yok edilir.</span><span class="sxs-lookup"><span data-stu-id="84554-117">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="84554-118">Değer türlerinin örnekleri, bunları içeren bağlam yok edilir oluşturmaz yok edilir.</span><span class="sxs-lookup"><span data-stu-id="84554-118">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="84554-119">Başvuru türlerinin örnekleri, son başvuru kaldırıldıktan sonra bazı belirtilmeyen bir zamanda [çöp toplayıcı](../../../standard/garbage-collection/index.md) tarafından yok edilir.</span><span class="sxs-lookup"><span data-stu-id="84554-119">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at some unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="84554-120">Yönetilmeyen kaynakları içeren tür örneklerinde, örneğin bir dosya tanıtıcısı için, içerdikleri kaynakların mümkün olan en kısa sürede serbest bırakılacağını sağlamak üzere belirleyici Temizleme kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="84554-120">For type instances that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="84554-121">Daha fazla bilgi için bkz <xref:System.IDisposable?displayProperty=nameWithType> . API başvurusu ve [using ekstresi](../keywords/using-statement.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="84554-121">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="84554-122">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="84554-122">Operator overloadability</span></span>

<span data-ttu-id="84554-123">Kullanıcı tanımlı bir tür işleci aşırı yükleyemez `new` .</span><span class="sxs-lookup"><span data-stu-id="84554-123">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="84554-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="84554-124">C# language specification</span></span>

<span data-ttu-id="84554-125">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Yeni işleç](~/_csharplang/spec/expressions.md#the-new-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="84554-125">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="84554-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84554-126">See also</span></span>

- [<span data-ttu-id="84554-127">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="84554-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="84554-128">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="84554-128">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="84554-129">Nesne ve koleksiyon başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="84554-129">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
