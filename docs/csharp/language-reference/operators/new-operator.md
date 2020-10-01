---
description: New işleci-C# başvurusu
title: New işleci-C# başvurusu
ms.date: 10/02/2020
f1_keywords:
- new_CSharpKeyword
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 3125f3d2c694dcfc5682ee482f3f76072ac3726d
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609388"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="2b2a4-103">New işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2b2a4-103">new operator (C# reference)</span></span>

<span data-ttu-id="2b2a4-104">`new`İşleci, bir türün yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2b2a4-104">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="2b2a4-105">`new`Anahtar sözcüğünü [üye bildirim değiştiricisi](../keywords/new-modifier.md) veya [genel tür kısıtlaması](../keywords/new-constraint.md)olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b2a4-105">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="2b2a4-106">Oluşturucu çağırma</span><span class="sxs-lookup"><span data-stu-id="2b2a4-106">Constructor invocation</span></span>

<span data-ttu-id="2b2a4-107">Bir türün yeni bir örneğini oluşturmak için, genellikle işlecini kullanarak bu türdeki [oluşturuculardan](../../programming-guide/classes-and-structs/constructors.md) birini çağırın `new` :</span><span class="sxs-lookup"><span data-stu-id="2b2a4-107">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](snippets/shared/NewOperator.cs#Constructor)]

<span data-ttu-id="2b2a4-108">[object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) `new` Aşağıdaki örnekte gösterildiği gibi, bir ifadede bir nesne oluşturmak ve başlatmak için işleciyle bir nesne veya koleksiyon başlatıcısı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2b2a4-108">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](snippets/shared/NewOperator.cs#ConstructorWithInitializer)]

<span data-ttu-id="2b2a4-109">C# 9,0 ile başlayarak, Oluşturucu çağırma ifadeleri Target türünde.</span><span class="sxs-lookup"><span data-stu-id="2b2a4-109">Beginning with C# 9.0, constructor invocation expressions are target-typed.</span></span> <span data-ttu-id="2b2a4-110">Diğer bir deyişle, bir ifadenin hedef türü biliniyorsa, aşağıdaki örnekte gösterildiği gibi, bir tür adını atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2b2a4-110">That is, if a target type of an expression is known, you can omit a type name, as the following example shows:</span></span>

:::code language="csharp" source="snippets/shared/NewOperator.cs" id="SnippetTargetTyped":::

<span data-ttu-id="2b2a4-111">Yukarıdaki örnekte gösterildiği gibi, her zaman ayraçları hedef türü bir `new` ifadede kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="2b2a4-111">As the preceding example shows, you always use parentheses in a target-typed `new` expression.</span></span>

<span data-ttu-id="2b2a4-112">Bir ifadenin hedef türü `new` bilinmiyorsa (örneğin, [`var`](../keywords/var.md) anahtar sözcüğünü kullandığınızda), bir tür adı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b2a4-112">If a target type of a `new` expression is unknown (for example, when you use the [`var`](../keywords/var.md) keyword), you must specify a type name.</span></span>

## <a name="array-creation"></a><span data-ttu-id="2b2a4-113">Dizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="2b2a4-113">Array creation</span></span>

<span data-ttu-id="2b2a4-114">`new`Aşağıdaki örnekte gösterildiği gibi, bir dizi örneği oluşturmak için işlecini de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2b2a4-114">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](snippets/shared/NewOperator.cs#Array)]

<span data-ttu-id="2b2a4-115">Dizi başlatma söz dizimini kullanarak bir dizi örneği oluşturun ve tek bir deyimdeki öğelerle doldurun.</span><span class="sxs-lookup"><span data-stu-id="2b2a4-115">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="2b2a4-116">Aşağıdaki örnek, bunu nasıl yapabilmenizin çeşitli yollarını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="2b2a4-116">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](snippets/shared/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="2b2a4-117">Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="2b2a4-117">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="2b2a4-118">Anonim türlerin örneklenmesi</span><span class="sxs-lookup"><span data-stu-id="2b2a4-118">Instantiation of anonymous types</span></span>

<span data-ttu-id="2b2a4-119">[Anonim türün](../../programming-guide/classes-and-structs/anonymous-types.md)bir örneğini oluşturmak için `new` işleç ve nesne Başlatıcısı söz dizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="2b2a4-119">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](snippets/shared/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="2b2a4-120">Tür örneklerinin yok edilmesi</span><span class="sxs-lookup"><span data-stu-id="2b2a4-120">Destruction of type instances</span></span>

<span data-ttu-id="2b2a4-121">Önceden oluşturulmuş tür örneklerini yok etmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2b2a4-121">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="2b2a4-122">Başvuru ve değer türlerinin örnekleri otomatik olarak yok edilir.</span><span class="sxs-lookup"><span data-stu-id="2b2a4-122">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="2b2a4-123">Değer türlerinin örnekleri, bunları içeren bağlam yok edilir oluşturmaz yok edilir.</span><span class="sxs-lookup"><span data-stu-id="2b2a4-123">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="2b2a4-124">Başvuru türlerinin örnekleri, son başvuru kaldırıldıktan sonra bazı belirtilmeyen bir zamanda [çöp toplayıcı](../../../standard/garbage-collection/index.md) tarafından yok edilir.</span><span class="sxs-lookup"><span data-stu-id="2b2a4-124">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at some unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="2b2a4-125">Yönetilmeyen kaynakları içeren tür örneklerinde, örneğin bir dosya tanıtıcısı için, içerdikleri kaynakların mümkün olan en kısa sürede serbest bırakılacağını sağlamak üzere belirleyici Temizleme kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="2b2a4-125">For type instances that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="2b2a4-126">Daha fazla bilgi için bkz <xref:System.IDisposable?displayProperty=nameWithType> . API başvurusu ve [using ekstresi](../keywords/using-statement.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="2b2a4-126">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="2b2a4-127">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="2b2a4-127">Operator overloadability</span></span>

<span data-ttu-id="2b2a4-128">Kullanıcı tanımlı bir tür işleci aşırı yükleyemez `new` .</span><span class="sxs-lookup"><span data-stu-id="2b2a4-128">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2b2a4-129">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="2b2a4-129">C# language specification</span></span>

<span data-ttu-id="2b2a4-130">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Yeni işleç](~/_csharplang/spec/expressions.md#the-new-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2b2a4-130">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="2b2a4-131">Hedef türü belirtilmiş bir ifade hakkında daha fazla bilgi için `new` bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-9.0/target-typed-new.md).</span><span class="sxs-lookup"><span data-stu-id="2b2a4-131">For more information about a target-typed `new` expression, see the [feature proposal note](~/_csharplang/proposals/csharp-9.0/target-typed-new.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b2a4-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b2a4-132">See also</span></span>

- [<span data-ttu-id="2b2a4-133">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2b2a4-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2b2a4-134">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="2b2a4-134">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="2b2a4-135">Nesne ve koleksiyon başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="2b2a4-135">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
