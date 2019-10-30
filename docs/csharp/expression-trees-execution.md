---
title: Ifade ağaçları yürütülüyor
description: Onları yürütülebilir ara dil (IL) yönergelerine dönüştürerek, ifade ağaçları yürütme hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 9af4b346962cb743daddf774e8b3c1f8fa722ae4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037109"
---
# <a name="executing-expression-trees"></a><span data-ttu-id="05903-103">Ifade ağaçları yürütülüyor</span><span class="sxs-lookup"><span data-stu-id="05903-103">Executing Expression Trees</span></span>

[<span data-ttu-id="05903-104">Ifade ağaçlarını destekleyen önceki Framework türleri</span><span class="sxs-lookup"><span data-stu-id="05903-104">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="05903-105">*İfade ağacı* , bazı kodları temsil eden bir veri yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="05903-105">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="05903-106">Derlenmez ve çalıştırılabilir kod değildir.</span><span class="sxs-lookup"><span data-stu-id="05903-106">It is not compiled and executable code.</span></span> <span data-ttu-id="05903-107">Bir ifade ağacı tarafından temsil edilen .NET kodunu yürütmek istiyorsanız, onu yürütülebilir Il yönergelerine dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="05903-107">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span>

## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="05903-108">IŞLEVLERE lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="05903-108">Lambda Expressions to Functions</span></span>

<span data-ttu-id="05903-109">Herhangi bir Lambdavexpression veya Lambdavexpression 'dan türetilmiş herhangi bir tür çalıştırılabilir Il 'ye dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05903-109">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="05903-110">Diğer ifade türleri doğrudan koda dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="05903-110">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="05903-111">Bu kısıtlama pratikte çok daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="05903-111">This restriction has little effect in practice.</span></span> <span data-ttu-id="05903-112">Lambda ifadeleri, yürütülebilir ara dile (IL) dönüştürerek yürütmek istediğiniz tek ifade türleridir.</span><span class="sxs-lookup"><span data-stu-id="05903-112">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="05903-113">(Bir `ConstantExpression`doğrudan yürütmek için ne anlama geldiğini düşünün.</span><span class="sxs-lookup"><span data-stu-id="05903-113">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="05903-114">Herhangi bir şey yararlı mı?) `LambdaExpression`olan herhangi bir ifade ağacı veya `LambdaExpression` türetilmiş bir tür Il 'ye dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="05903-114">Would it mean anything useful?) Any expression tree that is a `LambdaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="05903-115">`Expression<TDelegate>` ifade türü, .NET Core kitaplıklarında tek somut örnektir.</span><span class="sxs-lookup"><span data-stu-id="05903-115">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="05903-116">Herhangi bir temsilci türüyle eşleşen bir ifadeyi temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="05903-116">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="05903-117">Bu tür bir temsilci türüne eşlendiğinden, .NET ifadeyi inceleyebilir ve lambda ifadesinin imzasıyla eşleşen uygun bir temsilci için Il oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="05903-117">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span> 

<span data-ttu-id="05903-118">Çoğu durumda bu, bir ifade ve onun karşılık gelen temsilcisi arasında basit bir eşleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05903-118">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="05903-119">Örneğin, `Expression<Func<int>>` tarafından temsil edilen bir ifade ağacı `Func<int>`türünün bir temsilcisine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="05903-119">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="05903-120">Herhangi bir dönüş türü ve bağımsız değişken listesi olan bir lambda ifadesinde, bu lambda ifadesi tarafından temsil edilen çalıştırılabilir kodun hedef türü olan bir temsilci türü vardır.</span><span class="sxs-lookup"><span data-stu-id="05903-120">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lambda expression.</span></span>

<span data-ttu-id="05903-121">`LambdaExpression` türü, bir ifade ağacını çalıştırılabilir koda dönüştürmek için kullanacağınız `Compile` ve `CompileToMethod` üyelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="05903-121">The `LambdaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="05903-122">`Compile` yöntemi bir temsilci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05903-122">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="05903-123">`CompileToMethod` yöntemi, ifade ağacının derlenmiş çıkışını temsil eden Il ile bir `MethodBuilder` nesnesini günceller.</span><span class="sxs-lookup"><span data-stu-id="05903-123">The `CompileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="05903-124">`CompileToMethod`, .NET Core 'da değil, yalnızca tam masaüstü çerçevesinde kullanılabilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="05903-124">Note that `CompileToMethod` is only available in the full desktop framework, not in the .NET Core.</span></span>

<span data-ttu-id="05903-125">İsteğe bağlı olarak, oluşturulan temsilci nesnesi için simge hata ayıklama bilgilerini alacak bir `DebugInfoGenerator` de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05903-125">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="05903-126">Bu, ifade ağacını bir temsilci nesnesine dönüştürmenize ve oluşturulan temsilciyle ilgili tam hata ayıklama bilgilerine sahip etmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="05903-126">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="05903-127">Aşağıdaki kodu kullanarak bir ifadeyi temsilciye dönüştürürsünüz:</span><span class="sxs-lookup"><span data-stu-id="05903-127">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="05903-128">Temsilci türünün ifade türüne göre olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="05903-128">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="05903-129">Temsilci nesnesini kesin olarak belirlenmiş bir şekilde kullanmak istiyorsanız, dönüş türünü ve bağımsız değişken listesini bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="05903-129">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="05903-130">`LambdaExpression.Compile()` yöntemi `Delegate` türünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="05903-130">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="05903-131">Herhangi bir derleme zamanı aracının bağımsız değişken listesini veya dönüş türünü denetlemesini sağlamak için onu doğru temsilci türüne atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="05903-131">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list or return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="05903-132">Yürütme ve yaşam süreleri</span><span class="sxs-lookup"><span data-stu-id="05903-132">Execution and Lifetimes</span></span>

<span data-ttu-id="05903-133">Kodu, `LambdaExpression.Compile()`çağrıldığında oluşturulan temsilciyi çağırarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="05903-133">You execute the code by invoking the delegate created when you called `LambdaExpression.Compile()`.</span></span> <span data-ttu-id="05903-134">Bunu, `add.Compile()` bir temsilci döndürdüğü yerde görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05903-134">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="05903-135">Bu temsilciyi çağırmak `func()` çağırarak kodu yürütür.</span><span class="sxs-lookup"><span data-stu-id="05903-135">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="05903-136">Bu temsilci, ifade ağacındaki kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="05903-136">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="05903-137">Bu temsilciye yönelik tanıtıcıyı koruyabilir ve daha sonra çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05903-137">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="05903-138">Temsil ettiği kodu yürütmek istediğiniz her seferinde ifade ağacını derlemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="05903-138">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="05903-139">(İfade ağaçlarının sabit olduğunu unutmayın ve aynı ifade ağacını daha sonra derlemek aynı kodu çalıştıran bir temsilci oluşturur.)</span><span class="sxs-lookup"><span data-stu-id="05903-139">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="05903-140">Gereksiz derleme çağrılarını önleyerek performansı artırmak için daha gelişmiş bir önbelleğe alma mekanizması oluşturmaya çalışırken dikkatli olunacaktır.</span><span class="sxs-lookup"><span data-stu-id="05903-140">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="05903-141">İki rastgele ifade ağacının karşılaştırılması, aynı algoritmanın aynı algoritmayı temsil ettiğini tespit etmek için zaman alıcı olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="05903-141">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="05903-142">Büyük olasılıkla, `LambdaExpression.Compile()` ek çağrılarından kaçınmaktan kaynaklanan işlem zamanının, aynı çalıştırılabilir kodun sonucu olan iki farklı ifade ağacının sonucunu belirleyen kod yürütme sırasında tüketildiğinden daha fazla olacağını fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="05903-142">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="05903-143">Uyarılar</span><span class="sxs-lookup"><span data-stu-id="05903-143">Caveats</span></span>

<span data-ttu-id="05903-144">Bir lambda ifadesini bir temsilciye derlemek ve bu temsilciyi çağırmak, bir ifade ağacı ile gerçekleştirebileceğiniz en basit işlemlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="05903-144">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="05903-145">Ancak, bu basit işlemle birlikte, bilmeniz gereken uyarılar da vardır.</span><span class="sxs-lookup"><span data-stu-id="05903-145">However, even with this simple operation, there are caveats you must be aware of.</span></span> 

<span data-ttu-id="05903-146">Lambda Ifadeleri, ifadede başvurulan herhangi bir yerel değişken üzerinde kapanışları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05903-146">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="05903-147">Temsilcinin parçası olacak tüm değişkenlerin `Compile`çağırdığınız konumda kullanılabilir olduğunu ve elde edilen temsilciyi yürüttüğünüzde emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="05903-147">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="05903-148">Genel olarak, derleyici bunun doğru olduğundan emin olur.</span><span class="sxs-lookup"><span data-stu-id="05903-148">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="05903-149">Ancak, ifadeniz `IDisposable`uygulayan bir değişkene eriştiğinde, kodunuzun nesneyi hala ifade ağacı tarafından tutulurken atma olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="05903-149">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="05903-150">Örneğin, `int` `IDisposable`uygulamadığından, bu kod düzgün çalışıyor:</span><span class="sxs-lookup"><span data-stu-id="05903-150">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="05903-151">Temsilci `constant`yerel değişkenine bir başvuru yakalamıştır.</span><span class="sxs-lookup"><span data-stu-id="05903-151">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="05903-152">Bu değişkene, daha sonra `CreateBoundFunc` tarafından döndürülen işlev çalıştırıldığında her zaman erişilir.</span><span class="sxs-lookup"><span data-stu-id="05903-152">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="05903-153">Ancak, `IDisposable`uygulayan (Bunun yerine contrived) sınıfını göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="05903-153">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

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

<span data-ttu-id="05903-154">Bunu aşağıda gösterildiği gibi bir ifadede kullanırsanız, `Resource.Argument` özelliği tarafından başvurulan kodu yürüttüğünüzde `ObjectDisposedException` alırsınız:</span><span class="sxs-lookup"><span data-stu-id="05903-154">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

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

<span data-ttu-id="05903-155">Bu yöntemden döndürülen temsilci, atılmış olan `constant` nesnesi üzerinde kapandı.</span><span class="sxs-lookup"><span data-stu-id="05903-155">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="05903-156">(Bir `using` bildiriminde bildirildiği için atılmış.)</span><span class="sxs-lookup"><span data-stu-id="05903-156">(It's been disposed, because it was declared in a `using` statement.)</span></span> 

<span data-ttu-id="05903-157">Artık bu yöntemden döndürülen temsilciyi yürüttüğünüzde, yürütme noktasında bir `ObjectDisposedException` oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="05903-157">Now, when you execute the delegate returned from this method, you'll have a `ObjectDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="05903-158">Derleme zamanı yapısını temsil eden bir çalışma zamanı hatası olması garip görünür, ancak bu, ifade ağaçları ile çalışırken girdiğimiz dünya.</span><span class="sxs-lookup"><span data-stu-id="05903-158">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="05903-159">Bu sorunun birçok permütasyon vardır. bu nedenle, bunu önlemek için genel rehberlik sunmak zordur.</span><span class="sxs-lookup"><span data-stu-id="05903-159">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="05903-160">İfadeleri tanımlarken yerel değişkenlere erişmede dikkatli olun ve genel bir API tarafından döndürülebilecek bir ifade ağacı oluştururken geçerli nesnedeki duruma (`this`göre gösterilen) erişme konusunda dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="05903-160">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="05903-161">Deyiminizdeki kod, diğer derlemelerdeki yöntemlere veya özelliklere başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="05903-161">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="05903-162">İfade tanımlandığında ve derlendikten sonra ve elde edilen temsilci çağrıldığında bu derlemeye erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="05903-162">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="05903-163">Mevcut olmadığı durumlarda `ReferencedAssemblyNotFoundException` karşılanır.</span><span class="sxs-lookup"><span data-stu-id="05903-163">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="05903-164">Özet</span><span class="sxs-lookup"><span data-stu-id="05903-164">Summary</span></span>

<span data-ttu-id="05903-165">Lambda ifadelerini temsil eden ifade ağaçları, yürütebilmeniz için bir temsilci oluşturmak üzere derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="05903-165">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="05903-166">Bu, bir ifade ağacı tarafından temsil edilen kodu yürütmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="05903-166">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="05903-167">Ifade ağacı, oluşturduğunuz herhangi bir yapı için yürütülecek kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="05903-167">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="05903-168">Kodu derlemek ve yürütmek istediğiniz ortam, ifadeyi oluşturduğunuz ortamla eşleşiyorsa, her şey beklendiği gibi çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="05903-168">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="05903-169">Bu durum gerçekleşmezse, hatalar çok öngörülebilir olur ve ifade ağaçları kullanılarak herhangi bir kodun ilk testlerinizde yakalanacaktır.</span><span class="sxs-lookup"><span data-stu-id="05903-169">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="05903-170">Sonraki--Ifadeleri yorumlama</span><span class="sxs-lookup"><span data-stu-id="05903-170">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)
