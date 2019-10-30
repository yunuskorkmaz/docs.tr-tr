---
title: İfade-Bodied Üyeler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b336834dcc021b986d79f09d2a9440de0b102f78
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039757"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="905a8-102">İfade-Bodied Üyeler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="905a8-102">Expression-bodied members (C# programming guide)</span></span>

<span data-ttu-id="905a8-103">İfade gövdesi tanımları, üyenin uygulamasını çok kısa, okunabilir bir biçimde sağlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="905a8-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="905a8-104">Bir yöntem veya özellik gibi desteklenen herhangi bir üyenin mantığı tek bir ifadeden oluşuyorsa, bir ifade gövdesi tanımı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="905a8-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="905a8-105">Bir ifade gövdesi tanımında aşağıdaki genel sözdizimi vardır:</span><span class="sxs-lookup"><span data-stu-id="905a8-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="905a8-106">Burada *ifadesi* geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="905a8-106">where *expression* is a valid expression.</span></span>

<span data-ttu-id="905a8-107">6 ' C# da Yöntemler ve salt okunurdur özellikler için ifade gövdesi tanımları desteği sunuldu ve 7,0 ' de C# genişletildi.</span><span class="sxs-lookup"><span data-stu-id="905a8-107">Support for expression body definitions was introduced for methods and read-only properties in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="905a8-108">İfade gövdesi tanımları, aşağıdaki tabloda listelenen tür üyeleri ile birlikte kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="905a8-108">Expression body definitions can be used with the type members listed in the following table:</span></span>

