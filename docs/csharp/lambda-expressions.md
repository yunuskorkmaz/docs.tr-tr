---
title: Lambda İfadeleri
description: Bağımsız değişken olarak geçirilebilir yürütülebilir kod blokları lambda ifadeleri kullanma edinin.
ms.author: ronpet
author: rpetrusha
ms.date: 11/22/2016
ms.assetid: b6a0539a-8ce5-4da7-adcf-44be345a2714
ms.openlocfilehash: 2469e8a0fbf8181a720201637ab5ac5ef02055d4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400871"
---
# <a name="lambda-expressions"></a><span data-ttu-id="9dde3-103">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="9dde3-103">Lambda expressions</span></span> #

<span data-ttu-id="9dde3-104">A *lambda ifadesi* (bir ifadeyi veya deyim bloğunu) bir nesne olarak işlem kod bloğudur.</span><span class="sxs-lookup"><span data-stu-id="9dde3-104">A *lambda expression* is a block of code (an expression or a statement block) that is treated as an object.</span></span> <span data-ttu-id="9dde3-105">Yöntemi için bağımsız değişken olarak geçirilebilir ve yöntem çağrıları tarafından da döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="9dde3-105">It can be passed as an argument to methods, and it can also be returned by method calls.</span></span> <span data-ttu-id="9dde3-106">Lambda ifadeleri için yaygın olarak kullanılır:</span><span class="sxs-lookup"><span data-stu-id="9dde3-106">Lambda expressions are used extensively for:</span></span>

- <span data-ttu-id="9dde3-107">Kod geçirmeden olduğu gibi zaman uyumsuz yöntemler için yürütülecek <xref:System.Threading.Tasks.Task.Run(System.Action)>.</span><span class="sxs-lookup"><span data-stu-id="9dde3-107">Passing the code that is to be executed to asynchronous methods, such as <xref:System.Threading.Tasks.Task.Run(System.Action)>.</span></span>

