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
# <a name="create-grpc-client-libraries"></a>GRPC istemci kitaplıkları oluşturma

Bir gRPC uygulaması için istemci kitaplıklarını dağıtmak gerekli değildir. Kuruluşunuzda paylaşılan bir `.proto` dosyaları kitaplığı oluşturabilirsiniz ve diğer takımlar bu dosyaları kendi projelerinde istemci kodu oluşturmak için kullanabilir. Ancak özel bir NuGet deponuz varsa ve diğer birçok ekip .NET Core kullanıyorsa, hizmet projenizin bir parçası olarak istemci NuGet paketleri oluşturabilir ve yayımlayabilirsiniz. Bu, hizmetinizi paylaşmak ve yükseltmek için iyi bir yoldur.

İstemci kitaplığı dağıtmanın avantajlarından biri, oluşturulan gRPC ve prototip sınıflarını faydalı "kullanışlı" yöntemlerle ve özellikleriyle geliştirebilmektir. İstemci kodunda, sunucusunda olduğu gibi, tüm sınıfların `partial`olarak bildirildiği için, bunları oluşturulan kodu düzenlemeden genişletebilirsiniz. Bu, temel türlere oluşturucular, Yöntemler ve hesaplanmış özellikler eklemenin kolay olduğunu gösterir.

> [!CAUTION]
> Önemli işlevselliği sağlamak için özel kod kullanmamalısınız. Paylaşılan kitaplığı kullanan .NET ekipleriyle ilgili önemli işlevselliği kısıtlamak ve Python ya da Java gibi diğer dilleri veya platformları kullanan takımlara sağlamamak istemezsiniz.

Mümkün olduğunca fazla ekibin gRPC hizmetinize erişebildiğinden emin olun. Bunu yapmanın en iyi yolu, geliştiricilerin kendi istemcilerini oluşturabileceği şekilde `.proto` dosyaları paylaşmalıdır. Bu özellikle, farklı takımların farklı programlama dilleri ve çerçeveleri kullanması veya API 'nizin dışarıdan erişilebilir olduğu durumlarda çok platformlu bir ortamda geçerlidir.

## <a name="useful-extensions"></a>Kullanışlı uzantılar

.NET ' te nesne akışlarıyla uğraşmadan önce iki yaygın olarak kullanılan arabirim vardır: <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IObservable%601>. .NET Core 3,0 ve C# 8,0 ' den itibaren, akışları zaman uyumsuz olarak işlemeye yönelik bir <xref:System.Collections.Generic.IAsyncEnumerable%601> arabirimi ve arabirimi kullanmak için `await foreach` söz dizimi vardır. Bu bölümde, bu arabirimlerin gRPC akışlarına uygulanması için yeniden kullanılabilir kod sunulmaktadır.

.NET Core gRPC istemci kitaplıkları ile `IAsyncEnumerable<T>` arabirimi oluşturan `IAsyncStreamReader<T>` için `ReadAllAsync` bir genişletme yöntemi vardır. Reaktif programlama kullanan geliştiriciler için, bir `IObservable<T>` arabirimi oluşturmak için eşdeğer bir genişletme yöntemi aşağıdaki bölümdeki örneğe benzeyebilir.

### <a name="iobservable"></a>IObservable

`IObservable<T>` arabirimi, `IEnumerable<T>`"reaktif" tersidir. Bir akıştan öğe çekmek yerine, reaktif yaklaşım akışa akış gönderme öğeleri sağlar. Bu, gRPC akışlarına çok benzer ve bir `IObservable<T>` arabirimini `IAsyncStreamReader<T>` bir arabirim etrafında sarmalaması kolaydır.

Bu kod `IAsyncEnumerable<T>` koddan daha uzun olduğundan C# , gözlemlenenler ile çalışmaya yönelik yerleşik desteği yoktur. Uygulama sınıfını el ile oluşturmanız gerekir. Bu, genel bir sınıftır, ancak tek bir uygulama tüm türler arasında çalışacaktır.

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
> Bu observable uygulamasının `Subscribe` yönteminin yalnızca bir kez çağrılmasına izin verir, çünkü akıştan okumaya çalışan birden fazla abone olması, Chaos ile sonuçlanacaktır. [System. reak. LINQ](https://www.nuget.org/packages/System.Reactive.Linq)içinde `Replay` gibi işleçler vardır ve bu uygulamayla birlikte kullanılabilecek gözlemlenenler 'in arabelleğe alma ve yinelenebilir paylaşımını olanaklı hale getirebilirsiniz.

`GrpcStreamSubscription` sınıfı `IAsyncStreamReader`numaralandırmasını işler:

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

`IAsyncEnumerable` ve `IObservable` modelleri, .NET 'te zaman uyumsuz veri akışları ile ilgilenmenin iyi desteklendiğinden ve iyi belgelenmiş yollardır. gRPC, Map 'i hem paradigmalarına hem de .NET Core ile yakın tümleştirme sunan ve reaktif ve zaman uyumsuz programlama stilleriyle birlikte akışlar.

>[!div class="step-by-step"]
>[Önceki](streaming-versus-repeated.md)
>[İleri](security.md)
