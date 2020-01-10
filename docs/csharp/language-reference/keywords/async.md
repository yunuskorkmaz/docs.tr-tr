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
ms.openlocfilehash: 3d3f045eed3bad3624ed4994aebb862c52a4e196
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713777"
---
# <a name="async-c-reference"></a>async (C# Başvurusu)

Bir yöntem, [lambda ifadesi](../../programming-guide/statements-expressions-operators/lambda-expressions.md)veya [anonim yöntemin](../operators/delegate-operator.md) zaman uyumsuz olduğunu belirtmek için `async` değiştiricisini kullanın. Bu değiştiriciyi bir yöntem veya ifadede kullanırsanız, *zaman uyumsuz bir yöntem*olarak adlandırılır. Aşağıdaki örnek, `ExampleMethodAsync`adlı bir zaman uyumsuz yöntemi tanımlar:
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

Zaman uyumsuz programlamaya yeni başladıysanız veya bir zaman uyumsuz yöntemin, uzun süre çalışan bir işi çağıranın iş parçacığını engellemeden nasıl [`await`](../operators/await.md) kullandığını anladıysanız, [Async ve await Ile zaman uyumsuz programlamaya](../../programming-guide/concepts/async/index.md)giriş makalesini okuyun. Aşağıdaki kod zaman uyumsuz bir yöntem içinde bulunur ve <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> yöntemini çağırır:
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
Zaman uyumsuz bir yöntem, ilk `await` ifadesine ulaşana kadar zaman uyumlu olarak çalışır ve bu noktada, beklenen görev tamamlanana kadar yöntem askıya alınır. Bu arada, denetim, bir sonraki bölümdeki örnekte gösterildiği gibi yöntemi çağırana döner.  
  
`async` anahtar sözcüğünün değiştirdiği Yöntem bir `await` ifadesi veya deyimi içermiyorsa, yöntem zaman uyumlu olarak yürütülür. Bir derleyici uyarısı, `await` deyimleri içermeyen herhangi bir zaman uyumsuz yöntemde sizi uyarır, çünkü bu durum bir hata gösteriyor olabilir. Bkz. [Derleyici Uyarısı (düzey 1) CS4014](../compiler-messages/cs4014.md).  
  
 `async` anahtar sözcüğü, yalnızca bir metodu, bir lambda ifadesini veya anonim bir yöntemi değiştirdiğinde anahtar kelimedir. Tüm diğer bağlamlarda bu, tanımlayıcı olarak yorumlanır.  
  
## <a name="example"></a>Örnek  
Aşağıdaki örnek, bir zaman uyumsuz olay işleyicisi, `StartButton_Click`ve zaman uyumsuz yöntem `ExampleMethodAsync`arasındaki denetimin yapısını ve akışını gösterir. Zaman uyumsuz yöntemin sonucu bir Web sayfasının karakter sayısıdır. Kod, Visual Studio 'da oluşturduğunuz bir Windows Presentation Foundation (WPF) uygulamasına veya Windows Mağazası uygulamasına uygundur; uygulamayı ayarlamaya yönelik kod açıklamalarını inceleyin.  

Bu kodu, Visual Studio 'da bir Windows Presentation Foundation (WPF) uygulaması veya bir Windows Mağazası uygulaması olarak çalıştırabilirsiniz. `StartButton` adlı bir düğme denetimine ve `ResultsTextBox`adlı TextBox denetimine ihtiyacınız vardır. Adları ve işleyiciyi şuna benzer olacak şekilde ayarlamayı unutmayın:  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
Kodu WPF uygulaması olarak çalıştırmak için:  

- Bu kodu MainWindow.xaml.cs içindeki `MainWindow` sınıfına yapıştırın.  
- System .net. http öğesine bir başvuru ekleyin.  
- System .net. http için bir `using` yönergesi ekleyin.  
  
Kodu bir Windows Mağazası uygulaması olarak çalıştırmak için:  

- Bu kodu MainPage.xaml.cs içindeki `MainPage` sınıfına yapıştırın.  
- System .net. http ve System. Threading. Tasks için using yönergelerini ekleyin.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
> Görevler ve bir görevi beklerken yürütülen kod hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md). Benzer öğeleri kullanan tam bir WPF örneği için bkz. [Izlenecek yol: Async ve await kullanarak Web 'e erişme](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
## <a name="return-types"></a>Dönüş Türleri  
Zaman uyumsuz bir yöntem aşağıdaki dönüş türlerine sahip olabilir:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [void](./void.md). `async void` yöntemler genellikle olay işleyicileri dışındaki kod için önerilmez çünkü çağıranlar bu yöntemleri `await` ve başarılı tamamlamayı veya hata koşullarını raporlamak için farklı bir mekanizma uygulamalıdır.
- 7,0 ile C# başlayarak, erişilebilir `GetAwaiter` yöntemi olan herhangi bir tür. `System.Threading.Tasks.ValueTask<TResult>` türü, bu tür bir uygulama. NuGet paketi `System.Threading.Tasks.Extensions`eklenerek kullanılabilir. 

Async yöntemi [içinde](./in-parameter-modifier.md)herhangi bir [ref](./ref.md) veya [Out](./out-parameter-modifier.md) parametresi bildiremez ve [Başvuru dönüş değerine](../../programming-guide/classes-and-structs/ref-returns.md)sahip olabilir, ancak bu parametrelere sahip yöntemleri çağırabilir.  
  
Metodun [Return](./return.md) ifadesinde `TResult`türünde bir işlenen belirtiyorsa, zaman uyumsuz bir yöntemin dönüş türü olarak `Task<TResult>` belirtirsiniz. Yöntem tamamlandığında anlamlı bir değer döndürülmezse `Task` kullanırsınız. Diğer bir deyişle, yöntemine yapılan bir çağrı `Task`döndürür, ancak `Task` tamamlandığında, `Task` bekleyen herhangi bir `await` ifadesi `void`sonucunu verir.  
  
Bu dönüş türünü gerektiren olay işleyicilerini tanımlamak için öncelikle `void` dönüş türünü kullanırsınız. `void`döndüren zaman uyumsuz bir yöntem çağırıcısı bunu bekler ve yöntemin oluşturduğu özel durumları yakalayamaz.  

7,0 ile C# başlayarak, kodun performans açısından kritik bölümlerinde bellek ayırmalarını en aza indirmek için bir `GetAwaiter` yöntemi olan, genellikle bir değer türü olan başka bir tür döndürüyorsunuz. 

Daha fazla bilgi ve örnek için bkz. [zaman uyumsuz dönüş türleri](../../programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [await](../operators/await.md)
- [İzlenecek yol: Async ve Await Kullanarak Web'e Erişme](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async ve Await ile Zaman Uyumsuz Programlama](../../programming-guide/concepts/async/index.md)
