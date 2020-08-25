---
title: Görev listesini iptal etme (C#)
description: Bir görev listesine iptal isteği bildirmek için iptal belirteçlerini nasıl kullanacağınızı öğrenin.
ms.date: 08/19/2020
ms.topic: tutorial
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 000b6a89a9240344508a5ae6b248572c8a2177dc
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811489"
---
# <a name="cancel-a-list-of-tasks-c"></a><span data-ttu-id="19ca7-103">Görev listesini iptal etme (C#)</span><span class="sxs-lookup"><span data-stu-id="19ca7-103">Cancel a list of tasks (C#)</span></span>

<span data-ttu-id="19ca7-104">Bir zaman uyumsuz konsol uygulamasını, bitmesini beklemek istemiyorsanız iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19ca7-104">You can cancel an async console application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="19ca7-105">Bu konudaki örneği izleyerek, bir Web sitesi listesinin içeriğini yükleyen bir uygulamaya iptal ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19ca7-105">By following the example in this topic, you can add a cancellation to an application that downloads the contents of a list of websites.</span></span> <span data-ttu-id="19ca7-106">Örneği her görevle ilişkilendirerek birçok görevi iptal edebilirsiniz <xref:System.Threading.CancellationTokenSource> .</span><span class="sxs-lookup"><span data-stu-id="19ca7-106">You can cancel many tasks by associating the <xref:System.Threading.CancellationTokenSource> instance with each task.</span></span> <span data-ttu-id="19ca7-107"><kbd>ENTER</kbd> tuşunu seçerseniz, henüz tamamlanmamış tüm görevleri iptal edersiniz.</span><span class="sxs-lookup"><span data-stu-id="19ca7-107">If you select the <kbd>Enter</kbd> key, you cancel all tasks that aren't yet complete.</span></span>

<span data-ttu-id="19ca7-108">Bu öğreticinin içindekiler:</span><span class="sxs-lookup"><span data-stu-id="19ca7-108">This tutorial covers:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="19ca7-109">.NET konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="19ca7-109">Creating a .NET console application</span></span>
> - <span data-ttu-id="19ca7-110">İptali destekleyen bir zaman uyumsuz uygulama yazma</span><span class="sxs-lookup"><span data-stu-id="19ca7-110">Writing an async application that supports cancellation</span></span>
> - <span data-ttu-id="19ca7-111">Sinyal iptali gösterme</span><span class="sxs-lookup"><span data-stu-id="19ca7-111">Demonstrating signaling cancellation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="19ca7-112">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="19ca7-112">Prerequisites</span></span>

<span data-ttu-id="19ca7-113">Bu öğretici için aşağıdakiler gereklidir:</span><span class="sxs-lookup"><span data-stu-id="19ca7-113">This tutorial requires the following:</span></span>

- [<span data-ttu-id="19ca7-114">.NET 5,0 veya sonraki bir SDK</span><span class="sxs-lookup"><span data-stu-id="19ca7-114">.NET 5.0 or later SDK</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- <span data-ttu-id="19ca7-115">Tümleşik geliştirme ortamı (IDE)</span><span class="sxs-lookup"><span data-stu-id="19ca7-115">Integrated development environment (IDE)</span></span>
  - [<span data-ttu-id="19ca7-116">Visual Studio, Visual Studio Code veya Mac için Visual Studio önerilir</span><span class="sxs-lookup"><span data-stu-id="19ca7-116">We recommend Visual Studio, Visual Studio Code, or Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com)

### <a name="create-example-application"></a><span data-ttu-id="19ca7-117">Örnek uygulama oluştur</span><span class="sxs-lookup"><span data-stu-id="19ca7-117">Create example application</span></span>

<span data-ttu-id="19ca7-118">Yeni bir .NET Core konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="19ca7-118">Create a new .NET Core console application.</span></span> <span data-ttu-id="19ca7-119">[DotNet yeni konsol](../../../../core/tools/dotnet-new.md#console) komutunu veya [Visual Studio 'yu](/visualstudio/install/install-visual-studio)kullanarak bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19ca7-119">You can create one by using the [dotnet new console](../../../../core/tools/dotnet-new.md#console) command or from [Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="19ca7-120">En sevdiğiniz kod düzenleyicisinde *program.cs* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="19ca7-120">Open the *Program.cs* file in your favorite code editor.</span></span>

### <a name="replace-using-statements"></a><span data-ttu-id="19ca7-121">Using deyimlerini Değiştir</span><span class="sxs-lookup"><span data-stu-id="19ca7-121">Replace using statements</span></span>

<span data-ttu-id="19ca7-122">Var olan using deyimlerini bu bildirimlerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="19ca7-122">Replace the existing using statements with these declarations:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;
```

## <a name="add-fields"></a><span data-ttu-id="19ca7-123">Alan Ekle</span><span class="sxs-lookup"><span data-stu-id="19ca7-123">Add fields</span></span>

<span data-ttu-id="19ca7-124">`Program`Sınıf tanımında şu üç alanı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="19ca7-124">In the `Program` class definition, add these three fields:</span></span>

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

<span data-ttu-id="19ca7-125">, <xref:System.Threading.CancellationTokenSource> İstenen iptalinin bir öğesine işaret etmek için kullanılır <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="19ca7-125">The <xref:System.Threading.CancellationTokenSource> is used to signal a requested cancellation to a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="19ca7-126">, `HttpClient` Http isteklerini gönderme ve http yanıtlarını alma özelliğini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="19ca7-126">The `HttpClient` exposes the ability to send HTTP requests and receive HTTP responses.</span></span> <span data-ttu-id="19ca7-127">, `s_urlList` Uygulamanın işlemek için kullandığı tüm URL 'leri tutar.</span><span class="sxs-lookup"><span data-stu-id="19ca7-127">The `s_urlList` holds all of the URLs that the application plans to process.</span></span>

## <a name="update-application-entry-point"></a><span data-ttu-id="19ca7-128">Uygulama giriş noktasını Güncelleştir</span><span class="sxs-lookup"><span data-stu-id="19ca7-128">Update application entry point</span></span>

<span data-ttu-id="19ca7-129">Konsol uygulamasına ana giriş noktası `Main` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="19ca7-129">The main entry point into the console application is the `Main` method.</span></span> <span data-ttu-id="19ca7-130">Mevcut yöntemi aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="19ca7-130">Replace the existing method with the following:</span></span>

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

<span data-ttu-id="19ca7-131">Updated `Main` yöntemi artık zaman uyumsuz bir [Main](../../../whats-new/csharp-7-1.md#async-main)olarak değerlendirilir ve bu, yürütülebilir bir giriş noktasına bir zaman uyumsuz giriş noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="19ca7-131">The updated `Main` method is now considered an [Async main](../../../whats-new/csharp-7-1.md#async-main), which allows for an asynchronous entry point into the executable.</span></span> <span data-ttu-id="19ca7-132">Konsola birkaç eğitici ileti yazar ve ardından <xref:System.Threading.Tasks.Task> `cancelTask` Konsol anahtar vuruşlarını okuyan adlı bir örnek bildirir.</span><span class="sxs-lookup"><span data-stu-id="19ca7-132">It writes a few instructional messages to the console, then declares a <xref:System.Threading.Tasks.Task> instance named `cancelTask`, which will read console key strokes.</span></span> <span data-ttu-id="19ca7-133"><kbd>ENTER</kbd> tuşuna basıldığında bir çağrısı <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> yapılır.</span><span class="sxs-lookup"><span data-stu-id="19ca7-133">If the <kbd>Enter</kbd> key is pressed, a call to <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> is made.</span></span> <span data-ttu-id="19ca7-134">Bu işlem iptali işaret eder.</span><span class="sxs-lookup"><span data-stu-id="19ca7-134">This will signal cancellation.</span></span> <span data-ttu-id="19ca7-135">Sonra, `sumPageSizesTask` değişkeni `SumPageSizesAsync` yönteminden atanır.</span><span class="sxs-lookup"><span data-stu-id="19ca7-135">Next, the `sumPageSizesTask` variable is assigned from the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="19ca7-136">Her iki görev daha sonra öğesine geçirilir <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType> ve bu, iki görevden herhangi biri tamamlandığında devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="19ca7-136">Both tasks are then passed to <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType>, which will continue when any of the two tasks have completed.</span></span>

## <a name="create-the-asynchronous-sum-page-sizes-method"></a><span data-ttu-id="19ca7-137">Zaman uyumsuz toplam sayfa boyutları yöntemini oluşturma</span><span class="sxs-lookup"><span data-stu-id="19ca7-137">Create the asynchronous sum page sizes method</span></span>

<span data-ttu-id="19ca7-138">Yönteminin altına `Main` şunu ekleyin `SumPageSizesAsync` :</span><span class="sxs-lookup"><span data-stu-id="19ca7-138">Below the `Main` method, add the `SumPageSizesAsync` method:</span></span>

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

<span data-ttu-id="19ca7-139">Yöntemi, örneğini oluşturarak ve başlatarak başlar <xref:System.Diagnostics.Stopwatch> .</span><span class="sxs-lookup"><span data-stu-id="19ca7-139">The method starts by instantiating and starting a <xref:System.Diagnostics.Stopwatch>.</span></span> <span data-ttu-id="19ca7-140">Ardından, ve çağrılarındaki her bir URL aracılığıyla döngü yapılır `s_urlList` `ProcessUrlAsync` .</span><span class="sxs-lookup"><span data-stu-id="19ca7-140">It then loops through each URL in the `s_urlList` and calls `ProcessUrlAsync`.</span></span> <span data-ttu-id="19ca7-141">Her yinelemede, `s_cts.Token` `ProcessUrlAsync` yöntemi yöntemine geçirilir ve kod bir <xref:System.Threading.Tasks.Task%601> `TResult` tam sayı olan bir döndürür:</span><span class="sxs-lookup"><span data-stu-id="19ca7-141">With each iteration, the `s_cts.Token` is passed into the `ProcessUrlAsync` method and the code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
int total = 0;
foreach (string url in s_urlList)
{
    int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
    total += contentLength;
}
```

## <a name="add-process-method"></a><span data-ttu-id="19ca7-142">İşlem yöntemi ekle</span><span class="sxs-lookup"><span data-stu-id="19ca7-142">Add process method</span></span>

<span data-ttu-id="19ca7-143">Aşağıdaki `ProcessUrlAsync` yöntemi yönteminin altına ekleyin `SumPageSizesAsync` :</span><span class="sxs-lookup"><span data-stu-id="19ca7-143">Add the following `ProcessUrlAsync` method below the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client, CancellationToken token)
{
    HttpResponseMessage response = await client.GetAsync(url, token);
    byte[] content = await response.Content.ReadAsByteArrayAsync(token);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

<span data-ttu-id="19ca7-144">Verilen herhangi bir URL için yöntemi, `client` yanıtı bir olarak almak için sağlanan örneği kullanacaktır `byte[]` .</span><span class="sxs-lookup"><span data-stu-id="19ca7-144">For any given URL, the method will use the `client` instance provided to get the response as a `byte[]`.</span></span> <span data-ttu-id="19ca7-145"><xref:System.Threading.CancellationToken>Örnek <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> ve <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync(System.Threading.CancellationToken)?displayProperty=nameWithType> yöntemlerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="19ca7-145">The <xref:System.Threading.CancellationToken> instance is passed into the <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> and <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync(System.Threading.CancellationToken)?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="19ca7-146">, `token` İstenen iptal için kaydolmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="19ca7-146">The `token` is used to register for requested cancellation.</span></span> <span data-ttu-id="19ca7-147">Uzunluk, URL ve uzunluk konsola yazıldıktan sonra döndürülür.</span><span class="sxs-lookup"><span data-stu-id="19ca7-147">The length is returned after the URL and length is written to the console.</span></span>

### <a name="example-application-output"></a><span data-ttu-id="19ca7-148">Örnek uygulama çıkışı</span><span class="sxs-lookup"><span data-stu-id="19ca7-148">Example application output</span></span>

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

## <a name="complete-example"></a><span data-ttu-id="19ca7-149">Örnek Tamam</span><span class="sxs-lookup"><span data-stu-id="19ca7-149">Complete example</span></span>

<span data-ttu-id="19ca7-150">Aşağıdaki kod, örnek için *program.cs* dosyasının tüm metinkodudur.</span><span class="sxs-lookup"><span data-stu-id="19ca7-150">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/cancel-tasks/cancel-tasks/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="19ca7-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19ca7-151">See also</span></span>

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [<span data-ttu-id="19ca7-152">Async ve await ile zaman uyumsuz programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="19ca7-152">Asynchronous programming with async and await (C#)</span></span>](index.md)

## <a name="next-steps"></a><span data-ttu-id="19ca7-153">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="19ca7-153">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="19ca7-154">Zaman uyumsuz görevleri bir süre sonra iptal etme (C#)</span><span class="sxs-lookup"><span data-stu-id="19ca7-154">Cancel async tasks after a period of time (C#)</span></span>](cancel-async-tasks-after-a-period-of-time.md)
