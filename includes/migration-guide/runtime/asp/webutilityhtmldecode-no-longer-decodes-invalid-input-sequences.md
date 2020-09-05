---
ms.openlocfilehash: ef3114a4eb9f62030c3ec36d3b463d07ccd59f6d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497126"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a><span data-ttu-id="a722d-101">WebUtility.HtmLşifre çözme artık geçersiz giriş sıralarının kodunu çözer</span><span class="sxs-lookup"><span data-stu-id="a722d-101">WebUtility.HtmlDecode no longer decodes invalid input sequences</span></span>

#### <a name="details"></a><span data-ttu-id="a722d-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a722d-102">Details</span></span>

<span data-ttu-id="a722d-103">Varsayılan olarak, kod çözme yöntemleri artık geçersiz bir girdi dizisini geçersiz bir UTF-16 dizisi halinde çözemez.</span><span class="sxs-lookup"><span data-stu-id="a722d-103">By default, decoding methods no longer decode an invalid input sequence into an invalid UTF-16 string.</span></span> <span data-ttu-id="a722d-104">Bunun yerine, özgün girişi geri döndürürler.</span><span class="sxs-lookup"><span data-stu-id="a722d-104">Instead, they return the original input.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a722d-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="a722d-105">Suggestion</span></span>

<span data-ttu-id="a722d-106">Kod çözücü çıktısındaki değişiklik yalnızca dizelerde UTF-16 verileri yerine ikili veriler saklıyorsanız önemli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a722d-106">The change in decoder output should matter only if you store binary data instead of UTF-16 data in strings.</span></span> <span data-ttu-id="a722d-107">Bu davranışı açıkça denetlemek için, <code>aspnet:AllowRelaxedUnicodeDecoding</code> [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) öğesinin özniteliğini, <code>true</code> eski davranışı etkinleştirmek veya <code>false</code> geçerli davranışı etkinleştirmek için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a722d-107">To explicitly control this behavior, set the <code>aspnet:AllowRelaxedUnicodeDecoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) element to <code>true</code> to enable legacy behavior or to <code>false</code> to enable the current behavior.</span></span>

| <span data-ttu-id="a722d-108">Name</span><span class="sxs-lookup"><span data-stu-id="a722d-108">Name</span></span>    | <span data-ttu-id="a722d-109">Değer</span><span class="sxs-lookup"><span data-stu-id="a722d-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a722d-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="a722d-110">Scope</span></span>   |<span data-ttu-id="a722d-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="a722d-111">Minor</span></span>|
|<span data-ttu-id="a722d-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a722d-112">Version</span></span>|<span data-ttu-id="a722d-113">4,5</span><span class="sxs-lookup"><span data-stu-id="a722d-113">4.5</span></span>|
|<span data-ttu-id="a722d-114">Tür</span><span class="sxs-lookup"><span data-stu-id="a722d-114">Type</span></span>|<span data-ttu-id="a722d-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="a722d-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a722d-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a722d-116">Affected APIs</span></span>

- <xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Net.WebUtility.HtmlDecode(System.String)`
- `M:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)`
- `M:System.Net.WebUtility.UrlDecode(System.String)`

-->
