---
title: GRPC istemci kitaplıkları oluşturma-WCF geliştiricileri için gRPC
description: GRPC Hizmetleri için paylaşılan istemci kitaplıkları/paketleri tartışması.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 44a749c888528ca244f41b5b88354d7ed1db4190
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184591"
---
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="4687d-103">GRPC istemci kitaplıkları oluşturma</span><span class="sxs-lookup"><span data-stu-id="4687d-103">Create gRPC client libraries</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="4687d-104">Bir gPRC uygulaması için istemci kitaplıklarını dağıtmak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="4687d-104">It isn't necessary to distribute client libraries for a gPRC application.</span></span> <span data-ttu-id="4687d-105">Kuruluşunuz dahilinde paylaşılan bir `.proto` dosya kitaplığı oluşturabilirsiniz ve diğer takımlar bu dosyaları kendi projelerinde istemci kodu oluşturmak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="4687d-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="4687d-106">Ancak, özel bir NuGet deponuz varsa ve diğer birçok ekip .NET Core kullanıyorsa, hizmet projenizin bir parçası olarak istemci NuGet paketleri oluşturma ve yayımlama, hizmetinizi paylaşma ve yükseltme konusunda iyi bir yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="4687d-106">But if you have a private NuGet repository and many other teams are using .NET Core, creating and publishing client NuGet packages as part of your service project may be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="4687d-107">İstemci kitaplığı dağıtmanın avantajlarından biri, oluşturulan gRPC ve prototip sınıflarını faydalı "kullanışlı" yöntemlerle ve özellikleriyle geliştirebilmektir.</span><span class="sxs-lookup"><span data-stu-id="4687d-107">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="4687d-108">İstemci kodunda, sunucusunda olduğu gibi, oluşturulan kodu düzenlemeden bunları genişletebilmeniz için tüm sınıfların `partial` olarak bildirildiği belirtilir.</span><span class="sxs-lookup"><span data-stu-id="4687d-108">In the client code, as in the server, all the classes are declared as `partial` so you can extend them without editing the generated code.</span></span> <span data-ttu-id="4687d-109">Bu, temel türlere oluşturucular, Yöntemler, hesaplanmış Özellikler ve daha fazlasını eklemenin kolay olması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4687d-109">This means it's easy to add constructors, methods, calculated properties, and more to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="4687d-110">Önemli işlevselliği sağlamak için özel **kod kullanmamalısınız;** bunun anlamı, Işlevin, Python veya Java gibi diğer dilleri veya platformları kullanan ekipler için değil, paylaşılan kitaplığı kullanan .net ekipleri ile kısıtlandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4687d-110">You should **not** use custom code to provide essential functionality, as this would mean that functionality would be restricted to .NET teams using the shared library, and not to teams using other languages or platforms such as Python or Java.</span></span>

<span data-ttu-id="4687d-111">Farklı takımların genellikle farklı programlama dilleri ve çerçeveleri kullanıldığı veya API 'nizin dışarıdan erişilebilen `.proto` çok platformlu bir ortamda, geliştiricilerin kendi istemcilerini oluşturabilmesi için en iyi yolu birçok ekibin gRPC hizmetinize erişebildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4687d-111">In a multi-platform environment where different teams frequently use different programming languages and frameworks, or where your API is externally accessible, simply sharing `.proto` files so developers can generate their own clients is the best way to ensure as many teams as possible can access your gRPC service.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="4687d-112">Kullanışlı uzantılar</span><span class="sxs-lookup"><span data-stu-id="4687d-112">Useful extensions</span></span>

<span data-ttu-id="4687d-113">.Net ' te nesne akışları ile ilgili olarak yaygın olarak kullanılan iki arabirim vardır: <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IObservable%601>.</span><span class="sxs-lookup"><span data-stu-id="4687d-113">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="4687d-114">.NET Core 3,0 ve C# 8,0 ' den başlayarak, akışları zaman <xref:System.Collections.Generic.IAsyncEnumerable%601> uyumsuz olarak işlemeye yönelik bir arabirim ve arabirimi `await foreach` kullanmak için bir sözdizimi vardır.</span><span class="sxs-lookup"><span data-stu-id="4687d-114">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="4687d-115">Bu bölümde, bu arabirimlerin gRPC akışlarına uygulanması için yeniden kullanılabilir kod sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4687d-115">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="4687d-116">.NET Core GRPC istemci kitaplıkları ile, `ReadAllAsync` `IAsyncStreamReader<T>` tarafından oluşturulan bir `IAsyncEnumerable<T>`genişletme yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="4687d-116">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>`.</span></span> <span data-ttu-id="4687d-117">Reaktif programlama kullanan geliştiriciler için, oluşturmak `IObservable<T>` için eşdeğer bir genişletme yöntemi şöyle görünebilir.</span><span class="sxs-lookup"><span data-stu-id="4687d-117">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` might look like this.</span></span>

### <a name="iobservable"></a><span data-ttu-id="4687d-118">IObservable</span><span class="sxs-lookup"><span data-stu-id="4687d-118">IObservable</span></span>

