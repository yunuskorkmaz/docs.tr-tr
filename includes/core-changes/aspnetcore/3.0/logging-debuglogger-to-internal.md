---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393920"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="32911-101">Günlük: DebugLogger sınıfı dahili yaptı</span><span class="sxs-lookup"><span data-stu-id="32911-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="32911-102">Core 3.0ASP.NET önce, `DebugLogger`'erişim değiştirici `public`oldu.</span><span class="sxs-lookup"><span data-stu-id="32911-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="32911-103">ASP.NET Core 3.0'da erişim değiştirici `internal`.'</span><span class="sxs-lookup"><span data-stu-id="32911-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="32911-104">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="32911-104">Version introduced</span></span>

<span data-ttu-id="32911-105">3,0</span><span class="sxs-lookup"><span data-stu-id="32911-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="32911-106">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="32911-106">Reason for change</span></span>

<span data-ttu-id="32911-107">Değişiklik şu şekilde yapılmaktadır:</span><span class="sxs-lookup"><span data-stu-id="32911-107">The change is being made to:</span></span>

* <span data-ttu-id="32911-108">`ConsoleLogger`Diğer logger uygulamaları yla tutarlılığı zorlar.</span><span class="sxs-lookup"><span data-stu-id="32911-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="32911-109">API yüzeyini azaltın.</span><span class="sxs-lookup"><span data-stu-id="32911-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="32911-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="32911-110">Recommended action</span></span>

<span data-ttu-id="32911-111">Hata <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` ayıklama günlüğe kaydetmeyi etkinleştirmek için uzantı yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="32911-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="32911-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider>hizmetin `public` el ile kaydedilmesi gerektiğinde de devam etmektedir.</span><span class="sxs-lookup"><span data-stu-id="32911-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="32911-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="32911-113">Category</span></span>

<span data-ttu-id="32911-114">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="32911-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="32911-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="32911-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
