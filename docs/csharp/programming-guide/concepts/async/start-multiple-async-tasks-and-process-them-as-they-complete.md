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
# <a name="process-asynchronous-tasks-as-they-complete-c"></a><span data-ttu-id="9b665-103">Zaman uyumsuz görevleri tamamlarlar işleme (C#)</span><span class="sxs-lookup"><span data-stu-id="9b665-103">Process asynchronous tasks as they complete (C#)</span></span>

<span data-ttu-id="9b665-104">Kullanarak <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> , aynı anda birden çok görev başlatabilir ve bunları, başlatıldıkları sırada işlemek yerine, bir kez işlem tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="9b665-104">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they're completed rather than process them in the order in which they're started.</span></span>

<span data-ttu-id="9b665-105">Aşağıdaki örnek, bir görev koleksiyonu oluşturmak için bir sorgu kullanır.</span><span class="sxs-lookup"><span data-stu-id="9b665-105">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="9b665-106">Her görev belirtilen bir Web sitesinin içeriğini indirir.</span><span class="sxs-lookup"><span data-stu-id="9b665-106">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="9b665-107">Bir while döngüsünün her yinelemesinde, geri beklenmiş bir çağrı, <xref:System.Threading.Tasks.Task.WhenAny%2A> önce indirmeyi izleyen görevler koleksiyonundaki görevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="9b665-107">In each iteration of a while loop, an awaited call to <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="9b665-108">Bu görev koleksiyondan kaldırılır ve işlenir.</span><span class="sxs-lookup"><span data-stu-id="9b665-108">That task is removed from the collection and processed.</span></span> <span data-ttu-id="9b665-109">Döngü, koleksiyon daha fazla görev içerene kadar yinelenir.</span><span class="sxs-lookup"><span data-stu-id="9b665-109">The loop repeats until the collection contains no more tasks.</span></span>

## <a name="create-example-application"></a><span data-ttu-id="9b665-110">Örnek uygulama oluştur</span><span class="sxs-lookup"><span data-stu-id="9b665-110">Create example application</span></span>

