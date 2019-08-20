---
title: Değişken genel arabirimler (C#) oluşturma
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: 4ba72f28cd2ddd800f169387cc2c742159d4cb1b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595312"
---
# <a name="creating-variant-generic-interfaces-c"></a><span data-ttu-id="9a456-102">Değişken genel arabirimler (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a456-102">Creating Variant Generic Interfaces (C#)</span></span>

<span data-ttu-id="9a456-103">Arabirimlerdeki genel tür parametrelerini birlikte değişken veya değişken karşıtı olarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a456-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="9a456-104">*Kovaryans* , Arabirim yöntemlerinin genel tür parametreleri tarafından tanımlananla daha fazla türetilmiş dönüş türüne sahip olmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="9a456-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="9a456-105">*Değişken varyans* , Arabirim yöntemlerinin genel parametreler tarafından belirtilenden daha az türetilmiş bağımsız değişken türlerine sahip olmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a456-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="9a456-106">Değişkenle birlikte değişken veya değişken karşıtı genel tür parametrelerine sahip genel bir arabirim *değişken*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="9a456-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>

> [!NOTE]
> <span data-ttu-id="9a456-107">.NET Framework 4, mevcut birçok genel arabirim için varyans desteği getirmiştir.</span><span class="sxs-lookup"><span data-stu-id="9a456-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="9a456-108">.NET Framework değişken arabirimlerinin listesi için bkz. [Genel Arabirimlerde VaryansC#()](./variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="9a456-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>

## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="9a456-109">VARIANT genel arabirimlerini bildirme</span><span class="sxs-lookup"><span data-stu-id="9a456-109">Declaring Variant Generic Interfaces</span></span>

<span data-ttu-id="9a456-110">Genel tür parametreleri için `in` ve `out` anahtar sözcüklerini kullanarak VARIANT genel arabirimleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a456-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a456-111">`ref`, `in`ve `out` içindeki C# parametreleri varyant olamaz.</span><span class="sxs-lookup"><span data-stu-id="9a456-111">`ref`, `in`, and `out` parameters in C# cannot be variant.</span></span> <span data-ttu-id="9a456-112">Değer türleri de varyansı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9a456-112">Value types also do not support variance.</span></span>

<span data-ttu-id="9a456-113">`out` Anahtar sözcüğünü kullanarak genel tür parametresi ortak değişkeni bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a456-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="9a456-114">Covaryant türü şu koşulları karşılamalıdır:</span><span class="sxs-lookup"><span data-stu-id="9a456-114">The covariant type must satisfy the following conditions:</span></span>

- <span data-ttu-id="9a456-115">Tür, yalnızca Arabirim yöntemlerinin dönüş türü olarak kullanılır ve Yöntem bağımsız değişkenlerinin türü olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="9a456-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="9a456-116">Bu, türünün `R` birlikte değişken olarak bildirildiği aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9a456-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    <span data-ttu-id="9a456-117">Bu kural için bir özel durum var.</span><span class="sxs-lookup"><span data-stu-id="9a456-117">There is one exception to this rule.</span></span> <span data-ttu-id="9a456-118">Bir yöntem parametresi olarak bir değişken karşıtı genel temsilciniz varsa, türü temsilci için genel bir tür parametresi olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a456-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="9a456-119">Bu, aşağıdaki örnekteki tür `R` tarafından gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9a456-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="9a456-120">Daha fazla bilgi için bkz. [temsilcilerin içindeki varyansC#()](./variance-in-delegates.md) ve [Func ve ACTION Genel Temsilciler (C#) için varyans kullanma](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="9a456-120">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        void DoSomething(Action<R> callback);
    }
    ```

- <span data-ttu-id="9a456-121">Tür, arabirim yöntemleri için genel bir kısıtlama olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="9a456-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="9a456-122">Bu, aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9a456-122">This is illustrated in the following code.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        // The following statement generates a compiler error
        // because you can use only contravariant or invariant types
        // in generic constraints.
        // void DoSomething<T>() where T : R;
    }
    ```

<span data-ttu-id="9a456-123">`in` Anahtar sözcüğünü kullanarak genel tür parametresi değişken karşıtı bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a456-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="9a456-124">Değişken karşıtı türü, Arabirim yöntemlerinin dönüş türü olarak değil, yalnızca Yöntem bağımsız değişkenlerinin türü olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9a456-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="9a456-125">Değişken karşıtı türü, genel kısıtlamalar için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9a456-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="9a456-126">Aşağıdaki kod, bir değişken karşıtı arabirimin nasıl bildirilemeyeceğini ve yöntemlerinden biri için genel bir kısıtlama nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a456-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

