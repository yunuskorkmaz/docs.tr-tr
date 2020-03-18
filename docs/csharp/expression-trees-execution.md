---
title: İfade Ağaçlarını Yürütme
description: Yürütülebilir Ara Dil (IL) yönergelerine dönüştürerek ifade ağaçlarını yürütme hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 802a83f52f9c05a99c3f49f8f6511eff81ef3eaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146027"
---
# <a name="executing-expression-trees"></a><span data-ttu-id="b887a-103">İfade Ağaçlarını Yürütme</span><span class="sxs-lookup"><span data-stu-id="b887a-103">Executing Expression Trees</span></span>

[<span data-ttu-id="b887a-104">Önceki -- İfade Ağaçlarını Destekleyen Çerçeve Türleri</span><span class="sxs-lookup"><span data-stu-id="b887a-104">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="b887a-105">*İfade ağacı,* bazı kodları temsil eden bir veri yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="b887a-105">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="b887a-106">Derlenmiş ve çalıştırılabilir kod değildir.</span><span class="sxs-lookup"><span data-stu-id="b887a-106">It is not compiled and executable code.</span></span> <span data-ttu-id="b887a-107">Bir ifade ağacı tarafından temsil edilen .NET kodunu yürütmek istiyorsanız, bunu çalıştırılabilir IL yönergelerine dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b887a-107">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span>

## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="b887a-108">Lambda İfadeleri Fonksiyonlara</span><span class="sxs-lookup"><span data-stu-id="b887a-108">Lambda Expressions to Functions</span></span>

<span data-ttu-id="b887a-109">LambdaExpression'ı veya LambdaExpression'dan türetilen herhangi bir türü çalıştırılabilir IL'ye dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b887a-109">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="b887a-110">Diğer ifade türleri doğrudan koda dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="b887a-110">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="b887a-111">Bu kısıtlamanın pratikte çok az etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="b887a-111">This restriction has little effect in practice.</span></span> <span data-ttu-id="b887a-112">Lambda ifadeleri, yürütülebilir ara dile (IL) dönüştürerek yürütmek istediğiniz tek ifade türleridir.</span><span class="sxs-lookup"><span data-stu-id="b887a-112">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="b887a-113">(Doğrudan bir `ConstantExpression`yürütmek için ne anlama geleceğini düşünün .</span><span class="sxs-lookup"><span data-stu-id="b887a-113">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="b887a-114">Yararlı bir şey anlamına gelir mi?) Bir , veya `LambdaExpression`türetilen bir tür `LambdaExpression` herhangi bir ifade ağacı IL dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="b887a-114">Would it mean anything useful?) Any expression tree that is a `LambdaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="b887a-115">İfade türü `Expression<TDelegate>` .NET Core kitaplıklarında tek somut örnektir.</span><span class="sxs-lookup"><span data-stu-id="b887a-115">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="b887a-116">Herhangi bir temsilci türüyle eşleyen bir ifadeyi temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b887a-116">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="b887a-117">Bu tür bir temsilci türüyle eşleşip, .NET ifadeyi inceleyebilir ve lambda ifadesinin imzasıyla eşleşen uygun bir temsilci için IL oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="b887a-117">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span>

<span data-ttu-id="b887a-118">Çoğu durumda, bu bir ifade ve karşılık gelen temsilcisi arasında basit bir eşleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b887a-118">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="b887a-119">Örneğin, temsil `Expression<Func<int>>` edilen bir ifade ağacı türünün `Func<int>`bir temsilcisine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="b887a-119">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="b887a-120">Herhangi bir dönüş türü ve bağımsız değişken listesi olan bir lambda ifadesi için, bu lambda ifadesi tarafından temsil edilen yürütülebilir kodun hedef türü olan bir temsilci türü vardır.</span><span class="sxs-lookup"><span data-stu-id="b887a-120">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lambda expression.</span></span>

<span data-ttu-id="b887a-121">Bir `LambdaExpression` ifade `Compile` `CompileToMethod` ağacını yürütülebilir koda dönüştürmek için kullanacağınız tür ve üyeler.</span><span class="sxs-lookup"><span data-stu-id="b887a-121">The `LambdaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="b887a-122">Yöntem `Compile` bir temsilci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b887a-122">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="b887a-123">Yöntem, `CompileToMethod` ifade `MethodBuilder` ağacının derlenmiş çıktısını temsil eden IL ile bir nesneyi güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="b887a-123">The `CompileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="b887a-124">Sadece `CompileToMethod` masaüstü çerçevesinde kullanılabildiğini, .NET Core'da bulunmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b887a-124">Note that `CompileToMethod` is only available in the full desktop framework, not in the .NET Core.</span></span>

<span data-ttu-id="b887a-125">İsteğe bağlı olarak, `DebugInfoGenerator` oluşturulan temsilci nesnesi için simge hata ayıklama bilgilerini alacak bir de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b887a-125">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="b887a-126">Bu, ifade ağacını bir temsilci nesnesine dönüştürmenize ve oluşturulan temsilci hakkında tam hata ayıklama bilgisine sahip yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b887a-126">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="b887a-127">Aşağıdaki kodu kullanarak bir ifadeyi temsilciye dönüştürürsunuz:</span><span class="sxs-lookup"><span data-stu-id="b887a-127">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="b887a-128">Temsilci türünün ifade türüne dayandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b887a-128">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="b887a-129">Temsilci nesnesini güçlü bir şekilde kullanmak istiyorsanız, iade türünü ve bağımsız değişken listesini bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b887a-129">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="b887a-130">Yöntem `LambdaExpression.Compile()` türü `Delegate` döndürür.</span><span class="sxs-lookup"><span data-stu-id="b887a-130">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="b887a-131">Derleme zamanı araçlarının bağımsız değişken listesini veya dönüş türünü denetlemesi için doğru temsilci türüne dökmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b887a-131">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list or return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="b887a-132">Yürütme ve Ömür Ler</span><span class="sxs-lookup"><span data-stu-id="b887a-132">Execution and Lifetimes</span></span>

<span data-ttu-id="b887a-133">'yi çağırdığınızda `LambdaExpression.Compile()`oluşturulan temsilciyi çağırarak kodu çalıştırMışsınız.</span><span class="sxs-lookup"><span data-stu-id="b887a-133">You execute the code by invoking the delegate created when you called `LambdaExpression.Compile()`.</span></span> <span data-ttu-id="b887a-134">Bunu yukarıda bir `add.Compile()` temsilci döndürür.</span><span class="sxs-lookup"><span data-stu-id="b887a-134">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="b887a-135">Bu temsilciyi çağırmak, `func()` kodu çağırarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="b887a-135">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="b887a-136">Bu temsilci, ifade ağacındaki kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b887a-136">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="b887a-137">Tutamacı bu temsilciye saklayabilir ve daha sonra çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b887a-137">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="b887a-138">Temsil edilen kodu her yürütmek istediğinizde ifade ağacını derlemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b887a-138">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="b887a-139">(İfade ağaçlarının değişmez olduğunu unutmayın ve aynı ifade ağacını derlemek daha sonra aynı kodu çalıştıran bir temsilci oluşturur.)</span><span class="sxs-lookup"><span data-stu-id="b887a-139">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="b887a-140">Gereksiz derleme çağrılarından kaçınarak performansı artırmak için daha karmaşık önbelleğe alma mekanizmaları oluşturmaya çalışmamanızı konusunda sizi uyaracağım.</span><span class="sxs-lookup"><span data-stu-id="b887a-140">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="b887a-141">Aynı algoritmayı temsil edip etmediklerini belirlemek için iki rasgele ifade ağacını karşılaştırmak da yürütmek için zaman alıcı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b887a-141">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="b887a-142">Büyük olasılıkla, fazladan aramadan kaçınmak için `LambdaExpression.Compile()` kaydettiğiniz işlem süresinin, iki farklı ifade ağacının aynı yürütülebilir kodla sonuçlanan kod yürütme süresi tarafından tüketilenden daha fazla olacağını göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b887a-142">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="b887a-143">Uyarılar</span><span class="sxs-lookup"><span data-stu-id="b887a-143">Caveats</span></span>

<span data-ttu-id="b887a-144">Bir temsilciye lambda ifadesini derlemek ve bu temsilciyi çağırmak bir ifade ağacıyla gerçekleştirebileceğiniz en basit işlemlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="b887a-144">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="b887a-145">Ancak, bu basit operasyon bile, bilmeniz gereken uyarılar vardır.</span><span class="sxs-lookup"><span data-stu-id="b887a-145">However, even with this simple operation, there are caveats you must be aware of.</span></span>

<span data-ttu-id="b887a-146">Lambda İfadeleri, ifadede başvurulan tüm yerel değişkenler üzerinde kapanışlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b887a-146">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="b887a-147">Temsilcinin bir parçası olacak değişkenlerin, çağırdığınız `Compile`konumda ve ortaya çıkan temsilciyi çalıştırdığınızda kullanılabilir olduğunu garanti etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b887a-147">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="b887a-148">Genel olarak, derleyici bunun doğru olduğundan emin olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b887a-148">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="b887a-149">Ancak, ifadeniz uygulayan bir değişkene `IDisposable`erişirse, kodunuzun ifade ağacı tarafından hala tutulurken nesneyi elden çıkarabilmesi mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b887a-149">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="b887a-150">Örneğin, bu kod iyi `int` çalışır, `IDisposable`çünkü uygulanmaz:</span><span class="sxs-lookup"><span data-stu-id="b887a-150">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="b887a-151">Temsilci yerel değişkene `constant`bir başvuru yakaladı.</span><span class="sxs-lookup"><span data-stu-id="b887a-151">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="b887a-152">Bu değişkene daha sonra, işlev yürütüldüğünde `CreateBoundFunc` erişilir.</span><span class="sxs-lookup"><span data-stu-id="b887a-152">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="b887a-153">Ancak, bu (oldukça contrived) sınıf `IDisposable`uygular düşünün:</span><span class="sxs-lookup"><span data-stu-id="b887a-153">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

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

<span data-ttu-id="b887a-154">Aşağıda gösterildiği gibi bir ifadede kullanırsanız, `ObjectDisposedException` `Resource.Argument` özellik tarafından başvurulan kodu çalıştırdığınızda bir</span><span class="sxs-lookup"><span data-stu-id="b887a-154">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

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

<span data-ttu-id="b887a-155">Bu yöntemden döndürülen temsilci, `constant` elden çıkarılan nesnenin üzerine kapandı.</span><span class="sxs-lookup"><span data-stu-id="b887a-155">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="b887a-156">(Bir `using` açıklamada beyan edildiği için imha edildi.)</span><span class="sxs-lookup"><span data-stu-id="b887a-156">(It's been disposed, because it was declared in a `using` statement.)</span></span>

<span data-ttu-id="b887a-157">Şimdi, bu yöntemden döndürülen temsilciyi çalıştırdığınızda, yürütme noktasında bir `ObjectDisposedException` atma olacak.</span><span class="sxs-lookup"><span data-stu-id="b887a-157">Now, when you execute the delegate returned from this method, you'll have a `ObjectDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="b887a-158">Derleme zamanı yapısını temsil eden bir çalışma zamanı hatası olması garip görünüyor, ama ifade ağaçlarıyla çalışırken girdiğimiz dünya bu.</span><span class="sxs-lookup"><span data-stu-id="b887a-158">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="b887a-159">Bu sorunun permütasyon bir yeri vardır, bu yüzden bunu önlemek için genel rehberlik sunmak zor.</span><span class="sxs-lookup"><span data-stu-id="b887a-159">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="b887a-160">İfadeleri tanımlarken yerel değişkenlere erişirken dikkatli olun ve genel bir API tarafından `this`döndürülebilen bir ifade ağacı oluştururken geçerli nesnedeki (temsil edilen) duruma erişme konusunda dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="b887a-160">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="b887a-161">İfadenizdeki kod, diğer derlemelerde yöntemlere veya özelliklere başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="b887a-161">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="b887a-162">İfade tanımlandığında, derlendiğinde ve sonuç temsilcisi çağrıldığında bu derlemeye erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b887a-162">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="b887a-163">Mevcut olmayan durumlarda bir `ReferencedAssemblyNotFoundException` ile karşılanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="b887a-163">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="b887a-164">Özet</span><span class="sxs-lookup"><span data-stu-id="b887a-164">Summary</span></span>

<span data-ttu-id="b887a-165">Expression Trees bu ifadeyi temsil eden lambda ifadelerini yürütebileceğiniz bir temsilci oluşturmak için derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b887a-165">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="b887a-166">Bu, bir ifade ağacı tarafından temsil edilen kodu yürütmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="b887a-166">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="b887a-167">İfade Ağacı, oluşturduğunuz belirli bir yapı için yürütülecek kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b887a-167">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="b887a-168">Kodu derlediğiniz ve yürütdüğünüz ortam, ifadeyi oluşturduğunuz ortamla eşleştiği sürece, her şey beklendiği gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="b887a-168">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="b887a-169">Bu olmadığında, hatalar çok tahmin edilebilir ve ifade ağaçları kullanarak herhangi bir kod ilk testleri yakalanmış olacak.</span><span class="sxs-lookup"><span data-stu-id="b887a-169">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="b887a-170">Sonraki -- İfadeleri Yorumlama</span><span class="sxs-lookup"><span data-stu-id="b887a-170">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)
