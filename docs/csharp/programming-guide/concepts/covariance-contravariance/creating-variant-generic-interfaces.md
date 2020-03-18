---
title: Varyant Genel Arabirimler Oluşturma (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: 4ba72f28cd2ddd800f169387cc2c742159d4cb1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595312"
---
# <a name="creating-variant-generic-interfaces-c"></a><span data-ttu-id="c2e81-102">Varyant Genel Arabirimler Oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="c2e81-102">Creating Variant Generic Interfaces (C#)</span></span>

<span data-ttu-id="c2e81-103">Arabirimlerdeki genel tür parametrelerini ortak değişken veya zıt değişken olarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2e81-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="c2e81-104">*Covariance,* arabirim yöntemlerinin genel tür parametreleri tarafından tanımlanandan daha fazla türemiş iade türüne sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2e81-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="c2e81-105">*Kontravariance,* arabirim yöntemlerinin genel parametrelertarafından belirtilenden daha az türemiş bağımsız değişken türlerine sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2e81-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="c2e81-106">Ortak veya kontravariant genel tür parametrelerine sahip genel arabirim *varyant*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c2e81-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>

> [!NOTE]
> <span data-ttu-id="c2e81-107">.NET Framework 4, varolan birkaç genel arabirim için varyans desteği sundu.</span><span class="sxs-lookup"><span data-stu-id="c2e81-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="c2e81-108">.NET Framework'deki varyant arabirimlerinin listesi için [Genel Arabirimlerde Varyans (C#)](./variance-in-generic-interfaces.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c2e81-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>

## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="c2e81-109">Varyant Genel Arabirimleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="c2e81-109">Declaring Variant Generic Interfaces</span></span>

<span data-ttu-id="c2e81-110">Genel tür parametreleri için anahtar `in` `out` kelimeleri ve anahtar kelimeleri kullanarak varyant genel arabirimleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2e81-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c2e81-111">`ref`, `in`, `out` ve C# parametreleri varyant olamaz.</span><span class="sxs-lookup"><span data-stu-id="c2e81-111">`ref`, `in`, and `out` parameters in C# cannot be variant.</span></span> <span data-ttu-id="c2e81-112">Değer türleri de varyansı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c2e81-112">Value types also do not support variance.</span></span>

<span data-ttu-id="c2e81-113">Anahtar kelimeyi kullanarak genel bir tür `out` parametre eşdeğişkenini bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2e81-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="c2e81-114">Ortak varyant türü aşağıdaki koşulları karşılamalıdır:</span><span class="sxs-lookup"><span data-stu-id="c2e81-114">The covariant type must satisfy the following conditions:</span></span>

- <span data-ttu-id="c2e81-115">Tür yalnızca arabirim yöntemlerinin bir dönüş türü olarak kullanılır ve yöntem bağımsız değişkenleri türü olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="c2e81-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="c2e81-116">Bu, türün `R` eşdeğişken olarak ilan edildiği aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c2e81-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    <span data-ttu-id="c2e81-117">Bu kuralın bir istisnası vardır.</span><span class="sxs-lookup"><span data-stu-id="c2e81-117">There is one exception to this rule.</span></span> <span data-ttu-id="c2e81-118">Yöntem parametresi olarak karşıt genel temsilciniz varsa, temsilci için genel tür parametresi olarak türü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2e81-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="c2e81-119">Bu, aşağıdaki örnekteki türe `R` göre gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c2e81-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="c2e81-120">Daha fazla bilgi için, [Varyans In Delegates (C#)](./variance-in-delegates.md) ve [Func ve Action Generic Delegates (C#) için Varyans kullanma'ya](./using-variance-for-func-and-action-generic-delegates.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c2e81-120">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        void DoSomething(Action<R> callback);
    }
    ```

- <span data-ttu-id="c2e81-121">Tür, arabirim yöntemleri için genel bir kısıtlama olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="c2e81-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="c2e81-122">Bu, aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c2e81-122">This is illustrated in the following code.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        // The following statement generates a compiler error
        // because you can use only contravariant or invariant types
        // in generic constraints.
        // void DoSomething<T>() where T : R;
    }
    ```

<span data-ttu-id="c2e81-123">Anahtar kelimeyi kullanarak genel bir tür `in` parametre karşıtdeğişkenini bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2e81-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="c2e81-124">Karşıt tür, arabirim yöntemlerinin geri dönüş türü olarak değil, yalnızca yöntem bağımsız değişkenleri türü olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c2e81-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="c2e81-125">Karşıt değişken türü genel kısıtlamalar için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c2e81-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="c2e81-126">Aşağıdaki kod, karşıt arabirimi nasıl bildireceklerini ve yöntemlerinden biri için genel bir kısıtlamanın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2e81-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

<span data-ttu-id="c2e81-127">Aynı arabirimde hem covariance hem de contravariance'ı desteklemek de mümkündür, ancak aşağıdaki kod örneğinde gösterildiği gibi farklı tür parametreleri için.</span><span class="sxs-lookup"><span data-stu-id="c2e81-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="c2e81-128">Varyant Genel Arabirimlerin Uygulanması</span><span class="sxs-lookup"><span data-stu-id="c2e81-128">Implementing Variant Generic Interfaces</span></span>

<span data-ttu-id="c2e81-129">Değişmez arabirimler için kullanılan aynı sözdizimini kullanarak sınıflarda varyant genel arabirimleri uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="c2e81-129">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="c2e81-130">Aşağıdaki kod örneği, genel bir sınıfta bir ortak değişken arabiriminnasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2e81-130">The following code example shows how to implement a covariant interface in a generic class.</span></span>

