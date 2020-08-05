---
title: New işleci-C# başvurusu
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 1e1abb95d8b0b956e391b05ddc5a0a8a20d01a63
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555311"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="741ca-102">New işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="741ca-102">new operator (C# reference)</span></span>

<span data-ttu-id="741ca-103">`new`İşleci, bir türün yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="741ca-103">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="741ca-104">`new`Anahtar sözcüğünü [üye bildirim değiştiricisi](../keywords/new-modifier.md) veya [genel tür kısıtlaması](../keywords/new-constraint.md)olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="741ca-104">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="741ca-105">Oluşturucu çağırma</span><span class="sxs-lookup"><span data-stu-id="741ca-105">Constructor invocation</span></span>

<span data-ttu-id="741ca-106">Bir türün yeni bir örneğini oluşturmak için, genellikle işlecini kullanarak bu türdeki [oluşturuculardan](../../programming-guide/classes-and-structs/constructors.md) birini çağırın `new` :</span><span class="sxs-lookup"><span data-stu-id="741ca-106">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](snippets/NewOperator.cs#Constructor)]

<span data-ttu-id="741ca-107">[object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) `new` Aşağıdaki örnekte gösterildiği gibi, bir ifadede bir nesne oluşturmak ve başlatmak için işleciyle bir nesne veya koleksiyon başlatıcısı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="741ca-107">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](snippets/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a><span data-ttu-id="741ca-108">Dizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="741ca-108">Array creation</span></span>

<span data-ttu-id="741ca-109">`new`Aşağıdaki örnekte gösterildiği gibi, bir dizi örneği oluşturmak için işlecini de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="741ca-109">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](snippets/NewOperator.cs#Array)]

<span data-ttu-id="741ca-110">Dizi başlatma söz dizimini kullanarak bir dizi örneği oluşturun ve tek bir deyimdeki öğelerle doldurun.</span><span class="sxs-lookup"><span data-stu-id="741ca-110">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="741ca-111">Aşağıdaki örnek, bunu nasıl yapabilmenizin çeşitli yollarını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="741ca-111">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](snippets/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="741ca-112">Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="741ca-112">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="741ca-113">Anonim türlerin örneklenmesi</span><span class="sxs-lookup"><span data-stu-id="741ca-113">Instantiation of anonymous types</span></span>

<span data-ttu-id="741ca-114">[Anonim türün](../../programming-guide/classes-and-structs/anonymous-types.md)bir örneğini oluşturmak için `new` işleç ve nesne Başlatıcısı söz dizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="741ca-114">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](snippets/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="741ca-115">Tür örneklerinin yok edilmesi</span><span class="sxs-lookup"><span data-stu-id="741ca-115">Destruction of type instances</span></span>

<span data-ttu-id="741ca-116">Önceden oluşturulmuş tür örneklerini yok etmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="741ca-116">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="741ca-117">Başvuru ve değer türlerinin örnekleri otomatik olarak yok edilir.</span><span class="sxs-lookup"><span data-stu-id="741ca-117">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="741ca-118">Değer türlerinin örnekleri, bunları içeren bağlam yok edilir oluşturmaz yok edilir.</span><span class="sxs-lookup"><span data-stu-id="741ca-118">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="741ca-119">Başvuru türlerinin örnekleri, son başvuru kaldırıldıktan sonra bazı belirtilmeyen bir zamanda [çöp toplayıcı](../../../standard/garbage-collection/index.md) tarafından yok edilir.</span><span class="sxs-lookup"><span data-stu-id="741ca-119">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at some unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="741ca-120">Yönetilmeyen kaynakları içeren tür örneklerinde, örneğin bir dosya tanıtıcısı için, içerdikleri kaynakların mümkün olan en kısa sürede serbest bırakılacağını sağlamak üzere belirleyici Temizleme kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="741ca-120">For type instances that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="741ca-121">Daha fazla bilgi için bkz <xref:System.IDisposable?displayProperty=nameWithType> . API başvurusu ve [using ekstresi](../keywords/using-statement.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="741ca-121">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="741ca-122">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="741ca-122">Operator overloadability</span></span>

<span data-ttu-id="741ca-123">Kullanıcı tanımlı bir tür işleci aşırı yükleyemez `new` .</span><span class="sxs-lookup"><span data-stu-id="741ca-123">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="741ca-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="741ca-124">C# language specification</span></span>

<span data-ttu-id="741ca-125">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Yeni işleç](~/_csharplang/spec/expressions.md#the-new-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="741ca-125">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="741ca-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="741ca-126">See also</span></span>

- [<span data-ttu-id="741ca-127">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="741ca-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="741ca-128">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="741ca-128">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="741ca-129">Nesne ve koleksiyon başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="741ca-129">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
