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
ms.openlocfilehash: 89133339a75c70e3ac86d627065e78d555bff71d
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507210"
---
# <a name="async-c-reference"></a>async (C# Başvurusu)

Bir `async` yöntem, [lambda ifade](../../programming-guide/statements-expressions-operators/lambda-expressions.md)veya [anonim yöntem](../operators/delegate-operator.md) asynchronous olduğunu belirtmek için değiştirici kullanın. Bu değiştiriciyi bir yöntem veya ifadede kullanırsanız, buna *async yöntemi*denir. Aşağıdaki örnekte bir async `ExampleMethodAsync`yöntemi tanımlanır:
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

Asynchronous programlamada yeniyseniz veya async yönteminin [ `await` operatörü](../operators/await.md) arayanın iş parçacığıengellemeden uzun süreli bir iş yapmak için nasıl kullandığını anlamıyorsanız, [Asynchronous Programming'deki](../../programming-guide/concepts/async/index.md)girişi async ile okuyun ve bekleyin. Aşağıdaki kod bir async yöntemi içinde <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> bulunur ve yöntemi çağırır:
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
Bir async yöntemi, ilk `await` ifadesine ulaşana kadar eşzamanlı olarak çalışır ve bu noktada yöntem beklenen görev tamamlanana kadar askıya alınır. Bu arada, denetim, bir sonraki bölümdeki örnekte gösterildiği gibi yöntemi çağırana döner.  
  
Anahtar kelimenin `async` modiyi yöntemi bir `await` ifade veya deyim içermiyorsa, yöntem eşzamanlı olarak yürütülür. Derleyici uyarısı, bu durum bir hata gösterebilir, `await` çünkü ifadeler içermeyen herhangi bir async yöntemleri sizi uyarır. Bkz. [Derleyici Uyarısı (düzey 1) CS4014](../compiler-messages/cs4014.md).  
  
 Anahtar `async` kelime, yalnızca bir yöntemi, lambda ifadesini veya anonim bir yöntemi değiştirirken bir anahtar kelime olması açısından bağlamsaldır. Tüm diğer bağlamlarda bu, tanımlayıcı olarak yorumlanır.  
  
## <a name="example"></a>Örnek  
Aşağıdaki örnekte, bir async olay işleyicisi `StartButton_Click`ve bir async `ExampleMethodAsync`yöntemi arasındaki denetim yapısı ve akışı gösterir. Async yönteminin sonucu, bir web sayfasının karakter sayısıdır. Kod, Visual Studio'da oluşturduğunuz bir Windows Presentation Foundation (WPF) uygulaması veya Windows Mağazası uygulaması için uygundur; uygulamayı ayarlamak için kod açıklamalarına bakın.  

Bu kodu Visual Studio'da Windows Presentation Foundation (WPF) uygulaması veya Windows Mağazası uygulaması olarak çalıştırabilirsiniz. Bir Düğme denetimi `StartButton` ne adlı ve `ResultsTextBox`bir Textbox denetimi adlı gerekir. Adları ve işleyiciyi böyle bir şeye sahip olacak şekilde ayarlamayı unutmayın:  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
Kodu WPF uygulaması olarak çalıştırmak için:  

- Bu kodu MainWindow.xaml.cs `MainWindow` sınıfa yapıştırın.  
- System.Net.Http adresine bir başvuru ekleyin.  
- System.Net.Http için bir `using` yönerge ekleyin.  
  
Kodu Windows Mağazası uygulaması olarak çalıştırmak için:  

- Bu kodu MainPage.xaml.cs `MainPage` sınıfa yapıştırın.  
- System.Net.Http ve System.Threading.Tasks için yönergeleri kullanarak ekleyin.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
> Görevler ve bir görevi beklerken yürüten kod hakkında daha fazla bilgi için, [async ile Asynchronous Programming'e bakın ve bekliyoruz.](../../programming-guide/concepts/async/index.md) Benzer öğeleri kullanan tam bir WPF örneği için Bkz. [Walkthrough: Async kullanarak Web'e erişim ve Bekleme](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
## <a name="return-types"></a>Dönüş Türleri  
Bir async yöntemi aşağıdaki iade türlerine sahip olabilir:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [geçersizdir.](../builtin-types/void.md) `async void`arayanlar bu yöntemleri buşekildemedığından `await` ve başarılı tamamlama veya hata koşullarını bildirmek için farklı bir mekanizma uygulamagerektiğinden, yöntemler genellikle olay işleyicileri dışındaki kodlar için önerilmez.
- C# 7.0 ile başlayarak, erişilebilir `GetAwaiter` bir yönteme sahip herhangi bir tür. Türü `System.Threading.Tasks.ValueTask<TResult>` böyle bir uygulamadır. NuGet paketini `System.Threading.Tasks.Extensions`ekleyerek kullanılabilir.

Async yöntemi herhangi bir [beyan](./in-parameter-modifier.md)edemez , [ref](./ref.md) veya [out](./out-parameter-modifier.md) parametreleri, ne de bir [referans dönüş değeri](../../programming-guide/classes-and-structs/ref-returns.md)olabilir , ama bu tür parametrelere sahip yöntemleri çağırabilirsiniz.  
  
Yöntemin `Task<TResult>` [dönüş](./return.md) deyimi bir operand türü `TResult`belirtenden bir async yönteminin dönüş türü olarak belirtirsiniz. Yöntem `Task` tamamlandığında anlamlı bir değer döndürülmezse kullanırsınız. Diğer bir zamanda, yönteme `Task`yapılan bir `Task` çağrı, ancak `await` tamamlandığında, `Task` değerlendirmeyi bekleyen herhangi `void`bir ifadeyi döndürür.  
  
`void` İade türünü öncelikle bu iade türünü gerektiren olay işleyicilerini tanımlamak için kullanırsınız. -dönen async `void`yöntemini arayan kişi onu bekteemez ve yöntemin attığı özel durumları yakalayamaz.  

C# 7.0 ile başlayarak, kodun performans açısından kritik `GetAwaiter` bölümlerinde bellek ayırmalarını en aza indirmek için bir yöntemi olan başka bir tür ( genellikle bir değer türü, döndürür.

Daha fazla bilgi ve örnekler [için, Async İade Türleri'ne](../../programming-guide/concepts/async/async-return-types.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [await](../operators/await.md)
- [İzlenecek yol: Async ve Await Kullanarak Web'e Erişme](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async ve await ile Asynchronous Programlama](../../programming-guide/concepts/async/index.md)
