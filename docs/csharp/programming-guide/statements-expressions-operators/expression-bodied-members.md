---
title: İfade bodied üyeleri (C# programlama Kılavuzu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5690a2ddb9127bb0c9b06d3607e3d105fca9a2e8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="424a6-102">İfade bodied üyeleri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="424a6-102">Expression-bodied members (C# programming guide)</span></span>
<span data-ttu-id="424a6-103">İfade gövdesi tanımları çok kısa, okunabilir bir form bir üyenin uygulamasında sağlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="424a6-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="424a6-104">Tek bir ifade yöntemi veya özelliği gibi herhangi bir desteklenen üyesi mantığını oluşur her bir ifade gövdesi tanımı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="424a6-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="424a6-105">Bir ifade gövdesi tanımı genel sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="424a6-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="424a6-106">Burada *ifade* geçerli bir ifade değil.</span><span class="sxs-lookup"><span data-stu-id="424a6-106">where *expression* is a valid expression.</span></span> 

<span data-ttu-id="424a6-107">İfade gövdesi tanımları için destek yöntemleri için sunulmuştur ve özellik get Erişimciler C# 6've C# 7. 0'genişletildi.</span><span class="sxs-lookup"><span data-stu-id="424a6-107">Support for expression body definitions was introduced for methods and property get accessors in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="424a6-108">İfade gövdesi tanımları, aşağıdaki tabloda listelenen tür üyeleri ile birlikte kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="424a6-108">Expression body definitions can be used with the type members listed in the following table:</span></span> 

|<span data-ttu-id="424a6-109">Üye</span><span class="sxs-lookup"><span data-stu-id="424a6-109">Member</span></span>  |<span data-ttu-id="424a6-110">Sürümünden itibaren desteklenen...</span><span class="sxs-lookup"><span data-stu-id="424a6-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="424a6-111">Yöntemi</span><span class="sxs-lookup"><span data-stu-id="424a6-111">Method</span></span>](#methods)  |<span data-ttu-id="424a6-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="424a6-112">C# 6</span></span> |
|[<span data-ttu-id="424a6-113">Oluşturucusu</span><span class="sxs-lookup"><span data-stu-id="424a6-113">Constructor</span></span>](#constructors)   |<span data-ttu-id="424a6-114">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="424a6-114">C# 7.0</span></span> |
|[<span data-ttu-id="424a6-115">Sonlandırıcı</span><span class="sxs-lookup"><span data-stu-id="424a6-115">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="424a6-116">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="424a6-116">C# 7.0</span></span> |
|[<span data-ttu-id="424a6-117">Özellik Get</span><span class="sxs-lookup"><span data-stu-id="424a6-117">Property Get</span></span>](#property-get-statements)  |<span data-ttu-id="424a6-118">C# 6</span><span class="sxs-lookup"><span data-stu-id="424a6-118">C# 6</span></span> |
|[<span data-ttu-id="424a6-119">Özellik kümesi</span><span class="sxs-lookup"><span data-stu-id="424a6-119">Property Set</span></span>](#property-set-statements)  |<span data-ttu-id="424a6-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="424a6-120">C# 7.0</span></span> |
|[<span data-ttu-id="424a6-121">Dizin Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="424a6-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="424a6-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="424a6-122">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="424a6-123">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="424a6-123">Methods</span></span>

<span data-ttu-id="424a6-124">Tek bir ifade türü yöntemin dönüş türü ile eşleşen bir değeri döndürür veya, döndüren yöntemler için bir ifade bodied yöntemi oluşur `void`, bazı işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="424a6-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="424a6-125">Örneğin, bu geçersiz kılma türleri <xref:System.Object.ToString%2A> yöntemi genellikle geçerli nesnenin dize gösterimini döndürür tek bir ifade içerir.</span><span class="sxs-lookup"><span data-stu-id="424a6-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span> 

<span data-ttu-id="424a6-126">Aşağıdaki örnek tanımlayan bir `Person` geçersiz kılmaları sınıf <xref:System.Object.ToString%2A> bir ifade gövdesi tanımıyla yöntemi.</span><span class="sxs-lookup"><span data-stu-id="424a6-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="424a6-127">Ayrıca tanımlayan bir `Show` bir ad konsola görüntüler yöntemi.</span><span class="sxs-lookup"><span data-stu-id="424a6-127">It also defines a `Show` method that displays a name to the console.</span></span> <span data-ttu-id="424a6-128">Unutmayın `return` anahtar sözcüğü kullanılan değil `ToString` ifade gövdesi tanımı.</span><span class="sxs-lookup"><span data-stu-id="424a6-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="424a6-129">Daha fazla bilgi için bkz: [yöntemler (C# programlama Kılavuzu)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="424a6-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>
 
## <a name="constructors"></a><span data-ttu-id="424a6-130">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="424a6-130">Constructors</span></span>

<span data-ttu-id="424a6-131">Bir oluşturucu için bir ifade gövdesi tanımı genellikle tek bir atama ifadesi veya Oluşturucusu'nın bağımsız değişkenleri işleme veya örnek durum başlatır yöntem çağrısı oluşur.</span><span class="sxs-lookup"><span data-stu-id="424a6-131">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span> 

<span data-ttu-id="424a6-132">Aşağıdaki örnek tanımlayan bir `Location` sınıfı, bir oluşturucuya sahip tek bir dize adlı parametre *adı*.</span><span class="sxs-lookup"><span data-stu-id="424a6-132">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="424a6-133">Bağımsız değişkeni ifadesi gövde tanımı atar `Name` özelliği.</span><span class="sxs-lookup"><span data-stu-id="424a6-133">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="424a6-134">Daha fazla bilgi için bkz: [oluşturucular (C# programlama Kılavuzu)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="424a6-134">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="424a6-135">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="424a6-135">Finalizers</span></span>

<span data-ttu-id="424a6-136">Bir sonlandırıcı için bir ifade gövdesi tanımı genellikle, yönetilmeyen kaynakları serbest deyimleri gibi temizleme ifadeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="424a6-136">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="424a6-137">Aşağıdaki örnek, sonlandırıcıyı çağrıldı belirtmek için bir ifade gövdesi tanımını kullanan bir sonlandırıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="424a6-137">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="424a6-138">Daha fazla bilgi için bkz: [sonlandırıcılar (C# programlama Kılavuzu)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="424a6-138">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="property-get-statements"></a><span data-ttu-id="424a6-139">Özellik get deyimleri</span><span class="sxs-lookup"><span data-stu-id="424a6-139">Property get statements</span></span>

<span data-ttu-id="424a6-140">Uygulamak isterseniz bir özellik get erişimcisi kendiniz, bir ifade gövdesi tanımı yalnızca özellik değeri döndüren tek ifadeler için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="424a6-140">If you choose to implement a property get accessor yourself, you can use an expression body definition for single expressions that simply return the property value.</span></span> <span data-ttu-id="424a6-141">Unutmayın `return` değil deyimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="424a6-141">Note that the `return` statement isn't used.</span></span>

<span data-ttu-id="424a6-142">Aşağıdaki örnek tanımlayan bir `Location.Name` özelliği, özellik get erişimcisi özel değerini döndürür `locationName` özelliği yedekler alan.</span><span class="sxs-lookup"><span data-stu-id="424a6-142">The following example defines a `Location.Name` property whose property get accessor returns the value of the private `locationName` field that backs the property.</span></span> 

[!code-csharp[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="424a6-143">Bir ifade gövdesi tanımı kullanmak salt okunur özellikler uygulanabilir açık bir `set` deyimi.</span><span class="sxs-lookup"><span data-stu-id="424a6-143">Read-only properties that use an expression body definition can be implemented without an explicit `set` statement.</span></span> <span data-ttu-id="424a6-144">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="424a6-144">The syntax is:</span></span>

```csharp
PropertyName => returnValue;
```

<span data-ttu-id="424a6-145">Aşağıdaki örnek tanımlayan bir `Location` sınıfının salt okunur `Name` özelliği özel değerini döndüren bir ifade gövdesi tanımı olarak uygulanan `locationName` alan.</span><span class="sxs-lookup"><span data-stu-id="424a6-145">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="424a6-146">Daha fazla bilgi için bkz: [özellikler (C# programlama Kılavuzu)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="424a6-146">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="property-set-statements"></a><span data-ttu-id="424a6-147">Özellik set deyimleri</span><span class="sxs-lookup"><span data-stu-id="424a6-147">Property set statements</span></span>

<span data-ttu-id="424a6-148">Bir özellik set erişimcisi kendiniz uygulamak isterseniz özelliği yedekler alan için değer atayan bir tek satırlı deyim için bir ifade gövdesi tanımı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="424a6-148">If you choose to implement a property set accessor yourself, you can use an expression body definition for a single-line expression that assigns a value to the field that backs the property.</span></span>

<span data-ttu-id="424a6-149">Aşağıdaki örnek tanımlayan bir `Location.Name` özelliği, özelliği ayarlanmış deyimi özel kendi giriş bağımsız değişkenine atar `locationName` özelliği yedekler alan.</span><span class="sxs-lookup"><span data-stu-id="424a6-149">The following example defines a `Location.Name` property whose property set statement assigns its input argument to the private `locationName` field that backs the property.</span></span>

[!code-csharp[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="424a6-150">Daha fazla bilgi için bkz: [özellikler (C# programlama Kılavuzu)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="424a6-150">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="424a6-151">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="424a6-151">Indexers</span></span>

<span data-ttu-id="424a6-152">Özellikler gibi bir oluşturucunun get ve set erişimcileri get erişimcisine bir değer döndüren bir tek deyiminden oluşan ya da basit atama set erişimcisine gerçekleştirir ifade gövdesi tanımlarını oluşur.</span><span class="sxs-lookup"><span data-stu-id="424a6-152">Like properties, an indexer's get and set accessors consist of expression body definitions if the get accessor consists of a single statement that returns a value or the set accessor performs a simple assignment.</span></span>

<span data-ttu-id="424a6-153">Aşağıdaki örnek adlı bir sınıf tanımlar `Sports` iç içeren <xref:System.String> Spor sayısı adlarını içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="424a6-153">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="424a6-154">Oluşturucunun get ve set erişimcileri ifade gövdesi tanımları uygulanır.</span><span class="sxs-lookup"><span data-stu-id="424a6-154">Both the indexer's get and set accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)] 

<span data-ttu-id="424a6-155">Daha fazla bilgi için bkz: [dizin oluşturucular (C# programlama Kılavuzu)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="424a6-155">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>