<span data-ttu-id="9b665-111">Yeni bir .NET Core konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9b665-111">Create a new .NET Core console application.</span></span> <span data-ttu-id="9b665-112">[DotNet yeni konsol](../../../../core/tools/dotnet-new.md#console) komutunu veya [Visual Studio 'yu](/visualstudio/install/install-visual-studio)kullanarak bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b665-112">You can create one by using the [dotnet new console](../../../../core/tools/dotnet-new.md#console) command or from [Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="9b665-113">En sevdiğiniz kod düzenleyicisinde *program.cs* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="9b665-113">Open the *Program.cs* file in your favorite code editor.</span></span>

### <a name="replace-using-statements"></a><span data-ttu-id="9b665-114">Using deyimlerini Değiştir</span><span class="sxs-lookup"><span data-stu-id="9b665-114">Replace using statements</span></span>

<span data-ttu-id="9b665-115">Var olan using deyimlerini bu bildirimlerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9b665-115">Replace the existing using statements with these declarations:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Linq;
using System.Net.Http;
using System.Threading.Tasks;
```

## <a name="add-fields"></a><span data-ttu-id="9b665-116">Alan Ekle</span><span class="sxs-lookup"><span data-stu-id="9b665-116">Add fields</span></span>

<span data-ttu-id="9b665-117">`Program`Sınıf tanımında aşağıdaki iki alanı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9b665-117">In the `Program` class definition, add the following two fields:</span></span>

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

<span data-ttu-id="9b665-118">, `HttpClient` Http isteklerini gönderme ve http yanıtlarını alma özelliğini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="9b665-118">The `HttpClient` exposes the ability to send HTTP requests and receive HTTP responses.</span></span> <span data-ttu-id="9b665-119">, `s_urlList` Uygulamanın işlemek için kullandığı tüm URL 'leri tutar.</span><span class="sxs-lookup"><span data-stu-id="9b665-119">The `s_urlList` holds all of the URLs that the application plans to process.</span></span>

## <a name="update-application-entry-point"></a><span data-ttu-id="9b665-120">Uygulama giriş noktasını Güncelleştir</span><span class="sxs-lookup"><span data-stu-id="9b665-120">Update application entry point</span></span>

<span data-ttu-id="9b665-121">Konsol uygulamasına ana giriş noktası `Main` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="9b665-121">The main entry point into the console application is the `Main` method.</span></span> <span data-ttu-id="9b665-122">Mevcut yöntemi aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9b665-122">Replace the existing method with the following:</span></span>

```csharp
static Task Main() => SumPageSizesAsync();
```

<span data-ttu-id="9b665-123">Updated `Main` yöntemi artık zaman uyumsuz bir [Main](../../../whats-new/csharp-7-1.md#async-main)olarak değerlendirilir ve bu, yürütülebilir bir giriş noktasına bir zaman uyumsuz giriş noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b665-123">The updated `Main` method is now considered an [Async main](../../../whats-new/csharp-7-1.md#async-main), which allows for an asynchronous entry point into the executable.</span></span> <span data-ttu-id="9b665-124">Bir çağrısı ifade edilir `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="9b665-124">It is expressed a call to `SumPageSizesAsync`.</span></span>

## <a name="create-the-asynchronous-sum-page-sizes-method"></a><span data-ttu-id="9b665-125">Zaman uyumsuz toplam sayfa boyutları yöntemini oluşturma</span><span class="sxs-lookup"><span data-stu-id="9b665-125">Create the asynchronous sum page sizes method</span></span>

<span data-ttu-id="9b665-126">Yönteminin altına `Main` şunu ekleyin `SumPageSizesAsync` :</span><span class="sxs-lookup"><span data-stu-id="9b665-126">Below the `Main` method, add the `SumPageSizesAsync` method:</span></span>

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

<span data-ttu-id="9b665-127">Yöntemi, örneğini oluşturarak ve başlatarak başlar <xref:System.Diagnostics.Stopwatch> .</span><span class="sxs-lookup"><span data-stu-id="9b665-127">The method starts by instantiating and starting a <xref:System.Diagnostics.Stopwatch>.</span></span> <span data-ttu-id="9b665-128">Daha sonra, yürütüldüğünde bir görev koleksiyonu oluşturan bir sorgu içerir.</span><span class="sxs-lookup"><span data-stu-id="9b665-128">It then includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="9b665-129">Aşağıdaki kodda öğesine yapılan her çağrı `ProcessUrlAsync` <xref:System.Threading.Tasks.Task%601> , bir `TResult` tam sayı olan bir döndürür:</span><span class="sxs-lookup"><span data-stu-id="9b665-129">Each call to `ProcessUrlAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
IEnumerable<Task<int>> downloadTasksQuery =
    from url in s_urlList
    select ProcessUrlAsync(url, s_client);
```

<span data-ttu-id="9b665-130">LINQ ile [ertelenmiş yürütme](../../../../standard/linq/deferred-execution-example.md) nedeniyle <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> her bir görevi başlatmak için öğesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="9b665-130">Due to [deferred execution](../../../../standard/linq/deferred-execution-example.md) with the LINQ, you call <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> to start each task.</span></span>

```csharp
List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
```

<span data-ttu-id="9b665-131">`while`Döngü, koleksiyondaki her bir görev için aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="9b665-131">The `while` loop performs the following steps for each task in the collection:</span></span>

1. <span data-ttu-id="9b665-132">, `WhenAny` Koleksiyondaki ilk görevi tanımlamak için bir çağrısı bekler.</span><span class="sxs-lookup"><span data-stu-id="9b665-132">Awaits a call to `WhenAny` to identify the first task in the collection that has finished its download.</span></span>

    ```csharp
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
    ```

1. <span data-ttu-id="9b665-133">Bu görevi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9b665-133">Removes that task from the collection.</span></span>

    ```csharp
    downloadTasks.Remove(firstFinishedTask);
    ```

1. <span data-ttu-id="9b665-134">`finishedTask`Bir çağrısıyla döndürülen await `ProcessUrlAsync` .</span><span class="sxs-lookup"><span data-stu-id="9b665-134">Awaits `finishedTask`, which is returned by a call to `ProcessUrlAsync`.</span></span> <span data-ttu-id="9b665-135">`finishedTask`Değişkeni bir <xref:System.Threading.Tasks.Task%601> WHERE `TResult` tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="9b665-135">The `finishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span> <span data-ttu-id="9b665-136">Görev zaten tamamlanmış, ancak aşağıdaki örnekte gösterildiği gibi, indirilen Web sitesinin uzunluğunu almak için bu işlemi beklediniz.</span><span class="sxs-lookup"><span data-stu-id="9b665-136">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span> <span data-ttu-id="9b665-137">Görev hata verdiyse, `await` `AggregateException` özelliğini okumaktan farklı olarak içinde depolanan ilk alt özel durumu oluşturur <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> `AggregateException` .</span><span class="sxs-lookup"><span data-stu-id="9b665-137">If the task is faulted, `await` will throw the first child exception stored in the `AggregateException`, unlike reading the <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> property, which would throw the `AggregateException`.</span></span>

    ```csharp
    total += await finishedTask;
    ```

## <a name="add-process-method"></a><span data-ttu-id="9b665-138">İşlem yöntemi ekle</span><span class="sxs-lookup"><span data-stu-id="9b665-138">Add process method</span></span>

<span data-ttu-id="9b665-139">Aşağıdaki `ProcessUrlAsync` yöntemi yönteminin altına ekleyin `SumPageSizesAsync` :</span><span class="sxs-lookup"><span data-stu-id="9b665-139">Add the following `ProcessUrlAsync` method below the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client)
{
    byte[] content = await client.GetByteArrayAsync(url);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

<span data-ttu-id="9b665-140">Verilen herhangi bir URL için yöntemi, `client` yanıtı bir olarak almak için sağlanan örneği kullanacaktır `byte[]` .</span><span class="sxs-lookup"><span data-stu-id="9b665-140">For any given URL, the method will use the `client` instance provided to get the response as a `byte[]`.</span></span> <span data-ttu-id="9b665-141">Uzunluk, URL ve uzunluk konsola yazıldıktan sonra döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9b665-141">The length is returned after the URL and length is written to the console.</span></span>

<span data-ttu-id="9b665-142">İndirilen uzunluklarının her zaman aynı sırada görünmediğini doğrulamak için programı birkaç kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9b665-142">Run the program several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

> [!CAUTION]
> <span data-ttu-id="9b665-143">`WhenAny`Az sayıda görevle ilgili sorunları gidermek için örnekte açıklandığı gibi bir döngüde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b665-143">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="9b665-144">Ancak, işlemek için çok sayıda göreviniz varsa diğer yaklaşımlar daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="9b665-144">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="9b665-145">Daha fazla bilgi ve örnek için bkz. [görevleri tamamladıklarında işleme](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete).</span><span class="sxs-lookup"><span data-stu-id="9b665-145">For more information and examples, see [Processing tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete).</span></span>

## <a name="complete-example"></a><span data-ttu-id="9b665-146">Örnek Tamam</span><span class="sxs-lookup"><span data-stu-id="9b665-146">Complete example</span></span>

<span data-ttu-id="9b665-147">Aşağıdaki kod, örnek için *program.cs* dosyasının tüm metinkodudur.</span><span class="sxs-lookup"><span data-stu-id="9b665-147">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/multiple-tasks/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="9b665-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b665-148">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="9b665-149">Async ve await ile zaman uyumsuz programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="9b665-149">Asynchronous programming with async and await (C#)</span></span>](index.md)