```csharp
interface ICovariant<out R>
{
    R GetSomething();
}
class SampleImplementation<R> : ICovariant<R>
{
    public R GetSomething()
    {
        // Some code.
        return default(R);
    }
}
```

<span data-ttu-id="c2e81-131">Varyant arabirimlerini uygulayan sınıflar değişmez.</span><span class="sxs-lookup"><span data-stu-id="c2e81-131">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="c2e81-132">Örneğin, aşağıdaki kodu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c2e81-132">For example, consider the following code.</span></span>

```csharp
// The interface is covariant.
ICovariant<Button> ibutton = new SampleImplementation<Button>();
ICovariant<Object> iobj = ibutton;

// The class is invariant.
SampleImplementation<Button> button = new SampleImplementation<Button>();
// The following statement generates a compiler error
// because classes are invariant.
// SampleImplementation<Object> obj = button;
```

## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="c2e81-133">Varyant Genel Arabirimlerini Genişletme</span><span class="sxs-lookup"><span data-stu-id="c2e81-133">Extending Variant Generic Interfaces</span></span>

<span data-ttu-id="c2e81-134">Bir varyant genel arabirimi genişletdiğinizde, `in` türetilen arabirimin varyansı destekleyip desteklemediğini açıkça belirtmek için anahtar kelimeleri ve `out` anahtar kelimeleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2e81-134">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="c2e81-135">Derleyici, genişletilmekte olan arabirimden varyans çıkarmıyor.</span><span class="sxs-lookup"><span data-stu-id="c2e81-135">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="c2e81-136">Örneğin, aşağıdaki arabirimleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c2e81-136">For example, consider the following interfaces.</span></span>

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

<span data-ttu-id="c2e81-137">`IInvariant<T>` Arabirimde, genel tür `T` parametresi değişmez, `IExtCovariant<out T>` tür parametresi ise aynı arabirimde olsa da, tür parametresi birlikte değişmezdir.</span><span class="sxs-lookup"><span data-stu-id="c2e81-137">In the `IInvariant<T>` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant<out T>` the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="c2e81-138">Aynı kural, karşıt genel tip parametrelere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c2e81-138">The same rule is applied to contravariant generic type parameters.</span></span>

<span data-ttu-id="c2e81-139">Hem genel tür parametresinin `T` bir araya geldiği arabirimi hem de genişletme arabiriminde genel tür parametresi `T` değişmezse, karşıt olduğu arabirimi genişleten bir arabirim oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2e81-139">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="c2e81-140">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c2e81-140">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

<span data-ttu-id="c2e81-141">Ancak, genel bir tür `T` parametresi tek bir arabirimde eşdeğişken olarak bildirilirse, bunu genişletme arabiriminde karşıt değişken olarak beyan edemezsiniz veya tam tersi.</span><span class="sxs-lookup"><span data-stu-id="c2e81-141">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="c2e81-142">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c2e81-142">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a><span data-ttu-id="c2e81-143">Belirsizlikten Kaçınma</span><span class="sxs-lookup"><span data-stu-id="c2e81-143">Avoiding Ambiguity</span></span>

<span data-ttu-id="c2e81-144">Varyant genel arabirimleri uyguladığınız zaman, varyans bazen belirsizliğe yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="c2e81-144">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="c2e81-145">Bu kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c2e81-145">This should be avoided.</span></span>

<span data-ttu-id="c2e81-146">Örneğin, bir sınıfta farklı genel tür parametreleri ile aynı varyant genel arabirimi açıkça uygularsanız, belirsizlik oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2e81-146">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="c2e81-147">Derleyici bu durumda bir hata üretmez, ancak çalışma zamanında hangi arabirim uygulamasının seçileceği belirtilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="c2e81-147">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="c2e81-148">Bu, kodunuzda ince hatalara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="c2e81-148">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="c2e81-149">Aşağıdaki kod örneğini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="c2e81-149">Consider the following code example.</span></span>

```csharp
// Simple class hierarchy.
class Animal { }
class Cat : Animal { }
class Dog : Animal { }

// This class introduces ambiguity
// because IEnumerable<out T> is covariant.
class Pets : IEnumerable<Cat>, IEnumerable<Dog>
{
    IEnumerator<Cat> IEnumerable<Cat>.GetEnumerator()
    {
        Console.WriteLine("Cat");
        // Some code.
        return null;
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        // Some code.
        return null;
    }

    IEnumerator<Dog> IEnumerable<Dog>.GetEnumerator()
    {
        Console.WriteLine("Dog");
        // Some code.
        return null;
    }
}
class Program
{
    public static void Test()
    {
        IEnumerable<Animal> pets = new Pets();
        pets.GetEnumerator();
    }
}
```

<span data-ttu-id="c2e81-150">Bu örnekte, yöntemin `pets.GetEnumerator` ve `Cat` . `Dog`</span><span class="sxs-lookup"><span data-stu-id="c2e81-150">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="c2e81-151">Bu, kodunuzda sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c2e81-151">This could cause problems in your code.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2e81-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2e81-152">See also</span></span>

- [<span data-ttu-id="c2e81-153">Genel Arabirimlerde Varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="c2e81-153">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
- [<span data-ttu-id="c2e81-154">Func ve Action Generic Delegeler için Varyans Kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="c2e81-154">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
