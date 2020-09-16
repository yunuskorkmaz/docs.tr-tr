---
title: Zaman uyumsuz görevleri tamamlandıkları anda işleme
description: Bu örnek, birden çok görevi başlatmak ve sonuçlarını tamamlandığında işlem sırasında işlemek yerine sonuçları işlemek Için C# ' de Task. WhenAny 'ın nasıl kullanılacağını gösterir.
ms.date: 08/19/2020
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: 520953eaf851dc82440e39b348aa4b246255e126
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557313"
---
# <a name="process-asynchronous-tasks-as-they-complete-c"></a>Zaman uyumsuz görevleri tamamlarlar işleme (C#)

Kullanarak <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> , aynı anda birden çok görev başlatabilir ve bunları, başlatıldıkları sırada işlemek yerine, bir kez işlem tamamlanır.

Aşağıdaki örnek, bir görev koleksiyonu oluşturmak için bir sorgu kullanır. Her görev belirtilen bir Web sitesinin içeriğini indirir. Bir while döngüsünün her yinelemesinde, geri beklenmiş bir çağrı, <xref:System.Threading.Tasks.Task.WhenAny%2A> önce indirmeyi izleyen görevler koleksiyonundaki görevi döndürür. Bu görev koleksiyondan kaldırılır ve işlenir. Döngü, koleksiyon daha fazla görev içerene kadar yinelenir.

## <a name="create-example-application"></a>Örnek uygulama oluştur

Yeni bir .NET Core konsol uygulaması oluşturun. [DotNet yeni konsol](../../../../core/tools/dotnet-new.md#console) komutunu veya [Visual Studio 'yu](/visualstudio/install/install-visual-studio)kullanarak bir tane oluşturabilirsiniz. En sevdiğiniz kod düzenleyicisinde *program.cs* dosyasını açın.

### <a name="replace-using-statements"></a>Using deyimlerini Değiştir

Var olan using deyimlerini bu bildirimlerle değiştirin:

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Linq;
using System.Net.Http;
using System.Threading.Tasks;
```

## <a name="add-fields"></a>Alan Ekle

`Program`Sınıf tanımında aşağıdaki iki alanı ekleyin:

```csharp
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

, `HttpClient` Http isteklerini gönderme ve http yanıtlarını alma özelliğini kullanıma sunar. , `s_urlList` Uygulamanın işlemek için kullandığı tüm URL 'leri tutar.

## <a name="update-application-entry-point"></a>Uygulama giriş noktasını Güncelleştir

Konsol uygulamasına ana giriş noktası `Main` yöntemidir. Mevcut yöntemi aşağıdaki kodla değiştirin:

```csharp
static Task Main() => SumPageSizesAsync();
```

Updated `Main` yöntemi artık zaman uyumsuz bir [Main](../../../whats-new/csharp-7-1.md#async-main)olarak değerlendirilir ve bu, yürütülebilir bir giriş noktasına bir zaman uyumsuz giriş noktası sağlar. Bir çağrısı ifade edilir `SumPageSizesAsync` .

## <a name="create-the-asynchronous-sum-page-sizes-method"></a>Zaman uyumsuz toplam sayfa boyutları yöntemini oluşturma

Yönteminin altına `Main` şunu ekleyin `SumPageSizesAsync` :

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    IEnumerable<Task<int>> downloadTasksQuery =
        from url in s_urlList
        select ProcessUrlAsync(url, s_client);

    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();

    int total = 0;
    while (downloadTasks.Any())
    {
        Task<int> finishedTask = await Task.WhenAny(downloadTasks);
        downloadTasks.Remove(finishedTask);
        total += await finishedTask;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

Yöntemi, örneğini oluşturarak ve başlatarak başlar <xref:System.Diagnostics.Stopwatch> . Daha sonra, yürütüldüğünde bir görev koleksiyonu oluşturan bir sorgu içerir. Aşağıdaki kodda öğesine yapılan her çağrı `ProcessUrlAsync` <xref:System.Threading.Tasks.Task%601> , bir `TResult` tam sayı olan bir döndürür:

```csharp
IEnumerable<Task<int>> downloadTasksQuery =
    from url in s_urlList
    select ProcessUrlAsync(url, s_client);
```

LINQ ile [ertelenmiş yürütme](../../../../standard/linq/deferred-execution-example.md) nedeniyle <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> her bir görevi başlatmak için öğesini çağırın.

```csharp
List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
```

`while`Döngü, koleksiyondaki her bir görev için aşağıdaki adımları gerçekleştirir:

1. , `WhenAny` Koleksiyondaki ilk görevi tanımlamak için bir çağrısı bekler.

    ```csharp
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
    ```

1. Bu görevi koleksiyondan kaldırır.

    ```csharp
    downloadTasks.Remove(firstFinishedTask);
    ```

1. `finishedTask`Bir çağrısıyla döndürülen await `ProcessUrlAsync` . `finishedTask`Değişkeni bir <xref:System.Threading.Tasks.Task%601> WHERE `TResult` tamsayıdır. Görev zaten tamamlanmış, ancak aşağıdaki örnekte gösterildiği gibi, indirilen Web sitesinin uzunluğunu almak için bu işlemi beklediniz. Görev hata verdiyse, `await` `AggregateException` özelliğini okumaktan farklı olarak içinde depolanan ilk alt özel durumu oluşturur <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> `AggregateException` .

    ```csharp
    total += await finishedTask;
    ```

## <a name="add-process-method"></a>İşlem yöntemi ekle

Aşağıdaki `ProcessUrlAsync` yöntemi yönteminin altına ekleyin `SumPageSizesAsync` :

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client)
{
    byte[] content = await client.GetByteArrayAsync(url);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

Verilen herhangi bir URL için yöntemi, `client` yanıtı bir olarak almak için sağlanan örneği kullanacaktır `byte[]` . Uzunluk, URL ve uzunluk konsola yazıldıktan sonra döndürülür.

İndirilen uzunluklarının her zaman aynı sırada görünmediğini doğrulamak için programı birkaç kez çalıştırın.

> [!CAUTION]
> `WhenAny`Az sayıda görevle ilgili sorunları gidermek için örnekte açıklandığı gibi bir döngüde kullanabilirsiniz. Ancak, işlemek için çok sayıda göreviniz varsa diğer yaklaşımlar daha etkilidir. Daha fazla bilgi ve örnek için bkz. [görevleri tamamladıklarında işleme](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete).

## <a name="complete-example"></a>Örnek Tamam

Aşağıdaki kod, örnek için *program.cs* dosyasının tüm metinkodudur.

:::code language="csharp" source="snippets/multiple-tasks/Program.cs":::

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Async ve await ile zaman uyumsuz programlama (C#)](index.md)
