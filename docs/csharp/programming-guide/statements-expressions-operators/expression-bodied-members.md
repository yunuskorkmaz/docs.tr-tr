---
title: İfade gövdeli üyeler - C# Programlama Kılavuzu
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: f212bb707d3dd2d4a7cc917d335a83cff01ed0cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711993"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="048c5-102">İfade gövdeli üyeler (C# programlama kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="048c5-102">Expression-bodied members (C# programming guide)</span></span>

<span data-ttu-id="048c5-103">İfade gövdesi tanımları, bir üyenin uygulamasını çok kısa ve okunabilir bir biçimde sağlamanıza izin sağlar.</span><span class="sxs-lookup"><span data-stu-id="048c5-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="048c5-104">Bir yöntem veya özellik gibi desteklenen herhangi bir üyenin mantığı tek bir ifadeden oluştuğunda bir ifade gövdesi tanımı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="048c5-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="048c5-105">Bir ifade gövdesi tanımı aşağıdaki genel sözdizimine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="048c5-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="048c5-106">*ifadenin* geçerli bir ifade olduğu yerde.</span><span class="sxs-lookup"><span data-stu-id="048c5-106">where *expression* is a valid expression.</span></span>

<span data-ttu-id="048c5-107">C# 6'daki yöntemler ve salt okunur özellikler için ifade gövdesi tanımları desteği tanıtıldı ve C# 7.0'da genişletildi.</span><span class="sxs-lookup"><span data-stu-id="048c5-107">Support for expression body definitions was introduced for methods and read-only properties in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="048c5-108">İfade gövdesi tanımları aşağıdaki tabloda listelenen tür üyeleri ile kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="048c5-108">Expression body definitions can be used with the type members listed in the following table:</span></span>

