---
title: New işleci - C# başvurusu
ms.custom: seodec18
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 3d64c4805abe38c80301748ffa6b35fc87563b60
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402513"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="77ab7-102">New işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="77ab7-102">new operator (C# reference)</span></span>

<span data-ttu-id="77ab7-103">`new` İşleci, bir türün yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77ab7-103">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="77ab7-104">Ayrıca `new` as anahtar sözcüğü bir [üye bildirim değiştirici](../keywords/new-modifier.md) veya [genel tür kısıtlaması](../keywords/new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="77ab7-104">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="77ab7-105">Oluşturucu çağrı</span><span class="sxs-lookup"><span data-stu-id="77ab7-105">Constructor invocation</span></span>

<span data-ttu-id="77ab7-106">Bir türün yeni bir örneğini oluşturmak için genellikle aşağıdakilerden birini çağırma [oluşturucular](../../programming-guide/classes-and-structs/constructors.md) bu türü kullanarak `new` işleci:</span><span class="sxs-lookup"><span data-stu-id="77ab7-106">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](~/samples/csharp/language-reference/operators/NewOperator.cs#Constructor)]

<span data-ttu-id="77ab7-107">Kullanabileceğiniz bir [nesne veya koleksiyon Başlatıcı](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) ile `new` işleci örneği oluşturun ve aşağıdaki örnekte gösterildiği gibi bir ifade bir nesneyi başlatmak için:</span><span class="sxs-lookup"><span data-stu-id="77ab7-107">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](~/samples/csharp/language-reference/operators/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a><span data-ttu-id="77ab7-108">Dizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="77ab7-108">Array creation</span></span>

<span data-ttu-id="77ab7-109">Ayrıca `new` işleci aşağıdaki örnekte gösterildiği gibi bir dizi örneği oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="77ab7-109">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](~/samples/csharp/language-reference/operators/NewOperator.cs#Array)]

<span data-ttu-id="77ab7-110">Dizi başlatma söz dizimi, bir dizi örneği oluşturun ve öğeleri bir ifade ile doldurmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="77ab7-110">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="77ab7-111">Aşağıdaki örnekte, nasıl yapabileceğiniz çeşitli yollar gösterir:</span><span class="sxs-lookup"><span data-stu-id="77ab7-111">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](~/samples/csharp/language-reference/operators/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="77ab7-112">Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="77ab7-112">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="77ab7-113">Anonim türdeki örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="77ab7-113">Instantiation of anonymous types</span></span>

<span data-ttu-id="77ab7-114">Bir örneğini oluşturmak için bir [anonim tür](../../programming-guide/classes-and-structs/anonymous-types.md), kullanın `new` işleci ve nesne Başlatıcısı sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="77ab7-114">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](~/samples/csharp/language-reference/operators/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="77ab7-115">Tür örnekleri, yok etme</span><span class="sxs-lookup"><span data-stu-id="77ab7-115">Destruction of type instances</span></span>

<span data-ttu-id="77ab7-116">Daha önce oluşturulan tür örnekleri yok gerekmez.</span><span class="sxs-lookup"><span data-stu-id="77ab7-116">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="77ab7-117">Hem başvuru ve değer türlerinin örnekleri otomatik olarak yok edilir.</span><span class="sxs-lookup"><span data-stu-id="77ab7-117">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="77ab7-118">Değer türlerinin örnekleri, bunları içeren bir bağlam yok hemen sonra yok edilir.</span><span class="sxs-lookup"><span data-stu-id="77ab7-118">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="77ab7-119">Başvuru türlerinin örnekleri tarafından edilir [çöp toplayıcı](../../../standard/garbage-collection/index.md) bunları son başvuruysa kaldırıldıktan sonra belirtilmeyen zaman.</span><span class="sxs-lookup"><span data-stu-id="77ab7-119">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="77ab7-120">Yönetilmeyen kaynakları içeren türleri için örneğin, bir dosya tanıtıcısı, belirlenimci içerdikleri kaynakları hemen serbest emin olmak için temizleme kullanmak istemiyorsunuz önerilir.</span><span class="sxs-lookup"><span data-stu-id="77ab7-120">For types that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="77ab7-121">Daha fazla bilgi için <xref:System.IDisposable?displayProperty=nameWithType> API Başvurusu ve [using deyimi](../keywords/using-statement.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="77ab7-121">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="77ab7-122">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="77ab7-122">Operator overloadability</span></span>

<span data-ttu-id="77ab7-123">Kullanıcı tanımlı bir tür aşırı yüklenemez `new` işleci.</span><span class="sxs-lookup"><span data-stu-id="77ab7-123">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="77ab7-124">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="77ab7-124">C# language specification</span></span>

<span data-ttu-id="77ab7-125">Daha fazla bilgi için [new işleci](~/_csharplang/spec/expressions.md#the-new-operator) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="77ab7-125">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="77ab7-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77ab7-126">See also</span></span>

- [<span data-ttu-id="77ab7-127">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="77ab7-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="77ab7-128">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="77ab7-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="77ab7-129">Nesne ve koleksiyon başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="77ab7-129">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