<span data-ttu-id="4687d-119">Arabirim, "reaktif" `IEnumerable<T>`tersidir. `IObservable<T>`</span><span class="sxs-lookup"><span data-stu-id="4687d-119">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="4687d-120">Bir akıştan öğe çekmek yerine, reaktif yaklaşım akışa akış gönderme öğeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4687d-120">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="4687d-121">Bu, GRPC akışlarına çok benzer ve bir `IObservable<T>` `IAsyncStreamReader<T>`etrafında sarmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="4687d-121">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` around an `IAsyncStreamReader<T>`.</span></span>

<span data-ttu-id="4687d-122">Bu kod `IAsyncEnumerable<T>` koddan daha uzundur, çünkü C# gözlemlenenler ile çalışmak için yerleşik desteği yoktur, bu nedenle uygulama sınıfının el ile oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4687d-122">This code is longer than the `IAsyncEnumerable<T>` code because C# doesn't have built-in support for working with observables, so the implementation class has to be created manually.</span></span> <span data-ttu-id="4687d-123">Bu, genel bir sınıftır, ancak tek bir uygulama tüm türler arasında çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="4687d-123">It's a generic class, though, so a single implementation will work across all types.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public class GrpcStreamObservable<T> : IObservable<T>
    {
        private readonly IAsyncStreamReader<T> _reader;
        private readonly CancellationToken _token;
        private int _used;

        public Observable(IAsyncStreamReader<T> reader, CancellationToken token = default)
        {
            _reader = reader;
            _token = token;
            _used = 0;
        }

        public IDisposable Subscribe(IObserver<T> observer) =>
            Interlocked.Exchange(ref _used, 1) == 0
                ? new GrpcStreamSubscription(_reader, observer, _token)
                : throw new InvalidOperationException("Subscribe can only be called once.");

    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="4687d-124">Bu observable uygulamasının yalnızca bir kez `Subscribe` bir kez çağrılmasına izin verir. Bu, akıştan okumayı deneyen birden çok abone olması, Chaos ile sonuçlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="4687d-124">This observable implementation only allows the `Subscribe` method to be called once, as having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="4687d-125">`Replay` [System. reak. LINQ](https://www.nuget.org/packages/System.Reactive.Linq) içinde, bu uygulamayla kullanılabilen gözlemlenenler 'in arabelleğe alma ve yinelenebilir paylaşımını etkinleştiren işleçler vardır.</span><span class="sxs-lookup"><span data-stu-id="4687d-125">There are operators such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq) that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="4687d-126">`GrpcStreamSubscription` Sınıfı ,`IAsyncStreamReader`öğesinin sabit listesini işler.</span><span class="sxs-lookup"><span data-stu-id="4687d-126">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`.</span></span>

```csharp
public class GrpcStreamSubscription : IDisposable
{
    private readonly Task _task;
    private readonly CancellationTokenSource _tokenSource;
    private bool _completed;

    public Subscription(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        Debug.Assert(reader != null);
        Debug.Assert(observer != null);
        _tokenSource = new CancellationTokenSource();
        token.Register(_tokenSource.Cancel);
        _task = Run(reader, observer, _tokenSource.Token);
    }

    private async Task Run(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        while (!token.IsCancellationRequested)
        {
            try
            {
                if (!await reader.MoveNext(token)) break;
            }
            catch (RpcException e) when (e.StatusCode == Grpc.Core.StatusCode.NotFound)
            {
                break;
            }
            catch (OperationCanceledException)
            {
                break;
            }
            catch (Exception e)
            {
                observer.OnError(e);
                _completed = true;
                return;
            }

            observer.OnNext(reader.Current);
        }

        _completed = true;
        observer.OnCompleted();
    }

    public void Dispose()
    {
        if (!_completed && !_tokenSource.IsCancellationRequested)
        {
            _tokenSource.Cancel();
        }

        _tokenSource.Dispose();
        _task.Dispose();
    }

}
```

<span data-ttu-id="4687d-127">Artık gereken tek şey, Stream okuyucusundan observable oluşturmaya yönelik basit bir genişletme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="4687d-127">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public static class AsyncStreamReaderObservableExtensions
    {
        public static IObservable<T> AsObservable<T>(this IAsyncStreamReader<T> reader) =>
            new GrpcStreamObservable<T>(reader);
    }
}
```

## <a name="summary"></a><span data-ttu-id="4687d-128">Özet</span><span class="sxs-lookup"><span data-stu-id="4687d-128">Summary</span></span>

<span data-ttu-id="4687d-129">`IAsyncEnumerable` Ve`IObservable` modelleri, .NET içinde zaman uyumsuz veri akışları ile ilgilenmenin iyi desteklendiğinden ve iyi belgelenmiş yollardır.</span><span class="sxs-lookup"><span data-stu-id="4687d-129">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="4687d-130">gRPC, modern .NET Core Framework ve reaktif/zaman uyumsuz programlama stilleriyle, yakın tümleştirme sunan paradigmalarına ve her ikisine de eşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="4687d-130">gRPC streams map well to both paradigms, offering close integration with the modern .NET Core framework and reactive/asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4687d-131">[Önceki](streaming-versus-repeated.md)
>[İleri](security.md)</span><span class="sxs-lookup"><span data-stu-id="4687d-131">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
