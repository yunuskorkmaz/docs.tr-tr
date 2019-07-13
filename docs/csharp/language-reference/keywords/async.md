---
title: zaman uyumsuz - C# başvurusu
ms.custom: seodec18
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 346cfccd076866e9c321974aaa8c8ddd367a17ea
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859572"
---
# <a name="async-c-reference"></a><span data-ttu-id="400aa-102">async (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="400aa-102">async (C# Reference)</span></span>
<span data-ttu-id="400aa-103">Kullanım `async` değiştiricisi belirtmek için bir yöntemin [lambda ifadesi](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), veya [anonim yöntem](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) zaman uyumsuzdur.</span><span class="sxs-lookup"><span data-stu-id="400aa-103">Use the `async` modifier to specify that a method, [lambda expression](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), or [anonymous method](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) is asynchronous.</span></span> <span data-ttu-id="400aa-104">Bu değiştiriciyi bir yöntem veya ifadede kullanırsanız, şeklinde adlandırılan bir *zaman uyumsuz yöntem*.</span><span class="sxs-lookup"><span data-stu-id="400aa-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="400aa-105">Aşağıdaki örnek adlı bir zaman uyumsuz yöntem tanımlar `ExampleMethodAsync`:</span><span class="sxs-lookup"><span data-stu-id="400aa-105">The following example defines an async method named `ExampleMethodAsync`:</span></span> 
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  
 
