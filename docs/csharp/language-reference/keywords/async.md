---
description: Async-C# başvurusu
title: Async-C# başvurusu
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 78079d9940ea5363215411acea6b9ca269ff3ae1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160547"
---
# <a name="async-c-reference"></a>async (C# Başvurusu)

`async`Bir yöntem, [lambda ifadesi](../operators/lambda-expressions.md)veya [anonim yöntemin](../operators/delegate-operator.md) zaman uyumsuz olduğunu belirtmek için değiştiricisini kullanın. Bu değiştiriciyi bir yöntem veya ifadede kullanırsanız, *zaman uyumsuz bir yöntem*olarak adlandırılır. Aşağıdaki örnek adlı bir zaman uyumsuz metodu tanımlar `ExampleMethodAsync` :

```csharp
public async Task<int> ExampleMethodAsync()
{
    //...
}
```

Zaman uyumsuz programlamaya yeni başladıysanız veya zaman uyumsuz bir yöntemin, çağıranın iş parçacığını engellemeden uzun süre çalışan bir iş yapmak için [ `await` işlecini](../operators/await.md) nasıl kullandığını anlamayın, zaman uyumsuz [programlamada girişi zaman uyumsuz ve await ile](../../programming-guide/concepts/async/index.md)okuyun. Aşağıdaki kod zaman uyumsuz bir yöntem içinde bulunur ve <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> yöntemini çağırır:

```csharp
string contents = await httpClient.GetStringAsync(requestUrl);
```

Zaman uyumsuz bir yöntem, ilk ifadesine ulaşana dek zaman uyumlu `await` olarak çalışır ve bu noktada, beklenen görev tamamlanana kadar yöntem askıya alınır. Bu arada, denetim, bir sonraki bölümdeki örnekte gösterildiği gibi yöntemi çağırana döner.

`async`Anahtar sözcüğünün değiştirdiği Yöntem bir `await` ifade veya deyim içermiyorsa, yöntem zaman uyumlu olarak yürütülür. Bir derleyici uyarısı, deyimi içermeyen herhangi bir zaman uyumsuz metotlarda sizi uyarır `await` , çünkü bu durum bir hata gösteriyor olabilir. Bkz. [Derleyici Uyarısı (düzey 1) CS4014](../compiler-messages/cs4014.md).

 Anahtar sözcüğü, `async` yalnızca bir metodu, bir lambda ifadesini veya anonim bir yöntemi değiştirdiğinde anahtar kelimedir. Tüm diğer bağlamlarda bu, tanımlayıcı olarak yorumlanır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, zaman uyumsuz olay işleyicisi, `StartButton_Click` ve zaman uyumsuz bir yöntem arasındaki denetimin yapısını ve akışını gösterir `ExampleMethodAsync` . Zaman uyumsuz yöntemin sonucu bir Web sayfasının karakter sayısıdır. Kod, Visual Studio 'da oluşturduğunuz bir Windows Presentation Foundation (WPF) uygulamasına veya Windows Mağazası uygulamasına uygundur; uygulamayı ayarlamaya yönelik kod açıklamalarını inceleyin.

Bu kodu, Visual Studio 'da bir Windows Presentation Foundation (WPF) uygulaması veya bir Windows Mağazası uygulaması olarak çalıştırabilirsiniz. Adlı bir düğme denetimine `StartButton` ve adlı TextBox denetimine ihtiyacınız vardır `ResultsTextBox` . Adları ve işleyiciyi şuna benzer olacak şekilde ayarlamayı unutmayın:

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"
        Click="StartButton_Click" Name="StartButton"/>
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>
```

Kodu WPF uygulaması olarak çalıştırmak için:

- Bu kodu `MainWindow` MainWindow.xaml.cs içindeki sınıfa yapıştırın.
- System .net. http öğesine bir başvuru ekleyin.
- `using`System .net. http için bir yönerge ekleyin.

Kodu bir Windows Mağazası uygulaması olarak çalıştırmak için:

- Bu kodu `MainPage` MainPage.xaml.cs içindeki sınıfa yapıştırın.
- System .net. http ve System. Threading. Tasks için using yönergelerini ekleyin.

[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]

> [!IMPORTANT]
> Görevler ve bir görevi beklerken yürütülen kod hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md). Benzer öğeleri kullanan tam bir konsol örneği için bkz. [işlem zaman uyumsuz görevleri tamamlandıklarında işleme (C#)](../../programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).

## <a name="return-types"></a>Dönüş Türleri

Zaman uyumsuz bir yöntem aşağıdaki dönüş türlerine sahip olabilir:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [void](../builtin-types/void.md). `async void` yöntemler genellikle olay işleyicileri dışındaki kod için önerilmez çünkü çağıranlar `await` Bu yöntemlere izin vermez ve başarılı tamamlamayı veya hata koşullarını raporlamak için farklı bir mekanizma uygulamalıdır.
- C# 7,0 ile başlayarak, erişilebilir bir yöntemi olan herhangi bir tür `GetAwaiter` . `System.Threading.Tasks.ValueTask<TResult>`Bu tür bir uygulama. NuGet paketi eklenerek kullanılabilir `System.Threading.Tasks.Extensions` .

Async yöntemi [içinde](./in-parameter-modifier.md)herhangi bir [ref](./ref.md) veya [Out](./out-parameter-modifier.md) parametresi bildiremez ve [Başvuru dönüş değerine](../../programming-guide/classes-and-structs/ref-returns.md)sahip olabilir, ancak bu parametrelere sahip yöntemleri çağırabilir.

`Task<TResult>`Metodun [Return](./return.md) ifadesinde bir işlenen belirtiyorsa, zaman uyumsuz bir yöntemin dönüş türü olarak belirtirsiniz `TResult` . `Task`Yöntem tamamlandığında anlamlı bir değer döndürülmezse kullanırsınız. Diğer bir deyişle, yöntemine yapılan bir çağrı bir döndürür `Task` , ancak tamamlandığında, `Task` `await` sonucunu bekleyen tüm ifadeler `Task` `void` .

Dönüş türünü `void` öncelikle bu dönüş türü gerektiren olay işleyicilerini tanımlamak için kullanırsınız. `void`Döndüren zaman uyumsuz bir yöntemi çağıran, bunu bekler ve yöntemin oluşturduğu özel durumları yakalayamaz.

C# 7,0 ' den başlayarak, `GetAwaiter` kodun performans açısından kritik bölümlerinde bellek ayırmalarını en aza indirmek için bir yöntemine sahip olan, genellikle bir değer türü olan başka bir tür döndürüyorsunuz.

Daha fazla bilgi ve örnek için bkz. [zaman uyumsuz dönüş türleri](../../programming-guide/concepts/async/async-return-types.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [await](../operators/await.md)
- [Async ve await ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md)
- [Zaman uyumsuz görevleri tamamlandıkları anda işleme](../../programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)
