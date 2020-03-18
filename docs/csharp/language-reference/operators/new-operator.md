---
title: yeni operatör - C# referans
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 84131bc503a106961419a27fc4e3e0f2d82306a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846239"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="36e1e-102">yeni işleç (C# referans)</span><span class="sxs-lookup"><span data-stu-id="36e1e-102">new operator (C# reference)</span></span>

<span data-ttu-id="36e1e-103">İşleç, `new` yeni bir tür örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="36e1e-103">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="36e1e-104">Anahtar kelimeyi `new` üye bildirimi [değiştiricisi](../keywords/new-modifier.md) veya genel tür [kısıtlaması](../keywords/new-constraint.md)olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36e1e-104">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="36e1e-105">Yapıcı çağırma</span><span class="sxs-lookup"><span data-stu-id="36e1e-105">Constructor invocation</span></span>

<span data-ttu-id="36e1e-106">Yeni bir tür örneği oluşturmak için, genellikle `new` işleci kullanarak bu tür [yapıcılardan](../../programming-guide/classes-and-structs/constructors.md) birini çağırırsınız:</span><span class="sxs-lookup"><span data-stu-id="36e1e-106">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](snippets/NewOperator.cs#Constructor)]

<span data-ttu-id="36e1e-107">Aşağıdaki örnekte görüldüğü gibi, bir `new` [nesneyi](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) bir ifadede anlık olarak kullanmak ve başlatmak için işleçle birlikte bir nesne veya koleksiyon başlatılması nı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="36e1e-107">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](snippets/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a><span data-ttu-id="36e1e-108">Dizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="36e1e-108">Array creation</span></span>

<span data-ttu-id="36e1e-109">Aşağıdaki örnekte `new` görüldüğü gibi, bir dizi örneği oluşturmak için işleci de kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="36e1e-109">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](snippets/NewOperator.cs#Array)]

<span data-ttu-id="36e1e-110">Dizi örneği oluşturmak ve tek bir deyimdeki öğelerle doldurmak için dizi başlatma sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="36e1e-110">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="36e1e-111">Aşağıdaki örnek, bunu nasıl yapabileceğinizi çeşitli şekillerde gösterir:</span><span class="sxs-lookup"><span data-stu-id="36e1e-111">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](snippets/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="36e1e-112">Diziler hakkında daha fazla bilgi için [Diziler'e](../../programming-guide/arrays/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="36e1e-112">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="36e1e-113">Anonim türlerin anında</span><span class="sxs-lookup"><span data-stu-id="36e1e-113">Instantiation of anonymous types</span></span>

<span data-ttu-id="36e1e-114">Anonim bir [tür](../../programming-guide/classes-and-structs/anonymous-types.md)örneği oluşturmak `new` için, işleç ve nesne başharf sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="36e1e-114">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](snippets/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="36e1e-115">Tür örneklerinin yok edilmesi</span><span class="sxs-lookup"><span data-stu-id="36e1e-115">Destruction of type instances</span></span>

<span data-ttu-id="36e1e-116">Daha önce oluşturulmuş tür örneklerini yok etmek zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="36e1e-116">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="36e1e-117">Hem başvuru hem de değer türlerinin örnekleri otomatik olarak yok edilir.</span><span class="sxs-lookup"><span data-stu-id="36e1e-117">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="36e1e-118">Değer türleri örnekleri, bunları içeren bağlam yok edilir yok edilir etmez yok edilir.</span><span class="sxs-lookup"><span data-stu-id="36e1e-118">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="36e1e-119">Başvuru türleri örnekleri, son başvuru kaldırıldıktan sonra, çöp [toplayıcı](../../../standard/garbage-collection/index.md) tarafından belirtilmeyen bir zamanda yok edilir.</span><span class="sxs-lookup"><span data-stu-id="36e1e-119">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="36e1e-120">Yönetilmeyen kaynaklar içeren tür örnekleriiçin ( örneğin, bir dosya işlemesi, içerdikleri kaynakların mümkün olan en kısa sürede serbest bırakıldığından emin olmak için deterministik temizleme kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="36e1e-120">For type instances that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="36e1e-121">Daha fazla bilgi <xref:System.IDisposable?displayProperty=nameWithType> için API başvurusuna ve [kullanarak ifade](../keywords/using-statement.md) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="36e1e-121">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="36e1e-122">Operatör aşırı yüklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="36e1e-122">Operator overloadability</span></span>

<span data-ttu-id="36e1e-123">Kullanıcı tanımlı bir tür `new` işleci aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="36e1e-123">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="36e1e-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="36e1e-124">C# language specification</span></span>

<span data-ttu-id="36e1e-125">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [yeni işleç](~/_csharplang/spec/expressions.md#the-new-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="36e1e-125">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="36e1e-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36e1e-126">See also</span></span>

- [<span data-ttu-id="36e1e-127">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="36e1e-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="36e1e-128">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="36e1e-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="36e1e-129">Nesne ve toplama başharfleri</span><span class="sxs-lookup"><span data-stu-id="36e1e-129">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
