---
title: Görev listesini iptal etme (C#)
description: Bir görev listesine iptal isteği bildirmek için iptal belirteçlerini nasıl kullanacağınızı öğrenin.
ms.date: 08/19/2020
ms.topic: tutorial
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 84cd1bb413d20b6c13be8415c13c72b57873b1cf
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654711"
---
# <a name="cancel-a-list-of-tasks-c"></a>Görev listesini iptal etme (C#)

Bir zaman uyumsuz konsol uygulamasını, bitmesini beklemek istemiyorsanız iptal edebilirsiniz. Bu konudaki örneği izleyerek, bir Web sitesi listesinin içeriğini yükleyen bir uygulamaya iptal ekleyebilirsiniz. Örneği her görevle ilişkilendirerek birçok görevi iptal edebilirsiniz <xref:System.Threading.CancellationTokenSource> . <kbd>ENTER</kbd> tuşunu seçerseniz, henüz tamamlanmamış tüm görevleri iptal edersiniz.

Bu öğreticinin içindekiler:

> [!div class="checklist"]
>
> - .NET konsol uygulaması oluşturma
> - İptali destekleyen bir zaman uyumsuz uygulama yazma
> - Sinyal iptali gösterme

## <a name="prerequisites"></a>Önkoşullar

Bu öğretici için aşağıdakiler gereklidir:

- [.NET 5,0 veya sonraki bir SDK](https://dotnet.microsoft.com/download/dotnet/5.0)
- Tümleşik geliştirme ortamı (IDE)
  - [Visual Studio, Visual Studio Code veya Mac için Visual Studio önerilir](https://visualstudio.microsoft.com)

### <a name="create-example-application"></a>Örnek uygulama oluştur

Yeni bir .NET Core konsol uygulaması oluşturun. [`dotnet new console`](../../../../core/tools/dotnet-new.md#console)Komutunu kullanarak veya [Visual Studio](/visualstudio/install/install-visual-studio)'dan bir tane oluşturabilirsiniz. En sevdiğiniz kod düzenleyicisinde *program.cs* dosyasını açın.

### <a name="replace-using-statements"></a>Using deyimlerini Değiştir

Var olan using deyimlerini bu bildirimlerle değiştirin:

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;
```

## <a name="add-fields"></a>Alan Ekle

`Program`Sınıf tanımında şu üç alanı ekleyin:

```csharp
static readonly CancellationTokenSource s_cts = new CancellationTokenSource();

static readonly HttpClient s_client = new HttpClient
{
    MaxResponseContentBufferSize = 1_000_000
};

static readonly IEnumerable<string> s_urlList = new string[]
{
    "https://docs.microsoft.com",
    "https://docs.microsoft.com/aspnet/core",
    "https://docs.microsoft.com/azure",
    "https://docs.microsoft.com/azure/devops",
    "https://docs.microsoft.com/dotnet",
    "https://docs.microsoft.com/dynamics365",
    "https://docs.microsoft.com/education",
    "https://docs.microsoft.com/enterprise-mobility-security",
    "https://docs.microsoft.com/gaming",
    "https://docs.microsoft.com/graph",
    "https://docs.microsoft.com/microsoft-365",
    "https://docs.microsoft.com/office",
    "https://docs.microsoft.com/powershell",
    "https://docs.microsoft.com/sql",
    "https://docs.microsoft.com/surface",
    "https://docs.microsoft.com/system-center",
    "https://docs.microsoft.com/visualstudio",
    "https://docs.microsoft.com/windows",
    "https://docs.microsoft.com/xamarin"
};
```

, <xref:System.Threading.CancellationTokenSource> İstenen iptalinin bir öğesine işaret etmek için kullanılır <xref:System.Threading.CancellationToken> . , `HttpClient` Http isteklerini gönderme ve http yanıtlarını alma özelliğini kullanıma sunar. , `s_urlList` Uygulamanın işlemek için kullandığı tüm URL 'leri tutar.

## <a name="update-application-entry-point"></a>Uygulama giriş noktasını Güncelleştir

Konsol uygulamasına ana giriş noktası `Main` yöntemidir. Mevcut yöntemi aşağıdaki kodla değiştirin:

```csharp
static async Task Main()
{
    Console.WriteLine("Application started.");
    Console.WriteLine("Press the ENTER key to cancel...\n");

    Task cancelTask = Task.Run(() =>
    {
        while (Console.ReadKey().Key != ConsoleKey.Enter)
        {
            Console.WriteLine("Press the ENTER key to cancel...");
        }

        Console.WriteLine("\nENTER key pressed: cancelling downloads.\n");
        s_cts.Cancel();
    });

    Task sumPageSizesTask = SumPageSizesAsync();

    await Task.WhenAny(new[] { cancelTask, sumPageSizesTask });

    Console.WriteLine("Application ending.");
}
```

Updated `Main` yöntemi artık zaman uyumsuz bir [Main](../../../whats-new/csharp-7-1.md#async-main)olarak değerlendirilir ve bu, yürütülebilir bir giriş noktasına bir zaman uyumsuz giriş noktası sağlar. Konsola birkaç eğitici ileti yazar ve ardından <xref:System.Threading.Tasks.Task> `cancelTask` Konsol anahtar vuruşlarını okuyan adlı bir örnek bildirir. <kbd>ENTER</kbd> tuşuna basıldığında bir çağrısı <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> yapılır. Bu işlem iptali işaret eder. Sonra, `sumPageSizesTask` değişkeni `SumPageSizesAsync` yönteminden atanır. Her iki görev daha sonra öğesine geçirilir <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType> ve bu, iki görevden herhangi biri tamamlandığında devam edecektir.

## <a name="create-the-asynchronous-sum-page-sizes-method"></a>Zaman uyumsuz toplam sayfa boyutları yöntemini oluşturma

Yönteminin altına `Main` şunu ekleyin `SumPageSizesAsync` :

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    int total = 0;
    foreach (string url in s_urlList)
    {
        int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
        total += contentLength;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

Yöntemi, örneğini oluşturarak ve başlatarak başlar <xref:System.Diagnostics.Stopwatch> . Ardından, ve çağrılarındaki her bir URL aracılığıyla döngü yapılır `s_urlList` `ProcessUrlAsync` . Her yinelemede, `s_cts.Token` `ProcessUrlAsync` yöntemi yöntemine geçirilir ve kod bir <xref:System.Threading.Tasks.Task%601> `TResult` tam sayı olan bir döndürür:

```csharp
int total = 0;
foreach (string url in s_urlList)
{
    int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
    total += contentLength;
}
```

## <a name="add-process-method"></a>İşlem yöntemi ekle

Aşağıdaki `ProcessUrlAsync` yöntemi yönteminin altına ekleyin `SumPageSizesAsync` :

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client, CancellationToken token)
{
    HttpResponseMessage response = await client.GetAsync(url, token);
    byte[] content = await response.Content.ReadAsByteArrayAsync();
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

Verilen herhangi bir URL için yöntemi, `client` yanıtı bir olarak almak için sağlanan örneği kullanacaktır `byte[]` . <xref:System.Threading.CancellationToken>Örnek <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> ve <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync?displayProperty=nameWithType> yöntemlerine geçirilir. , `token` İstenen iptal için kaydolmak için kullanılır. Uzunluk, URL ve uzunluk konsola yazıldıktan sonra döndürülür.

### <a name="example-application-output"></a>Örnek uygulama çıkışı

```console
Application started.
Press the ENTER key to cancel...

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663
https://docs.microsoft.com/dotnet                                67,452
https://docs.microsoft.com/dynamics365                           48,582
https://docs.microsoft.com/education                             22,924

ENTER key pressed: cancelling downloads.

Application ending.
```

## <a name="complete-example"></a>Örnek Tamam

Aşağıdaki kod, örnek için *program.cs* dosyasının tüm metinkodudur.

:::code language="csharp" source="snippets/cancel-tasks/cancel-tasks/Program.cs":::

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [Async ve await ile zaman uyumsuz programlama (C#)](index.md)

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Zaman uyumsuz görevleri bir süre sonra iptal etme (C#)](cancel-async-tasks-after-a-period-of-time.md)
