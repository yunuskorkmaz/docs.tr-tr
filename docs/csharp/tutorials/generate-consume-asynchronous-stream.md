---
title: Zaman uyumsuz akışlar oluşturma ve kullanma
description: Bu gelişmiş öğreticide, zaman uyumsuz akışlarının oluşturulması ve kullanılması, zaman uyumsuz olarak oluşturulabilecek veri dizileri ile çalışmak için daha doğal bir yol sağlar.
ms.date: 02/10/2019
ms.custom: mvc
ms.openlocfilehash: 04c4fe1c7e33138273c5b49c6985efc60767a724
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216560"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a><span data-ttu-id="ef6c0-103">Öğretici: 8,0 ve .NET Core 3,0 kullanarak C# zaman uyumsuz akışlar oluşturun ve kullanın</span><span class="sxs-lookup"><span data-stu-id="ef6c0-103">Tutorial: Generate and consume async streams using C# 8.0 and .NET Core 3.0</span></span>

<span data-ttu-id="ef6c0-104">C#8,0, veri akışındaki öğeler alınabilir veya zaman uyumsuz olarak oluşturulduğunda verilerin akış kaynağını modelleyebilir ve **zaman uyumsuz akışları**tanıtır.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-104">C# 8.0 introduces **async streams**, which model a streaming source of data when the elements in the data stream may be retrieved or generated asynchronously.</span></span> <span data-ttu-id="ef6c0-105">Zaman uyumsuz akışlar .NET Standard 2,1 ' de tanıtılan ve .NET Core 3,0 ' de uygulanan yeni arabirimleri kullanır ve zaman uyumsuz akış veri kaynakları için doğal bir programlama modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-105">Async streams rely on new interfaces introduced in .NET Standard 2.1 and implemented in .NET Core 3.0 to provide a natural programming model for asynchronous streaming data sources.</span></span>

<span data-ttu-id="ef6c0-106">Bu öğreticide, aşağıdakileri nasıl yapacağınızı öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="ef6c0-106">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="ef6c0-107">Zaman uyumsuz bir veri öğeleri dizisi üreten bir veri kaynağı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-107">Create a data source that generates a sequence of data elements asynchronously.</span></span>
> - <span data-ttu-id="ef6c0-108">Bu veri kaynağını zaman uyumsuz olarak tükettin.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-108">Consume that data source asynchronously.</span></span>
> - <span data-ttu-id="ef6c0-109">Yeni arabirim ve veri kaynağı daha önceki zaman uyumlu veri dizileri için tercih edildiği zaman tanıyın.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-109">Recognize when the new interface and data source are preferred to earlier synchronous data sequences.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ef6c0-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="ef6c0-110">Prerequisites</span></span>

<span data-ttu-id="ef6c0-111">Makinenizi, C# 8,0 derleyicisi dahil .NET Core çalıştıracak şekilde ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-111">You’ll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="ef6c0-112">8 C# derleyicisi, [Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download)ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-112">The C# 8 compiler is available starting with [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="ef6c0-113">GitHub GraphQL uç noktasına erişebilmek için bir [GitHub erişim belirteci](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-113">You'll need to create a [GitHub access token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) so that you can access the GitHub GraphQL endpoint.</span></span> <span data-ttu-id="ef6c0-114">GitHub erişim belirteciniz için aşağıdaki izinleri seçin:</span><span class="sxs-lookup"><span data-stu-id="ef6c0-114">Select the following permissions for your GitHub Access Token:</span></span>

- <span data-ttu-id="ef6c0-115">Depo: durum</span><span class="sxs-lookup"><span data-stu-id="ef6c0-115">repo:status</span></span>
- <span data-ttu-id="ef6c0-116">public_repo</span><span class="sxs-lookup"><span data-stu-id="ef6c0-116">public_repo</span></span>

<span data-ttu-id="ef6c0-117">Erişim belirtecini, GitHub API uç noktasına erişim kazanmak için kullanabilmeniz için güvenli bir yere kaydedin.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-117">Save the access token in a safe place so you can use it to gain access to the GitHub API endpoint.</span></span>

