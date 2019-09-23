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
# <a name="create-grpc-client-libraries"></a>GRPC istemci kitaplıkları oluşturma

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bir gPRC uygulaması için istemci kitaplıklarını dağıtmak gerekli değildir. Kuruluşunuz dahilinde paylaşılan bir `.proto` dosya kitaplığı oluşturabilirsiniz ve diğer takımlar bu dosyaları kendi projelerinde istemci kodu oluşturmak için kullanabilir. Ancak, özel bir NuGet deponuz varsa ve diğer birçok ekip .NET Core kullanıyorsa, hizmet projenizin bir parçası olarak istemci NuGet paketleri oluşturma ve yayımlama, hizmetinizi paylaşma ve yükseltme konusunda iyi bir yöntem olabilir.

İstemci kitaplığı dağıtmanın avantajlarından biri, oluşturulan gRPC ve prototip sınıflarını faydalı "kullanışlı" yöntemlerle ve özellikleriyle geliştirebilmektir. İstemci kodunda, sunucusunda olduğu gibi, oluşturulan kodu düzenlemeden bunları genişletebilmeniz için tüm sınıfların `partial` olarak bildirildiği belirtilir. Bu, temel türlere oluşturucular, Yöntemler, hesaplanmış Özellikler ve daha fazlasını eklemenin kolay olması anlamına gelir.

> [!CAUTION]
> Önemli işlevselliği sağlamak için özel **kod kullanmamalısınız;** bunun anlamı, Işlevin, Python veya Java gibi diğer dilleri veya platformları kullanan ekipler için değil, paylaşılan kitaplığı kullanan .net ekipleri ile kısıtlandığı anlamına gelir.

Farklı takımların genellikle farklı programlama dilleri ve çerçeveleri kullanıldığı veya API 'nizin dışarıdan erişilebilen `.proto` çok platformlu bir ortamda, geliştiricilerin kendi istemcilerini oluşturabilmesi için en iyi yolu birçok ekibin gRPC hizmetinize erişebildiğinden emin olun.

## <a name="useful-extensions"></a>Kullanışlı uzantılar

.Net ' te nesne akışları ile ilgili olarak yaygın olarak kullanılan iki arabirim vardır: <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IObservable%601>. .NET Core 3,0 ve C# 8,0 ' den başlayarak, akışları zaman <xref:System.Collections.Generic.IAsyncEnumerable%601> uyumsuz olarak işlemeye yönelik bir arabirim ve arabirimi `await foreach` kullanmak için bir sözdizimi vardır. Bu bölümde, bu arabirimlerin gRPC akışlarına uygulanması için yeniden kullanılabilir kod sunulmaktadır.

.NET Core GRPC istemci kitaplıkları ile, `ReadAllAsync` `IAsyncStreamReader<T>` tarafından oluşturulan bir `IAsyncEnumerable<T>`genişletme yöntemi vardır. Reaktif programlama kullanan geliştiriciler için, oluşturmak `IObservable<T>` için eşdeğer bir genişletme yöntemi şöyle görünebilir.

### <a name="iobservable"></a>IObservable

Arabirim, "reaktif" `IEnumerable<T>`tersidir. `IObservable<T>` Bir akıştan öğe çekmek yerine, reaktif yaklaşım akışa akış gönderme öğeleri sağlar. Bu, GRPC akışlarına çok benzer ve bir `IObservable<T>` `IAsyncStreamReader<T>`etrafında sarmayı kolaylaştırır.

Bu kod `IAsyncEnumerable<T>` koddan daha uzundur, çünkü C# gözlemlenenler ile çalışmak için yerleşik desteği yoktur, bu nedenle uygulama sınıfının el ile oluşturulması gerekir. Bu, genel bir sınıftır, ancak tek bir uygulama tüm türler arasında çalışacaktır.

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
> Bu observable uygulamasının yalnızca bir kez `Subscribe` bir kez çağrılmasına izin verir. Bu, akıştan okumayı deneyen birden çok abone olması, Chaos ile sonuçlanacaktır. `Replay` [System. reak. LINQ](https://www.nuget.org/packages/System.Reactive.Linq) içinde, bu uygulamayla kullanılabilen gözlemlenenler 'in arabelleğe alma ve yinelenebilir paylaşımını etkinleştiren işleçler vardır.

`GrpcStreamSubscription` Sınıfı ,`IAsyncStreamReader`öğesinin sabit listesini işler.

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

`IAsyncEnumerable` Ve`IObservable` modelleri, .NET içinde zaman uyumsuz veri akışları ile ilgilenmenin iyi desteklendiğinden ve iyi belgelenmiş yollardır. gRPC, modern .NET Core Framework ve reaktif/zaman uyumsuz programlama stilleriyle, yakın tümleştirme sunan paradigmalarına ve her ikisine de eşleme sağlar.

>[!div class="step-by-step"]
>[Önceki](streaming-versus-repeated.md)
>[İleri](security.md)
