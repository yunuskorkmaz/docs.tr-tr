---
title: zaman uyumsuz C# -başvuru
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 30ee13a4174a137481fbcd36ccef721958b94a12
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450862"
---
# <a name="async-c-reference"></a><span data-ttu-id="44cd4-102">async (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="44cd4-102">async (C# Reference)</span></span>

<span data-ttu-id="44cd4-103">Bir yöntem, [lambda ifadesi](../../programming-guide/statements-expressions-operators/lambda-expressions.md)veya [anonim yöntemin](../operators/delegate-operator.md) zaman uyumsuz olduğunu belirtmek için `async` değiştiricisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="44cd4-103">Use the `async` modifier to specify that a method, [lambda expression](../../programming-guide/statements-expressions-operators/lambda-expressions.md), or [anonymous method](../operators/delegate-operator.md) is asynchronous.</span></span> <span data-ttu-id="44cd4-104">Bu değiştiriciyi bir yöntem veya ifadede kullanırsanız, *zaman uyumsuz bir yöntem*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="44cd4-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="44cd4-105">Aşağıdaki örnek, `ExampleMethodAsync`adlı bir zaman uyumsuz yöntemi tanımlar:</span><span class="sxs-lookup"><span data-stu-id="44cd4-105">The following example defines an async method named `ExampleMethodAsync`:</span></span>
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

