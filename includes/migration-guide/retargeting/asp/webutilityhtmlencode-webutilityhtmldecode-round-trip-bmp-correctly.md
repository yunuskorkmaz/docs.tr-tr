---
ms.openlocfilehash: acb5b467fc8f0692d8fa1b3b8263fd27308cc124
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617261"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a><span data-ttu-id="f1e73-101">WebUtility.HtmlEncode ve WebUtility.HtmlDecode, BMP üzerinde doğru şekilde gidiş ve dönüş gerçekleştiriyor</span><span class="sxs-lookup"><span data-stu-id="f1e73-101">WebUtility.HtmlEncode and WebUtility.HtmlDecode round-trip BMP correctly</span></span>

#### <a name="details"></a><span data-ttu-id="f1e73-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f1e73-102">Details</span></span>

<span data-ttu-id="f1e73-103">.NET Framework 4.5’i hedefleyen uygulamalar için, Temel Çok Dilli Düzlem (BMP) dışındaki karakterler <xref:System.Net.WebUtility.HtmlDecode(System.String)> metotlarına geçirildiğinde, doğru bir şekilde gidiş ve dönüş yapar.</span><span class="sxs-lookup"><span data-stu-id="f1e73-103">For applications that target the .NET Framework 4.5, characters that are outside the Basic Multilingual Plane (BMP) round-trip correctly when they are passed to the <xref:System.Net.WebUtility.HtmlDecode(System.String)> methods.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f1e73-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="f1e73-104">Suggestion</span></span>

<span data-ttu-id="f1e73-105">Bu değişikliğin geçerli uygulamalar üzerinde hiçbir etkisi olmamalıdır, ancak özgün davranışı geri yüklemek için, `targetFramework` `<httpRuntime>` öğesinin özniteliğini "4,5" dışında bir dizeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f1e73-105">This change should have no effect on current applications, but to restore the original behavior, set the `targetFramework` attribute of the `<httpRuntime>` element to a string other than "4.5".</span></span> <span data-ttu-id="f1e73-106">Ayrıca bu davranışı, hedeflenen .NET Framework sürümünden bağımsız olarak denetlemek için `<webUtility>` yapılandırma öğesinin `unicodeEncodingConformance` ve `unicodeDecodingConformance` özniteliklerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1e73-106">You can also set the `unicodeEncodingConformance` and `unicodeDecodingConformance` attributes of the `<webUtility>` configuration element to control this behavior independently of the targeted version of the .NET Framework.</span></span>

| <span data-ttu-id="f1e73-107">Name</span><span class="sxs-lookup"><span data-stu-id="f1e73-107">Name</span></span>    | <span data-ttu-id="f1e73-108">Değer</span><span class="sxs-lookup"><span data-stu-id="f1e73-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f1e73-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="f1e73-109">Scope</span></span>   | <span data-ttu-id="f1e73-110">Edge</span><span class="sxs-lookup"><span data-stu-id="f1e73-110">Edge</span></span>        |
| <span data-ttu-id="f1e73-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f1e73-111">Version</span></span> | <span data-ttu-id="f1e73-112">4,5</span><span class="sxs-lookup"><span data-stu-id="f1e73-112">4.5</span></span>         |
| <span data-ttu-id="f1e73-113">Tür</span><span class="sxs-lookup"><span data-stu-id="f1e73-113">Type</span></span>    | <span data-ttu-id="f1e73-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="f1e73-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="f1e73-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f1e73-115">Affected APIs</span></span>

- <xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType>
