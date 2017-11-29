---
title: "İfade ağaçlarını yürütme"
description: "İfade ağaçları yürütülebilir Ara dile (IL) talimatları dönüştürerek çalıştırma hakkında bilgi edinin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 4ca87c8410a04e9198e9dd6c379760e7b6596585
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="executing-expression-trees"></a><span data-ttu-id="f2a07-104">İfade ağaçlarını yürütme</span><span class="sxs-lookup"><span data-stu-id="f2a07-104">Executing Expression Trees</span></span>

[<span data-ttu-id="f2a07-105">Önceki--Framework destekleyen ifade ağaçları türleri</span><span class="sxs-lookup"><span data-stu-id="f2a07-105">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="f2a07-106">Bir *ifade ağacına* biraz kod temsil eden bir veri yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="f2a07-106">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="f2a07-107">Derlenmiş ve yürütülebilir kodu değil.</span><span class="sxs-lookup"><span data-stu-id="f2a07-107">It is not compiled and executable code.</span></span> <span data-ttu-id="f2a07-108">Bir ifade ağacına tarafından temsil edilen .NET kodu çalıştırmak istiyorsanız, yürütülebilir IL talimatları dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2a07-108">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span> 
## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="f2a07-109">Lambda ifadeleri İşlevler</span><span class="sxs-lookup"><span data-stu-id="f2a07-109">Lambda Expressions to Functions</span></span>
<span data-ttu-id="f2a07-110">Tüm LambdaExpression veya yürütülebilir IL LambdaExpression türetilmiş herhangi bir tür dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2a07-110">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="f2a07-111">Diğer ifade türleri doğrudan koda dönüştürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="f2a07-111">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="f2a07-112">Bu kısıtlama, uygulamada çok az etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f2a07-112">This restriction has little effect in practice.</span></span> <span data-ttu-id="f2a07-113">Lambda ifadeleri yürütülebilir Ara dile (IL) dönüştürerek yürütmek istediğiniz ifadeleri yalnızca türleridir.</span><span class="sxs-lookup"><span data-stu-id="f2a07-113">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="f2a07-114">(Hakkında BT'nin doğrudan yürütmek anlamına gelir düşündüğünüz bir `ConstantExpression`.</span><span class="sxs-lookup"><span data-stu-id="f2a07-114">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="f2a07-115">Bu yararlı bir şey anlamına gelir?) Olan herhangi bir ifade ağacına bir `LamdbaExpression`, veya türetilmiş bir tür `LambdaExpression` için IL dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="f2a07-115">Would it mean anything useful?) Any expression tree that is a `LamdbaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="f2a07-116">İfade türü `Expression<TDelegate>` .NET Core kitaplıklarında yalnızca somut bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="f2a07-116">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="f2a07-117">Bir temsilci türüyle eşleşen bir ifade göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2a07-117">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="f2a07-118">Bu tür bir temsilci türüyle eşleyen çünkü .NET ifade inceleyin ve lambda ifadesi imza eşleşen uygun bir temsilci için IL oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2a07-118">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span> 

<span data-ttu-id="f2a07-119">Çoğu durumda, bu deyim ve karşılık gelen temsilci arasında basit bir eşleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2a07-119">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="f2a07-120">Örneğin, tarafından temsil edilen bir ifade ağacına `Expression<Func<int>>` türü temsilciye dönüştürülür `Func<int>`.</span><span class="sxs-lookup"><span data-stu-id="f2a07-120">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="f2a07-121">Dönüş türü ve bağımsız değişken listesi lambda ifadesi için bu lamdba ifade tarafından temsil edilen yürütülebilir kod hedef türü olan bir temsilci türü vardır.</span><span class="sxs-lookup"><span data-stu-id="f2a07-121">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lamdba expression.</span></span>

<span data-ttu-id="f2a07-122">`LamdbaExpression` Türünü içeren `Compile` ve `CompileToMethod` bir ifade ağacına yürütülebilir koduna dönüştürmek için kullanacağınız üyeleri.</span><span class="sxs-lookup"><span data-stu-id="f2a07-122">The `LamdbaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="f2a07-123">`Compile` Yöntemi, bir temsilci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2a07-123">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="f2a07-124">`ConmpileToMethod` Yöntemi güncelleştirmeleri bir `MethodBuilder` ifade ağacına derlenmiş çıktısını gösterir IL nesnesiyle.</span><span class="sxs-lookup"><span data-stu-id="f2a07-124">The `ConmpileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="f2a07-125">Unutmayın `CompileToMethod` yalnızca tam masaüstü çerçevesi, .NET Core framework üzerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2a07-125">Note that `CompileToMethod` is only available on the full desktop framework, not on the .NET Core framework.</span></span>

<span data-ttu-id="f2a07-126">İsteğe bağlı olarak, ayrıca sağlayabilirsiniz bir `DebugInfoGenerator` bilgi oluşturulan temsilci nesne için hata ayıklama simgesi alırsınız.</span><span class="sxs-lookup"><span data-stu-id="f2a07-126">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="f2a07-127">Bu, ifade ağacına bir temsilci nesnesine dönüştürmek ve oluşturulan temsilci hakkında tam hata ayıklama bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2a07-127">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="f2a07-128">Aşağıdaki kodu kullanarak temsilci bir ifade dönüştürecektir:</span><span class="sxs-lookup"><span data-stu-id="f2a07-128">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="f2a07-129">Temsilci türü ifade türüne dayalıdır dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f2a07-129">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="f2a07-130">Kesin türü belirtilmiş bir biçimde temsilci nesnesini kullanmak istiyorsanız, dönüş türü ve bağımsız değişken listesi bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2a07-130">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="f2a07-131">`LambdaExpression.Compile()` Yöntemi döndürür `Delegate` türü.</span><span class="sxs-lookup"><span data-stu-id="f2a07-131">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="f2a07-132">Dönüş türü bağımsız değişken listesini kontrol edin herhangi bir derleme zamanı aracı için doğru temsilci türüne dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2a07-132">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list of return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="f2a07-133">Yürütme ve yaşam süresi</span><span class="sxs-lookup"><span data-stu-id="f2a07-133">Execution and Lifetimes</span></span>

<span data-ttu-id="f2a07-134">Çağırdığınızda oluşturulan temsilci çağırarak kod yürütmek `LamdbaExpression.Compile()`.</span><span class="sxs-lookup"><span data-stu-id="f2a07-134">You execute the code by invoking the delegate created when you called `LamdbaExpression.Compile()`.</span></span> <span data-ttu-id="f2a07-135">Bu where gördüğünüz `add.Compile()` temsilci döndürür.</span><span class="sxs-lookup"><span data-stu-id="f2a07-135">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="f2a07-136">Bu temsilci çağırarak çağırma `func()` kodu yürütür.</span><span class="sxs-lookup"><span data-stu-id="f2a07-136">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="f2a07-137">Bu temsilci ifade ağacına kodda temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2a07-137">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="f2a07-138">Bu temsilci tanıtıcısını korumak ve daha sonra çağırma.</span><span class="sxs-lookup"><span data-stu-id="f2a07-138">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="f2a07-139">İfade ağacına temsil ettiği kod yürütmek istediğiniz her seferinde derleme gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f2a07-139">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="f2a07-140">(İfade ağaçları sabittir ve daha sonra aynı ifade ağacına derleme aynı kodu yürütür bir temsilci oluşturacak unutmayın.)</span><span class="sxs-lookup"><span data-stu-id="f2a07-140">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="f2a07-141">I gereksiz derleme çağrıları önleyerek performansı artırmak için daha karmaşık bir önbelleğe alma mekanizmasını oluşturulmaya çalışılırken karşı dikkat.</span><span class="sxs-lookup"><span data-stu-id="f2a07-141">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="f2a07-142">Aynı algoritmayı temsil ediyorsa belirlemek için iki rastgele ifade ağaçları karşılaştırma de yürütmek için zun.</span><span class="sxs-lookup"><span data-stu-id="f2a07-142">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="f2a07-143">İşlem süresi, hiçbir ek çağrı önleme kaydetmeniz olasılıkla bulacaksınız `LambdaExpression.Compile()` birden çok farklı iki ifade ağaçları neden aynı yürütülebilir kod belirler kodu yürütme süresi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2a07-143">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="f2a07-144">Uyarılar</span><span class="sxs-lookup"><span data-stu-id="f2a07-144">Caveats</span></span>

<span data-ttu-id="f2a07-145">Lambda ifadesi bir temsilci derleme ve bu temsilciyi çağrılırken bir ifade ağacına ile gerçekleştirebileceğiniz en basit işlemler biridir.</span><span class="sxs-lookup"><span data-stu-id="f2a07-145">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="f2a07-146">Ancak, basit işlemiyle bile bu farkında olması gereken uyarılar vardır.</span><span class="sxs-lookup"><span data-stu-id="f2a07-146">However, even with this simple operation, there are caveats you must be aware of.</span></span> 

<span data-ttu-id="f2a07-147">Lambda ifadeleri kapanışlar ifadesinde başvurulan tüm yerel değişkenler üzerinden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f2a07-147">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="f2a07-148">Burada, çağrı konumda temsilci parçası olacak tüm değişkenler kullanılabilir güvence altına almalıdır `Compile`, ve sonuçta elde edilen temsilci yürütülürken.</span><span class="sxs-lookup"><span data-stu-id="f2a07-148">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="f2a07-149">Genel olarak, derleyici doğru olduğundan emin.</span><span class="sxs-lookup"><span data-stu-id="f2a07-149">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="f2a07-150">Ancak, İfadenizde uygulayan bir değişken erişirse `IDisposable`, ifade ağacına tarafından tutulan işlemi hala durumdayken kodunuzu nesnesinin dispose mümkündür.</span><span class="sxs-lookup"><span data-stu-id="f2a07-150">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="f2a07-151">Örneğin, bu kod düzgün, çünkü çalışır `int` uygulamayan `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="f2a07-151">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="f2a07-152">Temsilci yerel değişken başvuru yakalandı `constant`.</span><span class="sxs-lookup"><span data-stu-id="f2a07-152">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="f2a07-153">İşlevi tarafından döndürülen zaman dilediğiniz zaman daha sonra bu değişken erişilen `CreateBoundFunc` yürütür.</span><span class="sxs-lookup"><span data-stu-id="f2a07-153">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="f2a07-154">Ancak, uygular (yerine contrived) Bu sınıf göz önünde bulundurun `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="f2a07-154">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

```csharp
public class Resource : IDisposable
{
    private bool isDisposed = false;
    public int Argument
    {
        get
        {
            if (!isDisposed)
                return 5;
            else throw new ObjectDisposedException("Resource");
        }
    }

    public void Dispose()
    {
        isDisposed = true;
    }
}
```

<span data-ttu-id="f2a07-155">Bir ifadeyi aşağıda gösterildiği gibi kullanırsanız, elde edersiniz bir `ObjectDisposedException` başvurduğu kod yürütülürken `Resource.Argument` özelliği:</span><span class="sxs-lookup"><span data-stu-id="f2a07-155">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

```csharp
private static Func<int, int> CreateBoundResource()
{
    using (var constant = new Resource()) // constant is captured by the expression tree
    {
        Expression<Func<int, int>> expression = (b) => constant.Argument + b;
        var rVal = expression.Compile();
        return rVal;
    }
}
```

<span data-ttu-id="f2a07-156">Bu yöntemin döndürdüğü temsilci üzerinden kapattı `constant` , atıldı nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f2a07-156">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="f2a07-157">(Olarak bildirildi çünkü bu, atılmış olan bir `using` deyimi.)</span><span class="sxs-lookup"><span data-stu-id="f2a07-157">(It's been disposed, because it was declared in a `using` statement.)</span></span> 

<span data-ttu-id="f2a07-158">Bu yöntemin döndürdüğü temsilci yürüttüğünüzde, şimdi gerekir bir `ObjecctDisposedException` yürütme noktasında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f2a07-158">Now, when you execute the delegate returned from this method, you'll have a `ObjecctDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="f2a07-159">Derleme zamanı yapısını temsil eden bir çalışma zamanı hata garip görünüyor, ancak biz ifade ağaçları ile çalışırken biz girin world olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f2a07-159">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="f2a07-160">Bunu önlemek için genel rehberlik sunma sabit olması için çok sayıda permütasyon bu sorunun vardır.</span><span class="sxs-lookup"><span data-stu-id="f2a07-160">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="f2a07-161">İfadeler tanımlarken yerel değişkenler erişme hakkında dikkatli olun ve geçerli nesne durumda erişme hakkında dikkatli olun (tarafından temsil edilen `this`) ne zaman bir ifade ağacına oluşturma döndürülmesi ortak API'si tarafından.</span><span class="sxs-lookup"><span data-stu-id="f2a07-161">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="f2a07-162">İfadeniz kodda yöntemleri veya diğer derlemelerden özelliklerinde başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="f2a07-162">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="f2a07-163">Bu derleme ifade zaman tanımlanmış ve ne zaman derlenir ve ne zaman ortaya çıkan temsilci çağrılır erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2a07-163">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="f2a07-164">İle karşılanması bir `ReferencedAssemblyNotFoundException` durumlarda burada da mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="f2a07-164">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="f2a07-165">Özet</span><span class="sxs-lookup"><span data-stu-id="f2a07-165">Summary</span></span>

<span data-ttu-id="f2a07-166">Lambda ifadeleri temsil ifade ağaçları yürütebilirsiniz bir temsilci oluşturmak için derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="f2a07-166">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="f2a07-167">Bu, bir ifade ağacına tarafından temsil edilen kod yürütmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2a07-167">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="f2a07-168">İfade ağacına oluşturduğunuz belirli yapı için yürütülür kodunu temsil etmiyor.</span><span class="sxs-lookup"><span data-stu-id="f2a07-168">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="f2a07-169">Burada derlemek ve kod yürütmek ortamı ifade oluşturduğunuz ortamı eşleştiği sürece her şeyin beklendiği gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="f2a07-169">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="f2a07-170">Gerçekleşen değil, hataları çok tahmin edilebilir ve ilk ifade ağaçları kullanma herhangi bir kod testlerinizde yakalanan.</span><span class="sxs-lookup"><span data-stu-id="f2a07-170">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="f2a07-171">Sonraki--İfadeleri yorumlama</span><span class="sxs-lookup"><span data-stu-id="f2a07-171">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)
