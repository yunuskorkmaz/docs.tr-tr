---
title: GRPC istemci kitaplıkları oluşturma - WCF Geliştiricileri için gRPC
description: gRPC hizmetleri için paylaşılan istemci kitaplıklarının/paketlerinin tartışılması.
ms.date: 09/02/2019
ms.openlocfilehash: bb58cb3cda4b0cbb3a5d34129961349bcb0093e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401671"
---
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="fc03d-103">gRPC istemci kitaplıkları oluşturma</span><span class="sxs-lookup"><span data-stu-id="fc03d-103">Create gRPC client libraries</span></span>

<span data-ttu-id="fc03d-104">Bir gRPC uygulaması için istemci kitaplıkları dağıtmak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="fc03d-104">It isn't necessary to distribute client libraries for a gRPC application.</span></span> <span data-ttu-id="fc03d-105">Kuruluşunuz içinde paylaşılan `.proto` bir dosya kitaplığı oluşturabilirsiniz ve diğer ekipler bu dosyaları kendi projelerinde istemci kodu oluşturmak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="fc03d-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="fc03d-106">Ancak özel bir NuGet deponuz varsa ve diğer birçok takım .NET Core kullanıyorsa, hizmet projenizin bir parçası olarak istemci NuGet paketleri oluşturabilir ve yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc03d-106">But if you have a private NuGet repository and many other teams are using .NET Core, you can create and publish client NuGet packages as part of your service project.</span></span> <span data-ttu-id="fc03d-107">Bu, hizmetinizi paylaşmanın ve tanıtmanın iyi bir yolu olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc03d-107">This can be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="fc03d-108">İstemci kitaplığı dağıtmanın bir avantajı, oluşturulan gRPC ve Protobuf sınıflarını yararlı "kolaylık" yöntemleri ve özellikleriyle geliştirebilmektir.</span><span class="sxs-lookup"><span data-stu-id="fc03d-108">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="fc03d-109">İstemci kodunda, sunucuda olduğu gibi, `partial`tüm sınıflar , oluşturulan kodu düzenlemeden genişletebilirsiniz olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="fc03d-109">In the client code, as in the server, all the classes are declared as `partial`, so you can extend them without editing the generated code.</span></span> <span data-ttu-id="fc03d-110">Bu, temel türlere oluşturucular, yöntemler ve hesaplanmış özellikler eklemenin kolay olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fc03d-110">This means it's easy to add constructors, methods, and calculated properties to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="fc03d-111">Temel işlevselliği sağlamak için özel kod kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="fc03d-111">You shouldn't use custom code to provide essential functionality.</span></span> <span data-ttu-id="fc03d-112">Bu temel işlevselliği paylaşılan kitaplığı kullanan .NET ekipleriyle sınırlamak ve bunu Python veya Java gibi diğer dilleri veya platformları kullanan takımlara sağlamamak istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc03d-112">You don't want to restrict that essential functionality to .NET teams that use the shared library, and not provide it to teams that use other languages or platforms, such as Python or Java.</span></span>

<span data-ttu-id="fc03d-113">Mümkün olduğunca çok takımın gRPC hizmetinize erişebilmesini sağlayın.</span><span class="sxs-lookup"><span data-stu-id="fc03d-113">Ensure that as many teams as possible can access your gRPC service.</span></span> <span data-ttu-id="fc03d-114">Bunu yapmanın en iyi yolu, geliştiricilerin kendi istemcilerini oluşturabilmesi için dosyaları paylaşmaktır. `.proto`</span><span class="sxs-lookup"><span data-stu-id="fc03d-114">The best way to do this is to share `.proto` files so developers can generate their own clients.</span></span> <span data-ttu-id="fc03d-115">Bu, özellikle farklı ekiplerin sık sık farklı programlama dillerini ve çerçevelerini kullandığı veya API'nizin dışarıdan erişilebilir olduğu çok platformlu bir ortamda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fc03d-115">This is particularly true in a multi-platform environment, where different teams frequently use different programming languages and frameworks, or where your API is externally accessible.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="fc03d-116">Yararlı uzantılar</span><span class="sxs-lookup"><span data-stu-id="fc03d-116">Useful extensions</span></span>

