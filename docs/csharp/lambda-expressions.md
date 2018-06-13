---
title: Lambda İfadeleri
description: Bağımsız değişken olarak geçirilen yürütülebilir kod blokları lambda ifadeleri kullanma yalın.
ms.author: ronpet
author: rpetrusha
ms.date: 11/22/2016
ms.assetid: b6a0539a-8ce5-4da7-adcf-44be345a2714
ms.openlocfilehash: e37f0e72ee02915d16509fb2ff48bd114e8ad466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217980"
---
# <a name="lambda-expressions"></a><span data-ttu-id="2e712-103">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="2e712-103">Lambda expressions</span></span> #

<span data-ttu-id="2e712-104">A *lambda ifadesi* bir nesne olarak kabul edilir kodu (bir deyim veya bir ifade bloğu) bloğudur.</span><span class="sxs-lookup"><span data-stu-id="2e712-104">A *lambda expression* is a block of code (an expression or a statement block) that is treated as an object.</span></span> <span data-ttu-id="2e712-105">Yöntemlere bağımsız değişken olarak geçirilebilir ve ayrıca yöntem çağrıları tarafından döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="2e712-105">It can be passed as an argument to methods, and it can also be returned by method calls.</span></span> <span data-ttu-id="2e712-106">Lambda ifadeleri için yaygın olarak kullanılır:</span><span class="sxs-lookup"><span data-stu-id="2e712-106">Lambda expressions are used extensively for:</span></span>

- <span data-ttu-id="2e712-107">Kod geçirme olduğu gibi zaman uyumsuz yöntemleri için yürütülecek <xref:System.Threading.Tasks.Task.Run(System.Action)>.</span><span class="sxs-lookup"><span data-stu-id="2e712-107">Passing the code that is to be executed to asynchronous methods, such as <xref:System.Threading.Tasks.Task.Run(System.Action)>.</span></span>

