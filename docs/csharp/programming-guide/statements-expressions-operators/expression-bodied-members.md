---
title: İfade gövdeli üyeler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7c282157639a6a60270ce8dbebbc91dd0e0a3f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61709997"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="8afee-102">İfade gövdeli üyeler (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8afee-102">Expression-bodied members (C# programming guide)</span></span>

<span data-ttu-id="8afee-103">İfade gövdesi tanımları çok kısa, okunabilir bir form uygulamasında bir üyenin sağlamanıza izin veren.</span><span class="sxs-lookup"><span data-stu-id="8afee-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="8afee-104">Mantığı herhangi bir yöntemi veya özelliği gibi desteklenen bir üyesi için tek bir ifadeye oluşur. her bir deyim gövdesi tanımına kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8afee-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="8afee-105">Bir ifade gövdesi tanımına genel sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8afee-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="8afee-106">Burada *ifade* geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="8afee-106">where *expression* is a valid expression.</span></span>

<span data-ttu-id="8afee-107">Yöntem ve salt okunur özellikler için ifade gövdesi tanımları için destek sunulmuştur C# 6 ve içinde genişletilmiş C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="8afee-107">Support for expression body definitions was introduced for methods and read-only properties in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="8afee-108">İfade gövdesi tanımları, aşağıdaki tabloda listelenen tür üyeleri birlikte kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="8afee-108">Expression body definitions can be used with the type members listed in the following table:</span></span>

|<span data-ttu-id="8afee-109">Üye</span><span class="sxs-lookup"><span data-stu-id="8afee-109">Member</span></span>  |<span data-ttu-id="8afee-110">Sürümünden desteklenen...</span><span class="sxs-lookup"><span data-stu-id="8afee-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="8afee-111">Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8afee-111">Method</span></span>](#methods)  |<span data-ttu-id="8afee-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="8afee-112">C# 6</span></span> |
|[<span data-ttu-id="8afee-113">Salt okunur özelliği</span><span class="sxs-lookup"><span data-stu-id="8afee-113">Read-only property</span></span>](#read-only-properties)   |<span data-ttu-id="8afee-114">C# 6</span><span class="sxs-lookup"><span data-stu-id="8afee-114">C# 6</span></span>  |
|[<span data-ttu-id="8afee-115">Özelliği</span><span class="sxs-lookup"><span data-stu-id="8afee-115">Property</span></span>](#properties)  |<span data-ttu-id="8afee-116">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="8afee-116">C# 7.0</span></span> |
|[<span data-ttu-id="8afee-117">Oluşturucusu</span><span class="sxs-lookup"><span data-stu-id="8afee-117">Constructor</span></span>](#constructors)   |<span data-ttu-id="8afee-118">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="8afee-118">C# 7.0</span></span> |
|[<span data-ttu-id="8afee-119">Sonlandırıcı</span><span class="sxs-lookup"><span data-stu-id="8afee-119">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="8afee-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="8afee-120">C# 7.0</span></span> |
|[<span data-ttu-id="8afee-121">Dizin Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="8afee-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="8afee-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="8afee-122">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="8afee-123">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8afee-123">Methods</span></span>

<span data-ttu-id="8afee-124">Bir ifade gövdeli yöntem türü yöntemin dönüş türü ile eşleşen bir değer döndüren tek bir ifade ya da, döndüren yöntemler oluşur `void`, olan bazı işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8afee-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="8afee-125">Örneğin, bu geçersiz kılma türleri <xref:System.Object.ToString%2A> yöntemi genellikle geçerli nesnenin dize gösterimini döndürür, tek bir ifade içerir.</span><span class="sxs-lookup"><span data-stu-id="8afee-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span>

<span data-ttu-id="8afee-126">Aşağıdaki örnekte tanımlayan bir `Person` kılan sınıf <xref:System.Object.ToString%2A> yöntemi bir deyim gövdesi tanımına sahip.</span><span class="sxs-lookup"><span data-stu-id="8afee-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="8afee-127">Ayrıca tanımlar bir `DisplayName` adını konsolda görüntüler yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8afee-127">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="8afee-128">Unutmayın `return` anahtar sözcüğü kullanılan değil `ToString` ifade gövdesi tanımı.</span><span class="sxs-lookup"><span data-stu-id="8afee-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="8afee-129">Daha fazla bilgi için [yöntemler (C# programlama Kılavuzu)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="8afee-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>

## <a name="read-only-properties"></a><span data-ttu-id="8afee-130">Salt okunur özellikler</span><span class="sxs-lookup"><span data-stu-id="8afee-130">Read-only properties</span></span>

<span data-ttu-id="8afee-131">İle başlayarak C# 6, salt okunur özelliği uygulamak için ifade gövdesi tanımına kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8afee-131">Starting with C# 6, you can use expression body definition to implement a read-only property.</span></span> <span data-ttu-id="8afee-132">Bunu yapmak için aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="8afee-132">To do that, use the following syntax:</span></span>

```csharp
PropertyType PropertyName => expression;
```

<span data-ttu-id="8afee-133">Aşağıdaki örnekte tanımlayan bir `Location` sınıfının salt okunur `Name` özel değerini döndüren bir ifade gövdesi tanımını olarak gerçekleştirilen özellik `locationName` alan:</span><span class="sxs-lookup"><span data-stu-id="8afee-133">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field:</span></span>

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="8afee-134">Özellikleri hakkında daha fazla bilgi için bkz. [özellikleri (C# Programlama Kılavuzu)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="8afee-134">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="properties"></a><span data-ttu-id="8afee-135">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8afee-135">Properties</span></span>

<span data-ttu-id="8afee-136">İle başlayarak C# 7.0 özelliği uygulamak için ifade gövdesi tanımları kullanabilirsiniz `get` ve `set` erişimcileri.</span><span class="sxs-lookup"><span data-stu-id="8afee-136">Starting with C# 7.0, you can use expression body definitions to implement property `get` and `set` accessors.</span></span> <span data-ttu-id="8afee-137">Aşağıdaki örnek bunu nasıl yapacağınız gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8afee-137">The following example demonstrates how to do that:</span></span>

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

<span data-ttu-id="8afee-138">Özellikleri hakkında daha fazla bilgi için bkz. [özellikleri (C# Programlama Kılavuzu)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="8afee-138">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="constructors"></a><span data-ttu-id="8afee-139">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="8afee-139">Constructors</span></span>

<span data-ttu-id="8afee-140">Bir oluşturucu için bir ifade gövdesi tanımına, genellikle tek bir atama ifadesi veya Oluşturucunun bağımsız değişkenleri işleme veya örnek durumu başlatan bir yöntem çağrısı oluşur.</span><span class="sxs-lookup"><span data-stu-id="8afee-140">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span>

<span data-ttu-id="8afee-141">Aşağıdaki örnekte tanımlayan bir `Location` sınıfı, Oluşturucusu olan tek bir dize parametresi adlı *adı*.</span><span class="sxs-lookup"><span data-stu-id="8afee-141">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="8afee-142">Bağımsız değişkeni için ifade gövdesi tanımına atar `Name` özelliği.</span><span class="sxs-lookup"><span data-stu-id="8afee-142">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="8afee-143">Daha fazla bilgi için [oluşturucular (C# programlama Kılavuzu)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="8afee-143">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="8afee-144">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="8afee-144">Finalizers</span></span>

<span data-ttu-id="8afee-145">Bir sonlandırıcı için ifade gövdesi tanımına, genellikle, yönetilmeyen kaynakları serbest deyimleri gibi temizleme ifadeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="8afee-145">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="8afee-146">Aşağıdaki örnek, sonlandırıcı adı belirtmek için bir ifade gövdesi tanımı kullanan bir sonlandırıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8afee-146">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="8afee-147">Daha fazla bilgi için [sonlandırıcılar (C# programlama Kılavuzu)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="8afee-147">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="8afee-148">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="8afee-148">Indexers</span></span>

<span data-ttu-id="8afee-149">Özellikleri gibi bir oluşturucunun get ve set erişimcileri değer döndüren tek bir deyimde get erişimcisinin oluşur veya set erişimcisi basit atama gerçekleştirir ifade gövdesi tanımlarını oluşur.</span><span class="sxs-lookup"><span data-stu-id="8afee-149">Like properties, an indexer's get and set accessors consist of expression body definitions if the get accessor consists of a single statement that returns a value or the set accessor performs a simple assignment.</span></span>

<span data-ttu-id="8afee-150">Aşağıdaki örnek adlı bir sınıf tanımlar `Sports` bir iç içeren <xref:System.String> Spor sayısını adlarını içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="8afee-150">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="8afee-151">İfade gövdesi tanımlarla hem oluşturucunun get ve set erişimcileri uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8afee-151">Both the indexer's get and set accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

<span data-ttu-id="8afee-152">Daha fazla bilgi için [dizin oluşturucular (C# programlama Kılavuzu)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="8afee-152">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>