<span data-ttu-id="fc03d-117">.NET'te nesnelerin akışlarıyla başa çıkmak için yaygın olarak <xref:System.Collections.Generic.IEnumerable%601> kullanılan <xref:System.IObservable%601>iki arabirim vardır: ve.</span><span class="sxs-lookup"><span data-stu-id="fc03d-117">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="fc03d-118">.NET Core 3.0 ve C# 8.0 ile <xref:System.Collections.Generic.IAsyncEnumerable%601> başlayarak, akışları eşit bir şekilde `await foreach` işlemek için bir arabirim ve arabirimi kullanmak için bir sözdizimi vardır.</span><span class="sxs-lookup"><span data-stu-id="fc03d-118">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="fc03d-119">Bu bölümde, bu arabirimleri gRPC akışlarına uygulamak için yeniden kullanılabilir kod lar bulunur.</span><span class="sxs-lookup"><span data-stu-id="fc03d-119">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="fc03d-120">.NET Core gRPC istemci kitaplıklarında, `ReadAllAsync` arabirim `IAsyncStreamReader<T>` oluşturan bir `IAsyncEnumerable<T>` uzantı yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="fc03d-120">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>` interface.</span></span> <span data-ttu-id="fc03d-121">Reaktif programlama yı kullanan geliştiriciler için, arabirim oluşturmak için eşdeğer bir `IObservable<T>` uzantı yöntemi aşağıdaki bölümdeki örnek gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="fc03d-121">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` interface might look like the example in the following section.</span></span>

### <a name="iobservable"></a><span data-ttu-id="fc03d-122">ıobservable</span><span class="sxs-lookup"><span data-stu-id="fc03d-122">IObservable</span></span>

<span data-ttu-id="fc03d-123">Arabirim `IObservable<T>` "reaktif" ters `IEnumerable<T>`olduğunu.</span><span class="sxs-lookup"><span data-stu-id="fc03d-123">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="fc03d-124">Öğeleri akıştan çekmek yerine, reaktif yaklaşım, akış öğelerini aboneye itmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc03d-124">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="fc03d-125">Bu, gRPC akışlarına çok benzer ve `IObservable<T>` `IAsyncStreamReader<T>` arabirimi bir arabirim etrafında kaydırmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="fc03d-125">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` interface around an `IAsyncStreamReader<T>` interface.</span></span>

<span data-ttu-id="fc03d-126">C# gözlemlenebilirlerle `IAsyncEnumerable<T>` çalışmak için yerleşik desteği olmadığından, bu kod koddan daha uzundur.</span><span class="sxs-lookup"><span data-stu-id="fc03d-126">This code is longer than the `IAsyncEnumerable<T>` code, because C# doesn't have built-in support for working with observables.</span></span> <span data-ttu-id="fc03d-127">Uygulama sınıfını el ile oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc03d-127">You have to create the implementation class manually.</span></span> <span data-ttu-id="fc03d-128">Bu genel bir sınıf olsa da, tek bir uygulama her türlü çalışır.</span><span class="sxs-lookup"><span data-stu-id="fc03d-128">It's a generic class, though, so a single implementation works across all types.</span></span>

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
> <span data-ttu-id="fc03d-129">Bu gözlemlenebilir uygulama, `Subscribe` birden çok abonenin akıştan okumaya çalışması kaosa yol açacağından, yöntemin yalnızca bir kez çağrılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc03d-129">This observable implementation allows the `Subscribe` method to be called only once, because having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="fc03d-130">`Replay` [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq)gibi, bu uygulama ile kullanılabilir gözlemlenebilir, arabelleğe alma ve tekrarlanabilir paylaşımı sağlayan operatörler vardır.</span><span class="sxs-lookup"><span data-stu-id="fc03d-130">There are operators, such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="fc03d-131">Sınıf `GrpcStreamSubscription` numaralandırma `IAsyncStreamReader`işler:</span><span class="sxs-lookup"><span data-stu-id="fc03d-131">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`:</span></span>

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

<span data-ttu-id="fc03d-132">Şimdi gerekli olan tek şey akış okuyucudan gözlemlenebilir oluşturmak için basit bir uzantı yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="fc03d-132">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

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

## <a name="summary"></a><span data-ttu-id="fc03d-133">Özet</span><span class="sxs-lookup"><span data-stu-id="fc03d-133">Summary</span></span>

<span data-ttu-id="fc03d-134">Ve `IAsyncEnumerable` `IObservable` modeller, .NET'teki eşzamanlı veri akışlarıyla başa çıkmanın hem iyi desteklenen hem de iyi belgelenmiş yollarıdır.</span><span class="sxs-lookup"><span data-stu-id="fc03d-134">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="fc03d-135">gRPC akışları her iki paradigma için de harita, .NET Core ile yakın entegrasyon sunan ve reaktif ve asynchronous programlama stilleri.</span><span class="sxs-lookup"><span data-stu-id="fc03d-135">gRPC streams map well to both paradigms, offering close integration with .NET Core, and reactive and asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fc03d-136">[Önceki](streaming-versus-repeated.md)
>[Sonraki](security.md)</span><span class="sxs-lookup"><span data-stu-id="fc03d-136">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