<span data-ttu-id="9a456-127">Ayrıca, aşağıdaki kod örneğinde gösterildiği gibi farklı tür parametreleri için aynı arabirimdeki kovaryansı ve değişken varyansı desteklemek de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9a456-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="9a456-128">VARIANT genel arabirimlerini uygulama</span><span class="sxs-lookup"><span data-stu-id="9a456-128">Implementing Variant Generic Interfaces</span></span>

<span data-ttu-id="9a456-129">Sabit arabirimler için kullanılan söz dizimini kullanarak sınıflarda VARIANT genel arabirimler uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a456-129">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="9a456-130">Aşağıdaki kod örneği, bir genel sınıfta birlikte değişken arabiriminin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a456-130">The following code example shows how to implement a covariant interface in a generic class.</span></span>

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

<span data-ttu-id="9a456-131">Varyant arabirimlerini uygulayan sınıflar sabit.</span><span class="sxs-lookup"><span data-stu-id="9a456-131">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="9a456-132">Örneğin, aşağıdaki kodu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="9a456-132">For example, consider the following code.</span></span>

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

## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="9a456-133">VARIANT genel arabirimlerini genişletme</span><span class="sxs-lookup"><span data-stu-id="9a456-133">Extending Variant Generic Interfaces</span></span>

<span data-ttu-id="9a456-134">Bir varyant genel arabirimini genişlettiğinizde, türetilmiş arabirimin varyansı destekleyip desteklemediğini açıkça belirtmek `in` için `out` ve anahtar sözcüklerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a456-134">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="9a456-135">Derleyici, genişletilmekte olan arabirimden varyansı çıkarmıyor.</span><span class="sxs-lookup"><span data-stu-id="9a456-135">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="9a456-136">Örneğin, aşağıdaki arabirimleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="9a456-136">For example, consider the following interfaces.</span></span>

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

<span data-ttu-id="9a456-137">Arabirimde, genel tür parametresi `T` değişmez, `IExtCovariant<out T>` ancak her iki arabirim de aynı arabirimi genişletse de, tür parametresinde birlikte değişken olur. `IInvariant<T>`</span><span class="sxs-lookup"><span data-stu-id="9a456-137">In the `IInvariant<T>` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant<out T>` the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="9a456-138">Aynı kural, değişken karşıtı genel tür parametrelerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9a456-138">The same rule is applied to contravariant generic type parameters.</span></span>

<span data-ttu-id="9a456-139">Hem genel tür parametresinin `T` birlikte değişken olduğu arabirimi hem de genişletme arabiriminde genel tür parametresi `T` sabit ise değişken karşıtı olan arabirimi genişleten bir arabirim oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a456-139">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="9a456-140">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9a456-140">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

<span data-ttu-id="9a456-141">Ancak, bir genel tür parametresi `T` bir arabirimde birlikte değişken olarak bildirilirse, genişletme arabiriminde bu değişken karşıtı olarak bildiremezsiniz veya tam tersi de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9a456-141">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="9a456-142">Bu, aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9a456-142">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a><span data-ttu-id="9a456-143">Belirsizlik önleme</span><span class="sxs-lookup"><span data-stu-id="9a456-143">Avoiding Ambiguity</span></span>

<span data-ttu-id="9a456-144">VARIANT genel arabirimleri uyguladığınızda, fark bazen belirsizliğe neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a456-144">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="9a456-145">Bunun kaçınılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a456-145">This should be avoided.</span></span>

<span data-ttu-id="9a456-146">Örneğin, tek bir sınıfta farklı genel tür parametreleriyle aynı Varyant genel arabirimini açıkça uygularsanız, belirsizlik oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="9a456-146">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="9a456-147">Derleyici bu durumda bir hata oluşturmaz, ancak çalışma zamanında hangi arabirim uygulamasının seçilme belirtilecektir.</span><span class="sxs-lookup"><span data-stu-id="9a456-147">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="9a456-148">Bu, kodunuzda hafif hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a456-148">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="9a456-149">Aşağıdaki kod örneğini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="9a456-149">Consider the following code example.</span></span>

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

<span data-ttu-id="9a456-150">Bu örnekte, `pets.GetEnumerator` yönteminin ve `Dog`arasında `Cat` nasıl seçtiği belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="9a456-150">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="9a456-151">Bu, kodunuzda sorun oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a456-151">This could cause problems in your code.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a456-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a456-152">See also</span></span>

- [<span data-ttu-id="9a456-153">Genel Arabirimlerde Varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="9a456-153">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
- [<span data-ttu-id="9a456-154">Func ve eylem genel temsilcileri için varyans kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="9a456-154">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
