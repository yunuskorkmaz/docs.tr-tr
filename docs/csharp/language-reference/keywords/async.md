---
title: async - C# Referans
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 92e94d6fe1c07ab5cd8f29d040401a737a1db78e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173659"
---
# <a name="async-c-reference"></a><span data-ttu-id="b68f9-102">async (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b68f9-102">async (C# Reference)</span></span>

<span data-ttu-id="b68f9-103">Bir `async` yöntem, [lambda ifade](../../programming-guide/statements-expressions-operators/lambda-expressions.md)veya [anonim yöntem](../operators/delegate-operator.md) asynchronous olduğunu belirtmek için değiştirici kullanın.</span><span class="sxs-lookup"><span data-stu-id="b68f9-103">Use the `async` modifier to specify that a method, [lambda expression](../../programming-guide/statements-expressions-operators/lambda-expressions.md), or [anonymous method](../operators/delegate-operator.md) is asynchronous.</span></span> <span data-ttu-id="b68f9-104">Bu değiştiriciyi bir yöntem veya ifadede kullanırsanız, buna *async yöntemi*denir.</span><span class="sxs-lookup"><span data-stu-id="b68f9-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="b68f9-105">Aşağıdaki örnekte bir async `ExampleMethodAsync`yöntemi tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="b68f9-105">The following example defines an async method named `ExampleMethodAsync`:</span></span>
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

