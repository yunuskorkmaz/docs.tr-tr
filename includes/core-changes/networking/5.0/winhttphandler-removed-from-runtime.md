---
ms.openlocfilehash: 115cd6be935ae12a1293f948a0f899c6c3ff0d78
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608475"
---
### <a name="winhttphandler-removed-from-net-runtime"></a><span data-ttu-id="b1a4b-101">.NET çalışma zamanından WinHttpHandler kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="b1a4b-101">WinHttpHandler removed from .NET runtime</span></span>

<span data-ttu-id="b1a4b-102">`WinHttpHandler`Sınıf *System.Net.Http.dll* derlemesinden kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="b1a4b-102">The `WinHttpHandler` class was removed from the *System.Net.Http.dll* assembly.</span></span> <span data-ttu-id="b1a4b-103">Artık yalnızca bant dışı (OOB) [NuGet paketi](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b1a4b-103">It's now available only as an out-of-band (OOB) [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b1a4b-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b1a4b-104">Version introduced</span></span>

<span data-ttu-id="b1a4b-105">5.0</span><span class="sxs-lookup"><span data-stu-id="b1a4b-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="b1a4b-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="b1a4b-106">Change description</span></span>

<span data-ttu-id="b1a4b-107">Önceki .NET sürümlerinde, <xref:System.Net.Http.WinHttpHandler> sınıfı çekirdek .net kitaplıklarının bir parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b1a4b-107">In previous .NET versions, the <xref:System.Net.Http.WinHttpHandler> class is available as part of the core .NET libraries.</span></span> <span data-ttu-id="b1a4b-108">.NET 5,0 ' den başlayarak, <xref:System.Net.Http.WinHttpHandler> sınıfı yalnızca ayrı yüklenmiş bir [NuGet paketi](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b1a4b-108">Starting in .NET 5.0, the <xref:System.Net.Http.WinHttpHandler> class is only available as a separately installed [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b1a4b-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b1a4b-109">Recommended action</span></span>

<span data-ttu-id="b1a4b-110">[System .net. http. WinHttpHandler NuGet paketini](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)yükler.</span><span class="sxs-lookup"><span data-stu-id="b1a4b-110">Install the [System.Net.Http.WinHttpHandler NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span> <span data-ttu-id="b1a4b-111">Ya da, WinHTTP 'ye özgü özellikler gerekmiyorsa, <xref:System.Net.Http.SocketsHttpHandler> bunun yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="b1a4b-111">Or, if you don't require WinHTTP-specific features, use <xref:System.Net.Http.SocketsHttpHandler> instead.</span></span>

#### <a name="category"></a><span data-ttu-id="b1a4b-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="b1a4b-112">Category</span></span>

<span data-ttu-id="b1a4b-113">Ağ</span><span class="sxs-lookup"><span data-stu-id="b1a4b-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b1a4b-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b1a4b-114">Affected APIs</span></span>

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

-->
