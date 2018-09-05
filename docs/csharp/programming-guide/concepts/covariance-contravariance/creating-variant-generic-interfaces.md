---
title: Değişken genel arabirimler oluşturma (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: d8e7e8a59aeff27531187e5171a76651440ffc4c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526913"
---
# <a name="creating-variant-generic-interfaces-c"></a><span data-ttu-id="df769-102">Değişken genel arabirimler oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="df769-102">Creating Variant Generic Interfaces (C#)</span></span>
<span data-ttu-id="df769-103">Genel Tür parametrelerine birlikte değişken olarak arabirimleri bildirebilir veya değişken karşıtı.</span><span class="sxs-lookup"><span data-stu-id="df769-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="df769-104">*Kovaryans* dönüş türleri genel tür parametreleri tarafından tanımlanan değerinden daha fazla türetilmiş arabirim yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="df769-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="df769-105">*Kontravaryans* genel parametreler tarafından belirtilenden daha az türetilmiş bağımsız değişken türleri arabirim yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="df769-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="df769-106">Birlikte değişken olan genel bir arabirim veya değişken karşıtı genel tür parametreleri çağrılır *değişken*.</span><span class="sxs-lookup"><span data-stu-id="df769-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df769-107">.NET framework 4, çeşitli genel arabirimlerin mevcut sapma desteği sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="df769-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="df769-108">.NET Framework'teki değişken arabirimler listesi için bkz. [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="df769-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="df769-109">Bildirim değişken genel arabirimler</span><span class="sxs-lookup"><span data-stu-id="df769-109">Declaring Variant Generic Interfaces</span></span>  
 <span data-ttu-id="df769-110">Değişken genel arabirimler kullanarak bildirebilirsiniz `in` ve `out` genel tür parametreleri için anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="df769-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="df769-111">`ref`, `in`, ve `out` C# parametrelerinde değişken olamaz.</span><span class="sxs-lookup"><span data-stu-id="df769-111">`ref`, `in`, and `out` parameters in C# cannot be variant.</span></span> <span data-ttu-id="df769-112">Değer türleri varyansı da desteklemez.</span><span class="sxs-lookup"><span data-stu-id="df769-112">Value types also do not support variance.</span></span>  
  
 <span data-ttu-id="df769-113">Genel tür parametresi birlikte değişken kullanarak bildirebilirsiniz `out` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="df769-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="df769-114">Birlikte değişen türde aşağıdaki koşulları karşılaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="df769-114">The covariant type must satisfy the following conditions:</span></span>  
  
-   <span data-ttu-id="df769-115">Türü yalnızca bir dönüş türü arabirim yöntemleri olarak kullanılan ve yöntem bağımsız bir türü olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="df769-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="df769-116">Bu, aşağıdaki örnekte gösterilmiştir türü `R` birlikte değişken olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="df769-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        R GetSomething();  
        // The following statement generates a compiler error.  
        // void SetSometing(R sampleArg);  
  
    }  
    ```  
  
     <span data-ttu-id="df769-117">Bu kuralın tek istisnası yoktur.</span><span class="sxs-lookup"><span data-stu-id="df769-117">There is one exception to this rule.</span></span> <span data-ttu-id="df769-118">Bir yöntem parametresi olarak bir değişken karşıtı Genel temsilci varsa, türü için temsilci genel tür parametre olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df769-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="df769-119">Bu tür tarafından gösterilmiştir `R` aşağıdaki örnekte.</span><span class="sxs-lookup"><span data-stu-id="df769-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="df769-120">Daha fazla bilgi için [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [işlev ve eylem genel temsilcileri (C#) kullanarak varyansını](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="df769-120">For more information, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        void DoSomething(Action<R> callback);  
    }  
    ```  
  
