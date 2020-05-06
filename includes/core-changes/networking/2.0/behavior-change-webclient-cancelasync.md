---
ms.openlocfilehash: 80d4bbbfe52ab9685d7ca54f21b80d4b1773da22
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859628"
---
### <a name="webclientcancelasync-doesnt-always-cancel-immediately"></a><span data-ttu-id="c3f68-101">WebClient. Iptallasync her zaman hemen iptal etmez</span><span class="sxs-lookup"><span data-stu-id="c3f68-101">WebClient.CancelAsync doesn't always cancel immediately</span></span>

<span data-ttu-id="c3f68-102">.NET Core 2,0 ' den başlayarak, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> çağrı yanıt getirilmeye başladıysa isteği hemen iptal etmez.</span><span class="sxs-lookup"><span data-stu-id="c3f68-102">Starting in .NET Core 2.0, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> doesn't cancel the request immediately if the response has started to fetch.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c3f68-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="c3f68-103">Change description</span></span>

<span data-ttu-id="c3f68-104">Daha önce, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> çağıran isteği hemen iptal etti.</span><span class="sxs-lookup"><span data-stu-id="c3f68-104">Previously, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> canceled the request immediately.</span></span> <span data-ttu-id="c3f68-105">.NET Core 2,0 ' den başlayarak, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> çağrı yalnızca yanıt getirmeyi başlatmamışsa isteği hemen iptal eder.</span><span class="sxs-lookup"><span data-stu-id="c3f68-105">Starting in .NET Core 2.0, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> cancels the request immediately only if the response hasn't started fetching.</span></span> <span data-ttu-id="c3f68-106">Yanıt getirilmeye başladıysa, istek yalnızca bir yanıt okunduktan sonra iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="c3f68-106">If the response has started to fetch, the request is cancelled only after a complete response is read.</span></span>

<span data-ttu-id="c3f68-107">Bu değişiklik, API 'nin <xref:System.Net.WebClient> <xref:System.Net.Http.HttpClient>kullanım dışı bırakıldığı için uygulandı.</span><span class="sxs-lookup"><span data-stu-id="c3f68-107">This change was implemented because the <xref:System.Net.WebClient> API is deprecated in favor of <xref:System.Net.Http.HttpClient>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c3f68-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c3f68-108">Version introduced</span></span>

<span data-ttu-id="c3f68-109">2,0</span><span class="sxs-lookup"><span data-stu-id="c3f68-109">2.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c3f68-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c3f68-110">Recommended action</span></span>

<span data-ttu-id="c3f68-111">Kullanım dışı <xref:System.Net.Http.HttpClient?displayProperty=fullName> olan yerine <xref:System.Net.WebClient?displayProperty=fullName>sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="c3f68-111">Use the <xref:System.Net.Http.HttpClient?displayProperty=fullName> class instead of <xref:System.Net.WebClient?displayProperty=fullName>, which is deprecated.</span></span>

#### <a name="category"></a><span data-ttu-id="c3f68-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="c3f68-112">Category</span></span>

<span data-ttu-id="c3f68-113">Ağ</span><span class="sxs-lookup"><span data-stu-id="c3f68-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c3f68-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c3f68-114">Affected APIs</span></span>

- <xref:System.Net.WebClient.CancelAsync?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Net.WebClient.CancelAsync`

-->
