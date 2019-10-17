---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393920"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="05991-101">Günlüğe kaydetme: Debuggünlükçü sınıfı iç oluşturulmuş</span><span class="sxs-lookup"><span data-stu-id="05991-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="05991-102">ASP.NET Core 3,0 ' dan önce `DebugLogger` ' dan `public` ' e kadar olan erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="05991-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="05991-103">ASP.NET Core 3,0 ' de, erişim değiştiricisi `internal` olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="05991-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="05991-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="05991-104">Version introduced</span></span>

<span data-ttu-id="05991-105">3.0</span><span class="sxs-lookup"><span data-stu-id="05991-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="05991-106">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="05991-106">Reason for change</span></span>

<span data-ttu-id="05991-107">Değişiklik şu şekilde yapılıyor:</span><span class="sxs-lookup"><span data-stu-id="05991-107">The change is being made to:</span></span>

* <span data-ttu-id="05991-108">@No__t-0 gibi diğer günlükçü uygulamalarıyla tutarlılığı zorunlu tutun.</span><span class="sxs-lookup"><span data-stu-id="05991-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="05991-109">API yüzeyini küçültün.</span><span class="sxs-lookup"><span data-stu-id="05991-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="05991-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="05991-110">Recommended action</span></span>

<span data-ttu-id="05991-111">Hata ayıklama günlüğünü etkinleştirmek için <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` genişletme yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="05991-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="05991-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider>, hizmetin el ile kaydedilmesi gereken olayda hala `public` ' i de.</span><span class="sxs-lookup"><span data-stu-id="05991-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="05991-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="05991-113">Category</span></span>

<span data-ttu-id="05991-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="05991-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="05991-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="05991-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
