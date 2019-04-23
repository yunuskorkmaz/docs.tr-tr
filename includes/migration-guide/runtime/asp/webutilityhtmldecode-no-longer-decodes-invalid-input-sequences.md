---
ms.openlocfilehash: dfc1a0d05142861ff1c1b7391126d86e09fa71c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805329"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a><span data-ttu-id="30fc4-101">Geçersiz giriş dizilerini WebUtility.HtmlDecode artık kodunu çözer</span><span class="sxs-lookup"><span data-stu-id="30fc4-101">WebUtility.HtmlDecode no longer decodes invalid input sequences</span></span>

|   |   |
|---|---|
|<span data-ttu-id="30fc4-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="30fc4-102">Details</span></span>|<span data-ttu-id="30fc4-103">Varsayılan olarak, kod çözme yöntemleri artık geçersiz bir girdi dizisini geçersiz bir UTF-16 dizisi halinde çözemez.</span><span class="sxs-lookup"><span data-stu-id="30fc4-103">By default, decoding methods no longer decode an invalid input sequence into an invalid UTF-16 string.</span></span> <span data-ttu-id="30fc4-104">Bunun yerine, özgün girişi geri döndürürler.</span><span class="sxs-lookup"><span data-stu-id="30fc4-104">Instead, they return the original input.</span></span>|
|<span data-ttu-id="30fc4-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="30fc4-105">Suggestion</span></span>|<span data-ttu-id="30fc4-106">Kod çözücü çıktısındaki değişiklik yalnızca dizelerde UTF-16 verileri yerine ikili veriler saklıyorsanız önemli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="30fc4-106">The change in decoder output should matter only if you store binary data instead of UTF-16 data in strings.</span></span> <span data-ttu-id="30fc4-107">Bu davranışı açıkça denetlemek için ayarlanmış <code>aspnet:AllowRelaxedUnicodeDecoding</code> özniteliği [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) öğesine <code>true</code> eski davranışı etkinleştirmek için veya <code>false</code> geçerli davranışı etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="30fc4-107">To explicitly control this behavior, set the <code>aspnet:AllowRelaxedUnicodeDecoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) element to <code>true</code> to enable legacy behavior or to <code>false</code> to enable the current behavior.</span></span>|
|<span data-ttu-id="30fc4-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="30fc4-108">Scope</span></span>|<span data-ttu-id="30fc4-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="30fc4-109">Minor</span></span>|
|<span data-ttu-id="30fc4-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="30fc4-110">Version</span></span>|<span data-ttu-id="30fc4-111">4,5</span><span class="sxs-lookup"><span data-stu-id="30fc4-111">4.5</span></span>|
|<span data-ttu-id="30fc4-112">Tür</span><span class="sxs-lookup"><span data-stu-id="30fc4-112">Type</span></span>|<span data-ttu-id="30fc4-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="30fc4-113">Runtime</span></span>|
|<span data-ttu-id="30fc4-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="30fc4-114">Affected APIs</span></span>|<ul><li><xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|
