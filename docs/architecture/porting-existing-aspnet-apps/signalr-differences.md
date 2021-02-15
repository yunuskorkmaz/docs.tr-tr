---
title: ASP.NET SignalR ve ASP.NET Core SignalR karşılaştırması
description: ASP.NET Core SignalR nasıl öncülü, ASP.NET SignalR 'den farklıdır?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: f3605112da59fe7e014606aab170ea21aa892222
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488948"
---
# <a name="compare-aspnet-signalr-and-aspnet-core-signalr"></a><span data-ttu-id="4232c-103">ASP.NET SignalR ve ASP.NET Core SignalR karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="4232c-103">Compare ASP.NET SignalR and ASP.NET Core SignalR</span></span>

<span data-ttu-id="4232c-104">ASP.NET Core SignalR, ASP.NET SignalR kullanan istemcilerle veya sunucularla uyumsuzdur.</span><span class="sxs-lookup"><span data-stu-id="4232c-104">ASP.NET Core SignalR is incompatible with clients or servers using ASP.NET SignalR.</span></span> <span data-ttu-id="4232c-105">ASP.NET Core SignalR kullanmak için hem istemcileri hem de sunucuyu güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4232c-105">You'll need to update both clients and server to use ASP.NET Core SignalR.</span></span> <span data-ttu-id="4232c-106">Bu bölümde, tam liste [Belgeler](https://docs.microsoft.com/aspnet/core/signalr/version-differences)' de kullanılabilir olduğunda bazı farklılıklar açıklanmaktadır. ASP.NET Core SignalR, .NET Core 2,1 veya üstünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4232c-106">Some differences are described in this section, while the full list is available in the [docs](https://docs.microsoft.com/aspnet/core/signalr/version-differences). ASP.NET Core SignalR requires .NET Core 2.1 or greater.</span></span>

## <a name="feature-differences"></a><span data-ttu-id="4232c-107">Özellik farklılıkları</span><span class="sxs-lookup"><span data-stu-id="4232c-107">Feature differences</span></span>

- <span data-ttu-id="4232c-108">ASP.NET SignalR, bırakılan bağlantıları otomatik olarak yeniden bağlamaya çalışır; Bu davranış ASP.NET Core SignalR istemcileri için kabul edilir</span><span class="sxs-lookup"><span data-stu-id="4232c-108">ASP.NET SignalR automatically attempts to reconnect dropped connections; this behavior is opt-in for ASP.NET Core SignalR clients</span></span>
- <span data-ttu-id="4232c-109">Her iki çerçeve de JSON 'ı destekler; ASP.NET Core SignalR, MessagePack tabanlı bir ikili protokolü de destekler ve özel protokoller oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="4232c-109">Both frameworks support JSON; ASP.NET Core SignalR also supports a binary protocol based on MessagePack, and custom protocols can be created.</span></span>
- <span data-ttu-id="4232c-110">ASP.NET SignalR tarafından desteklenen süresiz çerçeve taşıması ASP.NET Core SignalR içinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="4232c-110">The Forever Frame transport, supported by ASP.NET SignalR, isn't supported in ASP.NET Core SignalR.</span></span>
- <span data-ttu-id="4232c-111">ASP.NET Core SignalR `services.AddSignalR()` `app.UseEndpoints` `Startup.ConfigureServices` , sırasıyla ve ile eklenerek yapılandırılmalıdır `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="4232c-111">ASP.NET Core SignalR must be configured by adding `services.AddSignalR()` and `app.UseEndpoints` in `Startup.ConfigureServices` and `Startup.Configure`, respectively.</span></span>
- <span data-ttu-id="4232c-112">ASP.NET Core SignalR, yapışkan oturumlar gerektirir; ASP.NET SignalR değil.</span><span class="sxs-lookup"><span data-stu-id="4232c-112">ASP.NET Core SignalR requires sticky sessions; ASP.NET SignalR doesn't.</span></span>
- <span data-ttu-id="4232c-113">ASP.NET Core bağlantı modelini basitleştirir; bağlantılar yalnızca tek bir hub 'a yapılır.</span><span class="sxs-lookup"><span data-stu-id="4232c-113">ASP.NET Core simplifies the connection model; connections are only made to a single hub.</span></span>
- <span data-ttu-id="4232c-114">ASP.NET Core SignalR, hub 'dan istemciye veri akışını destekler.</span><span class="sxs-lookup"><span data-stu-id="4232c-114">ASP.NET Core SignalR supports streaming data from the hub to the client.</span></span>
- <span data-ttu-id="4232c-115">ASP.NET Core SignalR, istemcilerle hub arasında durum geçirmeyi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4232c-115">ASP.NET Core SignalR doesn't support passing state between clients and the hub.</span></span>
- <span data-ttu-id="4232c-116">`PersistentConnection`Sınıf ASP.NET Core SignalR içinde yok.</span><span class="sxs-lookup"><span data-stu-id="4232c-116">The `PersistentConnection` class doesn't exist in ASP.NET Core SignalR.</span></span>
- <span data-ttu-id="4232c-117">ASP.NET SignalR SQL Server ve Redsıs 'yi destekler.</span><span class="sxs-lookup"><span data-stu-id="4232c-117">ASP.NET SignalR supports SQL Server and Redis.</span></span> <span data-ttu-id="4232c-118">ASP.NET Core SignalR, [Azure SignalR](https://docs.microsoft.com/azure/azure-signalr/) ve redsıs 'yi destekler.</span><span class="sxs-lookup"><span data-stu-id="4232c-118">ASP.NET Core SignalR supports [Azure SignalR](https://docs.microsoft.com/azure/azure-signalr/) and Redis.</span></span>

## <a name="references"></a><span data-ttu-id="4232c-119">Başvurular</span><span class="sxs-lookup"><span data-stu-id="4232c-119">References</span></span>

- [<span data-ttu-id="4232c-120">ASP.NET SignalR ile ASP.NET Core SignalR arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="4232c-120">Differences between ASP.NET SignalR and ASP.NET Core SignalR</span></span>](https://docs.microsoft.com/aspnet/core/signalr/version-differences)
- [<span data-ttu-id="4232c-121">Azure SignalR Hizmeti</span><span class="sxs-lookup"><span data-stu-id="4232c-121">Azure SignalR Service</span></span>](https://docs.microsoft.com/azure/azure-signalr/)

>[!div class="step-by-step"]
><span data-ttu-id="4232c-122">[Önceki](razor-differences.md) 
> [Sonraki](testing-differences.md)</span><span class="sxs-lookup"><span data-stu-id="4232c-122">[Previous](razor-differences.md)
[Next](testing-differences.md)</span></span>
