---
ms.openlocfilehash: 8cc2e1436059f92564d4c3ec534632674081ae75
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394458"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a>SignalR: HubConnectionContext oluşturucuları değişti

SignalR 'nin `HubConnectionContext` oluşturucuları, daha sonra düzeltme ekleme seçeneklerine daha fazla parametre yerine bir seçenek türü kabul edecek şekilde değiştirilmiştir. Bu değişiklik, iki Oluşturucuyu bir seçenek türü kabul eden tek bir Oluşturucu ile değiştirir.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

`HubConnectionContext` iki oluşturucuya sahiptir:

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a>Yeni davranış

İki Oluşturucu kaldırılmıştır ve bir Oluşturucu ile değiştirilmiştir:

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a>Değişiklik nedeni

Yeni Oluşturucu yeni bir seçenekler nesnesi kullanır. Sonuç olarak, `HubConnectionContext` ' ın özellikleri daha fazla Oluşturucu ve son değişiklikler yapılmadan gelecekte genişletilebilir.

#### <a name="recommended-action"></a>Önerilen eylem

Aşağıdaki oluşturucuyu kullanmak yerine:

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext, 
    keepAliveInterval: TimeSpan.FromSeconds(15), 
    loggerFactory, 
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

Aşağıdaki oluşturucuyu kullanın:

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
