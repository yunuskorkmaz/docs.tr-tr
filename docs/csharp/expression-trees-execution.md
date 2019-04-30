---
title: İfade ağaçlarını yürütme
description: Yürütülebilir Ara dil (IL) talimatları dönüştürerek ifade ağaçlarını yürütme hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: f6dca5a3965924e8eb6e1c04fe7ffc3c78c7df93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664564"
---
# <a name="executing-expression-trees"></a><span data-ttu-id="36515-103">İfade ağaçlarını yürütme</span><span class="sxs-lookup"><span data-stu-id="36515-103">Executing Expression Trees</span></span>

[<span data-ttu-id="36515-104">Önceki--İfade ağaçlarını destekleyen çerçeve türleri</span><span class="sxs-lookup"><span data-stu-id="36515-104">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="36515-105">Bir *ifade ağacı* bazı kod temsil eden bir veri yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="36515-105">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="36515-106">Derlenmiş ve yürütülebilir kodu değil.</span><span class="sxs-lookup"><span data-stu-id="36515-106">It is not compiled and executable code.</span></span> <span data-ttu-id="36515-107">Bir ifade ağacı tarafından temsil edilen .NET kodu çalıştırmak istiyorsanız, bunu yürütülebilir IL yönergelerinden dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="36515-107">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span>

## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="36515-108">Lambda ifadeleri işlevleri</span><span class="sxs-lookup"><span data-stu-id="36515-108">Lambda Expressions to Functions</span></span>

<span data-ttu-id="36515-109">Tüm LambdaExpression veya yürütülebilir IL LambdaExpression türetilmiş herhangi bir tür dönüştürme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36515-109">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="36515-110">Diğer ifade türleri, doğrudan koda dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="36515-110">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="36515-111">Bu kısıtlama, uygulamada çok az etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="36515-111">This restriction has little effect in practice.</span></span> <span data-ttu-id="36515-112">Lambda ifadeleri, yalnızca yürütülebilir Ara dil (IL) dönüştürerek yürütmek istediğiniz ifadeleri türleridir.</span><span class="sxs-lookup"><span data-stu-id="36515-112">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="36515-113">(Doğrudan çalıştırmak bunun ne anlama düşündüğünüz bir `ConstantExpression`.</span><span class="sxs-lookup"><span data-stu-id="36515-113">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="36515-114">Bu faydalı bir şey anlamına gelir?) Olan herhangi bir ifade ağacı bir `LambdaExpression`, veya türetilmiş bir tür `LambdaExpression` için IL dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="36515-114">Would it mean anything useful?) Any expression tree that is a `LambdaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="36515-115">İfade türü `Expression<TDelegate>` .NET Core kitaplıklarında yalnızca somut bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="36515-115">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="36515-116">Bu, tüm temsilci türüyle eşleyen bir ifade temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="36515-116">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="36515-117">Bu tür bir temsilci türüne eşlediğinden, .NET ifade inceleyin ve lambda ifadesinin imzayla eşleşen uygun bir temsilci için IL oluşturur.</span><span class="sxs-lookup"><span data-stu-id="36515-117">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span> 

<span data-ttu-id="36515-118">Çoğu durumda, bu ifade, karşılık gelen temsilci arasında basit bir eşleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="36515-118">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="36515-119">Örneğin, tarafından temsil edilen bir ifade ağacı `Expression<Func<int>>` türden bir temsilciye dönüştürülmüş `Func<int>`.</span><span class="sxs-lookup"><span data-stu-id="36515-119">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="36515-120">Herhangi bir dönüş türü ve bağımsız değişken listesi ile bir lambda ifadesi için yürütülebilir kodu bu lambda ifadesi tarafından temsil edilen hedef türü bir temsilci türü vardır.</span><span class="sxs-lookup"><span data-stu-id="36515-120">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lambda expression.</span></span>

<span data-ttu-id="36515-121">`LambdaExpression` Türünü içeren `Compile` ve `CompileToMethod` yürütülebilir kodu bir ifade ağacı dönüştürmek için kullanacağınız üyeleri.</span><span class="sxs-lookup"><span data-stu-id="36515-121">The `LambdaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="36515-122">`Compile` Yöntemi, bir temsilci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="36515-122">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="36515-123">`CompileToMethod` Yöntemi güncelleştirmeleri bir `MethodBuilder` derlenen Çıkışta ifade ağacı temsil eden IL nesne.</span><span class="sxs-lookup"><span data-stu-id="36515-123">The `CompileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="36515-124">Unutmayın `CompileToMethod` yalnızca tam masaüstü Framework, .NET Core de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="36515-124">Note that `CompileToMethod` is only available in the full desktop framework, not in the .NET Core.</span></span>

<span data-ttu-id="36515-125">İsteğe bağlı olarak, sağlayabilirsiniz bir `DebugInfoGenerator` oluşturulan temsilci nesne için hata ayıklama bilgisi sembol alırsınız.</span><span class="sxs-lookup"><span data-stu-id="36515-125">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="36515-126">İfade ağacı bir temsilci nesnesine dönüştürmek ve oluşturulan temsilci tam hata ayıklama bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="36515-126">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="36515-127">Bir ifade aşağıdaki kodu kullanarak bir temsilciye dönüştürmeniz:</span><span class="sxs-lookup"><span data-stu-id="36515-127">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="36515-128">Bu ifade türünde temsilci türüne dayalı olduğunu dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="36515-128">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="36515-129">Temsilci nesne türü kesin belirlenmiş bir şekilde kullanmak istiyorsanız, dönüş türü ve bağımsız değişken listesi bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="36515-129">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="36515-130">`LambdaExpression.Compile()` Yöntemi döndürür `Delegate` türü.</span><span class="sxs-lookup"><span data-stu-id="36515-130">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="36515-131">Bağımsız değişken listesini kontrol edin veya dönüş türü herhangi bir derleme zamanı aracı için doğru temsilci türüne dönüştürme gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="36515-131">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list or return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="36515-132">Yürütme ve yaşam süresi yok</span><span class="sxs-lookup"><span data-stu-id="36515-132">Execution and Lifetimes</span></span>

<span data-ttu-id="36515-133">Temsilci çağrıldığında, oluşturulan harekete geçirerek siz kodu yürütürken `LambdaExpression.Compile()`.</span><span class="sxs-lookup"><span data-stu-id="36515-133">You execute the code by invoking the delegate created when you called `LambdaExpression.Compile()`.</span></span> <span data-ttu-id="36515-134">Bunu yeri görebilirsiniz `add.Compile()` temsilci döndürür.</span><span class="sxs-lookup"><span data-stu-id="36515-134">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="36515-135">Çağırarak bu temsilci çağırma `func()` kodu yürütür.</span><span class="sxs-lookup"><span data-stu-id="36515-135">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="36515-136">Bu temsilci kodda bir ifade ağacı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="36515-136">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="36515-137">Bu temsilci tanıtıcısını korumak ve daha sonra çağırma.</span><span class="sxs-lookup"><span data-stu-id="36515-137">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="36515-138">İfade ağacı her zaman temsil ettiği kod yürütmek istediğiniz derleme gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="36515-138">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="36515-139">(İfade ağaçları sabittir ve daha sonra aynı ifade ağacı derleme, aynı kodu yürüten bir temsilci oluşturur unutmayın.)</span><span class="sxs-lookup"><span data-stu-id="36515-139">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="36515-140">Ben gereksiz derleme çağrıları önleyerek performansı artırmak için daha karmaşık bir önbelleğe alma mekanizmasını oluşturulmaya çalışılırken karşı dikkat.</span><span class="sxs-lookup"><span data-stu-id="36515-140">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="36515-141">Bunlar aynı algoritmayı temsil ediyorsa belirlemek için iki rastgele ifade ağaçları karşılaştırma ayrıca zaman yürütmek için alabilir.</span><span class="sxs-lookup"><span data-stu-id="36515-141">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="36515-142">İşlem süresi, ek çağrıları kaydederken, büyük olasılıkla bulabilirsiniz `LambdaExpression.Compile()` birden fazla ifade ağaçları neden aynı yürütülebilir kodu tanımlayan iki farklı kod yürütme zamanına göre tüketilir.</span><span class="sxs-lookup"><span data-stu-id="36515-142">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="36515-143">Uyarılar</span><span class="sxs-lookup"><span data-stu-id="36515-143">Caveats</span></span>

<span data-ttu-id="36515-144">Bir lambda ifadesi, bir temsilci derleme ve bu temsilciyi çağrılırken bir ifade ağacı ile gerçekleştirebileceğiniz en basit işlemler biridir.</span><span class="sxs-lookup"><span data-stu-id="36515-144">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="36515-145">Ancak, basit işlemle bile bu farkında olması gereken uyarılar vardır.</span><span class="sxs-lookup"><span data-stu-id="36515-145">However, even with this simple operation, there are caveats you must be aware of.</span></span> 

<span data-ttu-id="36515-146">Lambda ifadeleri, ifade başvurulmayan yerel değişkenlerin üzerine kapanışlar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="36515-146">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="36515-147">Temsilci bir parçası olan tüm değişkenler çağırdığınız konumda kullanılabilir olduğunu garanti gerekir `Compile`, ve sonuç olarak oluşan temsilci yürüttüğünüzde.</span><span class="sxs-lookup"><span data-stu-id="36515-147">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="36515-148">Genel olarak, derleyici bu doğru olduğundan emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="36515-148">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="36515-149">Ancak, ifadeniz uygulayan bir değişkenine erişiyorsa `IDisposable`, ifade ağacına tarafından hala açık tutulduğu sürece kodunuzun nesnesini atmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="36515-149">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="36515-150">Örneğin, bu kod düzgün, çünkü çalışır `int` uygulamıyor `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="36515-150">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="36515-151">Temsilci bir başvuru yerel değişkene yakalandı `constant`.</span><span class="sxs-lookup"><span data-stu-id="36515-151">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="36515-152">İşlev tarafından döndürülen daha sonra istediğiniz zaman bu değişken erişilir `CreateBoundFunc` yürütür.</span><span class="sxs-lookup"><span data-stu-id="36515-152">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="36515-153">Ancak, bu (Bunun yerine contrived) uygulayan sınıf göz önünde bulundurun `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="36515-153">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

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

<span data-ttu-id="36515-154">Bir ifadede aşağıda gösterildiği gibi kullanırsanız, elde edecekleriniz bir `ObjectDisposedException` tarafından başvurulan kodu yürüttüğünüzde `Resource.Argument` özelliği:</span><span class="sxs-lookup"><span data-stu-id="36515-154">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

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

<span data-ttu-id="36515-155">Bu yöntemin döndürdüğü temsilci üzerinden kapattı `constant` , atıldı nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="36515-155">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="36515-156">(Olarak bildirildiğinden, atılmış olan bir `using` deyimi.)</span><span class="sxs-lookup"><span data-stu-id="36515-156">(It's been disposed, because it was declared in a `using` statement.)</span></span> 

<span data-ttu-id="36515-157">Bu yöntemin döndürdüğü temsilci yürüttüğünüzde, şimdi gerekir bir `ObjectDisposedException` yürütme noktasında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="36515-157">Now, when you execute the delegate returned from this method, you'll have a `ObjectDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="36515-158">Bir derleme zamanı yapısı temsil eden bir çalışma zamanı hatası için ilginç görünüyor, ancak bu ifade ağaçları ile çalıştığımız biz geçilmesidir dünya.</span><span class="sxs-lookup"><span data-stu-id="36515-158">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="36515-159">Bunu önlemek için genel rehberlik sunmak zor, bu nedenle bu sorunun permütasyon çok fazla vardır.</span><span class="sxs-lookup"><span data-stu-id="36515-159">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="36515-160">İfadeleri tanımlarken yerel değişkenlere erişme hakkında dikkatli olun ve durumunda geçerli nesneye erişme hakkında dikkatli olun (tarafından temsil edilen `this`) ne zaman bir ifade ağacı oluşturma döndürülen bir genel API tarafından.</span><span class="sxs-lookup"><span data-stu-id="36515-160">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="36515-161">İfadeniz kodda yöntemleri veya özellikleri diğer derlemelerdeki başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="36515-161">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="36515-162">Bu derleme ne zaman ifade tanımlanır ve ne zaman derlenir ve sonuç olarak oluşan temsilci zaman çağrılır erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="36515-162">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="36515-163">İle karşılanması bir `ReferencedAssemblyNotFoundException` durumlarda burada da mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="36515-163">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="36515-164">Özet</span><span class="sxs-lookup"><span data-stu-id="36515-164">Summary</span></span>

<span data-ttu-id="36515-165">Lambda ifadeleri temsil eden ifade ağaçları yürütebilirsiniz temsilci oluşturmak için derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="36515-165">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="36515-166">Bu, bir ifade ağacı tarafından temsil edilen kod yürütmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="36515-166">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="36515-167">İfade ağacı, oluşturduğunuz belirli yapısı için yürütmek kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="36515-167">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="36515-168">İfade oluşturduğunuz ortamı, derleme ve kod yürütme ortamı eşleşmesi şartıyla, her şeyin beklendiği gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="36515-168">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="36515-169">Gerçekleşen değil, hatalar, öngörülebilir ve ilk ifade ağaçları kullanma herhangi bir kod testlerinizde yakalanır.</span><span class="sxs-lookup"><span data-stu-id="36515-169">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="36515-170">Sonraki--İfade yorumlama</span><span class="sxs-lookup"><span data-stu-id="36515-170">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)
