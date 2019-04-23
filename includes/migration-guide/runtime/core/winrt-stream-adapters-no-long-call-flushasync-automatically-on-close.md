---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805323"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="a332c-101">WinRT stream bağdaştırıcıları en uzun FlushAsync otomatik olarak Kapat üzerinde çağrı</span><span class="sxs-lookup"><span data-stu-id="a332c-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a332c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a332c-102">Details</span></span>|<span data-ttu-id="a332c-103">Windows Store uygulamalarında, Windows çalışma zamanı akış bağdaştırıcıları artık Dispose yönteminden FlushAsync yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="a332c-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>|
|<span data-ttu-id="a332c-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="a332c-104">Suggestion</span></span>|<span data-ttu-id="a332c-105">Bu değişiklik, saydam olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a332c-105">This change should be transparent.</span></span> <span data-ttu-id="a332c-106">Geliştiriciler, şunun gibi kod yazarak önceki davranışı geri yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a332c-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|<span data-ttu-id="a332c-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="a332c-107">Scope</span></span>|<span data-ttu-id="a332c-108">Geçirgen</span><span class="sxs-lookup"><span data-stu-id="a332c-108">Transparent</span></span>|
|<span data-ttu-id="a332c-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a332c-109">Version</span></span>|<span data-ttu-id="a332c-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="a332c-110">4.5.1</span></span>|
|<span data-ttu-id="a332c-111">Tür</span><span class="sxs-lookup"><span data-stu-id="a332c-111">Type</span></span>|<span data-ttu-id="a332c-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="a332c-112">Runtime</span></span>|
