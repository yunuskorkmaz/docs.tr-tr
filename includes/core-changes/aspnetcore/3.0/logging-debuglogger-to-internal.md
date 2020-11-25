---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032820"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="ec7c0-101">Günlüğe kaydetme: Debuggünlükçü sınıfı iç oluşturulmuş</span><span class="sxs-lookup"><span data-stu-id="ec7c0-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="ec7c0-102">ASP.NET Core 3,0 ' den önce `DebugLogger` erişim değiştiricisi idi `public` .</span><span class="sxs-lookup"><span data-stu-id="ec7c0-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="ec7c0-103">ASP.NET Core 3,0 ' de, erişim değiştiricisi olarak değiştirilmiştir `internal` .</span><span class="sxs-lookup"><span data-stu-id="ec7c0-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ec7c0-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="ec7c0-104">Version introduced</span></span>

<span data-ttu-id="ec7c0-105">3,0</span><span class="sxs-lookup"><span data-stu-id="ec7c0-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ec7c0-106">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="ec7c0-106">Reason for change</span></span>

<span data-ttu-id="ec7c0-107">Değişiklik şu şekilde yapılıyor:</span><span class="sxs-lookup"><span data-stu-id="ec7c0-107">The change is being made to:</span></span>

* <span data-ttu-id="ec7c0-108">Gibi diğer günlükçü uygulamalarıyla tutarlılığı zorunlu tutun `ConsoleLogger` .</span><span class="sxs-lookup"><span data-stu-id="ec7c0-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="ec7c0-109">API yüzeyini küçültün.</span><span class="sxs-lookup"><span data-stu-id="ec7c0-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ec7c0-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="ec7c0-110">Recommended action</span></span>

<span data-ttu-id="ec7c0-111"><xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` Hata ayıklama günlüğünü etkinleştirmek için genişletme yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec7c0-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="ec7c0-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> Ayrıca `public` hizmetin el ile kaydedilmesi gereken bir olaydır.</span><span class="sxs-lookup"><span data-stu-id="ec7c0-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="ec7c0-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="ec7c0-113">Category</span></span>

<span data-ttu-id="ec7c0-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ec7c0-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ec7c0-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ec7c0-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