|<span data-ttu-id="048c5-109">Üye</span><span class="sxs-lookup"><span data-stu-id="048c5-109">Member</span></span>  |<span data-ttu-id="048c5-110">Itibariyle desteklenen ...</span><span class="sxs-lookup"><span data-stu-id="048c5-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="048c5-111">Yöntem</span><span class="sxs-lookup"><span data-stu-id="048c5-111">Method</span></span>](#methods)  |<span data-ttu-id="048c5-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="048c5-112">C# 6</span></span> |
|[<span data-ttu-id="048c5-113">Salt okunur özellik</span><span class="sxs-lookup"><span data-stu-id="048c5-113">Read-only property</span></span>](#read-only-properties)   |<span data-ttu-id="048c5-114">C# 6</span><span class="sxs-lookup"><span data-stu-id="048c5-114">C# 6</span></span>  |
|[<span data-ttu-id="048c5-115">Özellik</span><span class="sxs-lookup"><span data-stu-id="048c5-115">Property</span></span>](#properties)  |<span data-ttu-id="048c5-116">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="048c5-116">C# 7.0</span></span> |
|[<span data-ttu-id="048c5-117">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="048c5-117">Constructor</span></span>](#constructors)   |<span data-ttu-id="048c5-118">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="048c5-118">C# 7.0</span></span> |
|[<span data-ttu-id="048c5-119">Sonlandırıcıyı</span><span class="sxs-lookup"><span data-stu-id="048c5-119">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="048c5-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="048c5-120">C# 7.0</span></span> |
|[<span data-ttu-id="048c5-121">Dizin Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="048c5-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="048c5-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="048c5-122">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="048c5-123">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="048c5-123">Methods</span></span>

<span data-ttu-id="048c5-124">İfade gövdeli yöntem, türü yöntemin dönüş türüyle eşleşen bir değer döndüren veya bazı `void`işlemleri gerçekleştiren dönen yöntemler için tek bir ifadeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="048c5-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="048c5-125">Örneğin, <xref:System.Object.ToString%2A> yöntemi geçersiz kılınan türler genellikle geçerli nesnenin dize temsilini döndüren tek bir ifade içerir.</span><span class="sxs-lookup"><span data-stu-id="048c5-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span>

<span data-ttu-id="048c5-126">Aşağıdaki örnek, `Person` <xref:System.Object.ToString%2A> bir ifade gövdesi tanımı ile yöntemi geçersiz kılan bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="048c5-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="048c5-127">Ayrıca konsola `DisplayName` bir ad gösteren bir yöntem tanımlar.</span><span class="sxs-lookup"><span data-stu-id="048c5-127">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="048c5-128">Anahtar kelimenin `return` ifade gövdesi tanımında `ToString` kullanılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="048c5-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="048c5-129">Daha fazla bilgi için [Bkz. Yöntemler (C# Programlama Kılavuzu).](../classes-and-structs/methods.md)</span><span class="sxs-lookup"><span data-stu-id="048c5-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>

## <a name="read-only-properties"></a><span data-ttu-id="048c5-130">Salt okunur özellikler</span><span class="sxs-lookup"><span data-stu-id="048c5-130">Read-only properties</span></span>

<span data-ttu-id="048c5-131">C# 6 ile başlayarak, salt okunur özelliği uygulamak için ifade gövdesi tanımını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="048c5-131">Starting with C# 6, you can use expression body definition to implement a read-only property.</span></span> <span data-ttu-id="048c5-132">Bunu yapmak için aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="048c5-132">To do that, use the following syntax:</span></span>

```csharp
PropertyType PropertyName => expression;
```

<span data-ttu-id="048c5-133">Aşağıdaki örnekte, `Location` salt `Name` okunur özelliği özel `locationName` alanın değerini döndüren bir ifade gövdesi tanımı olarak uygulanan bir sınıf tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="048c5-133">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field:</span></span>

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="048c5-134">Özellikler hakkında daha fazla bilgi için [Özellikler (C# Programlama Kılavuzu)](../classes-and-structs/properties.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="048c5-134">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="properties"></a><span data-ttu-id="048c5-135">Özellikler</span><span class="sxs-lookup"><span data-stu-id="048c5-135">Properties</span></span>

<span data-ttu-id="048c5-136">C# 7.0 ile başlayarak, özellik `get` ve `set` erişimciuygulamak için ifade gövdesi tanımlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="048c5-136">Starting with C# 7.0, you can use expression body definitions to implement property `get` and `set` accessors.</span></span> <span data-ttu-id="048c5-137">Aşağıdaki örnek, bunun nasıl yapılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="048c5-137">The following example demonstrates how to do that:</span></span>

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

<span data-ttu-id="048c5-138">Özellikler hakkında daha fazla bilgi için [Özellikler (C# Programlama Kılavuzu)](../classes-and-structs/properties.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="048c5-138">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="constructors"></a><span data-ttu-id="048c5-139">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="048c5-139">Constructors</span></span>

<span data-ttu-id="048c5-140">Bir oluşturucu için bir ifade gövdesi tanımı genellikle tek bir atama ifadesi veya oluşturucunun bağımsız değişkenlerini işleyen veya örnek durumunu ilke açan bir yöntem çağrısından oluşur.</span><span class="sxs-lookup"><span data-stu-id="048c5-140">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span>

<span data-ttu-id="048c5-141">Aşağıdaki örnek, oluşturucu `Location` *adı*adlı tek bir dize parametresi olan bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="048c5-141">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="048c5-142">İfade gövdesi tanımı bağımsız değişkeni `Name` özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="048c5-142">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="048c5-143">Daha fazla bilgi için [Constructors (C# Programlama Kılavuzu)](../classes-and-structs/constructors.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="048c5-143">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="048c5-144">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="048c5-144">Finalizers</span></span>

<span data-ttu-id="048c5-145">Sonlandırıcı için bir ifade gövdesi tanımı genellikle yönetilmeyen kaynakları serbest bırakmak ifadeler gibi temizleme deyimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="048c5-145">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="048c5-146">Aşağıdaki örnek, sonlandırıcının çağrıldığını belirtmek için ifade gövdesi tanımını kullanan bir sonlandırıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="048c5-146">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="048c5-147">Daha fazla bilgi için [Finalizers (C# Programlama Kılavuzu)](../classes-and-structs/destructors.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="048c5-147">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="048c5-148">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="048c5-148">Indexers</span></span>

<span data-ttu-id="048c5-149">Özelliklerde olduğu gibi, `get` indeksleyici ve `set` erişimci, `get` erişimci bir değer döndüren tek `set` bir ifadeden oluşuyorsa veya erişimci basit bir atama gerçekleştiriyorsa ifade gövdesi tanımlarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="048c5-149">Like with properties, indexer `get` and `set` accessors consist of expression body definitions if the `get` accessor consists of a single expression that returns a value or the `set` accessor performs a simple assignment.</span></span>

<span data-ttu-id="048c5-150">Aşağıdaki örnek, bir dizi `Sports` sporun <xref:System.String> adlarını içeren dahili bir dizi içeren bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="048c5-150">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="048c5-151">Hem `get` dizinleyici `set` hem de erişime girenler ifade gövdesi tanımları olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="048c5-151">Both the indexer `get` and `set` accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

<span data-ttu-id="048c5-152">Daha fazla bilgi için [Bkz. Dizinleyiciler (C# Programlama Kılavuzu)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="048c5-152">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>
