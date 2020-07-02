---
ms.openlocfilehash: b521f4163bf5bf4a369d0eec12dae503703a976e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614643"
---
### <a name="throttle-concurrent-requests-per-session"></a><span data-ttu-id="14beb-101">Oturum başına eşzamanlı istekleri kısıtlama</span><span class="sxs-lookup"><span data-stu-id="14beb-101">Throttle concurrent requests per session</span></span>

#### <a name="details"></a><span data-ttu-id="14beb-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="14beb-102">Details</span></span>

<span data-ttu-id="14beb-103">.NET Framework 4.6.2 ve önceki sürümlerde, ASP.NET aynı SessionID ile istekleri sırayla yürütür ve ASP.NET her zaman varsayılan olarak tanımlama bilgileri aracılığıyla SessionID 'yi yayınlar.</span><span class="sxs-lookup"><span data-stu-id="14beb-103">In the .NET Framework 4.6.2 and earlier, ASP.NET executes requests with the same Sessionid sequentially, and ASP.NET always issues the Sessionid through cookies by default.</span></span> <span data-ttu-id="14beb-104">Bir sayfanın yanıt vermesi uzun sürerse, tarayıcıda <kbd>F5</kbd> tuşuna basarak sunucu performansını önemli ölçüde düşürür.</span><span class="sxs-lookup"><span data-stu-id="14beb-104">If a page takes a long time to respond, it will significantly degrade server performance just by pressing <kbd>F5</kbd> on the browser.</span></span> <span data-ttu-id="14beb-105">Bu durumda, sıradaki istekleri izlemek için bir sayaç ekledik ve belirtilen sınırı aştığında istekleri sonlandıracağız.</span><span class="sxs-lookup"><span data-stu-id="14beb-105">In the fix, we added a counter to track the queued requests and terminate the requests when they exceed a specified limit.</span></span> <span data-ttu-id="14beb-106">Varsayılan değer 50 ' dir.</span><span class="sxs-lookup"><span data-stu-id="14beb-106">The default value is 50.</span></span> <span data-ttu-id="14beb-107">Sınıra ulaşılırsa, olay günlüğüne bir uyarı kaydedilir ve IIS günlüğüne bir HTTP 500 yanıtı kaydedilebilir.</span><span class="sxs-lookup"><span data-stu-id="14beb-107">If the limit is reached, a warning will be logged in the event log, and an HTTP 500 response may be recorded in the IIS log.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="14beb-108">Öneri</span><span class="sxs-lookup"><span data-stu-id="14beb-108">Suggestion</span></span>

<span data-ttu-id="14beb-109">Eski davranışı geri yüklemek için, yeni davranışı devre dışı bırakmak üzere web.config dosyanıza aşağıdaki ayarı ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14beb-109">To restore the old behavior, you can add the following setting to your web.config file to opt out of the new behavior.</span></span>

```xml
<appSettings>
    <add key="aspnet:RequestQueueLimitPerSession" value="2147483647"/>
</appSettings>
```

| <span data-ttu-id="14beb-110">Name</span><span class="sxs-lookup"><span data-stu-id="14beb-110">Name</span></span>    | <span data-ttu-id="14beb-111">Değer</span><span class="sxs-lookup"><span data-stu-id="14beb-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="14beb-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="14beb-112">Scope</span></span>   | <span data-ttu-id="14beb-113">Edge</span><span class="sxs-lookup"><span data-stu-id="14beb-113">Edge</span></span>        |
| <span data-ttu-id="14beb-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="14beb-114">Version</span></span> | <span data-ttu-id="14beb-115">4,7</span><span class="sxs-lookup"><span data-stu-id="14beb-115">4.7</span></span>         |
| <span data-ttu-id="14beb-116">Tür</span><span class="sxs-lookup"><span data-stu-id="14beb-116">Type</span></span>    | <span data-ttu-id="14beb-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="14beb-117">Retargeting</span></span> |
