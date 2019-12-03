---
title: GRPC istemci kitaplıkları oluşturma-WCF geliştiricileri için gRPC
description: GRPC Hizmetleri için paylaşılan istemci kitaplıkları/paketleri tartışması.
ms.date: 09/02/2019
ms.openlocfilehash: bb58cb3cda4b0cbb3a5d34129961349bcb0093e9
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711453"
---
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="376de-103">GRPC istemci kitaplıkları oluşturma</span><span class="sxs-lookup"><span data-stu-id="376de-103">Create gRPC client libraries</span></span>

<span data-ttu-id="376de-104">Bir gRPC uygulaması için istemci kitaplıklarını dağıtmak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="376de-104">It isn't necessary to distribute client libraries for a gRPC application.</span></span> <span data-ttu-id="376de-105">Kuruluşunuzda paylaşılan bir `.proto` dosyaları kitaplığı oluşturabilirsiniz ve diğer takımlar bu dosyaları kendi projelerinde istemci kodu oluşturmak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="376de-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="376de-106">Ancak özel bir NuGet deponuz varsa ve diğer birçok ekip .NET Core kullanıyorsa, hizmet projenizin bir parçası olarak istemci NuGet paketleri oluşturabilir ve yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="376de-106">But if you have a private NuGet repository and many other teams are using .NET Core, you can create and publish client NuGet packages as part of your service project.</span></span> <span data-ttu-id="376de-107">Bu, hizmetinizi paylaşmak ve yükseltmek için iyi bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="376de-107">This can be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="376de-108">İstemci kitaplığı dağıtmanın avantajlarından biri, oluşturulan gRPC ve prototip sınıflarını faydalı "kullanışlı" yöntemlerle ve özellikleriyle geliştirebilmektir.</span><span class="sxs-lookup"><span data-stu-id="376de-108">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="376de-109">İstemci kodunda, sunucusunda olduğu gibi, tüm sınıfların `partial`olarak bildirildiği için, bunları oluşturulan kodu düzenlemeden genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="376de-109">In the client code, as in the server, all the classes are declared as `partial`, so you can extend them without editing the generated code.</span></span> <span data-ttu-id="376de-110">Bu, temel türlere oluşturucular, Yöntemler ve hesaplanmış özellikler eklemenin kolay olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="376de-110">This means it's easy to add constructors, methods, and calculated properties to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="376de-111">Önemli işlevselliği sağlamak için özel kod kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="376de-111">You shouldn't use custom code to provide essential functionality.</span></span> <span data-ttu-id="376de-112">Paylaşılan kitaplığı kullanan .NET ekipleriyle ilgili önemli işlevselliği kısıtlamak ve Python ya da Java gibi diğer dilleri veya platformları kullanan takımlara sağlamamak istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="376de-112">You don't want to restrict that essential functionality to .NET teams that use the shared library, and not provide it to teams that use other languages or platforms, such as Python or Java.</span></span>

<span data-ttu-id="376de-113">Mümkün olduğunca fazla ekibin gRPC hizmetinize erişebildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="376de-113">Ensure that as many teams as possible can access your gRPC service.</span></span> <span data-ttu-id="376de-114">Bunu yapmanın en iyi yolu, geliştiricilerin kendi istemcilerini oluşturabileceği şekilde `.proto` dosyaları paylaşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="376de-114">The best way to do this is to share `.proto` files so developers can generate their own clients.</span></span> <span data-ttu-id="376de-115">Bu özellikle, farklı takımların farklı programlama dilleri ve çerçeveleri kullanması veya API 'nizin dışarıdan erişilebilir olduğu durumlarda çok platformlu bir ortamda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="376de-115">This is particularly true in a multi-platform environment, where different teams frequently use different programming languages and frameworks, or where your API is externally accessible.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="376de-116">Kullanışlı uzantılar</span><span class="sxs-lookup"><span data-stu-id="376de-116">Useful extensions</span></span>

