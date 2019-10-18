---
ms.openlocfilehash: 8979b7ffc09726c6588fe3ba60b916202697648f
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522708"
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
