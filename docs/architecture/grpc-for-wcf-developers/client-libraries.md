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
# <a name="create-grpc-client-libraries"></a>gRPC istemci kitaplıkları oluşturma

Bir gRPC uygulaması için istemci kitaplıkları dağıtmak gerekli değildir. Kuruluşunuz içinde paylaşılan `.proto` bir dosya kitaplığı oluşturabilirsiniz ve diğer ekipler bu dosyaları kendi projelerinde istemci kodu oluşturmak için kullanabilir. Ancak özel bir NuGet deponuz varsa ve diğer birçok takım .NET Core kullanıyorsa, hizmet projenizin bir parçası olarak istemci NuGet paketleri oluşturabilir ve yayımlayabilirsiniz. Bu, hizmetinizi paylaşmanın ve tanıtmanın iyi bir yolu olabilir.

İstemci kitaplığı dağıtmanın bir avantajı, oluşturulan gRPC ve Protobuf sınıflarını yararlı "kolaylık" yöntemleri ve özellikleriyle geliştirebilmektir. İstemci kodunda, sunucuda olduğu gibi, `partial`tüm sınıflar , oluşturulan kodu düzenlemeden genişletebilirsiniz olarak bildirilir. Bu, temel türlere oluşturucular, yöntemler ve hesaplanmış özellikler eklemenin kolay olduğu anlamına gelir.

> [!CAUTION]
> Temel işlevselliği sağlamak için özel kod kullanmamalısınız. Bu temel işlevselliği paylaşılan kitaplığı kullanan .NET ekipleriyle sınırlamak ve bunu Python veya Java gibi diğer dilleri veya platformları kullanan takımlara sağlamamak istemezsiniz.

Mümkün olduğunca çok takımın gRPC hizmetinize erişebilmesini sağlayın. Bunu yapmanın en iyi yolu, geliştiricilerin kendi istemcilerini oluşturabilmesi için dosyaları paylaşmaktır. `.proto` Bu, özellikle farklı ekiplerin sık sık farklı programlama dillerini ve çerçevelerini kullandığı veya API'nizin dışarıdan erişilebilir olduğu çok platformlu bir ortamda geçerlidir.

## <a name="useful-extensions"></a>Yararlı uzantılar

.NET'te nesnelerin akışlarıyla başa çıkmak için yaygın olarak <xref:System.Collections.Generic.IEnumerable%601> kullanılan <xref:System.IObservable%601>iki arabirim vardır: ve. .NET Core 3.0 ve C# 8.0 ile <xref:System.Collections.Generic.IAsyncEnumerable%601> başlayarak, akışları eşit bir şekilde `await foreach` işlemek için bir arabirim ve arabirimi kullanmak için bir sözdizimi vardır. Bu bölümde, bu arabirimleri gRPC akışlarına uygulamak için yeniden kullanılabilir kod lar bulunur.

.NET Core gRPC istemci kitaplıklarında, `ReadAllAsync` arabirim `IAsyncStreamReader<T>` oluşturan bir `IAsyncEnumerable<T>` uzantı yöntemi vardır. Reaktif programlama yı kullanan geliştiriciler için, arabirim oluşturmak için eşdeğer bir `IObservable<T>` uzantı yöntemi aşağıdaki bölümdeki örnek gibi görünebilir.

### <a name="iobservable"></a>ıobservable

Arabirim `IObservable<T>` "reaktif" ters `IEnumerable<T>`olduğunu. Öğeleri akıştan çekmek yerine, reaktif yaklaşım, akış öğelerini aboneye itmenizi sağlar. Bu, gRPC akışlarına çok benzer ve `IObservable<T>` `IAsyncStreamReader<T>` arabirimi bir arabirim etrafında kaydırmak kolaydır.

C# gözlemlenebilirlerle `IAsyncEnumerable<T>` çalışmak için yerleşik desteği olmadığından, bu kod koddan daha uzundur. Uygulama sınıfını el ile oluşturmanız gerekir. Bu genel bir sınıf olsa da, tek bir uygulama her türlü çalışır.

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
> Bu gözlemlenebilir uygulama, `Subscribe` birden çok abonenin akıştan okumaya çalışması kaosa yol açacağından, yöntemin yalnızca bir kez çağrılmasını sağlar. `Replay` [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq)gibi, bu uygulama ile kullanılabilir gözlemlenebilir, arabelleğe alma ve tekrarlanabilir paylaşımı sağlayan operatörler vardır.

Sınıf `GrpcStreamSubscription` numaralandırma `IAsyncStreamReader`işler:

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

Şimdi gerekli olan tek şey akış okuyucudan gözlemlenebilir oluşturmak için basit bir uzantı yöntemidir.

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

Ve `IAsyncEnumerable` `IObservable` modeller, .NET'teki eşzamanlı veri akışlarıyla başa çıkmanın hem iyi desteklenen hem de iyi belgelenmiş yollarıdır. gRPC akışları her iki paradigma için de harita, .NET Core ile yakın entegrasyon sunan ve reaktif ve asynchronous programlama stilleri.

>[!div class="step-by-step"]
>[Önceki](streaming-versus-repeated.md)
>[Sonraki](security.md)
