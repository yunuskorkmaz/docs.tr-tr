---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235879"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="06088-101">WinRT stream bağdaştırıcıları en uzun FlushAsync otomatik olarak Kapat üzerinde çağrı</span><span class="sxs-lookup"><span data-stu-id="06088-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

|   |   |
|---|---|
|<span data-ttu-id="06088-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="06088-102">Details</span></span>|<span data-ttu-id="06088-103">Windows Store uygulamalarında, Windows çalışma zamanı akış bağdaştırıcıları artık Dispose yönteminden FlushAsync yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="06088-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>|
|<span data-ttu-id="06088-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="06088-104">Suggestion</span></span>|<span data-ttu-id="06088-105">Bu değişiklik, saydam olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="06088-105">This change should be transparent.</span></span> <span data-ttu-id="06088-106">Geliştiriciler, şunun gibi kod yazarak önceki davranışı geri yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="06088-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|<span data-ttu-id="06088-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="06088-107">Scope</span></span>|<span data-ttu-id="06088-108">Geçirgen</span><span class="sxs-lookup"><span data-stu-id="06088-108">Transparent</span></span>|
|<span data-ttu-id="06088-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="06088-109">Version</span></span>|<span data-ttu-id="06088-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="06088-110">4.5.1</span></span>|
|<span data-ttu-id="06088-111">Tür</span><span class="sxs-lookup"><span data-stu-id="06088-111">Type</span></span>|<span data-ttu-id="06088-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="06088-112">Runtime</span></span>|