<span data-ttu-id="400aa-106">Zaman uyumsuz programlamada yeniyseniz veya zaman uyumsuz bir yöntem nasıl kullandığını `await` yapanın iş parçacığını engellemeden muhtemelen uzun süren iş yapmak için anahtar sözcüğü Giriş okuma [zaman uyumsuz programlama Async ve await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="400aa-106">If you're new to asynchronous programming or do not understand how an async method uses the `await` keyword to do potentially long-running work without blocking the caller’s thread, read the introduction in [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="400aa-107">Aşağıdaki kod, zaman uyumsuz bir yöntem ve çağrıları içinde bulunur <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="400aa-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span> 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
<span data-ttu-id="400aa-108">İlk ulaşana dek zaman uyumsuz bir yöntem zaman uyumlu olarak çalışır `await` ifadesi, bu noktada yöntem askıya alınır beklenen görev tamamlanana kadar.</span><span class="sxs-lookup"><span data-stu-id="400aa-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="400aa-109">Bu arada, denetim, bir sonraki bölümdeki örnekte gösterildiği gibi yöntemi çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="400aa-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
<span data-ttu-id="400aa-110">Yöntem, `async` anahtar sözcüğünün değiştirdiği içermeyen bir `await` ifadesi veya deyimi yürütülür zaman uyumlu olarak.</span><span class="sxs-lookup"><span data-stu-id="400aa-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="400aa-111">Bir derleyici uyarısı içermeyen zaman uyumsuz yöntemler konusunda uyarır `await` deyimleri, çünkü bu durumda bir hata gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="400aa-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="400aa-112">Bkz: [Derleyici Uyarısı (düzey 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="400aa-112">See [Compiler Warning (level 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="400aa-113">`async` Yalnızca bir yöntem, lambda ifadesi veya anonim yöntemi değiştirdiğinde anahtar sözcük olması. anahtar sözcüğü bağlamsal.</span><span class="sxs-lookup"><span data-stu-id="400aa-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="400aa-114">Tüm diğer bağlamlarda bu, tanımlayıcı olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="400aa-114">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="400aa-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="400aa-115">Example</span></span>  
<span data-ttu-id="400aa-116">Aşağıdaki örnek, yapısını ve zaman uyumsuz olay işleyicisi arasında denetim akışını gösterir `StartButton_Click`, zaman uyumsuz yöntemi `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="400aa-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="400aa-117">Zaman uyumsuz yöntemin sonucu karakter, bir web sayfasının sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="400aa-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="400aa-118">Kod, bir Windows Presentation Foundation (WPF) veya Visual Studio'da oluşturma Windows Store uygulaması için uygundur; uygulamayı hazırlama açıklamalarına bakın.</span><span class="sxs-lookup"><span data-stu-id="400aa-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  

<span data-ttu-id="400aa-119">Bu kodu Visual Studio'da bir Windows Presentation Foundation (WPF) veya Windows Store uygulaması çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="400aa-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="400aa-120">Adlı bir düğme denetimi ihtiyacınız `StartButton` ve adlı bir metin kutusu denetimi `ResultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="400aa-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="400aa-121">Aşağıdakine benzer olması adları ve işleyici ayarlamayı unutmayın:</span><span class="sxs-lookup"><span data-stu-id="400aa-121">Remember to set the names and handler so that you have something like this:</span></span>  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
<span data-ttu-id="400aa-122">WPF uygulaması olarak kodu çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="400aa-122">To run the code as a WPF app:</span></span>  

- <span data-ttu-id="400aa-123">Bu kodu yapıştırın `MainWindow` MainWindow.xaml.cs sınıfta.</span><span class="sxs-lookup"><span data-stu-id="400aa-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>  
- <span data-ttu-id="400aa-124">System.Net.Http bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="400aa-124">Add a reference to System.Net.Http.</span></span>  
- <span data-ttu-id="400aa-125">Ekleme bir `using` System.Net.Http yönergesi.</span><span class="sxs-lookup"><span data-stu-id="400aa-125">Add a `using` directive for System.Net.Http.</span></span>  
  
<span data-ttu-id="400aa-126">Windows Store uygulaması olarak kodu çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="400aa-126">To run the code as a Windows Store app:</span></span>  
- <span data-ttu-id="400aa-127">Bu kodu yapıştırın `MainPage` MainPage.xaml.cs sınıfta.</span><span class="sxs-lookup"><span data-stu-id="400aa-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>  
- <span data-ttu-id="400aa-128">System.Net.Http ve System.Threading.Tasks yönergeleri kullanarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="400aa-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  <span data-ttu-id="400aa-129">Görevler ve bir görevi beklerken yürütülen kod hakkında daha fazla bilgi için bkz. [Asynchronous Programming with async ve await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="400aa-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="400aa-130">Benzer öğeleri kullanan bir tam WPF örneği için bkz. [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="400aa-130">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="400aa-131">Dönüş türleri</span><span class="sxs-lookup"><span data-stu-id="400aa-131">Return Types</span></span>  
<span data-ttu-id="400aa-132">Zaman uyumsuz bir yöntem, aşağıdaki dönüş türlerine sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="400aa-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="400aa-133">[void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="400aa-133">[void](../../../csharp/language-reference/keywords/void.md).</span></span> <span data-ttu-id="400aa-134">`async void` yöntem genellikle önerilmez olay işleyicileri dışındaki kod için çağıranlar olamaz çünkü `await` bu yöntemleri ve başarıyla tamamlandığında veya hata koşullarını raporlamak için farklı bir mekanizma uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="400aa-134">`async void` methods are generally discouraged for code other than event handlers because callers cannot `await` those methods and must implement a different mechanism to report successful completion or error conditions.</span></span>
- <span data-ttu-id="400aa-135">C# 7.0, bir erişilebilir olan herhangi bir türü'ile başlayan `GetAwaiter` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="400aa-135">Starting with C# 7.0, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="400aa-136">`System.Threading.Tasks.ValueTask<TResult>` Böyle bir uygulama türüdür.</span><span class="sxs-lookup"><span data-stu-id="400aa-136">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="400aa-137">NuGet paketini ekleyerek kullanılabilir `System.Threading.Tasks.Extensions`.</span><span class="sxs-lookup"><span data-stu-id="400aa-137">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span> 

<span data-ttu-id="400aa-138">Zaman uyumsuz yöntemin herhangi bildiremezsiniz [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) veya [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametreleri ya da can sahip bir [başvuru dönüş değeri](../../programming-guide/classes-and-structs/ref-returns.md), ancak bu yöntemleri çağırabilirsiniz parametrelere sahip.</span><span class="sxs-lookup"><span data-stu-id="400aa-138">The async method can't declare any [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>  
  
<span data-ttu-id="400aa-139">Belirttiğiniz `Task<TResult>` zaman uyumsuz bir yöntemin dönüş türü, [dönüş](../../../csharp/language-reference/keywords/return.md) yöntemi deyiminin türünde bir işlenen belirtiyorsa `TResult`.</span><span class="sxs-lookup"><span data-stu-id="400aa-139">You specify `Task<TResult>` as the return type of an async method if the [return](../../../csharp/language-reference/keywords/return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="400aa-140">Kullandığınız `Task` yöntem tamamlandığında anlamlı bir değer döndürülürse.</span><span class="sxs-lookup"><span data-stu-id="400aa-140">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="400aa-141">Diğer bir deyişle, yönteme bir çağrı döndürür bir `Task`, ancak `Task` tamamlandığında, tüm `await` bekleyen ifade `Task` değerlendiren `void`.</span><span class="sxs-lookup"><span data-stu-id="400aa-141">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
<span data-ttu-id="400aa-142">Kullandığınız `void` dönüş ilgili dönüş türünü gerektiren olay işleyicilerini tanımlamak için öncelikle türü.</span><span class="sxs-lookup"><span data-stu-id="400aa-142">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="400aa-143">Çağıran bir `void`-döndüren zaman uyumsuz yöntemi Bekleyemez ve yöntemin oluşturduğu özel durumları yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="400aa-143">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  

<span data-ttu-id="400aa-144">İle başlayarak C# 7.0, başka bir türe sahip genellikle bir değer türü, iade bir `GetAwaiter` bellek ayırmaları performans açısından kritik kod bölümlerini en aza indirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="400aa-144">Starting with C# 7.0, you return another type, typically a value type, that has a `GetAwaiter` method to minimize memory allocations in performance-critical sections of code.</span></span> 

<span data-ttu-id="400aa-145">Daha fazla bilgi ve örnekler için bkz. [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="400aa-145">For more information and examples, see [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="400aa-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="400aa-146">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="400aa-147">await</span><span class="sxs-lookup"><span data-stu-id="400aa-147">await</span></span>](../../../csharp/language-reference/keywords/await.md)
- [<span data-ttu-id="400aa-148">İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await</span><span class="sxs-lookup"><span data-stu-id="400aa-148">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="400aa-149">Async ve Await ile Zaman Uyumsuz Programlama</span><span class="sxs-lookup"><span data-stu-id="400aa-149">Asynchronous Programming with async and await</span></span>](../../../csharp/programming-guide/concepts/async/index.md)