<span data-ttu-id="376de-117">.NET ' te nesne akışlarıyla uğraşmadan önce iki yaygın olarak kullanılan arabirim vardır: <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IObservable%601>.</span><span class="sxs-lookup"><span data-stu-id="376de-117">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="376de-118">.NET Core 3,0 ve C# 8,0 ' den itibaren, akışları zaman uyumsuz olarak işlemeye yönelik bir <xref:System.Collections.Generic.IAsyncEnumerable%601> arabirimi ve arabirimi kullanmak için `await foreach` söz dizimi vardır.</span><span class="sxs-lookup"><span data-stu-id="376de-118">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="376de-119">Bu bölümde, bu arabirimlerin gRPC akışlarına uygulanması için yeniden kullanılabilir kod sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="376de-119">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="376de-120">.NET Core gRPC istemci kitaplıkları ile `IAsyncEnumerable<T>` arabirimi oluşturan `IAsyncStreamReader<T>` için `ReadAllAsync` bir genişletme yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="376de-120">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>` interface.</span></span> <span data-ttu-id="376de-121">Reaktif programlama kullanan geliştiriciler için, bir `IObservable<T>` arabirimi oluşturmak için eşdeğer bir genişletme yöntemi aşağıdaki bölümdeki örneğe benzeyebilir.</span><span class="sxs-lookup"><span data-stu-id="376de-121">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` interface might look like the example in the following section.</span></span>

### <a name="iobservable"></a><span data-ttu-id="376de-122">IObservable</span><span class="sxs-lookup"><span data-stu-id="376de-122">IObservable</span></span>

<span data-ttu-id="376de-123">`IObservable<T>` arabirimi, `IEnumerable<T>`"reaktif" tersidir.</span><span class="sxs-lookup"><span data-stu-id="376de-123">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="376de-124">Bir akıştan öğe çekmek yerine, reaktif yaklaşım akışa akış gönderme öğeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="376de-124">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="376de-125">Bu, gRPC akışlarına çok benzer ve bir `IObservable<T>` arabirimini `IAsyncStreamReader<T>` bir arabirim etrafında sarmalaması kolaydır.</span><span class="sxs-lookup"><span data-stu-id="376de-125">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` interface around an `IAsyncStreamReader<T>` interface.</span></span>

<span data-ttu-id="376de-126">Bu kod `IAsyncEnumerable<T>` koddan daha uzun olduğundan C# , gözlemlenenler ile çalışmaya yönelik yerleşik desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="376de-126">This code is longer than the `IAsyncEnumerable<T>` code, because C# doesn't have built-in support for working with observables.</span></span> <span data-ttu-id="376de-127">Uygulama sınıfını el ile oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="376de-127">You have to create the implementation class manually.</span></span> <span data-ttu-id="376de-128">Bu, genel bir sınıftır, ancak tek bir uygulama tüm türler arasında çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="376de-128">It's a generic class, though, so a single implementation works across all types.</span></span>

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
> <span data-ttu-id="376de-129">Bu observable uygulamasının `Subscribe` yönteminin yalnızca bir kez çağrılmasına izin verir, çünkü akıştan okumaya çalışan birden fazla abone olması, Chaos ile sonuçlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="376de-129">This observable implementation allows the `Subscribe` method to be called only once, because having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="376de-130">[System. reak. LINQ](https://www.nuget.org/packages/System.Reactive.Linq)içinde `Replay` gibi işleçler vardır ve bu uygulamayla birlikte kullanılabilecek gözlemlenenler 'in arabelleğe alma ve yinelenebilir paylaşımını olanaklı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="376de-130">There are operators, such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="376de-131">`GrpcStreamSubscription` sınıfı `IAsyncStreamReader`numaralandırmasını işler:</span><span class="sxs-lookup"><span data-stu-id="376de-131">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`:</span></span>

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

<span data-ttu-id="376de-132">Artık gereken tek şey, Stream okuyucusundan observable oluşturmaya yönelik basit bir genişletme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="376de-132">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

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

## <a name="summary"></a><span data-ttu-id="376de-133">Özet</span><span class="sxs-lookup"><span data-stu-id="376de-133">Summary</span></span>

<span data-ttu-id="376de-134">`IAsyncEnumerable` ve `IObservable` modelleri, .NET 'te zaman uyumsuz veri akışları ile ilgilenmenin iyi desteklendiğinden ve iyi belgelenmiş yollardır.</span><span class="sxs-lookup"><span data-stu-id="376de-134">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="376de-135">gRPC, Map 'i hem paradigmalarına hem de .NET Core ile yakın tümleştirme sunan ve reaktif ve zaman uyumsuz programlama stilleriyle birlikte akışlar.</span><span class="sxs-lookup"><span data-stu-id="376de-135">gRPC streams map well to both paradigms, offering close integration with .NET Core, and reactive and asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="376de-136">[Önceki](streaming-versus-repeated.md)
>[İleri](security.md)</span><span class="sxs-lookup"><span data-stu-id="376de-136">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
