---
title: async (C# Başvurusu)
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 47c13f960cb6b70205feabfa0488e584ad6a098f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216944"
---
# <a name="async-c-reference"></a>async (C# Başvurusu)
Kullanım `async` belirtmek için değiştirici yöntemi, bir [lambda ifadesi](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), veya [anonim yöntemi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) zaman uyumsuz olarak çağrılır. Bir yöntem veya ifadesi bu değiştirici kullanıyorsanız, bunu olarak adlandırılır bir *async yöntemi*. Aşağıdaki örnek, adlandırılmış bir zaman uyumsuz yöntem tanımlar `ExampleMethodAsync`: 
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  
 
Zaman uyumsuz programlama yeni ya da bir zaman uyumsuz yöntem nasıl kullandığını anlaşılmıyor `await` arayanın iş parçacığı, engellenmeden potansiyel olarak uzun süre çalışan iş yapmak için anahtar sözcüğü okuma girişte [zaman uyumsuz programlama Async ve await](../../../csharp/programming-guide/concepts/async/index.md). Aşağıdaki kod bir zaman uyumsuz yöntem ve çağrıları içinde bulunur <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> yöntemi: 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
İlk ulaşana kadar bir zaman uyumsuz yöntem eşzamanlı olarak çalışan `await` hangi noktada yöntemi askıya awaited görevi tamamlanana kadar ifade. Bu arada, denetim, bir sonraki bölümdeki örnekte gösterildiği gibi yöntemi çağırana döner.  
  
Varsa yöntemi, `async` anahtar sözcüğü değiştirir içermiyor. bir `await` ifadesi veya deyimi, yöntem yürütür zaman uyumlu olarak. Derleyici Uyarısı içermeyen herhangi bir zaman uyumsuz yöntem uyarıları `await` deyimleri, çünkü bu durumu gösteren bir hata olabilir. Bkz: [Derleyici Uyarısı (düzey 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).  
  
 `async` Yalnızca bir yöntemi, bir lambda ifadesi veya anonim bir yöntem değişiklik yaptığında bir anahtar sözcüktür, anahtar sözcüğü bağlamsal. Tüm diğer bağlamlarda bu, tanımlayıcı olarak yorumlanır.  
  
## <a name="example"></a>Örnek  
Aşağıdaki örnek, yapı ve bir zaman uyumsuz olay işleyicisi arasındaki denetim akışını gösterir `StartButton_Click`ve bir zaman uyumsuz yöntem `ExampleMethodAsync`. Bir web sayfasının karakter sayısını zaman uyumsuz yönteminden sonucudur. Kod, bir Windows Presentation Foundation (WPF) uygulamasını veya Visual Studio'da oluşturma Windows mağazası uygulaması için uygundur; uygulamasını kurup için kod açıklamalarına bakın.  

Bir Windows Presentation Foundation (WPF) uygulaması veya bir Windows mağazası uygulaması olarak, bu kod Visual Studio'da çalıştırabilirsiniz. Adlı bir düğme denetimine gerek `StartButton` ve adlı Textbox denetimi `ResultsTextBox`. Böylece şöyle bir şey sahip adları ve işleyici ayarlamayı unutmayın:  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
Kod bir WPF uygulaması çalıştırmak için:  

- Bu kod içine yapıştırma `MainWindow` MainWindow.xaml.cs sınıfta.  
- System.Net.Http bir başvuru ekleyin.  
- Ekleme bir `using` System.Net.Http için yönerge.  
  
Kod bir Windows mağazası uygulaması çalıştırmak için:  
- Bu kod içine yapıştırma `MainPage` MainPage.xaml.cs sınıfta.  
- System.Net.Http ve System.Threading.Tasks için yönergeleri kullanarak ekleyin.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  Görevler ve bir görev için beklenirken yürütülen kodu hakkında daha fazla bilgi için bkz: [zaman uyumsuz programlama ile async ve await](../../../csharp/programming-guide/concepts/async/index.md). Benzer öğeleri kullanan bir tam WPF örnek için bkz: [izlenecek yol: Web kullanarak zaman uyumsuz ve bekleme tarafından erişme](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
## <a name="return-types"></a>Dönüş Türleri  
Async yöntemi, dönüş türleri aşağıdakilere sahip olabilir:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [void](../../../csharp/language-reference/keywords/void.md), hangi yalnızca kullanılmalıdır olay işleyicileri için.
- C# 7.0, bir erişilebilir olan herhangi bir tür'ile başlayan `GetAwaiter` yöntemi. `System.Threading.Tasks.ValueTask<TResult>` Bu tür bir uygulama türüdür. NuGet paketi ekleyerek kullanılabilir olur `System.Threading.Tasks.Extensions`. 

Async yöntemi herhangi bildiremezsiniz [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) veya [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametreleri ya da can sahip bir [başvuru dönüş değeri](../../programming-guide/classes-and-structs/ref-returns.md), ancak yöntemleri çağırabilir Bu tür parametreler sahip.  
  
Belirttiğiniz `Task<TResult>` bir zaman uyumsuz yönteminin dönüş türü olarak varsa [dönmek](../../../csharp/language-reference/keywords/return.md) yöntemin ifadesi işleneni türü belirtir `TResult`. Kullandığınız `Task` yöntemi tamamlandığında hiçbir anlamlı değeri döndürülür. Diğer bir deyişle, yöntemine bir çağrı döndürür bir `Task`, ancak ne zaman `Task` tamamlandığında, tüm `await` bekliyor ifade `Task` değerlendiren `void`.  
  
Kullandığınız `void` dönüş türü, dönüş türü gerektiren olay işleyicileri öncelikle tanımlayın. Çağıran bir `void`-zaman uyumsuz yöntem döndürme await olamaz ve yöntemi atar özel durumlarını yakalama olamaz.  

C# 7. 0'dan başlayarak, başka bir tür, sahip genellikle bir değer türü, dönüş bir `GetAwaiter` performans açısından kritik kod bölümlerini miminize bellek ayırma yöntemi. 

Daha fazla bilgi ve örnekler için bkz: [zaman uyumsuz dönüş türleri](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>  
 [await](../../../csharp/language-reference/keywords/await.md)  
 [İzlenecek yol: Async ve Await Kullanarak Web'e Erişme](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Async ve Await ile Zaman Uyumsuz Programlama](../../../csharp/programming-guide/concepts/async/index.md)
