---
title: İfade gövdeli üyeler (C# programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e58afadae78d3f6b15a8e859edc8d554d84c393
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42911912"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="ca1fb-102">İfade gövdeli üyeler (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ca1fb-102">Expression-bodied members (C# programming guide)</span></span>
<span data-ttu-id="ca1fb-103">İfade gövdesi tanımları çok kısa, okunabilir bir form uygulamasında bir üyenin sağlamanıza izin veren.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="ca1fb-104">Mantığı herhangi bir yöntemi veya özelliği gibi desteklenen bir üyesi için tek bir ifadeye oluşur. her bir deyim gövdesi tanımına kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="ca1fb-105">Bir ifade gövdesi tanımına genel sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ca1fb-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="ca1fb-106">Burada *ifade* geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-106">where *expression* is a valid expression.</span></span> 

<span data-ttu-id="ca1fb-107">Yöntemleri için ifade gövdesi tanımları için destek eklenmiştir ve özellik erişimcileri, C# 6'da Al ve C# 7.0 genişletildi.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-107">Support for expression body definitions was introduced for methods and property get accessors in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="ca1fb-108">İfade gövdesi tanımları, aşağıdaki tabloda listelenen tür üyeleri birlikte kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="ca1fb-108">Expression body definitions can be used with the type members listed in the following table:</span></span> 

|<span data-ttu-id="ca1fb-109">Üye</span><span class="sxs-lookup"><span data-stu-id="ca1fb-109">Member</span></span>  |<span data-ttu-id="ca1fb-110">Sürümünden desteklenen...</span><span class="sxs-lookup"><span data-stu-id="ca1fb-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="ca1fb-111">Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca1fb-111">Method</span></span>](#methods)  |<span data-ttu-id="ca1fb-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="ca1fb-112">C# 6</span></span> |
|[<span data-ttu-id="ca1fb-113">Oluşturucusu</span><span class="sxs-lookup"><span data-stu-id="ca1fb-113">Constructor</span></span>](#constructors)   |<span data-ttu-id="ca1fb-114">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="ca1fb-114">C# 7.0</span></span> |
|[<span data-ttu-id="ca1fb-115">Sonlandırıcı</span><span class="sxs-lookup"><span data-stu-id="ca1fb-115">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="ca1fb-116">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="ca1fb-116">C# 7.0</span></span> |
|[<span data-ttu-id="ca1fb-117">Özellik Al</span><span class="sxs-lookup"><span data-stu-id="ca1fb-117">Property Get</span></span>](#property-get-statements)  |<span data-ttu-id="ca1fb-118">C# 6</span><span class="sxs-lookup"><span data-stu-id="ca1fb-118">C# 6</span></span> |
|[<span data-ttu-id="ca1fb-119">Özellik kümesi</span><span class="sxs-lookup"><span data-stu-id="ca1fb-119">Property Set</span></span>](#property-set-statements)  |<span data-ttu-id="ca1fb-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="ca1fb-120">C# 7.0</span></span> |
|[<span data-ttu-id="ca1fb-121">Dizin Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="ca1fb-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="ca1fb-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="ca1fb-122">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="ca1fb-123">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ca1fb-123">Methods</span></span>

<span data-ttu-id="ca1fb-124">Bir ifade gövdeli yöntem türü yöntemin dönüş türü ile eşleşen bir değer döndüren tek bir ifade ya da, döndüren yöntemler oluşur `void`, olan bazı işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="ca1fb-125">Örneğin, bu geçersiz kılma türleri <xref:System.Object.ToString%2A> yöntemi genellikle geçerli nesnenin dize gösterimini döndürür, tek bir ifade içerir.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span> 

<span data-ttu-id="ca1fb-126">Aşağıdaki örnekte tanımlayan bir `Person` kılan sınıf <xref:System.Object.ToString%2A> yöntemi bir deyim gövdesi tanımına sahip.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="ca1fb-127">Ayrıca tanımlar bir `DisplayName` adını konsolda görüntüler yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-127">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="ca1fb-128">Unutmayın `return` anahtar sözcüğü kullanılan değil `ToString` ifade gövdesi tanımı.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="ca1fb-129">Daha fazla bilgi için [yöntemler (C# programlama Kılavuzu)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="ca1fb-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>
 
## <a name="constructors"></a><span data-ttu-id="ca1fb-130">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="ca1fb-130">Constructors</span></span>

<span data-ttu-id="ca1fb-131">Bir oluşturucu için bir ifade gövdesi tanımına, genellikle tek bir atama ifadesi veya Oluşturucunun bağımsız değişkenleri işleme veya örnek durumu başlatan bir yöntem çağrısı oluşur.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-131">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span> 

<span data-ttu-id="ca1fb-132">Aşağıdaki örnekte tanımlayan bir `Location` sınıfı, Oluşturucusu olan tek bir dize parametresi adlı *adı*.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-132">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="ca1fb-133">Bağımsız değişkeni için ifade gövdesi tanımına atar `Name` özelliği.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-133">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="ca1fb-134">Daha fazla bilgi için [oluşturucular (C# programlama Kılavuzu)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="ca1fb-134">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="ca1fb-135">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="ca1fb-135">Finalizers</span></span>

<span data-ttu-id="ca1fb-136">Bir sonlandırıcı için ifade gövdesi tanımına, genellikle, yönetilmeyen kaynakları serbest deyimleri gibi temizleme ifadeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-136">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="ca1fb-137">Aşağıdaki örnek, sonlandırıcı adı belirtmek için bir ifade gövdesi tanımı kullanan bir sonlandırıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-137">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="ca1fb-138">Daha fazla bilgi için [sonlandırıcılar (C# programlama Kılavuzu)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="ca1fb-138">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="property-get-statements"></a><span data-ttu-id="ca1fb-139">Özellik get deyimleri</span><span class="sxs-lookup"><span data-stu-id="ca1fb-139">Property get statements</span></span>

<span data-ttu-id="ca1fb-140">Uygulamak seçerseniz bir alma erişimcisi kendiniz, özellik değeri yalnızca döndüren tek ifadeler için bir ifade gövdesi tanımına kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-140">If you choose to implement a property get accessor yourself, you can use an expression body definition for single expressions that simply return the property value.</span></span> <span data-ttu-id="ca1fb-141">Unutmayın `return` deyimi kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-141">Note that the `return` statement isn't used.</span></span>

<span data-ttu-id="ca1fb-142">Aşağıdaki örnekte tanımlayan bir `Location.Name` özelliği olan özellik get erişimcisi özel değerini döndürür `locationName` özelliği yedekleyen alan.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-142">The following example defines a `Location.Name` property whose property get accessor returns the value of the private `locationName` field that backs the property.</span></span> 

[!code-csharp[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="ca1fb-143">Bir ifade gövdesi tanımına kullanan salt okunur özellikler uygulanabilir açık bir `set` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-143">Read-only properties that use an expression body definition can be implemented without an explicit `set` statement.</span></span> <span data-ttu-id="ca1fb-144">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="ca1fb-144">The syntax is:</span></span>

```csharp
PropertyName => returnValue;
```

<span data-ttu-id="ca1fb-145">Aşağıdaki örnekte tanımlayan bir `Location` sınıfının salt okunur `Name` özel değerini döndüren bir ifade gövdesi tanımını olarak gerçekleştirilen özellik `locationName` alan.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-145">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="ca1fb-146">Daha fazla bilgi için [özellikler (C# programlama Kılavuzu)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="ca1fb-146">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="property-set-statements"></a><span data-ttu-id="ca1fb-147">Özellik kümesi ifadeleri</span><span class="sxs-lookup"><span data-stu-id="ca1fb-147">Property set statements</span></span>

<span data-ttu-id="ca1fb-148">Bir özellik kümesi erişimcisi kendi başınıza uygulamak isterseniz, özelliği yedekleyen alana değer atayan bir tek satır ifadesi için bir ifade gövdesi tanımına kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-148">If you choose to implement a property set accessor yourself, you can use an expression body definition for a single-line expression that assigns a value to the field that backs the property.</span></span>

<span data-ttu-id="ca1fb-149">Aşağıdaki örnekte tanımlayan bir `Location.Name` özelliği, özelliği ayarlanmış deyimi, giriş bağımsız değişkeni özel atar `locationName` özelliği yedekleyen alan.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-149">The following example defines a `Location.Name` property whose property set statement assigns its input argument to the private `locationName` field that backs the property.</span></span>

[!code-csharp[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="ca1fb-150">Daha fazla bilgi için [özellikler (C# programlama Kılavuzu)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="ca1fb-150">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="ca1fb-151">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="ca1fb-151">Indexers</span></span>

<span data-ttu-id="ca1fb-152">Özellikleri gibi bir oluşturucunun get ve set erişimcileri değer döndüren tek bir deyimde get erişimcisinin oluşur veya set erişimcisi basit atama gerçekleştirir ifade gövdesi tanımlarını oluşur.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-152">Like properties, an indexer's get and set accessors consist of expression body definitions if the get accessor consists of a single statement that returns a value or the set accessor performs a simple assignment.</span></span>

<span data-ttu-id="ca1fb-153">Aşağıdaki örnek adlı bir sınıf tanımlar `Sports` bir iç içeren <xref:System.String> Spor sayısını adlarını içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-153">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="ca1fb-154">İfade gövdesi tanımlarla hem oluşturucunun get ve set erişimcileri uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ca1fb-154">Both the indexer's get and set accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)] 

<span data-ttu-id="ca1fb-155">Daha fazla bilgi için [dizin oluşturucular (C# programlama Kılavuzu)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="ca1fb-155">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>