<span data-ttu-id="b68f9-106">Asynchronous programlamada yeniyseniz veya async yönteminin [ `await` operatörü](../operators/await.md) arayanın iş parçacığıengellemeden uzun süreli bir iş yapmak için nasıl kullandığını anlamıyorsanız, [Asynchronous Programming'deki](../../programming-guide/concepts/async/index.md)girişi async ile okuyun ve bekleyin.</span><span class="sxs-lookup"><span data-stu-id="b68f9-106">If you're new to asynchronous programming or do not understand how an async method uses the [`await` operator](../operators/await.md) to do potentially long-running work without blocking the caller’s thread, read the introduction in [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="b68f9-107">Aşağıdaki kod bir async yöntemi içinde <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> bulunur ve yöntemi çağırır:</span><span class="sxs-lookup"><span data-stu-id="b68f9-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span>
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
<span data-ttu-id="b68f9-108">Bir async yöntemi, ilk `await` ifadesine ulaşana kadar eşzamanlı olarak çalışır ve bu noktada yöntem beklenen görev tamamlanana kadar askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="b68f9-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="b68f9-109">Bu arada, denetim, bir sonraki bölümdeki örnekte gösterildiği gibi yöntemi çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="b68f9-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
<span data-ttu-id="b68f9-110">Anahtar kelimenin `async` modiyi yöntemi bir `await` ifade veya deyim içermiyorsa, yöntem eşzamanlı olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b68f9-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="b68f9-111">Derleyici uyarısı, bu durum bir hata gösterebilir, `await` çünkü ifadeler içermeyen herhangi bir async yöntemleri sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="b68f9-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="b68f9-112">Bkz. [Derleyici Uyarısı (düzey 1) CS4014](../compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="b68f9-112">See [Compiler Warning (level 1) CS4014](../compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="b68f9-113">Anahtar `async` kelime, yalnızca bir yöntemi, lambda ifadesini veya anonim bir yöntemi değiştirirken bir anahtar kelime olması açısından bağlamsaldır.</span><span class="sxs-lookup"><span data-stu-id="b68f9-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="b68f9-114">Tüm diğer bağlamlarda bu, tanımlayıcı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="b68f9-114">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b68f9-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="b68f9-115">Example</span></span>  
<span data-ttu-id="b68f9-116">Aşağıdaki örnekte, bir async olay işleyicisi `StartButton_Click`ve bir async `ExampleMethodAsync`yöntemi arasındaki denetim yapısı ve akışı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b68f9-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="b68f9-117">Async yönteminin sonucu, bir web sayfasının karakter sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="b68f9-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="b68f9-118">Kod, Visual Studio'da oluşturduğunuz bir Windows Presentation Foundation (WPF) uygulaması veya Windows Mağazası uygulaması için uygundur; uygulamayı ayarlamak için kod açıklamalarına bakın.</span><span class="sxs-lookup"><span data-stu-id="b68f9-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  

<span data-ttu-id="b68f9-119">Bu kodu Visual Studio'da Windows Presentation Foundation (WPF) uygulaması veya Windows Mağazası uygulaması olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b68f9-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="b68f9-120">Bir Düğme denetimi `StartButton` ne adlı ve `ResultsTextBox`bir Textbox denetimi adlı gerekir.</span><span class="sxs-lookup"><span data-stu-id="b68f9-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="b68f9-121">Adları ve işleyiciyi böyle bir şeye sahip olacak şekilde ayarlamayı unutmayın:</span><span class="sxs-lookup"><span data-stu-id="b68f9-121">Remember to set the names and handler so that you have something like this:</span></span>  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
<span data-ttu-id="b68f9-122">Kodu WPF uygulaması olarak çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="b68f9-122">To run the code as a WPF app:</span></span>  

- <span data-ttu-id="b68f9-123">Bu kodu MainWindow.xaml.cs `MainWindow` sınıfa yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="b68f9-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>  
- <span data-ttu-id="b68f9-124">System.Net.Http adresine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b68f9-124">Add a reference to System.Net.Http.</span></span>  
- <span data-ttu-id="b68f9-125">System.Net.Http için bir `using` yönerge ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b68f9-125">Add a `using` directive for System.Net.Http.</span></span>  
  
<span data-ttu-id="b68f9-126">Kodu Windows Mağazası uygulaması olarak çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="b68f9-126">To run the code as a Windows Store app:</span></span>  

- <span data-ttu-id="b68f9-127">Bu kodu MainPage.xaml.cs `MainPage` sınıfa yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="b68f9-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>  
- <span data-ttu-id="b68f9-128">System.Net.Http ve System.Threading.Tasks için yönergeleri kullanarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b68f9-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
> <span data-ttu-id="b68f9-129">Görevler ve bir görevi beklerken yürüten kod hakkında daha fazla bilgi için, [async ile Asynchronous Programming'e bakın ve bekliyoruz.](../../programming-guide/concepts/async/index.md)</span><span class="sxs-lookup"><span data-stu-id="b68f9-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="b68f9-130">Benzer öğeleri kullanan tam bir WPF örneği için Bkz. [Walkthrough: Async kullanarak Web'e erişim ve Bekleme](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="b68f9-130">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="b68f9-131">Dönüş Türleri</span><span class="sxs-lookup"><span data-stu-id="b68f9-131">Return Types</span></span>  
<span data-ttu-id="b68f9-132">Bir async yöntemi aşağıdaki iade türlerine sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="b68f9-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="b68f9-133">[geçersizdir.](../builtin-types/void.md)</span><span class="sxs-lookup"><span data-stu-id="b68f9-133">[void](../builtin-types/void.md).</span></span> <span data-ttu-id="b68f9-134">`async void`arayanlar bu yöntemleri buşekildemedığından `await` ve başarılı tamamlama veya hata koşullarını bildirmek için farklı bir mekanizma uygulamagerektiğinden, yöntemler genellikle olay işleyicileri dışındaki kodlar için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="b68f9-134">`async void` methods are generally discouraged for code other than event handlers because callers cannot `await` those methods and must implement a different mechanism to report successful completion or error conditions.</span></span>
- <span data-ttu-id="b68f9-135">C# 7.0 ile başlayarak, erişilebilir `GetAwaiter` bir yönteme sahip herhangi bir tür.</span><span class="sxs-lookup"><span data-stu-id="b68f9-135">Starting with C# 7.0, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="b68f9-136">Türü `System.Threading.Tasks.ValueTask<TResult>` böyle bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="b68f9-136">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="b68f9-137">NuGet paketini `System.Threading.Tasks.Extensions`ekleyerek kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b68f9-137">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span>

<span data-ttu-id="b68f9-138">Async yöntemi herhangi bir [beyan](./in-parameter-modifier.md)edemez , [ref](./ref.md) veya [out](./out-parameter-modifier.md) parametreleri, ne de bir [referans dönüş değeri](../../programming-guide/classes-and-structs/ref-returns.md)olabilir , ama bu tür parametrelere sahip yöntemleri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b68f9-138">The async method can't declare any [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>  
  
<span data-ttu-id="b68f9-139">Yöntemin `Task<TResult>` [dönüş](./return.md) deyimi bir operand türü `TResult`belirtenden bir async yönteminin dönüş türü olarak belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b68f9-139">You specify `Task<TResult>` as the return type of an async method if the [return](./return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="b68f9-140">Yöntem `Task` tamamlandığında anlamlı bir değer döndürülmezse kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b68f9-140">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="b68f9-141">Diğer bir zamanda, yönteme `Task`yapılan bir `Task` çağrı, ancak `await` tamamlandığında, `Task` değerlendirmeyi bekleyen herhangi `void`bir ifadeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="b68f9-141">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
<span data-ttu-id="b68f9-142">`void` İade türünü öncelikle bu iade türünü gerektiren olay işleyicilerini tanımlamak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b68f9-142">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="b68f9-143">-dönen async `void`yöntemini arayan kişi onu bekteemez ve yöntemin attığı özel durumları yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="b68f9-143">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  

<span data-ttu-id="b68f9-144">C# 7.0 ile başlayarak, kodun performans açısından kritik `GetAwaiter` bölümlerinde bellek ayırmalarını en aza indirmek için bir yöntemi olan başka bir tür ( genellikle bir değer türü, döndürür.</span><span class="sxs-lookup"><span data-stu-id="b68f9-144">Starting with C# 7.0, you return another type, typically a value type, that has a `GetAwaiter` method to minimize memory allocations in performance-critical sections of code.</span></span>

<span data-ttu-id="b68f9-145">Daha fazla bilgi ve örnekler [için, Async İade Türleri'ne](../../programming-guide/concepts/async/async-return-types.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="b68f9-145">For more information and examples, see [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b68f9-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b68f9-146">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="b68f9-147">await</span><span class="sxs-lookup"><span data-stu-id="b68f9-147">await</span></span>](../operators/await.md)
- [<span data-ttu-id="b68f9-148">İzlenecek yol: Async ve Await Kullanarak Web'e Erişme</span><span class="sxs-lookup"><span data-stu-id="b68f9-148">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="b68f9-149">Async ve await ile Asynchronous Programlama</span><span class="sxs-lookup"><span data-stu-id="b68f9-149">Asynchronous Programming with async and await</span></span>](../../programming-guide/concepts/async/index.md)