> [!WARNING]
> <span data-ttu-id="ef6c0-118">Kişisel erişim belirtecinizi güvende tutun.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-118">Keep your personal access token secure.</span></span> <span data-ttu-id="ef6c0-119">Kişisel erişim belirtecinize sahip tüm yazılımlar, erişim haklarınızı kullanarak GitHub API çağrıları yapabilir.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-119">Any software with your personal access token could make GitHub API calls using your access rights.</span></span>

<span data-ttu-id="ef6c0-120">Bu öğreticide, Visual Studio veya C# .NET Core CLI dahil olmak üzere, .net hakkında bilgi sahibi olduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-120">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="run-the-starter-application"></a><span data-ttu-id="ef6c0-121">Başlangıç uygulamasını çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ef6c0-121">Run the starter application</span></span>

<span data-ttu-id="ef6c0-122">Bu öğreticide kullanılan başlangıç uygulamasının kodunu [CSharp/öğreticiler/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start) klasöründeki [DotNet/Samples](https://github.com/dotnet/samples) depomızdan alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-122">You can get the code for the starter application used in this tutorial from our [dotnet/samples](https://github.com/dotnet/samples) repository in the [csharp/tutorials/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start) folder.</span></span>

<span data-ttu-id="ef6c0-123">Başlangıç uygulaması, [DotNet/docs](https://github.com/dotnet/docs) deposunda yazılan son sorunları almak Için [GitHub graphql](https://developer.github.com/v4/) arabirimini kullanan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-123">The starter application is a console application that uses the [GitHub GraphQL](https://developer.github.com/v4/) interface to retrieve recent issues written in the [dotnet/docs](https://github.com/dotnet/docs) repository.</span></span> <span data-ttu-id="ef6c0-124">Başlangıç uygulaması `Main` yöntemi için aşağıdaki koda bakarak başlayın:</span><span class="sxs-lookup"><span data-stu-id="ef6c0-124">Start by looking at the following code for the starter app `Main` method:</span></span>

[!code-csharp[StarterAppMain](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#StarterAppMain)]

<span data-ttu-id="ef6c0-125">Kişisel erişim belirtecinize bir `GitHubKey` ortam değişkeni ayarlayabilir veya `GenEnvVariable` çağrısındaki son bağımsız değişkeni kişisel erişim belirtecinizle değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-125">You can either set a `GitHubKey` environment variable to your personal access token, or you can replace the last argument in the call to `GenEnvVariable` with your personal access token.</span></span> <span data-ttu-id="ef6c0-126">Kaynağı başkalarıyla kaydediyorsanız veya paylaşılan bir kaynak deposuna koymak istiyorsanız, erişim kodunuzu kaynak koda yerleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-126">Don't put your access code in source code if you'll be saving the source with others, or putting it in a shared source repository.</span></span>

<span data-ttu-id="ef6c0-127">GitHub istemcisini oluşturduktan sonra, içindeki `Main` kod bir ilerleme raporlama nesnesi ve bir iptal belirteci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-127">After creating the GitHub client, the code in `Main` creates a progress reporting object and a cancellation token.</span></span> <span data-ttu-id="ef6c0-128">Bu nesneler oluşturulduktan sonra, `Main` en son 250 oluşturulan sorunları almak için çağırır. `runPagedQueryAsync`</span><span class="sxs-lookup"><span data-stu-id="ef6c0-128">Once those objects are created, `Main` calls `runPagedQueryAsync` to retrieve the most recent 250 created issues.</span></span> <span data-ttu-id="ef6c0-129">Bu görev bittikten sonra sonuçlar görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-129">After that task has finished, the results are displayed.</span></span>

<span data-ttu-id="ef6c0-130">Başlangıç uygulamasını çalıştırdığınızda, bu uygulamanın nasıl çalıştığı hakkında bazı önemli gözlemlerinizi yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-130">When you run the starter application, you can make some important observations about how this application runs.</span></span>  <span data-ttu-id="ef6c0-131">GitHub 'dan döndürülen her sayfa için ilerleme durumunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-131">You'll see progress reported for each page returned from GitHub.</span></span> <span data-ttu-id="ef6c0-132">GitHub her yeni sorun sayfasını geri döndürdüğünden, dikkat çekici bir duraklama gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-132">You can observe a noticeable pause before GitHub returns each new page of issues.</span></span> <span data-ttu-id="ef6c0-133">Son olarak, sorunlar yalnızca GitHub 'dan 10 sayfa alındıktan sonra görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-133">Finally, the issues are displayed only after all 10 pages have been retrieved from GitHub.</span></span>

## <a name="examine-the-implementation"></a><span data-ttu-id="ef6c0-134">Uygulamayı İnceleme</span><span class="sxs-lookup"><span data-stu-id="ef6c0-134">Examine the implementation</span></span>

<span data-ttu-id="ef6c0-135">Uygulama, önceki bölümde ele alınan davranışı neden gözlemlediğinizi ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-135">The implementation reveals why you observed the behavior discussed in the previous section.</span></span> <span data-ttu-id="ef6c0-136">Kodu `runPagedQueryAsync`inceleyin:</span><span class="sxs-lookup"><span data-stu-id="ef6c0-136">Examine the code for `runPagedQueryAsync`:</span></span>

[!code-csharp[RunPagedQueryStarter](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#RunPagedQuery)]

<span data-ttu-id="ef6c0-137">Yukarıdaki kodun disk belleği algoritmasına ve zaman uyumsuz yapısına odaklanalım.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-137">Let's concentrate on the paging algorithm and async structure of the preceding code.</span></span> <span data-ttu-id="ef6c0-138">(GitHub GraphQL API 'SI ile ilgili ayrıntılar için [GitHub graphql belgelerine](https://developer.github.com/v4/guides/) başvurabilirsiniz.) `runPagedQueryAsync` Yöntemi en sonuncudan en eskiye doğru olan sorunları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-138">(You can consult the [GitHub GraphQL documentation](https://developer.github.com/v4/guides/) for details on the GitHub GraphQL API.) The `runPagedQueryAsync` method enumerates the issues from most recent to oldest.</span></span> <span data-ttu-id="ef6c0-139">Sayfa başına 25 sorun ister ve önceki sayfaya devam `pageInfo` etmek için yanıtın yapısını inceler.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-139">It requests 25 issues per page and examines the `pageInfo` structure of the response to continue with the previous page.</span></span> <span data-ttu-id="ef6c0-140">Bu, çok sayfalı yanıtlar için GraphQL 'in standart disk belleği desteğini izler.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-140">That follows GraphQL's standard paging support for multi-page responses.</span></span> <span data-ttu-id="ef6c0-141">Yanıt, bir `hasPreviousPages` değeri `pageInfo` ve önceki sayfayı istemek için kullanılan bir `startCursor` değeri içeren bir nesnesi içerir.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-141">The response includes a `pageInfo` object that includes a `hasPreviousPages` value and a `startCursor` value used to request the previous page.</span></span> <span data-ttu-id="ef6c0-142">Sorunlar `nodes` dizide bulunur.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-142">The issues are in the `nodes` array.</span></span> <span data-ttu-id="ef6c0-143">Yöntemi `runPagedQueryAsync` , tüm sayfalardaki sonuçları içeren bir diziye bu düğümleri ekler.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-143">The `runPagedQueryAsync` method appends these nodes to an array that contains all the results from all pages.</span></span>

<span data-ttu-id="ef6c0-144">Bir sonuç sayfasını aldıktan ve geri yükledikten sonra, `runPagedQueryAsync` ilerlemeyi raporlar ve iptal olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-144">After retrieving and restoring a page of results, `runPagedQueryAsync` reports progress and checks for cancellation.</span></span> <span data-ttu-id="ef6c0-145">İptal isteniyorsa, `runPagedQueryAsync` bir <xref:System.OperationCanceledException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-145">If cancellation has been requested, `runPagedQueryAsync` throws an <xref:System.OperationCanceledException>.</span></span>

<span data-ttu-id="ef6c0-146">Bu kodda iyileştirilen birkaç öğe vardır.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-146">There are several elements in this code that can be improved.</span></span> <span data-ttu-id="ef6c0-147">En önemlisi, `runPagedQueryAsync` döndürülen tüm sorunlar için depolama alanı ayırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-147">Most importantly, `runPagedQueryAsync` must allocate storage for all the issues returned.</span></span> <span data-ttu-id="ef6c0-148">Tüm açık sorunların alınması, alınan tüm sorunları depolamak için çok daha fazla bellek gerektirdiğinden, bu örnek 250 sorunlarını durduruyor.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-148">This sample stops at 250 issues because retrieving all open issues would require much more memory to store all the retrieved issues.</span></span> <span data-ttu-id="ef6c0-149">Ayrıca, ilerlemeyi destekleme ve iptali destekleme protokolleri, algoritmayı ilk okuma konusunda daha zor hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-149">In addition, the protocols for supporting progress and supporting cancellation make the algorithm harder to understand on its first reading.</span></span> <span data-ttu-id="ef6c0-150">İlerleme durumunun nerede bildirileceğini bulmak için ilerleme sınıfına bakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-150">You must look for the progress class to find where progress is reported.</span></span> <span data-ttu-id="ef6c0-151">Ayrıca, <xref:System.Threading.CancellationTokenSource> İptalin istendiği ve nerede verildiğini anlamak <xref:System.Threading.CancellationToken> için ve arasındaki iletişimi izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-151">You also have to trace the communications through the <xref:System.Threading.CancellationTokenSource> and its associated <xref:System.Threading.CancellationToken> to understand where cancellation is requested and where it's granted.</span></span>

## <a name="async-streams-provide-a-better-way"></a><span data-ttu-id="ef6c0-152">Zaman uyumsuz akışlar daha iyi bir yol sağlar</span><span class="sxs-lookup"><span data-stu-id="ef6c0-152">Async streams provide a better way</span></span>

<span data-ttu-id="ef6c0-153">Zaman uyumsuz akışlar ve ilişkili dil desteği Bu kaygıların tümünü ele.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-153">Async streams and the associated language support address all those concerns.</span></span> <span data-ttu-id="ef6c0-154">Diziyi oluşturan kod artık `yield return` `async` değiştiriciyle tanımlanmış bir yöntemde öğe döndürmek için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-154">The code that generates the sequence can now use `yield return` to return elements in a method that was declared with the `async` modifier.</span></span> <span data-ttu-id="ef6c0-155">Döngü kullanarak bir zaman uyumsuz akışı `await foreach` , bir `foreach` döngüyü kullanarak herhangi bir diziyi tüketiğinizde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-155">You can consume an async stream using an `await foreach` loop just as you consume any sequence using a `foreach` loop.</span></span>

<span data-ttu-id="ef6c0-156">Bu yeni dil özellikleri, 2,1 .NET Standard eklenen ve .NET Core 3,0 ' de uygulanan üç yeni arabirime bağımlıdır:</span><span class="sxs-lookup"><span data-stu-id="ef6c0-156">These new language features depend on three new interfaces added to .NET Standard 2.1 and implemented in .NET Core 3.0:</span></span>

```csharp
namespace System.Collections.Generic
{
    public interface IAsyncEnumerable<out T>
    {
        IAsyncEnumerator<T> GetAsyncEnumerator(CancellationToken cancellationToken = default);
    }

    public interface IAsyncEnumerator<out T> : IAsyncDisposable
    {
        T Current { get; }

        ValueTask<bool> MoveNextAsync();
    }
}

namespace System
{
    public interface IAsyncDisposable
    {
        ValueTask DisposeAsync();
    }
}
```

<span data-ttu-id="ef6c0-157">Bu üç arabirim çoğu C# geliştiricilere tanıdık gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-157">These three interfaces should be familiar to most C# developers.</span></span> <span data-ttu-id="ef6c0-158">Zaman uyumlu ortaklarınıza benzer bir şekilde davranır:</span><span class="sxs-lookup"><span data-stu-id="ef6c0-158">They behave in a manner similar to their synchronous counterparts:</span></span>

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

<span data-ttu-id="ef6c0-159">Alışkın olabilecek bir tür <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-159">One type that may be unfamiliar is <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ef6c0-160">Struct, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfa benzer bir API sağlar. `ValueTask`</span><span class="sxs-lookup"><span data-stu-id="ef6c0-160">The `ValueTask` struct provides a similar API to the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="ef6c0-161">`ValueTask`performans nedenleriyle bu arabirimlerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-161">`ValueTask` is used in these interfaces for performance reasons.</span></span>

## <a name="convert-to-async-streams"></a><span data-ttu-id="ef6c0-162">Zaman uyumsuz akışlara Dönüştür</span><span class="sxs-lookup"><span data-stu-id="ef6c0-162">Convert to async streams</span></span>

<span data-ttu-id="ef6c0-163">Sonra, zaman uyumsuz `runPagedQueryAsync` akış oluşturmak için yöntemini dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-163">Next, convert the `runPagedQueryAsync` method to generate an async stream.</span></span> <span data-ttu-id="ef6c0-164">İlk olarak, `runPagedQueryAsync` `IAsyncEnumerable<JToken>`öğesini döndürmek için imzasını değiştirin ve aşağıdaki kodda gösterildiği gibi parametre listesinden iptal belirtecini ve ilerleme nesnelerini kaldırın:</span><span class="sxs-lookup"><span data-stu-id="ef6c0-164">First, change the signature of `runPagedQueryAsync` to return an `IAsyncEnumerable<JToken>`, and remove the cancellation token and progress objects from the parameter list as shown in the following code:</span></span>

[!code-csharp[FinishedSignature](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#UpdateSignature)]

<span data-ttu-id="ef6c0-165">Başlangıç kodu, aşağıdaki kodda gösterildiği gibi her sayfayı sayfa alındığından işler:</span><span class="sxs-lookup"><span data-stu-id="ef6c0-165">The starter code processes each page as the page is retrieved, as shown in the following code:</span></span>

[!code-csharp[StarterPaging](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#ProcessPage)]

<span data-ttu-id="ef6c0-166">Bu üç satırı aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="ef6c0-166">Replace those three lines with the following code:</span></span>

[!code-csharp[FinishedPaging](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#YieldReturnPage)]

<span data-ttu-id="ef6c0-167">Ayrıca, bu yöntemin `finalResults` önceki bildirimini `return` ve değiştirdiğiniz döngüyü izleyen ifadeyi de kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-167">You can also remove the declaration of `finalResults` earlier in this method and the `return` statement that follows the loop you modified.</span></span>

<span data-ttu-id="ef6c0-168">Zaman uyumsuz akış oluşturma değişikliklerini tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-168">You've finished the changes to generate an async stream.</span></span> <span data-ttu-id="ef6c0-169">Tamamlanan yöntem aşağıdaki koda benzemelidir:</span><span class="sxs-lookup"><span data-stu-id="ef6c0-169">The finished method should resemble the code below:</span></span>

[!code-csharp[FinishedGenerate](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#GenerateAsyncStream)]

<span data-ttu-id="ef6c0-170">Daha sonra, zaman uyumsuz akışı kullanmak için koleksiyonu tüketen kodu değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-170">Next, you change the code that consumes the collection to consume the async stream.</span></span> <span data-ttu-id="ef6c0-171">Sorun koleksiyonunu işleyen ' de `Main` aşağıdaki kodu bulun:</span><span class="sxs-lookup"><span data-stu-id="ef6c0-171">Find the following code in `Main` that processes the collection of issues:</span></span>

[!code-csharp[EnumerateOldStyle](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#EnumerateOldStyle)]

<span data-ttu-id="ef6c0-172">Bu kodu aşağıdaki `await foreach` döngüyle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="ef6c0-172">Replace that code with the following `await foreach` loop:</span></span>

[!code-csharp[FinishedEnumerateAsyncStream](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#EnumerateAsyncStream)]

<span data-ttu-id="ef6c0-173">Tamamlanan öğreticinin kodunu [CSharp/öğreticiler/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished) klasöründeki [DotNet/Samples](https://github.com/dotnet/samples) deposundan alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-173">You can get the code for the finished tutorial from the [dotnet/samples](https://github.com/dotnet/samples) repository in the [csharp/tutorials/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished) folder.</span></span>

## <a name="run-the-finished-application"></a><span data-ttu-id="ef6c0-174">Tamamlanmış uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ef6c0-174">Run the finished application</span></span>

<span data-ttu-id="ef6c0-175">Uygulamayı yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-175">Run the application again.</span></span> <span data-ttu-id="ef6c0-176">Davranışını, başlangıç uygulamasının davranışıyla kontrast.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-176">Contrast its behavior with the behavior of the starter application.</span></span> <span data-ttu-id="ef6c0-177">Sonuçların ilk sayfası, kullanılabilir duruma geldiğinde numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-177">The first page of results is enumerated as soon as it's available.</span></span> <span data-ttu-id="ef6c0-178">Her yeni sayfa istendiği ve alındığı için bir observable durakladıkça, sonraki sayfanın sonuçları hızla numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-178">There's an observable pause as each new page is requested and retrieved, then the next page's results are quickly enumerated.</span></span> <span data-ttu-id="ef6c0-179">İptaliişlemekiçinblokgerekmez:çağıran,koleksiyonulistemeyidurdurabilir.`try`  /  `catch`</span><span class="sxs-lookup"><span data-stu-id="ef6c0-179">The `try` / `catch` block isn't needed to handle cancellation: the caller can stop enumerating the collection.</span></span> <span data-ttu-id="ef6c0-180">Zaman uyumsuz akış, her sayfa indirildiğinden sonuçlar oluşturduğundan, ilerleme durumu açıkça raporlanır.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-180">Progress is clearly reported because the async stream generates results as each page is downloaded.</span></span>

<span data-ttu-id="ef6c0-181">Kodu inceleyerek, bellek kullanımıyla iyileştirmeleri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-181">You can see improvements in memory use by examining the code.</span></span> <span data-ttu-id="ef6c0-182">Artık tüm sonuçları numaralandırılmadan önce depolamak için bir koleksiyon ayırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-182">You no longer need to allocate a collection to store all the results before they're enumerated.</span></span> <span data-ttu-id="ef6c0-183">Çağıran, sonuçların nasıl kullanıldığını ve bir depolama koleksiyonu gerekip gerekmediğini belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-183">The caller can determine how to consume the results and if a storage collection is needed.</span></span>

<span data-ttu-id="ef6c0-184">Hem Başlatıcı hem de tamamlanmış uygulamaları çalıştırın ve uygulamalar arasındaki farklılıkları gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-184">Run both the starter and finished applications and you can observe the differences between the implementations for yourself.</span></span> <span data-ttu-id="ef6c0-185">İşiniz bittiğinde, bu öğreticiyi başlattığınızda oluşturduğunuz GitHub erişim belirtecini silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-185">You can delete the GitHub access token you created when you started this tutorial after you've finished.</span></span> <span data-ttu-id="ef6c0-186">Bir saldırgan bu belirtece erişim kazanırsa, kimlik bilgilerinizi kullanarak GitHub API 'Lerine erişebilirler.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-186">If an attacker gained access to that token, they could access GitHub APIs using your credentials.</span></span>
