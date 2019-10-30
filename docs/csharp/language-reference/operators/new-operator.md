---
title: Yeni operatör- C# başvuru
ms.custom: seodec18
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: c21132a6622ce697fe3c52a461a33f548e0c8f31
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036387"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="e3b45-102">New işleci (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="e3b45-102">new operator (C# reference)</span></span>

<span data-ttu-id="e3b45-103">`new` işleci, bir türün yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e3b45-103">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="e3b45-104">`new` anahtar sözcüğünü [üye bildirimi değiştiricisi](../keywords/new-modifier.md) veya [genel tür kısıtlaması](../keywords/new-constraint.md)olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3b45-104">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="e3b45-105">Oluşturucu çağırma</span><span class="sxs-lookup"><span data-stu-id="e3b45-105">Constructor invocation</span></span>

<span data-ttu-id="e3b45-106">Bir türün yeni bir örneğini oluşturmak için, genellikle `new` işlecini kullanarak bu türdeki [oluşturuculardan](../../programming-guide/classes-and-structs/constructors.md) birini çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e3b45-106">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](~/samples/csharp/language-reference/operators/NewOperator.cs#Constructor)]

<span data-ttu-id="e3b45-107">Aşağıdaki örnekte gösterildiği gibi, tek bir ifadede bir nesne oluşturmak ve başlatmak için `new` işleçle bir [nesne veya koleksiyon başlatıcısı](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e3b45-107">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](~/samples/csharp/language-reference/operators/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a><span data-ttu-id="e3b45-108">Dizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3b45-108">Array creation</span></span>

<span data-ttu-id="e3b45-109">Aşağıdaki örnekte gösterildiği gibi, bir dizi örneği oluşturmak için `new` işlecini de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e3b45-109">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](~/samples/csharp/language-reference/operators/NewOperator.cs#Array)]

<span data-ttu-id="e3b45-110">Dizi başlatma söz dizimini kullanarak bir dizi örneği oluşturun ve tek bir deyimdeki öğelerle doldurun.</span><span class="sxs-lookup"><span data-stu-id="e3b45-110">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="e3b45-111">Aşağıdaki örnek, bunu nasıl yapabilmenizin çeşitli yollarını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="e3b45-111">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](~/samples/csharp/language-reference/operators/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="e3b45-112">Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="e3b45-112">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="e3b45-113">Anonim türlerin örneklenmesi</span><span class="sxs-lookup"><span data-stu-id="e3b45-113">Instantiation of anonymous types</span></span>

<span data-ttu-id="e3b45-114">[Anonim türün](../../programming-guide/classes-and-structs/anonymous-types.md)bir örneğini oluşturmak için `new` işlecini ve nesne Başlatıcısı sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="e3b45-114">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](~/samples/csharp/language-reference/operators/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="e3b45-115">Tür örneklerinin yok edilmesi</span><span class="sxs-lookup"><span data-stu-id="e3b45-115">Destruction of type instances</span></span>

<span data-ttu-id="e3b45-116">Önceden oluşturulmuş tür örneklerini yok etmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e3b45-116">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="e3b45-117">Başvuru ve değer türlerinin örnekleri otomatik olarak yok edilir.</span><span class="sxs-lookup"><span data-stu-id="e3b45-117">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="e3b45-118">Değer türlerinin örnekleri, bunları içeren bağlam yok edilir oluşturmaz yok edilir.</span><span class="sxs-lookup"><span data-stu-id="e3b45-118">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="e3b45-119">Başvuru türlerinin örnekleri, en son başvuru kaldırıldıktan sonra, belirlenemeyen sürede [çöp toplayıcı](../../../standard/garbage-collection/index.md) tarafından yok edilir.</span><span class="sxs-lookup"><span data-stu-id="e3b45-119">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="e3b45-120">Yönetilmeyen kaynakları içeren tür örneklerinde, örneğin bir dosya tanıtıcısı için, içerdikleri kaynakların mümkün olan en kısa sürede serbest bırakılacağını sağlamak üzere belirleyici Temizleme kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="e3b45-120">For type instances that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="e3b45-121">Daha fazla bilgi için bkz. <xref:System.IDisposable?displayProperty=nameWithType> API başvurusu ve [using açıklaması](../keywords/using-statement.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="e3b45-121">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="e3b45-122">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="e3b45-122">Operator overloadability</span></span>

<span data-ttu-id="e3b45-123">Kullanıcı tanımlı bir tür `new` işlecini aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="e3b45-123">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e3b45-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e3b45-124">C# language specification</span></span>

<span data-ttu-id="e3b45-125">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Yeni işleç](~/_csharplang/spec/expressions.md#the-new-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e3b45-125">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3b45-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3b45-126">See also</span></span>

- [<span data-ttu-id="e3b45-127">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="e3b45-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e3b45-128">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="e3b45-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="e3b45-129">Nesne ve koleksiyon başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="e3b45-129">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