|<span data-ttu-id="905a8-109">Üye</span><span class="sxs-lookup"><span data-stu-id="905a8-109">Member</span></span>  |<span data-ttu-id="905a8-110">İtibariyle destekleniyor...</span><span class="sxs-lookup"><span data-stu-id="905a8-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="905a8-111">Yöntemidir</span><span class="sxs-lookup"><span data-stu-id="905a8-111">Method</span></span>](#methods)  |<span data-ttu-id="905a8-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="905a8-112">C# 6</span></span> |
|[<span data-ttu-id="905a8-113">Salt okunurdur özelliği</span><span class="sxs-lookup"><span data-stu-id="905a8-113">Read-only property</span></span>](#read-only-properties)   |<span data-ttu-id="905a8-114">C# 6</span><span class="sxs-lookup"><span data-stu-id="905a8-114">C# 6</span></span>  |
|[<span data-ttu-id="905a8-115">Özelliði</span><span class="sxs-lookup"><span data-stu-id="905a8-115">Property</span></span>](#properties)  |<span data-ttu-id="905a8-116">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="905a8-116">C# 7.0</span></span> |
|[<span data-ttu-id="905a8-117">Constructor</span><span class="sxs-lookup"><span data-stu-id="905a8-117">Constructor</span></span>](#constructors)   |<span data-ttu-id="905a8-118">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="905a8-118">C# 7.0</span></span> |
|[<span data-ttu-id="905a8-119">Sonlandırıcı</span><span class="sxs-lookup"><span data-stu-id="905a8-119">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="905a8-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="905a8-120">C# 7.0</span></span> |
|[<span data-ttu-id="905a8-121">Dizinleyic</span><span class="sxs-lookup"><span data-stu-id="905a8-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="905a8-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="905a8-122">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="905a8-123">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="905a8-123">Methods</span></span>

<span data-ttu-id="905a8-124">İfade-Bodied yöntemi, türü yöntemin dönüş türüyle eşleşen bir değer döndüren tek bir ifadeden oluşur veya `void`döndüren yöntemler için bazı işlemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="905a8-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="905a8-125">Örneğin, <xref:System.Object.ToString%2A> yöntemini geçersiz kılan türler, genellikle geçerli nesnenin dize gösterimini döndüren tek bir ifade içerir.</span><span class="sxs-lookup"><span data-stu-id="905a8-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span>

<span data-ttu-id="905a8-126">Aşağıdaki örnek, bir ifade gövdesi tanımıyla <xref:System.Object.ToString%2A> yöntemini geçersiz kılan bir `Person` sınıfını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="905a8-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="905a8-127">Ayrıca, konsola bir ad görüntüleyen bir `DisplayName` yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="905a8-127">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="905a8-128">`return` anahtar sözcüğünün `ToString` ifadesi gövde tanımında kullanılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="905a8-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="905a8-129">Daha fazla bilgi için bkz. [YöntemlerC# (Programlama Kılavuzu)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="905a8-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>

## <a name="read-only-properties"></a><span data-ttu-id="905a8-130">Salt okunurdur özellikleri</span><span class="sxs-lookup"><span data-stu-id="905a8-130">Read-only properties</span></span>

<span data-ttu-id="905a8-131">C# 6 ' dan itibaren, salt okunurdur bir özellik uygulamak için ifade gövdesi tanımı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="905a8-131">Starting with C# 6, you can use expression body definition to implement a read-only property.</span></span> <span data-ttu-id="905a8-132">Bunu yapmak için aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="905a8-132">To do that, use the following syntax:</span></span>

```csharp
PropertyType PropertyName => expression;
```

<span data-ttu-id="905a8-133">Aşağıdaki örnek, salt okunurdur `Name` özelliği özel `locationName` alanının değerini döndüren bir ifade gövdesi tanımı olarak uygulanan bir `Location` sınıfını tanımlar:</span><span class="sxs-lookup"><span data-stu-id="905a8-133">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field:</span></span>

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="905a8-134">Özellikler hakkında daha fazla bilgi için bkz. [ÖzelliklerC# (Programlama Kılavuzu)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="905a8-134">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="properties"></a><span data-ttu-id="905a8-135">Özellikler</span><span class="sxs-lookup"><span data-stu-id="905a8-135">Properties</span></span>

<span data-ttu-id="905a8-136">7,0 ' C# den başlayarak, özellik`get`ve`set`erişimcileri uygulamak için ifade gövdesi tanımlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="905a8-136">Starting with C# 7.0, you can use expression body definitions to implement property `get` and `set` accessors.</span></span> <span data-ttu-id="905a8-137">Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="905a8-137">The following example demonstrates how to do that:</span></span>

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

<span data-ttu-id="905a8-138">Özellikler hakkında daha fazla bilgi için bkz. [ÖzelliklerC# (Programlama Kılavuzu)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="905a8-138">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="constructors"></a><span data-ttu-id="905a8-139">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="905a8-139">Constructors</span></span>

<span data-ttu-id="905a8-140">Bir oluşturucunun ifade gövdesi tanımı genellikle tek bir atama ifadesi veya oluşturucunun bağımsız değişkenlerini işleyen veya örnek durumunu Başlatan bir yöntem çağrısından oluşur.</span><span class="sxs-lookup"><span data-stu-id="905a8-140">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span>

<span data-ttu-id="905a8-141">Aşağıdaki örnek, oluşturucusunun *adı*adlı tek bir dize parametresine sahip bir `Location` sınıfını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="905a8-141">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="905a8-142">İfade gövdesi tanımı, bağımsız değişkeni `Name` özelliğine atar.</span><span class="sxs-lookup"><span data-stu-id="905a8-142">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="905a8-143">Daha fazla bilgi için bkz. [oluşturucularC# (Programlama Kılavuzu)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="905a8-143">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="905a8-144">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="905a8-144">Finalizers</span></span>

<span data-ttu-id="905a8-145">Sonlandırıcı için bir ifade gövdesi tanımı tipik olarak, yönetilmeyen kaynakları serbest bırakma deyimleri gibi temizleme deyimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="905a8-145">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="905a8-146">Aşağıdaki örnek, sonlandırıcının çağrıldığını göstermek için bir ifade gövde tanımı kullanan sonlandırıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="905a8-146">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="905a8-147">Daha fazla bilgi için bkz. [sonlandırıcılarC# (Programlama Kılavuzu)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="905a8-147">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="905a8-148">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="905a8-148">Indexers</span></span>

<span data-ttu-id="905a8-149">Özellikler ile benzer şekilde, `get` erişimci bir değer döndüren tek bir ifadeden oluşuyorsa veya `set` erişimcisi basit bir atama gerçekleştirdiğinden, Dizin Oluşturucu `get` ve `set` erişimcileri ifade gövdesi tanımlarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="905a8-149">Like with properties, indexer `get` and `set` accessors consist of expression body definitions if the `get` accessor consists of a single expression that returns a value or the `set` accessor performs a simple assignment.</span></span>

<span data-ttu-id="905a8-150">Aşağıdaki örnek, bir dizi spor adını içeren bir iç <xref:System.String> dizisi içeren `Sports` adlı bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="905a8-150">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="905a8-151">Dizin Oluşturucu `get` ve `set` erişimcileri, ifade gövdesi tanımları olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="905a8-151">Both the indexer `get` and `set` accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

<span data-ttu-id="905a8-152">Daha fazla bilgi için bkz. [DizinC# oluşturucular (Programlama Kılavuzu)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="905a8-152">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>
