---
title: GRPC istemci kitaplıkları oluşturma-WCF geliştiricileri için gRPC
description: GRPC Hizmetleri için paylaşılan istemci kitaplıkları/paketleri tartışması.
ms.date: 01/06/2021
ms.openlocfilehash: dee62bc793ab384f2556f1b3ff2fcb856c040f3a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427576"
---
# <a name="create-grpc-client-libraries"></a>GRPC istemci kitaplıkları oluşturma

Bir gRPC uygulaması için istemci kitaplıklarını dağıtmak gerekli değildir. Kuruluşunuz dahilinde paylaşılan bir dosya kitaplığı oluşturabilirsiniz `.proto` ve diğer takımlar bu dosyaları kendi projelerinde istemci kodu oluşturmak için kullanabilir. Ancak özel bir NuGet deponuz varsa ve diğer birçok ekip .NET kullanıyorsa, hizmet projenizin bir parçası olarak istemci NuGet paketleri oluşturabilir ve yayımlayabilirsiniz. Bu yaklaşım, hizmetinizi paylaşmak ve yükseltmek için iyi bir yoldur.

İstemci kitaplığı dağıtmanın avantajlarından biri, oluşturulan gRPC ve prototip sınıflarını faydalı "kullanışlı" yöntemlerle ve özellikleriyle geliştirebilmektir. İstemci kodunda, sunucusunda olduğu gibi, tüm sınıfların olarak bildirildiği için, `partial` bunları oluşturulan kodu düzenlemeden genişletebilirsiniz. Bu davranış, temel türlere oluşturucular, Yöntemler ve hesaplanmış özellikler eklemenin kolay olduğunu gösterir.

> [!CAUTION]
> Önemli işlevselliği sağlamak için özel kod kullanmamalısınız. Paylaşılan kitaplığı kullanan .NET ekipleriyle ilgili önemli işlevselliği kısıtlamak ve Python ya da Java gibi diğer dilleri veya platformları kullanan takımlara sağlamamak istemezsiniz.

Mümkün olduğunca fazla ekibin gRPC hizmetinize erişebildiğinden emin olun. Bu işlevi yapmanın en iyi yolu, `.proto` geliştiricilerin kendi istemcilerini oluşturabileceği şekilde dosyaları paylaşmalıdır. Bu yaklaşım özellikle farklı takımların farklı programlama dilleri ve çerçeveleri kullanması veya API 'nizin dışarıdan erişilebilir olduğu çok platformlu bir ortamda geçerlidir.

## <a name="useful-extensions"></a>Kullanışlı uzantılar

.NET ' te nesne akışları ile ilgili olarak yaygın olarak kullanılan iki arabirim vardır: <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IObservable%601> . .NET Core 3,0 ve C# 8,0 ' den başlayarak, <xref:System.Collections.Generic.IAsyncEnumerable%601> akışları zaman uyumsuz olarak işlemek için bir arabirim ve `await foreach` arabirimi kullanmak için bir sözdizimi vardır. Bu bölümde, bu arabirimlerin gRPC akışlarına uygulanması için yeniden kullanılabilir kod sunulmaktadır.

.NET gRPC istemci kitaplıkları ile, `ReadAllAsync` bir arabirim oluşturan için bir genişletme yöntemi vardır `IAsyncStreamReader<T>` `IAsyncEnumerable<T>` . Reaktif programlama kullanan geliştiriciler için, bir arabirim oluşturmak için eşdeğer bir genişletme yöntemi `IObservable<T>` aşağıdaki bölümde örnek gibi görünebilir.

### <a name="iobservable"></a>IObservable

`IObservable<T>`Arabirim, "reaktif" tersidir `IEnumerable<T>` . Bir akıştan öğe çekmek yerine, reaktif yaklaşım akışa akış gönderme öğeleri sağlar. Bu davranış, gRPC akışlarına çok benzer ve bir arabirimi bir arabirim etrafında sarmayı kolaylaştırır `IObservable<T>` `IAsyncStreamReader<T>` .

`IAsyncEnumerable<T>`C#, gözlemlenenler ile çalışmaya yönelik yerleşik destek içermediğinden, bu kod koddan daha uzundur. Uygulama sınıfını el ile oluşturmanız gerekir. Bu, genel bir sınıftır, ancak tek bir uygulama tüm türler arasında çalışacaktır.

```csharp
using System;
using System.Threading;

namespace Grpc.Core
{
    public class GrpcStreamObservable<T> : IObservable<T>
    {
        private readonly IAsyncStreamReader<T> _reader;
        private readonly CancellationToken _token;
        private int _used;

        public GrpcStreamObservable(IAsyncStreamReader<T> reader, CancellationToken token = default)
        {
            _reader = reader ?? throw new ArgumentNullException(nameof(reader));
            _token = token;
            _used = 0;
        }

        public IDisposable Subscribe(IObserver<T> observer) =>
            Interlocked.Exchange(ref _used, 1) == 0
                ? new GrpcStreamSubscription<T>(_reader, observer, _token)
                : throw new InvalidOperationException("Subscribe can only be called once.");

    }
}
```

> [!IMPORTANT]
> Bu observable uygulamasının her `Subscribe` bir kez çağrılmasına izin verir, çünkü akıştan okumaya çalışan birden fazla abone olması, Chaos ile sonuçlanacaktır. `Replay` [System. reak. LINQ](https://www.nuget.org/packages/System.Reactive.Linq)gibi, bu uygulamayla kullanılabilen gözlemlenenler 'in arabelleğe alma ve yinelenebilir paylaşımını etkinleştiren işleçler vardır.

`GrpcStreamSubscription`Sınıfı, öğesinin sabit listesini işler `IAsyncStreamReader` :

```csharp
public class GrpcStreamSubscription<T> : IDisposable
{
    private readonly IAsyncStreamReader<T> _reader;
    private readonly IObserver<T> _observer;

    private readonly CancellationTokenSource _tokenSource;

    private readonly Task _task;

    private bool _completed;

    public GrpcStreamSubscription(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token = default)
    {
        _reader = reader ?? throw new ArgumentNullException(nameof(reader));
        _observer = observer ?? throw new ArgumentNullException(nameof(observer));

        _tokenSource = new CancellationTokenSource();
        token.Register(_tokenSource.Cancel);

        _task = Run(_tokenSource.Token);
    }

    private async Task Run(CancellationToken token)
    {
        while (!token.IsCancellationRequested)
        {
            try
            {
                if (!await _reader.MoveNext(token)) break;
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
                _observer.OnError(e);
                _completed = true;
                return;
            }

            _observer.OnNext(_reader.Current);
        }

        _completed = true;
        _observer.OnCompleted();
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
using System.Threading;

namespace Grpc.Core
{
    public static class AsyncStreamReaderObservableExtensions
    {
        public static IObservable<T> AsObservable<T>(
            this IAsyncStreamReader<T> reader,
            CancellationToken cancellationToken = default) =>
            new GrpcStreamObservable<T>(reader, cancellationToken);
    }
}
```

## <a name="summary"></a>Özet

<xref:System.Collections.Generic.IAsyncEnumerable%601>Ve <xref:System.IObservable%601> modelleri, .NET içinde zaman uyumsuz veri akışları ile ilgilenmenin iyi desteklendiğinden ve iyi belgelenmiş yollardır. gRPC, Map 'i hem paradigmalarına hem de .NET ile yakın tümleştirme sunan ve reaktif ve zaman uyumsuz programlama stilleriyle birlikte akışları.

>[!div class="step-by-step"]
>[Önceki](streaming-versus-repeated.md) 
> [Sonraki](security.md)