- <span data-ttu-id="9dde3-108">Yazma [LINQ Sorgu ifadeleri](linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="9dde3-108">Writing [LINQ query expressions](linq/index.md).</span></span>

- <span data-ttu-id="9dde3-109">Oluşturma [ifade ağaçları](expression-trees-building.md).</span><span class="sxs-lookup"><span data-stu-id="9dde3-109">Creating [expression trees](expression-trees-building.md).</span></span>

<span data-ttu-id="9dde3-110">Lambda ifadeleri temsilci olarak veya bir ifade ağacına derleyen bir temsilciye olarak gösterilen kodu var.</span><span class="sxs-lookup"><span data-stu-id="9dde3-110">Lambda expressions are code that can be represented either as a delegate, or as an expression tree that compiles to a delegate.</span></span> <span data-ttu-id="9dde3-111">Bir lambda ifadesinin özel temsilci türü kendi parametrelerine göre değişir ve dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="9dde3-111">The specific delegate type of a lambda expression depends on its parameters and return value.</span></span> <span data-ttu-id="9dde3-112">Bir değer döndürmeyen bir lambda ifadeleri, belirli bir karşılık gelen `Action` , parametreleri, sayısına bağlı olarak temsilci.</span><span class="sxs-lookup"><span data-stu-id="9dde3-112">Lambda expressions that don't return a value correspond to a specific `Action` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="9dde3-113">Bir değer döndüren bir lambda ifadeleri, belirli bir karşılık gelen `Func` , parametreleri, sayısına bağlı olarak temsilci.</span><span class="sxs-lookup"><span data-stu-id="9dde3-113">Lambda expressions that return a value correspond to a specific `Func` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="9dde3-114">Örneğin, iki parametreye sahip ancak hiçbir değer döndürmeyen bir lambda ifadesi için karşılık gelen bir <xref:System.Action%602> temsilci.</span><span class="sxs-lookup"><span data-stu-id="9dde3-114">For example, a lambda expression that has two parameters but returns no value corresponds to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="9dde3-115">Bir parametreye sahiptir ve bir değer döndüren bir lambda ifadesi karşılık gelen <xref:System.Func%602> temsilci.</span><span class="sxs-lookup"><span data-stu-id="9dde3-115">A lambda expression that has one parameter and returns a value corresponds to <xref:System.Func%602> delegate.</span></span>

<span data-ttu-id="9dde3-116">Bir lambda ifadesi kullanır `=>`, [lambda bildirimi işleci](language-reference/operators/lambda-operator.md), lambdanın parametre listesi, yürütülebilir kodundan ayırın.</span><span class="sxs-lookup"><span data-stu-id="9dde3-116">A lambda expression uses `=>`, the [lambda declaration operator](language-reference/operators/lambda-operator.md), to separate the lambda's parameter list from its executable code.</span></span> <span data-ttu-id="9dde3-117">Bir lambda ifadesi oluşturmak için giriş parametreleri (varsa) lambda işlecinin sol tarafında belirtin ve ifadeyi veya deyim bloğunu diğer tarafa yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="9dde3-117">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator, and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="9dde3-118">Örneğin, tek satırlı lambda ifadesi `x => x * x` adlı bir parametre belirtir `x` ve değerini döndürür `x` karesi alınmış.</span><span class="sxs-lookup"><span data-stu-id="9dde3-118">For example, the single-line lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="9dde3-119">Bu ifadeyi aşağıdaki örnekte gösterildiği gibi bir temsilci türüne atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9dde3-119">You can assign this expression to a delegate type, as the following example shows:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda1.cs#1)]

<span data-ttu-id="9dde3-120">Veya doğrudan bir yöntemi bağımsız değişken geçirin:</span><span class="sxs-lookup"><span data-stu-id="9dde3-120">Or you can pass it directly as a method argument:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda2.cs#2)]

## <a name="expression-lambdas"></a><span data-ttu-id="9dde3-121">İfade lambdaları</span><span class="sxs-lookup"><span data-stu-id="9dde3-121">Expression lambdas</span></span> ##

 <span data-ttu-id="9dde3-122">Bir lambda ifadesi işlecin sağ tarafındaki bir ifadeyle = > işleci çağrıldığında bir *lambda ifadesi*.</span><span class="sxs-lookup"><span data-stu-id="9dde3-122">A lambda expression with an expression on the right side of the => operator is called an *expression lambda*.</span></span> <span data-ttu-id="9dde3-123">İfade lambdaları oluşumunu oluşturulurken sıkça kullanılır [ifade ağaçları](expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="9dde3-123">Expression lambdas are used extensively in the construction of [expression trees](expression-trees.md).</span></span> <span data-ttu-id="9dde3-124">Bir lambda ifadesi, ifadenin sonucunu verir ve aşağıdaki temel biçimi alır:</span><span class="sxs-lookup"><span data-stu-id="9dde3-124">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input parameters) => expression
```

<span data-ttu-id="9dde3-125">Parantezler yalnızca lambdanın bir çıktı parametresi varsa isteğe bağlıdır; aksi takdirde bunlar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9dde3-125">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span> <span data-ttu-id="9dde3-126">Boş ayraçlarla sıfır giriş parametrelerini belirtin:</span><span class="sxs-lookup"><span data-stu-id="9dde3-126">Specify zero input parameters with empty parentheses:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#1)]

<span data-ttu-id="9dde3-127">İki veya daha fazla giriş parametresi, ayraç içinde virgülle ayrılır:</span><span class="sxs-lookup"><span data-stu-id="9dde3-127">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#2)]

<span data-ttu-id="9dde3-128">Normalde, derleyici tür çıkarımı, parametre türleri belirlemede kullanır.</span><span class="sxs-lookup"><span data-stu-id="9dde3-128">Ordinarily, the compiler uses type inference in determining parameter types.</span></span> <span data-ttu-id="9dde3-129">Ancak, bazen zor veya imkansız derleyicinin giriş türlerini çıkarması öyledir.</span><span class="sxs-lookup"><span data-stu-id="9dde3-129">However, sometimes it is difficult or impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="9dde3-130">Bu durumda türleri aşağıdaki örnekte olduğu gibi açıkça belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9dde3-130">When this occurs, you can specify the types explicitly, as in the following example:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#3)]

<span data-ttu-id="9dde3-131">Önceki örnekte bir lambda ifadesi gövdesinin yöntem çağrısından oluşabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9dde3-131">Note in the previous example that the body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="9dde3-132">.NET Framework dışında değerlendirilen ifade ağaçları oluşturuyorsanız, ancak gibi SQL Server veya Entity Framework (EF), yöntem bağlamı dışında anlamlı olabileceği yöntem çağrıları lambda ifadelerinde kullanmadığınızdan .NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="9dde3-132">However, if you are creating expression trees that are evaluated outside of the .NET Framework, such as in SQL Server or Entity Framework (EF), you should refrain from using method calls in lambda expressions, since the methods may have no meaning outside the context of the .NET implementation.</span></span> <span data-ttu-id="9dde3-133">Bu durumda yöntem çağrılarını kullanmayı seçerseniz, bunları çağrıları başarıyla çözümlenip yöntemi kapsamlı emin olmak için test etmeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9dde3-133">If you do choose to use method calls in this case, be sure to test them thoroughly to ensure that the method calls can be successfuly resolved.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="9dde3-134">Deyim lambdaları</span><span class="sxs-lookup"><span data-stu-id="9dde3-134">Statement lambdas</span></span> ##

<span data-ttu-id="9dde3-135">Ayraçlar arasındaki deyimler hariç statement lambda, expression lambda'ya benzer:</span><span class="sxs-lookup"><span data-stu-id="9dde3-135">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp
(input parameters) => { statement; }
```

<span data-ttu-id="9dde3-136">Bir lambda deyiminin gövdesi herhangi bir sayıda deyimden oluşabilir; ancak, uygulamada genellikle iki veya üçten fazla değildir.</span><span class="sxs-lookup"><span data-stu-id="9dde3-136">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/statement1.cs#1)]

<span data-ttu-id="9dde3-137">Anonim yöntemler gibi deyim lambdaları da ifade ağacı oluşturmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9dde3-137">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="9dde3-138">Zaman uyumsuz lambdalar</span><span class="sxs-lookup"><span data-stu-id="9dde3-138">Async lambdas</span></span> ##

<span data-ttu-id="9dde3-139">İçeren kullanarak zaman uyumsuz işleme içeren lambda ifadeleri ve deyimlerini kolayca oluşturabilirsiniz [zaman uyumsuz](language-reference/keywords/async.md) ve [await](language-reference/keywords/await.md) anahtar sözcükleri.</span><span class="sxs-lookup"><span data-stu-id="9dde3-139">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](language-reference/keywords/async.md) and [await](language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="9dde3-140">Örneğin, örnek çağıran bir `ShowSquares` yöntemi zaman uyumsuz olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="9dde3-140">For example, the example calls a `ShowSquares` method that executes asynchronously.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/async1.cs#1)]

<span data-ttu-id="9dde3-141">Oluşturma ve zaman uyumsuz yöntemler kullanma hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlama ile zaman uyumsuz ve await](programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="9dde3-141">For more information about how to create and use async methods, see [Asynchronous programming with async and await](programming-guide/concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="9dde3-142">Lambda ifadeleri ve diziler</span><span class="sxs-lookup"><span data-stu-id="9dde3-142">Lambda expressions and tuples</span></span> ##

<span data-ttu-id="9dde3-143">C# 7.0 ile başlayarak, C# dili diziler için yerleşik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="9dde3-143">Starting with C# 7.0, the C# language provides built-in support for tuples.</span></span> <span data-ttu-id="9dde3-144">Bir lambda ifadesi bağımsız değişkeni olarak bir tanımlama grubu sağlayabilir ve, lambda ifadesi, ayrıca bir demet döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="9dde3-144">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="9dde3-145">Bazı durumlarda, tanımlama grubu bileşenleri türlerini belirlemek için tür çıkarımı C# derleyicisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9dde3-145">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="9dde3-146">Bir dizi, parantez içine alarak bileşenlerinden virgülle ayrılmış bir listesini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9dde3-146">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="9dde3-147">Aşağıdaki örnek, her değerin iki katına çıkar ve multiplications sonucunu içeren bir tanımlama grubu 5 bileşenlerle döndüren bir lambda ifadesi için bir sayı dizisi üzerinde geçirilecek 5 bileşenleri ile tanımlama grubu kullanır.</span><span class="sxs-lookup"><span data-stu-id="9dde3-147">The following example uses tuple with 5 components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with 5 components that contains the result of the multiplications.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples1.cs#1)]

<span data-ttu-id="9dde3-148">Normalde, bir kayıt düzeni alanlarını olarak da adlandırılır `Item1`, `Item2`vb. Ancak, aşağıdaki örnekte olduğu gibi bir dizi adlandırılmış bileşenlerle tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dde3-148">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples2.cs#1)]

<span data-ttu-id="9dde3-149">C# ' de tanımlama gruplarına yönelik destek hakkında daha fazla bilgi için bkz. [C# demet türleri](tuples.md).</span><span class="sxs-lookup"><span data-stu-id="9dde3-149">For more information on support for tuples in C#, see [C# Tuple types](tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="9dde3-150">Standart sorgu işleçleri ile lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="9dde3-150">Lambdas with the standard query operators</span></span> ##

<span data-ttu-id="9dde3-151">LINQ to Objects'in, diğer uygulamalar arasında olması, türü giriş parametresi, <xref:System.Func%601> Genel temsilci ailesinden olan.</span><span class="sxs-lookup"><span data-stu-id="9dde3-151">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="9dde3-152">Bu Temsilciler, tür parametreleri sayısı ve girdi parametrelerinin türünü ve temsilcinin dönüş türünü tanımlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9dde3-152">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="9dde3-153">`Func` Temsilciler, kaynak veri kümesindeki her öğeye uygulanan kullanıcı tanımlı ifadelerin Kapsüllenmesi için son çok yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="9dde3-153">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="9dde3-154">Örneğin, düşünün <xref:System.Func%601> temsilci, söz dizimi şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="9dde3-154">For example, consider the <xref:System.Func%601> delegate, whose syntax is:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#1)]

<span data-ttu-id="9dde3-155">Temsilci, aşağıdaki gibi kod kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="9dde3-155">The delegate can be instantiated with code like the following</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#2)]

<span data-ttu-id="9dde3-156">Burada `int` bir giriş parametresi ve `bool` dönüş değeridir.</span><span class="sxs-lookup"><span data-stu-id="9dde3-156">where `int` is an input parameter, and `bool` is the return value.</span></span> <span data-ttu-id="9dde3-157">Dönüş değeri her zaman son tür parametresinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="9dde3-157">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="9dde3-158">Aşağıdaki `Func` temsilcisi çağrıldığında, true veya false giriş parametresinin 5'e eşit olup olmadığını belirtmek için döndürür:</span><span class="sxs-lookup"><span data-stu-id="9dde3-158">When the following `Func` delegate is invoked, it returns true or false to indicate whether the input parameter is equal to 5:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#3)]

<span data-ttu-id="9dde3-159">Ayrıca bağımsız değişken türü bir lambda ifadesi sağlayabilirsiniz bir <xref:System.Linq.Expressions.Expression%601>, örneğin tanımlanan standart sorgu işleçleri içinde <xref:System.Linq.Queryable> türü.</span><span class="sxs-lookup"><span data-stu-id="9dde3-159">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="9dde3-160">Belirttiğinizde bir <xref:System.Linq.Expressions.Expression%601> bağımsız değişkeni, lambda ifade ağacında derlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="9dde3-160">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span> <span data-ttu-id="9dde3-161">Aşağıdaki örnekte [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) standart sorgu işleci.</span><span class="sxs-lookup"><span data-stu-id="9dde3-161">The following example uses the [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) standard query operator.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#4)]

<span data-ttu-id="9dde3-162">Derleyici giriş parametresinin türünü çıkarabilir veya bunu açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dde3-162">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="9dde3-163">Bu belirli lambda ifadesi tamsayıları sayar (`n`), ikiye bölündüğünde 1 kalan sahip.</span><span class="sxs-lookup"><span data-stu-id="9dde3-163">This particular lambda expression counts those integers (`n`) that, when divided by two, have a remainder of 1.</span></span>

<span data-ttu-id="9dde3-164">Aşağıdaki örnekte tüm öğelerini içeren bir dizi üretir `numbers` , dizisinde koşulu sağlamayan ilk sayı olduğundan 9 önünde bir dizi.</span><span class="sxs-lookup"><span data-stu-id="9dde3-164">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#5)]

<span data-ttu-id="9dde3-165">Aşağıdaki örnek, birden fazla giriş parametrelerini paranteze tarafından belirtir.</span><span class="sxs-lookup"><span data-stu-id="9dde3-165">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="9dde3-166">Yöntem dizi içindeki sıralı konumu'den küçük sayılar dizi değeri bir sayı karşılaşana kadar tüm öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="9dde3-166">The method returns all the elements in the numbers array until it encounters a number whose value is less than its ordinal position in the array.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#6)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="9dde3-167">Lambda ifadeleri içinde tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="9dde3-167">Type inference in lambda expressions</span></span> ##

<span data-ttu-id="9dde3-168">Lambda ifadeleri yazarken, genellikle C# dil Belirtimi'nde açıklanan derleyici lambda gövdesine, parametre türleri ve diğer etkenlere göre türü belirleyebilir giriş parametreleri için bir tür belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9dde3-168">When writing lambdas, you often do not have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors, as described in the C# Language Specification.</span></span> <span data-ttu-id="9dde3-169">Standart sorgu işleçlerinin çoğunda ilk giriş kaynak dizisindeki öğelerin türüdür.</span><span class="sxs-lookup"><span data-stu-id="9dde3-169">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="9dde3-170">Sorguluyorsanız bir `IEnumerable<Customer>`, giriş değişkeni olması sorguluyorsanız bir `Customer` nesne erişim yöntemleri ve özellikleri iznine sahip olduğunuz anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="9dde3-170">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/infer1.cs#1)]

<span data-ttu-id="9dde3-171">Lambdalar için tür çıkarımı için genel kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9dde3-171">The general rules for type inference for lambdas are:</span></span>

- <span data-ttu-id="9dde3-172">Lambda temsilci türüyle aynı sayıda parametre içermelidir.</span><span class="sxs-lookup"><span data-stu-id="9dde3-172">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="9dde3-173">Lambdadaki her bir giriş bağımsız değişkeni, karşılık gelen temsilci parametresine dolaylı olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9dde3-173">Each input argument in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="9dde3-174">Lambdanın (varsa) dönüş değeri örtük olarak temsilcinin dönüş türüne dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9dde3-174">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>

<span data-ttu-id="9dde3-175">Ortak tür sisteminin "lambda ifadesi" için iç kavramı olmadığından kendi içlerindeki lambda ifadelerinin türü olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9dde3-175">Note that lambda expressions in themselves do not have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="9dde3-176">Ancak bazen bir lambda ifadesinin "türünden" resmi olmayan bir şekilde bahsetmek daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="9dde3-176">However, it is sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="9dde3-177">Bu gibi durumlarda, tür temsilci türüne başvuruyor. veya <xref:System.Linq.Expressions.Expression> , lambda ifadesinin dönüştürüldüğü yazın.</span><span class="sxs-lookup"><span data-stu-id="9dde3-177">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="9dde3-178">Lambda İfadelerinde Değişken Kapsamı</span><span class="sxs-lookup"><span data-stu-id="9dde3-178">Variable Scope in Lambda Expressions</span></span> ##

<span data-ttu-id="9dde3-179">Lambdalar başvurabilir *dış değişkenlere* (bkz [anonim yöntemler](programming-guide/statements-expressions-operators/anonymous-methods.md)), lambda işlevini tanımlayan yöntemin kapsamındaki ya da lambda ifadesini içeren türün kapsamındaki.</span><span class="sxs-lookup"><span data-stu-id="9dde3-179">Lambdas can refer to *outer variables* (see [Anonymous methods](programming-guide/statements-expressions-operators/anonymous-methods.md)) that are in scope in the method that defines the lambda function, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="9dde3-180">Bu şekilde tutulan değişkenler, aksi halde kapsam dışına çıkacak ve çöp olarak toplanacak olsalar dahi kullanılmak üzere lambda ifadesinde saklanır.</span><span class="sxs-lookup"><span data-stu-id="9dde3-180">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="9dde3-181">Bir lambda ifadesinde tüketilebilmesi için öncelikle mutlaka bir harici değişken tayin edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="9dde3-181">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="9dde3-182">Aşağıdaki örnek bu kuralları gösterir.</span><span class="sxs-lookup"><span data-stu-id="9dde3-182">The following example demonstrates these rules.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/scope.cs#1)]

 <span data-ttu-id="9dde3-183">Lambda ifadelerindeki değişken kapsam için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="9dde3-183">The following rules apply to variable scope in lambda expressions:</span></span>

- <span data-ttu-id="9dde3-184">Tutulan bir değişkenin kullandığı bellek, ona başvuran temsilcinin kullandığı bellek geri kazanılmaya hazır hale gelinceye kadar geri kazanılmaz.</span><span class="sxs-lookup"><span data-stu-id="9dde3-184">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="9dde3-185">Bir lambda ifadesi içinde tanıtılan değişkenler, dış yöntemde görünmez.</span><span class="sxs-lookup"><span data-stu-id="9dde3-185">Variables introduced within a lambda expression are not visible in the outer method.</span></span>

- <span data-ttu-id="9dde3-186">Bir lambda ifadesini doğrudan yakalayamaz bir `in`, `ref`, veya `out` parametresi kapsayan bir yöntemden alınan.</span><span class="sxs-lookup"><span data-stu-id="9dde3-186">A lambda expression cannot directly capture an `in`, `ref`, or `out` parameter from an enclosing method.</span></span>

- <span data-ttu-id="9dde3-187">Lambda ifadesindeki bir dönüş ifadesi, kapsayan yöntemin döndürülmesine neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="9dde3-187">A return statement in a lambda expression does not cause the enclosing method to return.</span></span>

- <span data-ttu-id="9dde3-188">Bir lambda ifadesi içeremez bir `goto` deyimi `break` deyimi veya `continue` varsa atlama bildiriminin hedefi blok dışındaysa lambda işlevi içinde deyimi.</span><span class="sxs-lookup"><span data-stu-id="9dde3-188">A lambda expression cannot contain a `goto` statement, `break` statement, or `continue` statement that is inside the lambda function if the jump statement’s target is outside the block.</span></span> <span data-ttu-id="9dde3-189">Ayrıca, hedef, blok içinde ise lambda işlev bloğu dışında bir deyim olması bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="9dde3-189">It is also an error to have a jump statement outside the lambda function block if the target is inside the block.</span></span>

## <a name="see-also"></a><span data-ttu-id="9dde3-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dde3-190">See also</span></span> ##

- [<span data-ttu-id="9dde3-191">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="9dde3-191">LINQ (Language-Integrated Query)</span></span>](../standard/using-linq.md)
- [<span data-ttu-id="9dde3-192">Anonim yöntemler</span><span class="sxs-lookup"><span data-stu-id="9dde3-192">Anonymous methods</span></span>](programming-guide/statements-expressions-operators/anonymous-methods.md)
- [<span data-ttu-id="9dde3-193">İfade ağaçları</span><span class="sxs-lookup"><span data-stu-id="9dde3-193">Expression trees</span></span>](expression-trees.md)
