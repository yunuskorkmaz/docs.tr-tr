---
title: zaman uyumsuz C# -başvuru
ms.custom: seodec18
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 3bf71bbe0e3f4e14f140f5a1b98a662ceaaea419
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68362999"
---
# <a name="async-c-reference"></a><span data-ttu-id="a2e69-102">async (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a2e69-102">async (C# Reference)</span></span>

<span data-ttu-id="a2e69-103">Bir yöntem, [lambda ifadesi](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)veya [anonim yöntemin](../../../csharp/language-reference/operators/delegate-operator.md) zaman uyumsuz olduğunu belirtmek için değiştiricisinikullanın.`async`</span><span class="sxs-lookup"><span data-stu-id="a2e69-103">Use the `async` modifier to specify that a method, [lambda expression](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), or [anonymous method](../../../csharp/language-reference/operators/delegate-operator.md) is asynchronous.</span></span> <span data-ttu-id="a2e69-104">Bu değiştiriciyi bir yöntem veya ifadede kullanırsanız, *zaman uyumsuz bir yöntem*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a2e69-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="a2e69-105">Aşağıdaki örnek adlı `ExampleMethodAsync`bir zaman uyumsuz metodu tanımlar:</span><span class="sxs-lookup"><span data-stu-id="a2e69-105">The following example defines an async method named `ExampleMethodAsync`:</span></span>
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

