---
title: Async-C# başvurusu
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 279ea2f9875681401c9c7acab922d9e4424e6827
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062541"
---
# <a name="async-c-reference"></a><span data-ttu-id="221b6-102">async (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="221b6-102">async (C# Reference)</span></span>

<span data-ttu-id="221b6-103">`async`Bir yöntem, [lambda ifadesi](../operators/lambda-expressions.md)veya [anonim yöntemin](../operators/delegate-operator.md) zaman uyumsuz olduğunu belirtmek için değiştiricisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="221b6-103">Use the `async` modifier to specify that a method, [lambda expression](../operators/lambda-expressions.md), or [anonymous method](../operators/delegate-operator.md) is asynchronous.</span></span> <span data-ttu-id="221b6-104">Bu değiştiriciyi bir yöntem veya ifadede kullanırsanız, *zaman uyumsuz bir yöntem*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="221b6-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="221b6-105">Aşağıdaki örnek adlı bir zaman uyumsuz metodu tanımlar `ExampleMethodAsync` :</span><span class="sxs-lookup"><span data-stu-id="221b6-105">The following example defines an async method named `ExampleMethodAsync`:</span></span>
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

<span data-ttu-id="221b6-106">Zaman uyumsuz programlamaya yeni başladıysanız veya zaman uyumsuz bir yöntemin, çağıranın iş parçacığını engellemeden uzun süre çalışan bir iş yapmak için [ `await` işlecini](../operators/await.md) nasıl kullandığını anlamayın, zaman uyumsuz [programlamada girişi zaman uyumsuz ve await ile](../../programming-guide/concepts/async/index.md)okuyun.</span><span class="sxs-lookup"><span data-stu-id="221b6-106">If you're new to asynchronous programming or do not understand how an async method uses the [`await` operator](../operators/await.md) to do potentially long-running work without blocking the caller's thread, read the introduction in [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="221b6-107">Aşağıdaki kod zaman uyumsuz bir yöntem içinde bulunur ve <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> yöntemini çağırır:</span><span class="sxs-lookup"><span data-stu-id="221b6-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span>
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
<span data-ttu-id="221b6-108">Zaman uyumsuz bir yöntem, ilk ifadesine ulaşana dek zaman uyumlu `await` olarak çalışır ve bu noktada, beklenen görev tamamlanana kadar yöntem askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="221b6-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="221b6-109">Bu arada, denetim, bir sonraki bölümdeki örnekte gösterildiği gibi yöntemi çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="221b6-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
<span data-ttu-id="221b6-110">`async`Anahtar sözcüğünün değiştirdiği Yöntem bir `await` ifade veya deyim içermiyorsa, yöntem zaman uyumlu olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="221b6-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="221b6-111">Bir derleyici uyarısı, deyimi içermeyen herhangi bir zaman uyumsuz metotlarda sizi uyarır `await` , çünkü bu durum bir hata gösteriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="221b6-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="221b6-112">Bkz. [Derleyici Uyarısı (düzey 1) CS4014](../compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="221b6-112">See [Compiler Warning (level 1) CS4014](../compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="221b6-113">Anahtar sözcüğü, `async` yalnızca bir metodu, bir lambda ifadesini veya anonim bir yöntemi değiştirdiğinde anahtar kelimedir.</span><span class="sxs-lookup"><span data-stu-id="221b6-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="221b6-114">Tüm diğer bağlamlarda bu, tanımlayıcı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="221b6-114">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="221b6-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="221b6-115">Example</span></span>  
<span data-ttu-id="221b6-116">Aşağıdaki örnek, zaman uyumsuz olay işleyicisi, `StartButton_Click` ve zaman uyumsuz bir yöntem arasındaki denetimin yapısını ve akışını gösterir `ExampleMethodAsync` .</span><span class="sxs-lookup"><span data-stu-id="221b6-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="221b6-117">Zaman uyumsuz yöntemin sonucu bir Web sayfasının karakter sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="221b6-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="221b6-118">Kod, Visual Studio 'da oluşturduğunuz bir Windows Presentation Foundation (WPF) uygulamasına veya Windows Mağazası uygulamasına uygundur; uygulamayı ayarlamaya yönelik kod açıklamalarını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="221b6-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  

<span data-ttu-id="221b6-119">Bu kodu, Visual Studio 'da bir Windows Presentation Foundation (WPF) uygulaması veya bir Windows Mağazası uygulaması olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="221b6-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="221b6-120">Adlı bir düğme denetimine `StartButton` ve adlı TextBox denetimine ihtiyacınız vardır `ResultsTextBox` .</span><span class="sxs-lookup"><span data-stu-id="221b6-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="221b6-121">Adları ve işleyiciyi şuna benzer olacak şekilde ayarlamayı unutmayın:</span><span class="sxs-lookup"><span data-stu-id="221b6-121">Remember to set the names and handler so that you have something like this:</span></span>  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
<span data-ttu-id="221b6-122">Kodu WPF uygulaması olarak çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="221b6-122">To run the code as a WPF app:</span></span>  

- <span data-ttu-id="221b6-123">Bu kodu `MainWindow` MainWindow.xaml.cs içindeki sınıfa yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="221b6-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>  
- <span data-ttu-id="221b6-124">System .net. http öğesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="221b6-124">Add a reference to System.Net.Http.</span></span>  
- <span data-ttu-id="221b6-125">`using`System .net. http için bir yönerge ekleyin.</span><span class="sxs-lookup"><span data-stu-id="221b6-125">Add a `using` directive for System.Net.Http.</span></span>  
  
<span data-ttu-id="221b6-126">Kodu bir Windows Mağazası uygulaması olarak çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="221b6-126">To run the code as a Windows Store app:</span></span>  

- <span data-ttu-id="221b6-127">Bu kodu `MainPage` MainPage.xaml.cs içindeki sınıfa yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="221b6-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>  
- <span data-ttu-id="221b6-128">System .net. http ve System. Threading. Tasks için using yönergelerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="221b6-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
> <span data-ttu-id="221b6-129">Görevler ve bir görevi beklerken yürütülen kod hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="221b6-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="221b6-130">Benzer öğeleri kullanan tam bir WPF örneği için bkz. [Izlenecek yol: Async ve await kullanarak Web 'e erişme](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="221b6-130">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="221b6-131">Dönüş Türleri</span><span class="sxs-lookup"><span data-stu-id="221b6-131">Return Types</span></span>  
<span data-ttu-id="221b6-132">Zaman uyumsuz bir yöntem aşağıdaki dönüş türlerine sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="221b6-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="221b6-133">[void](../builtin-types/void.md).</span><span class="sxs-lookup"><span data-stu-id="221b6-133">[void](../builtin-types/void.md).</span></span> <span data-ttu-id="221b6-134">`async void`yöntemler genellikle olay işleyicileri dışındaki kod için önerilmez çünkü çağıranlar `await` Bu yöntemlere izin vermez ve başarılı tamamlamayı veya hata koşullarını raporlamak için farklı bir mekanizma uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="221b6-134">`async void` methods are generally discouraged for code other than event handlers because callers cannot `await` those methods and must implement a different mechanism to report successful completion or error conditions.</span></span>
- <span data-ttu-id="221b6-135">C# 7,0 ile başlayarak, erişilebilir bir yöntemi olan herhangi bir tür `GetAwaiter` .</span><span class="sxs-lookup"><span data-stu-id="221b6-135">Starting with C# 7.0, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="221b6-136">`System.Threading.Tasks.ValueTask<TResult>`Bu tür bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="221b6-136">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="221b6-137">NuGet paketi eklenerek kullanılabilir `System.Threading.Tasks.Extensions` .</span><span class="sxs-lookup"><span data-stu-id="221b6-137">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span>

<span data-ttu-id="221b6-138">Async yöntemi [içinde](./in-parameter-modifier.md)herhangi bir [ref](./ref.md) veya [Out](./out-parameter-modifier.md) parametresi bildiremez ve [Başvuru dönüş değerine](../../programming-guide/classes-and-structs/ref-returns.md)sahip olabilir, ancak bu parametrelere sahip yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="221b6-138">The async method can't declare any [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>  
  
<span data-ttu-id="221b6-139">`Task<TResult>`Metodun [Return](./return.md) ifadesinde bir işlenen belirtiyorsa, zaman uyumsuz bir yöntemin dönüş türü olarak belirtirsiniz `TResult` .</span><span class="sxs-lookup"><span data-stu-id="221b6-139">You specify `Task<TResult>` as the return type of an async method if the [return](./return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="221b6-140">`Task`Yöntem tamamlandığında anlamlı bir değer döndürülmezse kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="221b6-140">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="221b6-141">Diğer bir deyişle, yöntemine yapılan bir çağrı bir döndürür `Task` , ancak tamamlandığında, `Task` `await` sonucunu bekleyen tüm ifadeler `Task` `void` .</span><span class="sxs-lookup"><span data-stu-id="221b6-141">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
<span data-ttu-id="221b6-142">Dönüş türünü `void` öncelikle bu dönüş türü gerektiren olay işleyicilerini tanımlamak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="221b6-142">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="221b6-143">`void`Döndüren zaman uyumsuz bir yöntemi çağıran, bunu bekler ve yöntemin oluşturduğu özel durumları yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="221b6-143">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  

<span data-ttu-id="221b6-144">C# 7,0 ' den başlayarak, `GetAwaiter` kodun performans açısından kritik bölümlerinde bellek ayırmalarını en aza indirmek için bir yöntemine sahip olan, genellikle bir değer türü olan başka bir tür döndürüyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="221b6-144">Starting with C# 7.0, you return another type, typically a value type, that has a `GetAwaiter` method to minimize memory allocations in performance-critical sections of code.</span></span>

<span data-ttu-id="221b6-145">Daha fazla bilgi ve örnek için bkz. [zaman uyumsuz dönüş türleri](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="221b6-145">For more information and examples, see [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="221b6-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="221b6-146">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="221b6-147">await</span><span class="sxs-lookup"><span data-stu-id="221b6-147">await</span></span>](../operators/await.md)
- [<span data-ttu-id="221b6-148">İzlenecek yol: Async ve await kullanarak Web 'e erişme</span><span class="sxs-lookup"><span data-stu-id="221b6-148">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="221b6-149">Async ve await ile zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="221b6-149">Asynchronous Programming with async and await</span></span>](../../programming-guide/concepts/async/index.md)
