---
ms.openlocfilehash: 2b4f35fe15f806897e5e4d85ee774b2e4572d974
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497163"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="2e856-101">WinRT akış bağdaştırıcıları otomatik olarak kapanmaz FlushAsync</span><span class="sxs-lookup"><span data-stu-id="2e856-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

#### <a name="details"></a><span data-ttu-id="2e856-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2e856-102">Details</span></span>

<span data-ttu-id="2e856-103">Windows Mağazası uygulamalarında Windows Çalışma Zamanı akış bağdaştırıcıları artık Dispose yönteminden FlushAsync yöntemini çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="2e856-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2e856-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="2e856-104">Suggestion</span></span>

<span data-ttu-id="2e856-105">Bu değişiklik saydam olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2e856-105">This change should be transparent.</span></span> <span data-ttu-id="2e856-106">Geliştiriciler aşağıdakine benzer bir kod yazarak önceki davranışı geri yükleyebilir:</span><span class="sxs-lookup"><span data-stu-id="2e856-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>

| <span data-ttu-id="2e856-107">Name</span><span class="sxs-lookup"><span data-stu-id="2e856-107">Name</span></span>    | <span data-ttu-id="2e856-108">Değer</span><span class="sxs-lookup"><span data-stu-id="2e856-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2e856-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="2e856-109">Scope</span></span>   |<span data-ttu-id="2e856-110">Geçirgen</span><span class="sxs-lookup"><span data-stu-id="2e856-110">Transparent</span></span>|
|<span data-ttu-id="2e856-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="2e856-111">Version</span></span>|<span data-ttu-id="2e856-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="2e856-112">4.5.1</span></span>|
|<span data-ttu-id="2e856-113">Tür</span><span class="sxs-lookup"><span data-stu-id="2e856-113">Type</span></span>|<span data-ttu-id="2e856-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="2e856-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="2e856-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2e856-115">Affected APIs</span></span>

<span data-ttu-id="2e856-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="2e856-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