<span data-ttu-id="a2e69-106">Zaman uyumsuz programlamaya yeni başladıysanız veya bir zaman uyumsuz yöntemin, uzun süre çalışan bir işi `await` çağıranın iş parçacığını engellemeden nasıl kullandığını anladıysanız, zaman uyumsuz programlama ile giriş zaman uyumsuz olarak okuyun [ve await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="a2e69-106">If you're new to asynchronous programming or do not understand how an async method uses the `await` keyword to do potentially long-running work without blocking the caller’s thread, read the introduction in [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="a2e69-107">Aşağıdaki kod zaman uyumsuz bir yöntem içinde bulunur ve <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> yöntemini çağırır:</span><span class="sxs-lookup"><span data-stu-id="a2e69-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span> 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
<span data-ttu-id="a2e69-108">Zaman uyumsuz bir yöntem, ilk `await` ifadesine ulaşana dek zaman uyumlu olarak çalışır ve bu noktada, beklenen görev tamamlanana kadar yöntem askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="a2e69-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="a2e69-109">Bu arada, denetim, bir sonraki bölümdeki örnekte gösterildiği gibi yöntemi çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="a2e69-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
<span data-ttu-id="a2e69-110">`async` Anahtar sözcüğünün değiştirdiği Yöntem bir `await` ifade veya deyim içermiyorsa, yöntem zaman uyumlu olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a2e69-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="a2e69-111">Bir derleyici uyarısı, deyimi içermeyen `await` herhangi bir zaman uyumsuz metotlarda sizi uyarır, çünkü bu durum bir hata gösteriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="a2e69-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="a2e69-112">Bkz. [Derleyici Uyarısı (düzey 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="a2e69-112">See [Compiler Warning (level 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="a2e69-113">`async` Anahtar sözcüğü, yalnızca bir metodu, bir lambda ifadesini veya anonim bir yöntemi değiştirdiğinde anahtar kelimedir.</span><span class="sxs-lookup"><span data-stu-id="a2e69-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="a2e69-114">Tüm diğer bağlamlarda bu, tanımlayıcı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="a2e69-114">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2e69-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2e69-115">Example</span></span>  
<span data-ttu-id="a2e69-116">Aşağıdaki örnek, zaman uyumsuz olay işleyicisi, `StartButton_Click`ve zaman uyumsuz bir `ExampleMethodAsync`yöntem arasındaki denetimin yapısını ve akışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2e69-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="a2e69-117">Zaman uyumsuz yöntemin sonucu bir Web sayfasının karakter sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="a2e69-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="a2e69-118">Kod, Visual Studio 'da oluşturduğunuz bir Windows Presentation Foundation (WPF) uygulamasına veya Windows Mağazası uygulamasına uygundur; uygulamayı ayarlamaya yönelik kod açıklamalarını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="a2e69-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  

<span data-ttu-id="a2e69-119">Bu kodu, Visual Studio 'da bir Windows Presentation Foundation (WPF) uygulaması veya bir Windows Mağazası uygulaması olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2e69-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="a2e69-120">Adlı `StartButton` bir düğme denetimine ve adlı `ResultsTextBox`TextBox denetimine ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="a2e69-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="a2e69-121">Adları ve işleyiciyi şuna benzer olacak şekilde ayarlamayı unutmayın:</span><span class="sxs-lookup"><span data-stu-id="a2e69-121">Remember to set the names and handler so that you have something like this:</span></span>  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
<span data-ttu-id="a2e69-122">Kodu WPF uygulaması olarak çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="a2e69-122">To run the code as a WPF app:</span></span>  

- <span data-ttu-id="a2e69-123">Bu kodu `MainWindow` MainWindow.xaml.cs içindeki sınıfa yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="a2e69-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>  
- <span data-ttu-id="a2e69-124">System .net. http öğesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a2e69-124">Add a reference to System.Net.Http.</span></span>  
- <span data-ttu-id="a2e69-125">System .net `using` . http için bir yönerge ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a2e69-125">Add a `using` directive for System.Net.Http.</span></span>  
  
<span data-ttu-id="a2e69-126">Kodu bir Windows Mağazası uygulaması olarak çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="a2e69-126">To run the code as a Windows Store app:</span></span>  
- <span data-ttu-id="a2e69-127">Bu kodu `MainPage` MainPage.xaml.cs içindeki sınıfa yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="a2e69-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>  
- <span data-ttu-id="a2e69-128">System .net. http ve System. Threading. Tasks için using yönergelerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a2e69-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  <span data-ttu-id="a2e69-129">Görevler ve bir görevi beklerken yürütülen kod hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="a2e69-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="a2e69-130">Benzer öğeleri kullanan tam bir WPF örneği için bkz [. İzlenecek yol: Async ve await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)kullanarak Web 'e erişme.</span><span class="sxs-lookup"><span data-stu-id="a2e69-130">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="a2e69-131">Dönüş Türleri</span><span class="sxs-lookup"><span data-stu-id="a2e69-131">Return Types</span></span>  
<span data-ttu-id="a2e69-132">Zaman uyumsuz bir yöntem aşağıdaki dönüş türlerine sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="a2e69-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="a2e69-133">[void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="a2e69-133">[void](../../../csharp/language-reference/keywords/void.md).</span></span> <span data-ttu-id="a2e69-134">`async void`yöntemler genellikle olay işleyicileri dışındaki kod için önerilmez çünkü çağıranlar `await` bu yöntemlere izin vermez ve başarılı tamamlamayı veya hata koşullarını raporlamak için farklı bir mekanizma uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a2e69-134">`async void` methods are generally discouraged for code other than event handlers because callers cannot `await` those methods and must implement a different mechanism to report successful completion or error conditions.</span></span>
- <span data-ttu-id="a2e69-135">7,0 ile C# başlayarak, erişilebilir `GetAwaiter` bir yöntemi olan herhangi bir tür.</span><span class="sxs-lookup"><span data-stu-id="a2e69-135">Starting with C# 7.0, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="a2e69-136">Bu `System.Threading.Tasks.ValueTask<TResult>` tür bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="a2e69-136">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="a2e69-137">NuGet paketi `System.Threading.Tasks.Extensions`eklenerek kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a2e69-137">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span> 

<span data-ttu-id="a2e69-138">Async yöntemi [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md)herhangi bir [ref](../../../csharp/language-reference/keywords/ref.md) veya [Out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi bildiremez ve [Başvuru dönüş değerine](../../programming-guide/classes-and-structs/ref-returns.md)sahip olabilir, ancak bu parametrelere sahip yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="a2e69-138">The async method can't declare any [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>  
  
<span data-ttu-id="a2e69-139">Metodun `Task<TResult>` [Return](../../../csharp/language-reference/keywords/return.md) ifadesinde`TResult`bir işlenen belirtiyorsa, zaman uyumsuz bir yöntemin dönüş türü olarak belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2e69-139">You specify `Task<TResult>` as the return type of an async method if the [return](../../../csharp/language-reference/keywords/return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="a2e69-140">Yöntem tamamlandığında `Task` anlamlı bir değer döndürülmezse kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="a2e69-140">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="a2e69-141">Diğer bir deyişle, yöntemine yapılan bir `Task`çağrı bir döndürür, ancak `Task` tamamlandığında, `Task` sonucunu `void`bekleyen tüm `await` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="a2e69-141">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
<span data-ttu-id="a2e69-142">Dönüş türünü öncelikle `void` bu dönüş türü gerektiren olay işleyicilerini tanımlamak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="a2e69-142">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="a2e69-143">Döndüren zaman uyumsuz bir `void`yöntemi çağıran, bunu bekler ve yöntemin oluşturduğu özel durumları yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="a2e69-143">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  

<span data-ttu-id="a2e69-144">7,0 ' C# den başlayarak, kodun performans açısından kritik bölümlerinde bellek ayırmalarını en aza indirmek için bir `GetAwaiter` yöntemine sahip olan, genellikle bir değer türü olan başka bir tür döndürüyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="a2e69-144">Starting with C# 7.0, you return another type, typically a value type, that has a `GetAwaiter` method to minimize memory allocations in performance-critical sections of code.</span></span> 

<span data-ttu-id="a2e69-145">Daha fazla bilgi ve örnek için bkz. [zaman uyumsuz dönüş türleri](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="a2e69-145">For more information and examples, see [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e69-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2e69-146">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="a2e69-147">await</span><span class="sxs-lookup"><span data-stu-id="a2e69-147">await</span></span>](../../../csharp/language-reference/keywords/await.md)
- [<span data-ttu-id="a2e69-148">İzlenecek yol: Async ve await kullanarak Web 'e erişme</span><span class="sxs-lookup"><span data-stu-id="a2e69-148">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="a2e69-149">Async ve Await ile Zaman Uyumsuz Programlama</span><span class="sxs-lookup"><span data-stu-id="a2e69-149">Asynchronous Programming with async and await</span></span>](../../../csharp/programming-guide/concepts/async/index.md)
