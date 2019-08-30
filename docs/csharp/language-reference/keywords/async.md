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
ms.openlocfilehash: 71e3781b08bca3441dbd55704bcb0f7de635097e
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168643"
---
# <a name="async-c-reference"></a>async (C# Başvurusu)

Bir yöntem, [lambda ifadesi](../../programming-guide/statements-expressions-operators/lambda-expressions.md)veya [anonim yöntemin](../operators/delegate-operator.md) zaman uyumsuz olduğunu belirtmek için değiştiricisinikullanın.`async` Bu değiştiriciyi bir yöntem veya ifadede kullanırsanız, *zaman uyumsuz bir yöntem*olarak adlandırılır. Aşağıdaki örnek adlı `ExampleMethodAsync`bir zaman uyumsuz metodu tanımlar:
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

Zaman uyumsuz programlamaya yeni başladıysanız veya zaman uyumsuz bir yöntemin, çağıranın iş parçacığını engellemeden uzun süre çalışan bir iş yapmak için [ `await` işlecini](../operators/await.md) nasıl kullandığını anladıysanız, [ile zaman uyumsuz programlamaya giriş Async ve await](../../programming-guide/concepts/async/index.md). Aşağıdaki kod zaman uyumsuz bir yöntem içinde bulunur ve <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> yöntemini çağırır:
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
Zaman uyumsuz bir yöntem, ilk `await` ifadesine ulaşana dek zaman uyumlu olarak çalışır ve bu noktada, beklenen görev tamamlanana kadar yöntem askıya alınır. Bu arada, denetim, bir sonraki bölümdeki örnekte gösterildiği gibi yöntemi çağırana döner.  
  
`async` Anahtar sözcüğünün değiştirdiği Yöntem bir `await` ifade veya deyim içermiyorsa, yöntem zaman uyumlu olarak yürütülür. Bir derleyici uyarısı, deyimi içermeyen `await` herhangi bir zaman uyumsuz metotlarda sizi uyarır, çünkü bu durum bir hata gösteriyor olabilir. Bkz. [Derleyici Uyarısı (düzey 1) CS4014](../compiler-messages/cs4014.md).  
  
 `async` Anahtar sözcüğü, yalnızca bir metodu, bir lambda ifadesini veya anonim bir yöntemi değiştirdiğinde anahtar kelimedir. Tüm diğer bağlamlarda bu, tanımlayıcı olarak yorumlanır.  
  
## <a name="example"></a>Örnek  
Aşağıdaki örnek, zaman uyumsuz olay işleyicisi, `StartButton_Click`ve zaman uyumsuz bir `ExampleMethodAsync`yöntem arasındaki denetimin yapısını ve akışını gösterir. Zaman uyumsuz yöntemin sonucu bir Web sayfasının karakter sayısıdır. Kod, Visual Studio 'da oluşturduğunuz bir Windows Presentation Foundation (WPF) uygulamasına veya Windows Mağazası uygulamasına uygundur; uygulamayı ayarlamaya yönelik kod açıklamalarını inceleyin.  

Bu kodu, Visual Studio 'da bir Windows Presentation Foundation (WPF) uygulaması veya bir Windows Mağazası uygulaması olarak çalıştırabilirsiniz. Adlı `StartButton` bir düğme denetimine ve adlı `ResultsTextBox`TextBox denetimine ihtiyacınız vardır. Adları ve işleyiciyi şuna benzer olacak şekilde ayarlamayı unutmayın:  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
Kodu WPF uygulaması olarak çalıştırmak için:  

- Bu kodu `MainWindow` MainWindow.xaml.cs içindeki sınıfa yapıştırın.  
- System .net. http öğesine bir başvuru ekleyin.  
- System .net `using` . http için bir yönerge ekleyin.  
  
Kodu bir Windows Mağazası uygulaması olarak çalıştırmak için:  
- Bu kodu `MainPage` MainPage.xaml.cs içindeki sınıfa yapıştırın.  
- System .net. http ve System. Threading. Tasks için using yönergelerini ekleyin.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
> Görevler ve bir görevi beklerken yürütülen kod hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md). Benzer öğeleri kullanan tam bir WPF örneği için bkz [. İzlenecek yol: Async ve await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)kullanarak Web 'e erişme.  
  
## <a name="return-types"></a>Dönüş Türleri  
Zaman uyumsuz bir yöntem aşağıdaki dönüş türlerine sahip olabilir:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [void](./void.md). `async void`yöntemler genellikle olay işleyicileri dışındaki kod için önerilmez çünkü çağıranlar `await` bu yöntemlere izin vermez ve başarılı tamamlamayı veya hata koşullarını raporlamak için farklı bir mekanizma uygulamalıdır.
- 7,0 ile C# başlayarak, erişilebilir `GetAwaiter` bir yöntemi olan herhangi bir tür. Bu `System.Threading.Tasks.ValueTask<TResult>` tür bir uygulama. NuGet paketi `System.Threading.Tasks.Extensions`eklenerek kullanılabilir. 

Async yöntemi [içinde](./in-parameter-modifier.md)herhangi bir [ref](./ref.md) veya [Out](./out-parameter-modifier.md) parametresi bildiremez ve [Başvuru dönüş değerine](../../programming-guide/classes-and-structs/ref-returns.md)sahip olabilir, ancak bu parametrelere sahip yöntemleri çağırabilir.  
  
Metodun `Task<TResult>` [Return](./return.md) ifadesinde`TResult`bir işlenen belirtiyorsa, zaman uyumsuz bir yöntemin dönüş türü olarak belirtirsiniz. Yöntem tamamlandığında `Task` anlamlı bir değer döndürülmezse kullanırsınız. Diğer bir deyişle, yöntemine yapılan bir `Task`çağrı bir döndürür, ancak `Task` tamamlandığında, `Task` sonucunu `void`bekleyen tüm `await` ifadeler.  
  
Dönüş türünü öncelikle `void` bu dönüş türü gerektiren olay işleyicilerini tanımlamak için kullanırsınız. Döndüren zaman uyumsuz bir `void`yöntemi çağıran, bunu bekler ve yöntemin oluşturduğu özel durumları yakalayamaz.  

7,0 ' C# den başlayarak, kodun performans açısından kritik bölümlerinde bellek ayırmalarını en aza indirmek için bir `GetAwaiter` yöntemine sahip olan, genellikle bir değer türü olan başka bir tür döndürüyorsunuz. 

Daha fazla bilgi ve örnek için bkz. [zaman uyumsuz dönüş türleri](../../programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [await](../operators/await.md)
- [İzlenecek yol: Async ve await kullanarak Web 'e erişme](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async ve Await ile Zaman Uyumsuz Programlama](../../programming-guide/concepts/async/index.md)
