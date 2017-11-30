---
title: "async (C# Başvurusu)"
ms.date: 05/22/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
caps.latest.revision: "52"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4a89736822342a9d9a24db6d43435f9795b81b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="async-c-reference"></a><span data-ttu-id="13289-102">async (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="13289-102">async (C# Reference)</span></span>
<span data-ttu-id="13289-103">Kullanım `async` belirtmek için değiştirici yöntemi, bir [lambda ifadesi](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), veya [anonim yöntemi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) zaman uyumsuz olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="13289-103">Use the `async` modifier to specify that a method, [lambda expression](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), or [anonymous method](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) is asynchronous.</span></span> <span data-ttu-id="13289-104">Bir yöntem veya ifadesi bu değiştirici kullanıyorsanız, bunu olarak adlandırılır bir *async yöntemi*.</span><span class="sxs-lookup"><span data-stu-id="13289-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="13289-105">Aşağıdaki örnek, adlandırılmış bir zaman uyumsuz yöntem tanımlar `ExampleMethodAsync`:</span><span class="sxs-lookup"><span data-stu-id="13289-105">The following example defines an async method named `ExampleMethodAsync`:</span></span> 
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  
 
<span data-ttu-id="13289-106">Zaman uyumsuz programlama yeni ya da bir zaman uyumsuz yöntem nasıl kullandığını anlaşılmıyor `await` arayanın iş parçacığı, engellenmeden potansiyel olarak uzun süre çalışan iş yapmak için anahtar sözcüğü okuma girişte [zaman uyumsuz programlama Async ve await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="13289-106">If you're new to asynchronous programming or do not understand how an async method uses the `await` keyword to do potentially long-running work without blocking the caller’s thread, read the introduction in [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="13289-107">Aşağıdaki kod bir zaman uyumsuz yöntem ve çağrıları içinde bulunur <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="13289-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span> 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
<span data-ttu-id="13289-108">İlk ulaşana kadar bir zaman uyumsuz yöntem eşzamanlı olarak çalışan `await` hangi noktada yöntemi askıya awaited görevi tamamlanana kadar ifade.</span><span class="sxs-lookup"><span data-stu-id="13289-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="13289-109">Bu arada, denetim, bir sonraki bölümdeki örnekte gösterildiği gibi yöntemi çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="13289-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
<span data-ttu-id="13289-110">Varsa yöntemi, `async` anahtar sözcüğü değiştirir içermiyor. bir `await` ifadesi veya deyimi, yöntem yürütür zaman uyumlu olarak.</span><span class="sxs-lookup"><span data-stu-id="13289-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="13289-111">Derleyici Uyarısı içermeyen herhangi bir zaman uyumsuz yöntem uyarıları `await` deyimleri, çünkü bu durumu gösteren bir hata olabilir.</span><span class="sxs-lookup"><span data-stu-id="13289-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="13289-112">Bkz: [Derleyici Uyarısı (düzey 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="13289-112">See [Compiler Warning (level 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="13289-113">`async` Yalnızca bir yöntemi, bir lambda ifadesi veya anonim bir yöntem değişiklik yaptığında bir anahtar sözcüktür, anahtar sözcüğü bağlamsal.</span><span class="sxs-lookup"><span data-stu-id="13289-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="13289-114">Tüm diğer bağlamlarda bu, tanımlayıcı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="13289-114">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13289-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="13289-115">Example</span></span>  
<span data-ttu-id="13289-116">Aşağıdaki örnek, yapı ve bir zaman uyumsuz olay işleyicisi arasındaki denetim akışını gösterir `StartButton_Click`ve bir zaman uyumsuz yöntem `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="13289-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="13289-117">Bir web sayfasının karakter sayısını zaman uyumsuz yönteminden sonucudur.</span><span class="sxs-lookup"><span data-stu-id="13289-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="13289-118">Kod, bir Windows Presentation Foundation (WPF) uygulamasını veya Visual Studio'da oluşturma Windows mağazası uygulaması için uygundur; uygulamasını kurup için kod açıklamalarına bakın.</span><span class="sxs-lookup"><span data-stu-id="13289-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  

<span data-ttu-id="13289-119">Bir Windows Presentation Foundation (WPF) uygulaması veya bir Windows mağazası uygulaması olarak, bu kod Visual Studio'da çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13289-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="13289-120">Adlı bir düğme denetimine gerek `StartButton` ve adlı Textbox denetimi `ResultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="13289-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="13289-121">Böylece şöyle bir şey sahip adları ve işleyici ayarlamayı unutmayın:</span><span class="sxs-lookup"><span data-stu-id="13289-121">Remember to set the names and handler so that you have something like this:</span></span>  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
<span data-ttu-id="13289-122">Kod bir WPF uygulaması çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="13289-122">To run the code as a WPF app:</span></span>  

- <span data-ttu-id="13289-123">Bu kod içine yapıştırma `MainWindow` MainWindow.xaml.cs sınıfta.</span><span class="sxs-lookup"><span data-stu-id="13289-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>  
- <span data-ttu-id="13289-124">System.Net.Http bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="13289-124">Add a reference to System.Net.Http.</span></span>  
- <span data-ttu-id="13289-125">Ekleme bir `using` System.Net.Http için yönerge.</span><span class="sxs-lookup"><span data-stu-id="13289-125">Add a `using` directive for System.Net.Http.</span></span>  
  
<span data-ttu-id="13289-126">Kod bir Windows mağazası uygulaması çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="13289-126">To run the code as a Windows Store app:</span></span>  
- <span data-ttu-id="13289-127">Bu kod içine yapıştırma `MainPage` MainPage.xaml.cs sınıfta.</span><span class="sxs-lookup"><span data-stu-id="13289-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>  
- <span data-ttu-id="13289-128">System.Net.Http ve System.Threading.Tasks için yönergeleri kullanarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="13289-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  <span data-ttu-id="13289-129">Görevler ve bir görev için beklenirken yürütülen kodu hakkında daha fazla bilgi için bkz: [zaman uyumsuz programlama ile async ve await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="13289-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="13289-130">Benzer öğeleri kullanan bir tam WPF örnek için bkz: [izlenecek yol: Web kullanarak zaman uyumsuz ve bekleme tarafından erişme](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="13289-130">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="13289-131">Dönüş Türleri</span><span class="sxs-lookup"><span data-stu-id="13289-131">Return Types</span></span>  
<span data-ttu-id="13289-132">Async yöntemi, dönüş türleri aşağıdakilere sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="13289-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="13289-133">[void](../../../csharp/language-reference/keywords/void.md), hangi yalnızca kullanılmalıdır olay işleyicileri için.</span><span class="sxs-lookup"><span data-stu-id="13289-133">[void](../../../csharp/language-reference/keywords/void.md), which should only be used for event handlers.</span></span>
- <span data-ttu-id="13289-134">C# 7, bir erişilebilir olan herhangi bir tür'ile başlayan `GetAwaiter` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="13289-134">Starting with C# 7, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="13289-135">`System.Threading.Tasks.ValueTask<TResult>` Bu tür bir uygulama türüdür.</span><span class="sxs-lookup"><span data-stu-id="13289-135">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="13289-136">NuGet paketi ekleyerek kullanılabilir olur `System.Threading.Tasks.Extensions`.</span><span class="sxs-lookup"><span data-stu-id="13289-136">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span> 

<span data-ttu-id="13289-137">Async yöntemi herhangi bildiremezsiniz [ref](../../../csharp/language-reference/keywords/ref.md) veya [çıkışı](../../../csharp/language-reference/keywords/out.md) parametreleri ya da can sahip bir <!-- [reference return value](../../programming-guide/classes-and-structs/ref-returns.md) -->başvuru dönüş değeri, ancak bu tür parametrelerine sahip yöntemleri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13289-137">The async method can't declare any [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) parameters, nor can it have a <!-- [reference return value](../../programming-guide/classes-and-structs/ref-returns.md) -->reference return value, but it can call methods that have such parameters.</span></span>  
  
<span data-ttu-id="13289-138">Belirttiğiniz `Task<TResult>` bir zaman uyumsuz yönteminin dönüş türü olarak varsa [dönmek](../../../csharp/language-reference/keywords/return.md) yöntemin ifadesi işleneni türü belirtir `TResult`.</span><span class="sxs-lookup"><span data-stu-id="13289-138">You specify `Task<TResult>` as the return type of an async method if the [return](../../../csharp/language-reference/keywords/return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="13289-139">Kullandığınız `Task` yöntemi tamamlandığında hiçbir anlamlı değeri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="13289-139">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="13289-140">Diğer bir deyişle, yöntemine bir çağrı döndürür bir `Task`, ancak ne zaman `Task` tamamlandığında, tüm `await` bekliyor ifade `Task` değerlendiren `void`.</span><span class="sxs-lookup"><span data-stu-id="13289-140">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
<span data-ttu-id="13289-141">Kullandığınız `void` dönüş türü, dönüş türü gerektiren olay işleyicileri öncelikle tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="13289-141">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="13289-142">Çağıran bir `void`-zaman uyumsuz yöntem döndürme await olamaz ve yöntemi atar özel durumlarını yakalama olamaz.</span><span class="sxs-lookup"><span data-stu-id="13289-142">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  

<span data-ttu-id="13289-143">C# 7 ile başlayan, başka bir tür, sahip genellikle bir değer türü, dönüş bir `GetAwaiter` performans açısından kritik kod bölümlerini miminize bellek ayırma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="13289-143">Starting with C# 7, you return another type, typically a value type, that has a `GetAwaiter` method to miminize memory allocations in performance-critical sections of code.</span></span> 

<span data-ttu-id="13289-144">Daha fazla bilgi ve örnekler için bkz: [zaman uyumsuz dönüş türleri](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="13289-144">For more information and examples, see [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13289-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13289-145">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>  
 [<span data-ttu-id="13289-146">await</span><span class="sxs-lookup"><span data-stu-id="13289-146">await</span></span>](../../../csharp/language-reference/keywords/await.md)  
 [<span data-ttu-id="13289-147">İzlenecek yol: Async kullanarak Web'e erişme ve bekler</span><span class="sxs-lookup"><span data-stu-id="13289-147">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="13289-148">Zaman uyumsuz programlama ile zaman uyumsuz ve bekleme</span><span class="sxs-lookup"><span data-stu-id="13289-148">Asynchronous Programming with async and await</span></span>](../../../csharp/programming-guide/concepts/async/index.md)