<span data-ttu-id="44cd4-106">Zaman uyumsuz programlamaya yeni başladıysanız veya bir zaman uyumsuz yöntemin, uzun süre çalışan bir işi çağıranın iş parçacığını engellemeden nasıl [`await`](../operators/await.md) kullandığını anladıysanız, [Async ve await Ile zaman uyumsuz programlamaya](../../programming-guide/concepts/async/index.md)giriş makalesini okuyun.</span><span class="sxs-lookup"><span data-stu-id="44cd4-106">If you're new to asynchronous programming or do not understand how an async method uses the [`await` operator](../operators/await.md) to do potentially long-running work without blocking the caller’s thread, read the introduction in [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="44cd4-107">Aşağıdaki kod zaman uyumsuz bir yöntem içinde bulunur ve <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> yöntemini çağırır:</span><span class="sxs-lookup"><span data-stu-id="44cd4-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span>
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
<span data-ttu-id="44cd4-108">Zaman uyumsuz bir yöntem, ilk `await` ifadesine ulaşana kadar zaman uyumlu olarak çalışır ve bu noktada, beklenen görev tamamlanana kadar yöntem askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="44cd4-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="44cd4-109">Bu arada, denetim, bir sonraki bölümdeki örnekte gösterildiği gibi yöntemi çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="44cd4-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
<span data-ttu-id="44cd4-110">`async` anahtar sözcüğünün değiştirdiği Yöntem bir `await` ifadesi veya deyimi içermiyorsa, yöntem zaman uyumlu olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="44cd4-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="44cd4-111">Bir derleyici uyarısı, `await` deyimleri içermeyen herhangi bir zaman uyumsuz yöntemde sizi uyarır, çünkü bu durum bir hata gösteriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="44cd4-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="44cd4-112">Bkz. [Derleyici Uyarısı (düzey 1) CS4014](../compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="44cd4-112">See [Compiler Warning (level 1) CS4014](../compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="44cd4-113">`async` anahtar sözcüğü, yalnızca bir metodu, bir lambda ifadesini veya anonim bir yöntemi değiştirdiğinde anahtar kelimedir.</span><span class="sxs-lookup"><span data-stu-id="44cd4-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="44cd4-114">Tüm diğer bağlamlarda bu, tanımlayıcı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="44cd4-114">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44cd4-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="44cd4-115">Example</span></span>  
<span data-ttu-id="44cd4-116">Aşağıdaki örnek, bir zaman uyumsuz olay işleyicisi, `StartButton_Click`ve zaman uyumsuz yöntem `ExampleMethodAsync`arasındaki denetimin yapısını ve akışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="44cd4-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="44cd4-117">Zaman uyumsuz yöntemin sonucu bir Web sayfasının karakter sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="44cd4-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="44cd4-118">Kod, Visual Studio 'da oluşturduğunuz bir Windows Presentation Foundation (WPF) uygulamasına veya Windows Mağazası uygulamasına uygundur; uygulamayı ayarlamaya yönelik kod açıklamalarını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="44cd4-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  

<span data-ttu-id="44cd4-119">Bu kodu, Visual Studio 'da bir Windows Presentation Foundation (WPF) uygulaması veya bir Windows Mağazası uygulaması olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44cd4-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="44cd4-120">`StartButton` adlı bir düğme denetimine ve `ResultsTextBox`adlı TextBox denetimine ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="44cd4-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="44cd4-121">Adları ve işleyiciyi şuna benzer olacak şekilde ayarlamayı unutmayın:</span><span class="sxs-lookup"><span data-stu-id="44cd4-121">Remember to set the names and handler so that you have something like this:</span></span>  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
<span data-ttu-id="44cd4-122">Kodu WPF uygulaması olarak çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="44cd4-122">To run the code as a WPF app:</span></span>  

- <span data-ttu-id="44cd4-123">Bu kodu MainWindow.xaml.cs içindeki `MainWindow` sınıfına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="44cd4-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>  
- <span data-ttu-id="44cd4-124">System .net. http öğesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="44cd4-124">Add a reference to System.Net.Http.</span></span>  
- <span data-ttu-id="44cd4-125">System .net. http için bir `using` yönergesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="44cd4-125">Add a `using` directive for System.Net.Http.</span></span>  
  
<span data-ttu-id="44cd4-126">Kodu bir Windows Mağazası uygulaması olarak çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="44cd4-126">To run the code as a Windows Store app:</span></span>  

- <span data-ttu-id="44cd4-127">Bu kodu MainPage.xaml.cs içindeki `MainPage` sınıfına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="44cd4-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>  
- <span data-ttu-id="44cd4-128">System .net. http ve System. Threading. Tasks için using yönergelerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="44cd4-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
> <span data-ttu-id="44cd4-129">Görevler ve bir görevi beklerken yürütülen kod hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="44cd4-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="44cd4-130">Benzer öğeleri kullanan tam bir WPF örneği için bkz. [Izlenecek yol: Async ve await kullanarak Web 'e erişme](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="44cd4-130">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="44cd4-131">Dönüş Türleri</span><span class="sxs-lookup"><span data-stu-id="44cd4-131">Return Types</span></span>  
<span data-ttu-id="44cd4-132">Zaman uyumsuz bir yöntem aşağıdaki dönüş türlerine sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="44cd4-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="44cd4-133">[void](../builtin-types/void.md).</span><span class="sxs-lookup"><span data-stu-id="44cd4-133">[void](../builtin-types/void.md).</span></span> <span data-ttu-id="44cd4-134">`async void` yöntemler genellikle olay işleyicileri dışındaki kod için önerilmez çünkü çağıranlar bu yöntemleri `await` ve başarılı tamamlamayı veya hata koşullarını raporlamak için farklı bir mekanizma uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="44cd4-134">`async void` methods are generally discouraged for code other than event handlers because callers cannot `await` those methods and must implement a different mechanism to report successful completion or error conditions.</span></span>
- <span data-ttu-id="44cd4-135">7,0 ile C# başlayarak, erişilebilir `GetAwaiter` yöntemi olan herhangi bir tür.</span><span class="sxs-lookup"><span data-stu-id="44cd4-135">Starting with C# 7.0, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="44cd4-136">`System.Threading.Tasks.ValueTask<TResult>` türü, bu tür bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="44cd4-136">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="44cd4-137">NuGet paketi `System.Threading.Tasks.Extensions`eklenerek kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="44cd4-137">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span> 

<span data-ttu-id="44cd4-138">Async yöntemi [içinde](./in-parameter-modifier.md)herhangi bir [ref](./ref.md) veya [Out](./out-parameter-modifier.md) parametresi bildiremez ve [Başvuru dönüş değerine](../../programming-guide/classes-and-structs/ref-returns.md)sahip olabilir, ancak bu parametrelere sahip yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="44cd4-138">The async method can't declare any [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>  
  
<span data-ttu-id="44cd4-139">Metodun [Return](./return.md) ifadesinde `TResult`türünde bir işlenen belirtiyorsa, zaman uyumsuz bir yöntemin dönüş türü olarak `Task<TResult>` belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44cd4-139">You specify `Task<TResult>` as the return type of an async method if the [return](./return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="44cd4-140">Yöntem tamamlandığında anlamlı bir değer döndürülmezse `Task` kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="44cd4-140">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="44cd4-141">Diğer bir deyişle, yöntemine yapılan bir çağrı `Task`döndürür, ancak `Task` tamamlandığında, `Task` bekleyen herhangi bir `await` ifadesi `void`sonucunu verir.</span><span class="sxs-lookup"><span data-stu-id="44cd4-141">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
<span data-ttu-id="44cd4-142">Bu dönüş türünü gerektiren olay işleyicilerini tanımlamak için öncelikle `void` dönüş türünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="44cd4-142">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="44cd4-143">`void`döndüren zaman uyumsuz bir yöntem çağırıcısı bunu bekler ve yöntemin oluşturduğu özel durumları yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="44cd4-143">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  

<span data-ttu-id="44cd4-144">7,0 ile C# başlayarak, kodun performans açısından kritik bölümlerinde bellek ayırmalarını en aza indirmek için bir `GetAwaiter` yöntemi olan, genellikle bir değer türü olan başka bir tür döndürüyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="44cd4-144">Starting with C# 7.0, you return another type, typically a value type, that has a `GetAwaiter` method to minimize memory allocations in performance-critical sections of code.</span></span> 

<span data-ttu-id="44cd4-145">Daha fazla bilgi ve örnek için bkz. [zaman uyumsuz dönüş türleri](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="44cd4-145">For more information and examples, see [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44cd4-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44cd4-146">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="44cd4-147">await</span><span class="sxs-lookup"><span data-stu-id="44cd4-147">await</span></span>](../operators/await.md)
- [<span data-ttu-id="44cd4-148">İzlenecek yol: Async ve Await Kullanarak Web'e Erişme</span><span class="sxs-lookup"><span data-stu-id="44cd4-148">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="44cd4-149">Async ve Await ile Zaman Uyumsuz Programlama</span><span class="sxs-lookup"><span data-stu-id="44cd4-149">Asynchronous Programming with async and await</span></span>](../../programming-guide/concepts/async/index.md)
