---
title: 'Son değişiklik: WinHttpHandler .NET çalışma zamanından kaldırıldı'
description: .NET 5,0 ' de WinHttpHandler 'in .NET çalışma zamanından kaldırıldığı Son değişiklik hakkında bilgi edinin.
ms.date: 10/18/2020
ms.openlocfilehash: f8b9910ade8d459133791a23704d624a91cc5dff
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761434"
---
# <a name="winhttphandler-removed-from-net-runtime"></a><span data-ttu-id="ba8f6-103">.NET çalışma zamanından WinHttpHandler kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="ba8f6-103">WinHttpHandler removed from .NET runtime</span></span>

<span data-ttu-id="ba8f6-104">`WinHttpHandler`Sınıf *System.Net.Http.dll* derlemesinden kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="ba8f6-104">The `WinHttpHandler` class was removed from the *System.Net.Http.dll* assembly.</span></span> <span data-ttu-id="ba8f6-105">Artık yalnızca bant dışı (OOB) [NuGet paketi](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba8f6-105">It's now available only as an out-of-band (OOB) [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="ba8f6-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="ba8f6-106">Version introduced</span></span>

<span data-ttu-id="ba8f6-107">5.0</span><span class="sxs-lookup"><span data-stu-id="ba8f6-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="ba8f6-108">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="ba8f6-108">Change description</span></span>

<span data-ttu-id="ba8f6-109">Önceki .NET sürümlerinde, <xref:System.Net.Http.WinHttpHandler> sınıfı çekirdek .net kitaplıklarının bir parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba8f6-109">In previous .NET versions, the <xref:System.Net.Http.WinHttpHandler> class is available as part of the core .NET libraries.</span></span> <span data-ttu-id="ba8f6-110">.NET 5,0 ' den başlayarak, <xref:System.Net.Http.WinHttpHandler> sınıfı yalnızca ayrı yüklenmiş bir [NuGet paketi](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba8f6-110">Starting in .NET 5.0, the <xref:System.Net.Http.WinHttpHandler> class is only available as a separately installed [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ba8f6-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="ba8f6-111">Recommended action</span></span>

<span data-ttu-id="ba8f6-112">[System .net. http. WinHttpHandler NuGet paketini](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)yükler.</span><span class="sxs-lookup"><span data-stu-id="ba8f6-112">Install the [System.Net.Http.WinHttpHandler NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span> <span data-ttu-id="ba8f6-113">Ya da, WinHTTP 'ye özgü özellikler gerekmiyorsa, <xref:System.Net.Http.SocketsHttpHandler> bunun yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="ba8f6-113">Or, if you don't require WinHTTP-specific features, use <xref:System.Net.Http.SocketsHttpHandler> instead.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="ba8f6-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ba8f6-114">Affected APIs</span></span>

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

### Category

Networking

-->
