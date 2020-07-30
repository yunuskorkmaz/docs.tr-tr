---
title: İfade-Bodied Üyeler-C# Programlama Kılavuzu
description: İfade-Bodied Üyeler hakkında bilgi edinin. Özellikler, oluşturucular, sonlandırıcılar ve daha fazlası için ifade gövdesi tanımı kullanan kod örneklerine bakın.
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: e68e96e4aa3ff6a64590459a7197da1833e1a275
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381664"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="0be2b-104">İfade-Bodied Üyeler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0be2b-104">Expression-bodied members (C# programming guide)</span></span>

<span data-ttu-id="0be2b-105">İfade gövdesi tanımları, üyenin uygulamasını çok kısa, okunabilir bir biçimde sağlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0be2b-105">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="0be2b-106">Bir yöntem veya özellik gibi desteklenen herhangi bir üyenin mantığı tek bir ifadeden oluşuyorsa, bir ifade gövdesi tanımı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0be2b-106">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="0be2b-107">Bir ifade gövdesi tanımında aşağıdaki genel sözdizimi vardır:</span><span class="sxs-lookup"><span data-stu-id="0be2b-107">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="0be2b-108">Burada *ifadesi* geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="0be2b-108">where *expression* is a valid expression.</span></span>

<span data-ttu-id="0be2b-109">C# 6 ' da Yöntemler ve salt okunurdur özellikler için ifade gövdesi tanımları desteği sunuldu ve c# 7,0 ' de genişletilmişti.</span><span class="sxs-lookup"><span data-stu-id="0be2b-109">Support for expression body definitions was introduced for methods and read-only properties in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="0be2b-110">İfade gövdesi tanımları, aşağıdaki tabloda listelenen tür üyeleri ile birlikte kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="0be2b-110">Expression body definitions can be used with the type members listed in the following table:</span></span>

|<span data-ttu-id="0be2b-111">Üye</span><span class="sxs-lookup"><span data-stu-id="0be2b-111">Member</span></span>  |<span data-ttu-id="0be2b-112">İtibariyle destekleniyor...</span><span class="sxs-lookup"><span data-stu-id="0be2b-112">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="0be2b-113">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0be2b-113">Method</span></span>](#methods)  |<span data-ttu-id="0be2b-114">C# 6</span><span class="sxs-lookup"><span data-stu-id="0be2b-114">C# 6</span></span> |
|[<span data-ttu-id="0be2b-115">Salt okunurdur özelliği</span><span class="sxs-lookup"><span data-stu-id="0be2b-115">Read-only property</span></span>](#read-only-properties)   |<span data-ttu-id="0be2b-116">C# 6</span><span class="sxs-lookup"><span data-stu-id="0be2b-116">C# 6</span></span>  |
|[<span data-ttu-id="0be2b-117">Özellik</span><span class="sxs-lookup"><span data-stu-id="0be2b-117">Property</span></span>](#properties)  |<span data-ttu-id="0be2b-118">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="0be2b-118">C# 7.0</span></span> |
|[<span data-ttu-id="0be2b-119">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="0be2b-119">Constructor</span></span>](#constructors)   |<span data-ttu-id="0be2b-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="0be2b-120">C# 7.0</span></span> |
|[<span data-ttu-id="0be2b-121">Sonlandırıcı</span><span class="sxs-lookup"><span data-stu-id="0be2b-121">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="0be2b-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="0be2b-122">C# 7.0</span></span> |
|[<span data-ttu-id="0be2b-123">Dizin Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="0be2b-123">Indexer</span></span>](#indexers)       |<span data-ttu-id="0be2b-124">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="0be2b-124">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="0be2b-125">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0be2b-125">Methods</span></span>

<span data-ttu-id="0be2b-126">Bir ifade-Bodied yöntemi, türü yöntemin dönüş türüyle eşleşen bir değer döndüren tek bir ifadeden oluşur veya döndürülen yöntemler için `void` bazı işlemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="0be2b-126">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="0be2b-127">Örneğin, yöntemi geçersiz kılan türler, <xref:System.Object.ToString%2A> genellikle geçerli nesnenin dize gösterimini döndüren tek bir ifade içerir.</span><span class="sxs-lookup"><span data-stu-id="0be2b-127">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span>

<span data-ttu-id="0be2b-128">Aşağıdaki örnek, `Person` <xref:System.Object.ToString%2A> bir ifade gövdesi tanımıyla yöntemi geçersiz kılan bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0be2b-128">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="0be2b-129">Ayrıca `DisplayName` , konsola bir ad görüntüleyen bir yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0be2b-129">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="0be2b-130">`return`Anahtar sözcüğünün `ToString` ifade gövdesi tanımında kullanılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0be2b-130">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="0be2b-131">Daha fazla bilgi için bkz. [Yöntemler (C# Programlama Kılavuzu)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="0be2b-131">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>

## <a name="read-only-properties"></a><span data-ttu-id="0be2b-132">Salt okunurdur özellikleri</span><span class="sxs-lookup"><span data-stu-id="0be2b-132">Read-only properties</span></span>

<span data-ttu-id="0be2b-133">C# 6 ' dan itibaren, salt okunurdur bir özellik uygulamak için ifade gövdesi tanımı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0be2b-133">Starting with C# 6, you can use expression body definition to implement a read-only property.</span></span> <span data-ttu-id="0be2b-134">Bunu yapmak için aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="0be2b-134">To do that, use the following syntax:</span></span>

```csharp
PropertyType PropertyName => expression;
```

<span data-ttu-id="0be2b-135">Aşağıdaki örnek, `Location` salt okunurdur `Name` özelliği özel alanın değerini döndüren bir ifade gövdesi tanımı olarak uygulanan bir sınıfı tanımlar `locationName` :</span><span class="sxs-lookup"><span data-stu-id="0be2b-135">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field:</span></span>

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="0be2b-136">Özellikler hakkında daha fazla bilgi için bkz. [Özellikler (C# Programlama Kılavuzu)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="0be2b-136">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="properties"></a><span data-ttu-id="0be2b-137">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0be2b-137">Properties</span></span>

<span data-ttu-id="0be2b-138">C# 7,0 ' den başlayarak, özellik ve erişimcileri uygulamak için ifade gövdesi tanımları `get` kullanabilirsiniz `set` .</span><span class="sxs-lookup"><span data-stu-id="0be2b-138">Starting with C# 7.0, you can use expression body definitions to implement property `get` and `set` accessors.</span></span> <span data-ttu-id="0be2b-139">Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="0be2b-139">The following example demonstrates how to do that:</span></span>

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

<span data-ttu-id="0be2b-140">Özellikler hakkında daha fazla bilgi için bkz. [Özellikler (C# Programlama Kılavuzu)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="0be2b-140">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="constructors"></a><span data-ttu-id="0be2b-141">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="0be2b-141">Constructors</span></span>

<span data-ttu-id="0be2b-142">Bir oluşturucunun ifade gövdesi tanımı genellikle tek bir atama ifadesi veya oluşturucunun bağımsız değişkenlerini işleyen veya örnek durumunu Başlatan bir yöntem çağrısından oluşur.</span><span class="sxs-lookup"><span data-stu-id="0be2b-142">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span>

<span data-ttu-id="0be2b-143">Aşağıdaki örnek, `Location` oluşturucusunun *adı*adlı tek bir dize parametresine sahip olan bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0be2b-143">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="0be2b-144">İfade gövdesi tanımı bağımsız değişkeni `Name` özelliğine atar.</span><span class="sxs-lookup"><span data-stu-id="0be2b-144">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="0be2b-145">Daha fazla bilgi için bkz. [oluşturucular (C# Programlama Kılavuzu)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="0be2b-145">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="0be2b-146">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="0be2b-146">Finalizers</span></span>

<span data-ttu-id="0be2b-147">Sonlandırıcı için bir ifade gövdesi tanımı tipik olarak, yönetilmeyen kaynakları serbest bırakma deyimleri gibi temizleme deyimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0be2b-147">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="0be2b-148">Aşağıdaki örnek, sonlandırıcının çağrıldığını göstermek için bir ifade gövde tanımı kullanan sonlandırıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0be2b-148">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="0be2b-149">Daha fazla bilgi için bkz. [sonlandırıcılar (C# Programlama Kılavuzu)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="0be2b-149">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="0be2b-150">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="0be2b-150">Indexers</span></span>

<span data-ttu-id="0be2b-151">Özellikler ile olduğu gibi, `get` `set` `get` erişimci bir değer döndüren tek bir ifadeden oluşuyorsa veya `set` erişimci basit bir atama gerçekleştirdiğinde, Dizin Oluşturucu ve erişimciler ifade gövdesi tanımlarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="0be2b-151">Like with properties, indexer `get` and `set` accessors consist of expression body definitions if the `get` accessor consists of a single expression that returns a value or the `set` accessor performs a simple assignment.</span></span>

<span data-ttu-id="0be2b-152">Aşağıdaki örnek adlı bir sınıfı tanımlar `Sports` . Bu, bir dizi <xref:System.String> spor adını içeren bir iç dizi içerir.</span><span class="sxs-lookup"><span data-stu-id="0be2b-152">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="0be2b-153">Dizin Oluşturucu `get` ve `set` erişimciler, ifade gövdesi tanımları olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0be2b-153">Both the indexer `get` and `set` accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

<span data-ttu-id="0be2b-154">Daha fazla bilgi için bkz. [Dizin oluşturucular (C# Programlama Kılavuzu)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="0be2b-154">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>
