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
ms.openlocfilehash: f902d6a92f9d982dc00c3446f7b516c372f1a30e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709526"
---
# <a name="async-c-reference"></a>async (C# Başvurusu)
Kullanım `async` değiştiricisi belirtmek için bir yöntemin [lambda ifadesi](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), veya [anonim yöntem](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) zaman uyumsuzdur. Bu değiştiriciyi bir yöntem veya ifadede kullanırsanız, şeklinde adlandırılan bir *zaman uyumsuz yöntem*. Aşağıdaki örnek adlı bir zaman uyumsuz yöntem tanımlar `ExampleMethodAsync`: 
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  
 
Zaman uyumsuz programlamada yeniyseniz veya zaman uyumsuz bir yöntem nasıl kullandığını `await` yapanın iş parçacığını engellemeden muhtemelen uzun süren iş yapmak için anahtar sözcüğü Giriş okuma [zaman uyumsuz programlama Async ve await](../../../csharp/programming-guide/concepts/async/index.md). Aşağıdaki kod, zaman uyumsuz bir yöntem ve çağrıları içinde bulunur <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> yöntemi: 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
İlk ulaşana dek zaman uyumsuz bir yöntem zaman uyumlu olarak çalışır `await` ifadesi, bu noktada yöntem askıya alınır beklenen görev tamamlanana kadar. Bu arada, denetim, bir sonraki bölümdeki örnekte gösterildiği gibi yöntemi çağırana döner.  
  
Yöntem, `async` anahtar sözcüğünün değiştirdiği içermeyen bir `await` ifadesi veya deyimi yürütülür zaman uyumlu olarak. Bir derleyici uyarısı içermeyen zaman uyumsuz yöntemler konusunda uyarır `await` deyimleri, çünkü bu durumda bir hata gösterebilir. Bkz: [Derleyici Uyarısı (düzey 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).  
  
 `async` Yalnızca bir yöntem, lambda ifadesi veya anonim yöntemi değiştirdiğinde anahtar sözcük olması. anahtar sözcüğü bağlamsal. Tüm diğer bağlamlarda bu, tanımlayıcı olarak yorumlanır.  
  
## <a name="example"></a>Örnek  
Aşağıdaki örnek, yapısını ve zaman uyumsuz olay işleyicisi arasında denetim akışını gösterir `StartButton_Click`, zaman uyumsuz yöntemi `ExampleMethodAsync`. Zaman uyumsuz yöntemin sonucu karakter, bir web sayfasının sayısıdır. Kod, bir Windows Presentation Foundation (WPF) veya Visual Studio'da oluşturma Windows Store uygulaması için uygundur; uygulamayı hazırlama açıklamalarına bakın.  

Bu kodu Visual Studio'da bir Windows Presentation Foundation (WPF) veya Windows Store uygulaması çalıştırabilirsiniz. Adlı bir düğme denetimi ihtiyacınız `StartButton` ve adlı bir metin kutusu denetimi `ResultsTextBox`. Aşağıdakine benzer olması adları ve işleyici ayarlamayı unutmayın:  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
WPF uygulaması olarak kodu çalıştırmak için:  

- Bu kodu yapıştırın `MainWindow` MainWindow.xaml.cs sınıfta.  
- System.Net.Http bir başvuru ekleyin.  
- Ekleme bir `using` System.Net.Http yönergesi.  
  
Windows Store uygulaması olarak kodu çalıştırmak için:  
- Bu kodu yapıştırın `MainPage` MainPage.xaml.cs sınıfta.  
- System.Net.Http ve System.Threading.Tasks yönergeleri kullanarak ekleyin.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  Görevler ve bir görevi beklerken yürütülen kod hakkında daha fazla bilgi için bkz. [Asynchronous Programming with async ve await](../../../csharp/programming-guide/concepts/async/index.md). Benzer öğeleri kullanan bir tam WPF örneği için bkz. [izlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
## <a name="return-types"></a>Dönüş Türleri  
Zaman uyumsuz bir yöntem, aşağıdaki dönüş türlerine sahip olabilir:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [void](../../../csharp/language-reference/keywords/void.md), hangi yalnızca kullanılmalıdır için olay işleyicileri.
- C# 7.0, bir erişilebilir olan herhangi bir türü'ile başlayan `GetAwaiter` yöntemi. `System.Threading.Tasks.ValueTask<TResult>` Böyle bir uygulama türüdür. NuGet paketini ekleyerek kullanılabilir `System.Threading.Tasks.Extensions`. 

Zaman uyumsuz yöntemin herhangi bildiremezsiniz [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) veya [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametreleri ya da can sahip bir [başvuru dönüş değeri](../../programming-guide/classes-and-structs/ref-returns.md), ancak bu yöntemleri çağırabilirsiniz parametrelere sahip.  
  
Belirttiğiniz `Task<TResult>` zaman uyumsuz bir yöntemin dönüş türü, [dönüş](../../../csharp/language-reference/keywords/return.md) yöntemi deyiminin türünde bir işlenen belirtiyorsa `TResult`. Kullandığınız `Task` yöntem tamamlandığında anlamlı bir değer döndürülürse. Diğer bir deyişle, yönteme bir çağrı döndürür bir `Task`, ancak `Task` tamamlandığında, tüm `await` bekleyen ifade `Task` değerlendiren `void`.  
  
Kullandığınız `void` dönüş ilgili dönüş türünü gerektiren olay işleyicilerini tanımlamak için öncelikle türü. Çağıran bir `void`-döndüren zaman uyumsuz yöntemi Bekleyemez ve yöntemin oluşturduğu özel durumları yakalayamaz.  

İle başlayarak C# 7.0, başka bir türe sahip genellikle bir değer türü, iade bir `GetAwaiter` bellek ayırmaları performans açısından kritik kod bölümlerini en aza indirmek için yöntemi. 

Daha fazla bilgi ve örnekler için bkz. [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [await](../../../csharp/language-reference/keywords/await.md)
- [İzlenecek yol: Zaman uyumsuz kullanarak Web'e erişme ve Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async ve Await ile Zaman Uyumsuz Programlama](../../../csharp/programming-guide/concepts/async/index.md)