- <span data-ttu-id="2e712-108">Yazma [LINQ Sorgu ifadeleri](linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="2e712-108">Writing [LINQ query expressions](linq/index.md).</span></span>

- <span data-ttu-id="2e712-109">Oluşturma [ifade ağaçları](expression-trees-building.md).</span><span class="sxs-lookup"><span data-stu-id="2e712-109">Creating [expression trees](expression-trees-building.md).</span></span>

<span data-ttu-id="2e712-110">Lambda ifadeleri temsilci olarak ya da bir temsilciye derlenen bir ifade ağacına olarak temsil edilebilir kodu var.</span><span class="sxs-lookup"><span data-stu-id="2e712-110">Lambda expressions are code that can be represented either as a delegate, or as an expression tree that compiles to a delegate.</span></span> <span data-ttu-id="2e712-111">Lambda ifadesi belirli temsilci türü kendi parametrelerine göre değişir ve değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2e712-111">The specific delegate type of a lambda expression depends on its parameters and return value.</span></span> <span data-ttu-id="2e712-112">Bir değer döndürmez lambda ifadeleri karşılık gelen belirli bir `Action` , parametreleri, sayısına bağlı olarak temsilci.</span><span class="sxs-lookup"><span data-stu-id="2e712-112">Lambda expressions that don't return a value correspond to a specific `Action` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="2e712-113">Bir değer döndürmesi lambda ifadeleri karşılık gelen belirli bir `Func` , parametreleri, sayısına bağlı olarak temsilci.</span><span class="sxs-lookup"><span data-stu-id="2e712-113">Lambda expressions that return a value correspond to a specific `Func` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="2e712-114">Örneğin, iki parametreye sahip ancak hiçbir değer döndürmeyen bir lambda ifadesi için karşılık gelen bir <xref:System.Action%602> temsilci.</span><span class="sxs-lookup"><span data-stu-id="2e712-114">For example, a lambda expression that has two parameters but returns no value corresponds to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="2e712-115">Bir parametre içeriyor ve bir değer döndüren bir lambda ifadesi karşılık gelen <xref:System.Func%602> temsilci.</span><span class="sxs-lookup"><span data-stu-id="2e712-115">A lambda expression that has one parameter and returns a value corresponds to <xref:System.Func%602> delegate.</span></span>

<span data-ttu-id="2e712-116">Lambda ifadesi kullanan `=>`, [lambda bildirimi işleci](language-reference/operators/lambda-operator.md), yürütülebilir koddan lambda ait parametre listesi ayırmak için.</span><span class="sxs-lookup"><span data-stu-id="2e712-116">A lambda expression uses `=>`, the [lambda declaration operator](language-reference/operators/lambda-operator.md), to separate the lambda's parameter list from its executable code.</span></span> <span data-ttu-id="2e712-117">Lambda ifadesi oluşturmak için giriş parametreleri (varsa) lambda işlecinin sol tarafında belirtin ve diğer tarafta ifade veya deyimin blok yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="2e712-117">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator, and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="2e712-118">Örneğin, tek satırlı lambda ifadesi `x => x * x` adlı bir parametre belirtir `x` ve değerini döndürür `x` karesi alınmış.</span><span class="sxs-lookup"><span data-stu-id="2e712-118">For example, the single-line lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="2e712-119">Bu ifadeyi aşağıdaki örnekte gösterildiği gibi bir temsilci türüne atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2e712-119">You can assign this expression to a delegate type, as the following example shows:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda1.cs#1)]

<span data-ttu-id="2e712-120">Veya doğrudan bir yöntem bağımsız değişken olarak geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2e712-120">Or you can pass it directly as a method argument:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda2.cs#2)]

## <a name="expression-lambdas"></a><span data-ttu-id="2e712-121">İfade lambdas</span><span class="sxs-lookup"><span data-stu-id="2e712-121">Expression lambdas</span></span> ##

 <span data-ttu-id="2e712-122">Bir lambda ifadesi ile sağ tarafında bir ifade = > işleci adlı bir *lambda ifadesi*.</span><span class="sxs-lookup"><span data-stu-id="2e712-122">A lambda expression with an expression on the right side of the => operator is called an *expression lambda*.</span></span> <span data-ttu-id="2e712-123">İfade lambdas yaygın yapımı içinde kullanılan [ifade ağaçları](expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="2e712-123">Expression lambdas are used extensively in the construction of [expression trees](expression-trees.md).</span></span> <span data-ttu-id="2e712-124">Bir lambda ifadesi, ifadenin sonucunu verir ve aşağıdaki temel biçimi alır:</span><span class="sxs-lookup"><span data-stu-id="2e712-124">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input parameters) => expression
```

<span data-ttu-id="2e712-125">Parantezler yalnızca lambdanın bir çıktı parametresi varsa isteğe bağlıdır; aksi takdirde bunlar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2e712-125">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span> <span data-ttu-id="2e712-126">Boş ayraçlarla sıfır giriş parametrelerini belirtin:</span><span class="sxs-lookup"><span data-stu-id="2e712-126">Specify zero input parameters with empty parentheses:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#1)]

<span data-ttu-id="2e712-127">İki veya daha fazla giriş parametresi, ayraç içinde virgülle ayrılır:</span><span class="sxs-lookup"><span data-stu-id="2e712-127">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#2)]

<span data-ttu-id="2e712-128">Normalde, derleyici tür çıkarımı parametre türleri belirlemede kullanır.</span><span class="sxs-lookup"><span data-stu-id="2e712-128">Ordinarily, the compiler uses type inference in determining parameter types.</span></span> <span data-ttu-id="2e712-129">Ancak bazen zor veya giriş türlerinin gerçekleştirip derleyici mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="2e712-129">However, sometimes it is difficult or impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="2e712-130">Bu durumda, aşağıdaki örnekte olduğu gibi açıkça olarak türü belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2e712-130">When this occurs, you can specify the types explicitly, as in the following example:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#3)]

<span data-ttu-id="2e712-131">Önceki örnekte bir lambda ifadesi gövdesinin yöntem çağrısından oluşabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2e712-131">Note in the previous example that the body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="2e712-132">.NET Framework dışında değerlendirilen ifade ağaçları oluşturuyorsanız, ancak gibi SQL Server veya Entity Framework (EF), yöntem bağlamı dışında hiçbir anlamı sağlanmış olabileceği yöntem çağrıları lambda ifadeleri kullanmamalıdır .NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="2e712-132">However, if you are creating expression trees that are evaluated outside of the .NET Framework, such as in SQL Server or Entity Framework (EF), you should refrain from using method calls in lambda expressions, since the methods may have no meaning outside the context of the .NET implementation.</span></span> <span data-ttu-id="2e712-133">Yöntem çağrıları bu durumda kullanmayı seçerseniz, onları çağrıları başarıyla çözülebilir yöntemi baştan sona emin olmak için test emin olun.</span><span class="sxs-lookup"><span data-stu-id="2e712-133">If you do choose to use method calls in this case, be sure to test them thoroughly to ensure that the method calls can be successfuly resolved.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="2e712-134">Deyimi lambdas</span><span class="sxs-lookup"><span data-stu-id="2e712-134">Statement lambdas</span></span> ##

<span data-ttu-id="2e712-135">Ayraçlar arasındaki deyimler hariç statement lambda, expression lambda'ya benzer:</span><span class="sxs-lookup"><span data-stu-id="2e712-135">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp
(input parameters) => { statement; }
```

<span data-ttu-id="2e712-136">Bir lambda deyiminin gövdesi herhangi bir sayıda deyimden oluşabilir; ancak, uygulamada genellikle iki veya üçten fazla değildir.</span><span class="sxs-lookup"><span data-stu-id="2e712-136">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/statement1.cs#1)]

<span data-ttu-id="2e712-137">Anonim yöntemler gibi deyim lambdaları da ifade ağacı oluşturmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2e712-137">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="2e712-138">Zaman uyumsuz lambdas</span><span class="sxs-lookup"><span data-stu-id="2e712-138">Async lambdas</span></span> ##

<span data-ttu-id="2e712-139">Lambda ifadeleri ve kullanarak zaman uyumsuz işleme dahil deyimleri kolayca oluşturabilirsiniz [zaman uyumsuz](language-reference/keywords/async.md) ve [await](language-reference/keywords/await.md) anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="2e712-139">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](language-reference/keywords/async.md) and [await](language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="2e712-140">Örneğin, örnek çağıran bir `ShowSquares` yöntemi zaman uyumsuz olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="2e712-140">For example, the example calls a `ShowSquares` method that executes asynchronously.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/async1.cs#1)]

<span data-ttu-id="2e712-141">Oluşturma ve zaman uyumsuz yöntemler kullanma hakkında daha fazla bilgi için bkz [zaman uyumsuz programlama ile async ve await](programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="2e712-141">For more information about how to create and use async methods, see [Asynchronous programming with async and await](programming-guide/concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="2e712-142">Lambda ifadeleri ve diziler</span><span class="sxs-lookup"><span data-stu-id="2e712-142">Lambda expressions and tuples</span></span> ##

<span data-ttu-id="2e712-143">C# 7. 0'dan başlayarak, C# dili diziler için yerleşik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e712-143">Starting with C# 7.0, the C# language provides built-in support for tuples.</span></span> <span data-ttu-id="2e712-144">Lambda ifadesi bağımsız değişkeni olarak bir tanımlama grubu sağlayabilir ve lambda ifadesi bir tanımlama grubu geri dönebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e712-144">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="2e712-145">Bazı durumlarda, C# derleyici tür çıkarımı tanımlama grubu bileşenleri türlerini belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="2e712-145">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span> 

<span data-ttu-id="2e712-146">Parantez içinde virgülle ayrılmış bir liste bileşenlerini kapsayan tarafından bir tanımlama grubu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="2e712-146">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="2e712-147">Aşağıdaki örnek, her değerin iki katına çıkar ve multiplications sonucunu içeren bir tanımlama grubu 5 bileşenlerle döndüren bir lambda ifadesi için sayılardan oluşan bir dizi geçirmek için 5 bileşenleri ile tanımlama grubu kullanır.</span><span class="sxs-lookup"><span data-stu-id="2e712-147">The following example uses tuple with 5 components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with 5 components that contains the result of the multiplications.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples1.cs#1)]

<span data-ttu-id="2e712-148">Normalde, bir tanımlama grubu alanlarının adlı `Item1`, `Item2`vb. Ancak, aşağıdaki örnekte olduğu gibi bir tanımlama grubu adlandırılmış bileşenlerle tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e712-148">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples2.cs#1)]

<span data-ttu-id="2e712-149">C# diziler desteği hakkında daha fazla bilgi için bkz: [C# kayıt türlerinin](tuples.md).</span><span class="sxs-lookup"><span data-stu-id="2e712-149">For more information on support for tuples in C#, see [C# Tuple types](tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="2e712-150">Standart sorgu işleçleri ile Lambdas</span><span class="sxs-lookup"><span data-stu-id="2e712-150">Lambdas with the standard query operators</span></span> ##

<span data-ttu-id="2e712-151">Diğer uygulamalardan arasında nesnelere LINQ türü olan bir giriş parametresi vardır, <xref:System.Func%601> genel temsilciler ailesi.</span><span class="sxs-lookup"><span data-stu-id="2e712-151">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="2e712-152">Bu temsilci tür parametreleri sayısı ve türü giriş parametreleri ve temsilci dönüş türünü tanımlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="2e712-152">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="2e712-153">`Func` Temsilciler kaynak veri kümesindeki her öğeye uygulanan kullanıcı tanımlı ifadeleri kapsüllemek için çok kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="2e712-153">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="2e712-154">Örneğin, göz önünde bulundurun <xref:System.Func%601> temsilci, olan sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="2e712-154">For example, consider the <xref:System.Func%601> delegate, whose syntax is:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#1)]

<span data-ttu-id="2e712-155">Temsilci, aşağıdaki gibi bir kod kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="2e712-155">The delegate can be instantiated with code like the following</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#2)]

<span data-ttu-id="2e712-156">Burada `int` bir girdi parametresi ve `bool` dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="2e712-156">where `int` is an input parameter, and `bool` is the return value.</span></span> <span data-ttu-id="2e712-157">Dönüş değeri her zaman son tür parametresinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="2e712-157">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="2e712-158">Aşağıdaki `Func` temsilci çağrıldığında, true veya false giriş parametresi 5'e eşit olup olmadığını belirtmek için döndürür:</span><span class="sxs-lookup"><span data-stu-id="2e712-158">When the following `Func` delegate is invoked, it returns true or false to indicate whether the input parameter is equal to 5:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#3)]

<span data-ttu-id="2e712-159">Bağımsız değişken türü olduğunda, aynı zamanda bir lambda ifadesi sağlayabilir bir <xref:System.Linq.Expressions.Expression%601>, örneğin tanımlanan standart sorgu işleçleri içinde <xref:System.Linq.Queryable> türü.</span><span class="sxs-lookup"><span data-stu-id="2e712-159">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="2e712-160">Belirttiğinizde bir <xref:System.Linq.Expressions.Expression%601> bağımsız değişkeni, lambda bir ifade ağacına derlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="2e712-160">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span> <span data-ttu-id="2e712-161">Aşağıdaki örnek kullanır [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) standart sorgu işleci.</span><span class="sxs-lookup"><span data-stu-id="2e712-161">The following example uses the [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) standard query operator.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#4)]

<span data-ttu-id="2e712-162">Derleyici giriş parametresinin türünü çıkarabilir veya bunu açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e712-162">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="2e712-163">Bu belirli lambda ifadesi bu tamsayılar sayar (`n`), iki tarafından bölünmüş olduğunda 1 kalanı vardır.</span><span class="sxs-lookup"><span data-stu-id="2e712-163">This particular lambda expression counts those integers (`n`) that, when divided by two, have a remainder of 1.</span></span>

<span data-ttu-id="2e712-164">Aşağıdaki örnek, tüm öğeleri içeren bir sıra üretir `numbers` bu koşulu karşılamıyor sıradaki ilk sayı olduğundan, 9 koyun dizi.</span><span class="sxs-lookup"><span data-stu-id="2e712-164">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#5)]

<span data-ttu-id="2e712-165">Aşağıdaki örnek, parantez içinde kapsayan tarafından birden çok giriş parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e712-165">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="2e712-166">Metodu tüm öğeleri sıralı konumuna dizideki'den küçük değeri bir sayı bulduğu kadar numaraları dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="2e712-166">The method returns all the elements in the numbers array until it encounters a number whose value is less than its ordinal position in the array.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#6)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="2e712-167">Lambda ifadeleri tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="2e712-167">Type inference in lambda expressions</span></span> ##

<span data-ttu-id="2e712-168">Lambda'lar yazarken, genellikle C# dil belirtimi içinde açıklandığı gibi derleyici lambda gövdesi, parametre türleri ve diğer etkenlere göre türü çıkarımını çünkü giriş parametreleri için bir tür belirtin gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2e712-168">When writing lambdas, you often do not have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors, as described in the C# Language Specification.</span></span> <span data-ttu-id="2e712-169">Standart sorgu işleçlerinin çoğunda ilk giriş kaynak dizisindeki öğelerin türüdür.</span><span class="sxs-lookup"><span data-stu-id="2e712-169">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="2e712-170">Sizin için sorgu oluşturuyorsanız bir `IEnumerable<Customer>`, giriş değişkeni olarak algılanır sonra bir `Customer` erişiminiz yöntemleri ve özellikleri anlamına gelir nesnesi:</span><span class="sxs-lookup"><span data-stu-id="2e712-170">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/infer1.cs#1)]

<span data-ttu-id="2e712-171">Tür çıkarımı Lambda'lar için genel kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2e712-171">The general rules for type inference for lambdas are:</span></span>

- <span data-ttu-id="2e712-172">Lambda temsilci türüyle aynı sayıda parametre içermelidir.</span><span class="sxs-lookup"><span data-stu-id="2e712-172">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="2e712-173">Lambda her giriş bağımsız değişkeni, karşılık gelen bir temsilci parametre örtük olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2e712-173">Each input argument in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="2e712-174">Lambdanın (varsa) dönüş değeri örtük olarak temsilcinin dönüş türüne dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2e712-174">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>

<span data-ttu-id="2e712-175">Ortak tür sisteminin "lambda ifadesi" için iç kavramı olmadığından kendi içlerindeki lambda ifadelerinin türü olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2e712-175">Note that lambda expressions in themselves do not have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="2e712-176">Ancak bazen bir lambda ifadesinin "türünden" resmi olmayan bir şekilde bahsetmek daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="2e712-176">However, it is sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="2e712-177">Bu durumlarda türü temsilci türüne başvuruyor veya <xref:System.Linq.Expressions.Expression> yazın lambda ifadesi dönüştürülen.</span><span class="sxs-lookup"><span data-stu-id="2e712-177">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="2e712-178">Lambda İfadelerinde Değişken Kapsamı</span><span class="sxs-lookup"><span data-stu-id="2e712-178">Variable Scope in Lambda Expressions</span></span> ##

<span data-ttu-id="2e712-179">Lambda'lar başvurabilir *dış değişkenleri* (bkz [anonim yöntemler](programming-guide/statements-expressions-operators/anonymous-methods.md)) lambda işlevi tanımlar yöntemi kapsamında olan ya da lambda ifadesi içeren kapsamında yazın.</span><span class="sxs-lookup"><span data-stu-id="2e712-179">Lambdas can refer to *outer variables* (see [Anonymous methods](programming-guide/statements-expressions-operators/anonymous-methods.md)) that are in scope in the method that defines the lambda function, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="2e712-180">Bu şekilde tutulan değişkenler, aksi halde kapsam dışına çıkacak ve çöp olarak toplanacak olsalar dahi kullanılmak üzere lambda ifadesinde saklanır.</span><span class="sxs-lookup"><span data-stu-id="2e712-180">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="2e712-181">Bir lambda ifadesinde tüketilebilmesi için öncelikle mutlaka bir harici değişken tayin edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="2e712-181">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="2e712-182">Aşağıdaki örnek, bu kuralları gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e712-182">The following example demonstrates these rules.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/scope.cs#1)]

 <span data-ttu-id="2e712-183">Lambda ifadelerindeki değişken kapsam için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="2e712-183">The following rules apply to variable scope in lambda expressions:</span></span>

- <span data-ttu-id="2e712-184">Tutulan bir değişkenin kullandığı bellek, ona başvuran temsilcinin kullandığı bellek geri kazanılmaya hazır hale gelinceye kadar geri kazanılmaz.</span><span class="sxs-lookup"><span data-stu-id="2e712-184">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="2e712-185">Bir lambda ifadesi içinde tanıtılan değişkenler, dış yöntemde görünmez.</span><span class="sxs-lookup"><span data-stu-id="2e712-185">Variables introduced within a lambda expression are not visible in the outer method.</span></span>

- <span data-ttu-id="2e712-186">Lambda ifadesi doğrudan yakalayamazsınız bir `in`, `ref`, veya `out` kapsayan bir yöntem parametresi.</span><span class="sxs-lookup"><span data-stu-id="2e712-186">A lambda expression cannot directly capture an `in`, `ref`, or `out` parameter from an enclosing method.</span></span>

- <span data-ttu-id="2e712-187">Lambda ifadesindeki bir dönüş ifadesi, kapsayan yöntemin döndürülmesine neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="2e712-187">A return statement in a lambda expression does not cause the enclosing method to return.</span></span>

- <span data-ttu-id="2e712-188">Lambda ifadesi içeremez bir `goto` deyimi, `break` deyimi veya `continue` atlama deyiminin hedef dışında blok ise, lambda işlevinde deyimi.</span><span class="sxs-lookup"><span data-stu-id="2e712-188">A lambda expression cannot contain a `goto` statement, `break` statement, or `continue` statement that is inside the lambda function if the jump statement’s target is outside the block.</span></span> <span data-ttu-id="2e712-189">Ayrıca, hedef, blok içinde ise lambda işlev bloğu dışında bir deyim olması bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="2e712-189">It is also an error to have a jump statement outside the lambda function block if the target is inside the block.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e712-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e712-190">See also</span></span> ##

<span data-ttu-id="2e712-191">[LINQ (dil ile tümleşik sorgu)](../standard/using-linq.md) </span><span class="sxs-lookup"><span data-stu-id="2e712-191">[LINQ (Language-Integrated Query)](../standard/using-linq.md) </span></span>  
<span data-ttu-id="2e712-192">[Anonim yöntemler](programming-guide/statements-expressions-operators/anonymous-methods.md) </span><span class="sxs-lookup"><span data-stu-id="2e712-192">[Anonymous methods](programming-guide/statements-expressions-operators/anonymous-methods.md) </span></span>  
[<span data-ttu-id="2e712-193">İfade ağaçları</span><span class="sxs-lookup"><span data-stu-id="2e712-193">Expression trees</span></span>](expression-trees.md)
