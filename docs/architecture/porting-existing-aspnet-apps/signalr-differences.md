---
title: ASP.NET SignalR ve ASP.NET Core SignalR karşılaştırması
description: ASP.NET Core SignalR nasıl öncülü, ASP.NET SignalR 'den farklıdır?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 89236bd0272c8f20cf9838dddefeb9afee1f3d93
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105785"
---
# <a name="compare-aspnet-signalr-and-aspnet-core-signalr"></a>ASP.NET SignalR ve ASP.NET Core SignalR karşılaştırması

ASP.NET Core SignalR, ASP.NET SignalR kullanan istemcilerle veya sunucularla uyumsuzdur. ASP.NET Core SignalR kullanmak için hem istemcileri hem de sunucuyu güncelleştirmeniz gerekir. Bu bölümde, tam liste [Belgeler](/aspnet/core/signalr/version-differences)' de kullanılabilir olduğunda bazı farklılıklar açıklanmaktadır. ASP.NET Core SignalR, .NET Core 2,1 veya üstünü gerektirir.

## <a name="feature-differences"></a>Özellik farklılıkları

- ASP.NET SignalR, bırakılan bağlantıları otomatik olarak yeniden bağlamaya çalışır; Bu davranış ASP.NET Core SignalR istemcileri için kabul edilir
- Her iki çerçeve de JSON 'ı destekler; ASP.NET Core SignalR, MessagePack tabanlı bir ikili protokolü de destekler ve özel protokoller oluşturulabilir.
- ASP.NET SignalR tarafından desteklenen süresiz çerçeve taşıması ASP.NET Core SignalR içinde desteklenmez.
- ASP.NET Core SignalR `services.AddSignalR()` `app.UseEndpoints` `Startup.ConfigureServices` , sırasıyla ve ile eklenerek yapılandırılmalıdır `Startup.Configure` .
- ASP.NET Core SignalR, yapışkan oturumlar gerektirir; ASP.NET SignalR değil.
- ASP.NET Core bağlantı modelini basitleştirir; bağlantılar yalnızca tek bir hub 'a yapılır.
- ASP.NET Core SignalR, hub 'dan istemciye veri akışını destekler.
- ASP.NET Core SignalR, istemcilerle hub arasında durum geçirmeyi desteklemez.
- `PersistentConnection`Sınıf ASP.NET Core SignalR içinde yok.
- ASP.NET SignalR SQL Server ve Redsıs 'yi destekler. ASP.NET Core SignalR, [Azure SignalR](/azure/azure-signalr/) ve redsıs 'yi destekler.

## <a name="references"></a>Başvurular

- [ASP.NET SignalR ile ASP.NET Core SignalR arasındaki farklar](/aspnet/core/signalr/version-differences)
- [Azure SignalR Hizmeti](/azure/azure-signalr/)

>[!div class="step-by-step"]
>[Önceki](razor-differences.md) 
> [Sonraki](testing-differences.md)
