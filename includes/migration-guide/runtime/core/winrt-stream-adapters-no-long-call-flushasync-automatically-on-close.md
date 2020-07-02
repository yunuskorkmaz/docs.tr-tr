---
ms.openlocfilehash: 60937459b6f18e9abae87ad2dc97c3942325eedc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620597"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="84aaf-101">WinRT akış bağdaştırıcıları otomatik olarak kapanmaz FlushAsync</span><span class="sxs-lookup"><span data-stu-id="84aaf-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

#### <a name="details"></a><span data-ttu-id="84aaf-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="84aaf-102">Details</span></span>

<span data-ttu-id="84aaf-103">Windows Mağazası uygulamalarında Windows Çalışma Zamanı akış bağdaştırıcıları artık Dispose yönteminden FlushAsync yöntemini çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="84aaf-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="84aaf-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="84aaf-104">Suggestion</span></span>

<span data-ttu-id="84aaf-105">Bu değişiklik saydam olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="84aaf-105">This change should be transparent.</span></span> <span data-ttu-id="84aaf-106">Geliştiriciler aşağıdakine benzer bir kod yazarak önceki davranışı geri yükleyebilir:</span><span class="sxs-lookup"><span data-stu-id="84aaf-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>

| <span data-ttu-id="84aaf-107">Name</span><span class="sxs-lookup"><span data-stu-id="84aaf-107">Name</span></span>    | <span data-ttu-id="84aaf-108">Değer</span><span class="sxs-lookup"><span data-stu-id="84aaf-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="84aaf-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="84aaf-109">Scope</span></span>   |<span data-ttu-id="84aaf-110">Geçirgen</span><span class="sxs-lookup"><span data-stu-id="84aaf-110">Transparent</span></span>|
|<span data-ttu-id="84aaf-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="84aaf-111">Version</span></span>|<span data-ttu-id="84aaf-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="84aaf-112">4.5.1</span></span>|
|<span data-ttu-id="84aaf-113">Tür</span><span class="sxs-lookup"><span data-stu-id="84aaf-113">Type</span></span>|<span data-ttu-id="84aaf-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="84aaf-114">Runtime</span></span>|
