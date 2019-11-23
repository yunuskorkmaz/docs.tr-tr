---
title: GRPC istemci kitaplıkları oluşturma-WCF geliştiricileri için gRPC
description: GRPC Hizmetleri için paylaşılan istemci kitaplıkları/paketleri tartışması.
ms.date: 09/02/2019
ms.openlocfilehash: 2135fe8b24a2311a31cb2bed191d290b1112bc66
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967883"
---
# <a name="create-grpc-client-libraries"></a>GRPC istemci kitaplıkları oluşturma

Bir gRPC uygulaması için istemci kitaplıklarını dağıtmak gerekli değildir. Kuruluşunuzda paylaşılan bir `.proto` dosyaları kitaplığı oluşturabilirsiniz ve diğer takımlar bu dosyaları kendi projelerinde istemci kodu oluşturmak için kullanabilir. Ancak, özel bir NuGet deponuz varsa ve diğer birçok ekip .NET Core kullanıyorsa, hizmet projenizin bir parçası olarak istemci NuGet paketleri oluşturma ve yayımlama, hizmetinizi paylaşma ve yükseltme konusunda iyi bir yöntem olabilir.

İstemci kitaplığı dağıtmanın avantajlarından biri, oluşturulan gRPC ve prototip sınıflarını faydalı "kullanışlı" yöntemlerle ve özellikleriyle geliştirebilmektir. İstemci kodunda, sunucusunda olduğu gibi, tüm sınıfların `partial` olarak bildirildiği için, bunları oluşturulan kodu düzenlemeden genişletebilirsiniz. Bu, temel türlere oluşturucular, Yöntemler, hesaplanmış Özellikler ve daha fazlasını eklemenin kolay olması anlamına gelir.

> [!CAUTION]
> Önemli işlevselliği sağlamak için özel **kod kullanmamalısınız;** bunun anlamı, Işlevin, Python veya Java gibi diğer dilleri veya platformları kullanan ekipler için değil, paylaşılan kitaplığı kullanan .net ekipleri ile kısıtlandığı anlamına gelir.

Farklı takımların farklı programlama dilleri ve çerçeveleri kullanıldığı veya API 'nizin dışarıdan erişilebilen çok platformlu bir ortamda, geliştiricilerin kendi istemcilerini oluşturabilmesi için `.proto`, mümkün olduğunca çok ekibin gRPC hizmetinize erişebileceği sağlamanın en iyi yolu vardır.

## <a name="useful-extensions"></a>Kullanışlı uzantılar

.NET ' te nesne akışlarıyla uğraşmadan önce iki yaygın olarak kullanılan arabirim vardır: <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IObservable%601>. .NET Core 3,0 ve C# 8,0 ' den itibaren, akışları zaman uyumsuz olarak işlemeye yönelik bir <xref:System.Collections.Generic.IAsyncEnumerable%601> arabirimi ve arabirimi kullanmak için `await foreach` söz dizimi vardır. Bu bölümde, bu arabirimlerin gRPC akışlarına uygulanması için yeniden kullanılabilir kod sunulmaktadır.

.NET Core gRPC istemci kitaplıkları ile, bir `IAsyncEnumerable<T>`oluşturan `IAsyncStreamReader<T>` için `ReadAllAsync` bir genişletme yöntemi vardır. Reaktif programlama kullanan geliştiriciler için `IObservable<T>` oluşturmak için eşdeğer bir genişletme yöntemi şöyle görünebilir.

### <a name="iobservable"></a>IObservable

`IObservable<T>` arabirimi, `IEnumerable<T>`"reaktif" tersidir. Bir akıştan öğe çekmek yerine, reaktif yaklaşım akışa akış gönderme öğeleri sağlar. Bu, gRPC akışlarına çok benzer ve bir `IObservable<T>` `IAsyncStreamReader<T>`etrafında sarmayı kolay hale gelir.

Bu kod `IAsyncEnumerable<T>` koddan daha uzundur, çünkü C# gözlemlenenler ile çalışmaya yönelik yerleşik desteği yoktur, bu nedenle uygulama sınıfının el ile oluşturulması gerekir. Bu, genel bir sınıftır, ancak tek bir uygulama tüm türler arasında çalışacaktır.

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
> Bu observable uygulamasının yalnızca `Subscribe` yönteminin bir kez çağrılmasına izin verir. Bu, akıştan okumayı deneyen birden çok abone olması, Chaos ile sonuçlanacaktır. [System. reak. LINQ](https://www.nuget.org/packages/System.Reactive.Linq) içinde `Replay` gibi işleçler vardır ve bu uygulamayla birlikte kullanılabilecek gözlemlenenler 'in arabelleğe alma ve yinelenebilir paylaşımını olanaklı hale getirebilirsiniz.

`GrpcStreamSubscription` sınıfı `IAsyncStreamReader`numaralandırmasını işler.

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

Artık gereken tek şey, Stream okuyucusundan observable oluşturmaya yönelik basit bir genişletme yöntemidir.

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

## <a name="summary"></a>Özet

`IAsyncEnumerable` ve `IObservable` modelleri, .NET 'te zaman uyumsuz veri akışları ile ilgilenmenin iyi desteklendiğinden ve iyi belgelenmiş yollardır. gRPC, modern .NET Core Framework ve reaktif/zaman uyumsuz programlama stilleriyle, yakın tümleştirme sunan paradigmalarına ve her ikisine de eşleme sağlar.

>[!div class="step-by-step"]
>[Önceki](streaming-versus-repeated.md)
>[İleri](security.md)