-   <span data-ttu-id="df769-121">Türü genel kısıtlama olarak arabirim yöntemleri için kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="df769-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="df769-122">Bu, aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="df769-122">This is illustrated in the following code.</span></span>  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        // The following statement generates a compiler error  
        // because you can use only contravariant or invariant types  
        // in generic contstraints.  
        // void DoSomething<T>() where T : R;  
    }  
    ```  
  
 <span data-ttu-id="df769-123">Bir genel tür parametresi değişken karşıtı kullanarak bildirebilirsiniz `in` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="df769-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="df769-124">Değişken karşıtı türü arabirim yöntemleri dönüş türü olarak değil de yalnızca bir tür yöntem bağımsız olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="df769-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="df769-125">Değişken karşıtı türü genel kısıtlamalar için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="df769-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="df769-126">Aşağıdaki kod, bir değişken karşıtı arabirimi bildirme ve bir genel kısıtlama yöntemlerinden biri için kullanma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="df769-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>  
  
```csharp  
interface IContravariant<in A>  
{  
    void SetSomething(A sampleArg);  
    void DoSomething<T>() where T : A;  
    // The following statement generates a compiler error.  
    // A GetSomething();              
}  
```  
  
 <span data-ttu-id="df769-127">Ayrıca aşağıdaki kod örneğinde gösterildiği gibi aynı arabirimi, ancak farklı türde parametreler için hem Kovaryans ve kontravaryans desteklemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="df769-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>  
  
```csharp  
interface IVariant<out R, in A>  
{  
    R GetSomething();  
    void SetSomething(A sampleArg);  
    R GetSetSometings(A sampleArg);  
}  
```  
  
## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="df769-128">Değişken genel arabirimler uygulama</span><span class="sxs-lookup"><span data-stu-id="df769-128">Implementing Variant Generic Interfaces</span></span>  
 <span data-ttu-id="df769-129">Değişken genel arabirimler sınıflarda sabit arabirimler için kullanılan aynı sözdizimini kullanarak uygulayın.</span><span class="sxs-lookup"><span data-stu-id="df769-129">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="df769-130">Aşağıdaki kod örneği, birlikte değişken arabirimi genel bir sınıf uygulamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="df769-130">The following code example shows how to implement a covariant interface in a generic class.</span></span>  
  
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
  
 <span data-ttu-id="df769-131">Sabit değişken arabirimleri uygulayan sınıflar.</span><span class="sxs-lookup"><span data-stu-id="df769-131">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="df769-132">Örneğin, aşağıdaki kodu düşünün.</span><span class="sxs-lookup"><span data-stu-id="df769-132">For example, consider the following code.</span></span>  
  
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
  
## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="df769-133">Genişletme değişken genel arabirimler</span><span class="sxs-lookup"><span data-stu-id="df769-133">Extending Variant Generic Interfaces</span></span>  
 <span data-ttu-id="df769-134">Bir değişken genel arabirim genişlettiğinizde kullanmak zorunda `in` ve `out` açıkça türetilmiş bir arabirim varyansı destekleyip desteklemediğini belirlemek için anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="df769-134">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="df769-135">Derleyici, varyans Genişletilmekte olan arabiriminden Infer değil.</span><span class="sxs-lookup"><span data-stu-id="df769-135">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="df769-136">Örneğin, aşağıdaki arabirimlerinden göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="df769-136">For example, consider the following interfaces.</span></span>  
  
```csharp  
interface ICovariant<out T> { }  
interface IInvariant<T> : ICovariant<T> { }  
interface IExtCovariant<out T> : ICovariant<T> { }  
```  
  
 <span data-ttu-id="df769-137">İçinde `IInvariant<T>` arabirim, genel tür parametresi `T` değişmezdir, ise içinde `IExtCovariant<out T>` hem arabirimleri aynı arabirimi genişletmek rağmen tür parametresi değişkendir.</span><span class="sxs-lookup"><span data-stu-id="df769-137">In the `IInvariant<T>` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant<out T>` the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="df769-138">Aynı kural, değişken karşıtı genel tür parametreleri için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="df769-138">The same rule is applied to contravariant generic type parameters.</span></span>  
  
 <span data-ttu-id="df769-139">Burada, genel tür parametresi her iki arabirimini genişletir bir arabirim oluşturabilirsiniz `T` birlikte değişkendir ve genel tür parametresi, genişletme, değişken karşıtı olduğu arabirimi arabirim `T` değişmezdir.</span><span class="sxs-lookup"><span data-stu-id="df769-139">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="df769-140">Bu aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="df769-140">This is illustrated in the following code example.</span></span>  
  
```csharp  
interface ICovariant<out T> { }  
interface IContravariant<in T> { }  
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }  
```  
  
 <span data-ttu-id="df769-141">Ancak, genel tür parametresi, `T` olan tek bir arabirimde bildirilen değişken, değişken karşıtı bildirip genişletme arabiriminde veya tam tersi.</span><span class="sxs-lookup"><span data-stu-id="df769-141">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="df769-142">Bu aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="df769-142">This is illustrated in the following code example.</span></span>  
  
```csharp  
interface ICovariant<out T> { }  
// The following statement generates a compiler error.  
// interface ICoContraVariant<in T> : ICovariant<T> { }  
```  
  
### <a name="avoiding-ambiguity"></a><span data-ttu-id="df769-143">Belirsizlik kaçınma</span><span class="sxs-lookup"><span data-stu-id="df769-143">Avoiding Ambiguity</span></span>  
 <span data-ttu-id="df769-144">Değişken genel arabirimler uyguladığınızda, varyans bazen için karışıklığa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="df769-144">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="df769-145">Bu kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="df769-145">This should be avoided.</span></span>  
  
 <span data-ttu-id="df769-146">Örneğin, bir sınıf içinde farklı bir genel tür parametreleri ile aynı değişken genel arabirim açıkça uygularsanız, belirsizlik oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df769-146">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="df769-147">Derleyici bu durumda bir hata oluşturmaz, ancak çalışma zamanında hangi arabirim uygulaması seçilir belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="df769-147">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="df769-148">Bu küçük hatalar, kodunuzda neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="df769-148">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="df769-149">Aşağıdaki kod örneği göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="df769-149">Consider the following code example.</span></span>  
  
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
  
 <span data-ttu-id="df769-150">Bu örnekte, belirtilmeyen nasıl `pets.GetEnumerator` ücretlerinin arasında `Cat` ve `Dog`.</span><span class="sxs-lookup"><span data-stu-id="df769-150">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="df769-151">Kodunuzda bu sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="df769-151">This could cause problems in your code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df769-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df769-152">See Also</span></span>

- [<span data-ttu-id="df769-153">Variance in Generic Interfaces (C#)</span><span class="sxs-lookup"><span data-stu-id="df769-153">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
- [<span data-ttu-id="df769-154">İşlev ve eylem genel temsilcileri (C#) için varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="df769-154">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
