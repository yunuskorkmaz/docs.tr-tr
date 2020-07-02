---
ms.openlocfilehash: d587e542a72d584502ac3ac892619cc38b88ef77
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620535"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="c509c-101">HttpUtility. JavaScriptStringEncode kaçış ve amperde</span><span class="sxs-lookup"><span data-stu-id="c509c-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

#### <a name="details"></a><span data-ttu-id="c509c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c509c-102">Details</span></span>

<span data-ttu-id="c509c-103">4,5 .NET Framework başlayarak, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> ve işareti ( &amp; ) karakteri çıkar.</span><span class="sxs-lookup"><span data-stu-id="c509c-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> escapes the ampersand (&amp;) character.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c509c-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="c509c-104">Suggestion</span></span>

<span data-ttu-id="c509c-105">Uygulamanız bu yöntemin önceki davranışına bağımlıysa, yapılandırma dosyanızdaki [ASP.net appSettings öğesine](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) bir ASPNET: Javascriptdonotencodeamperu ayarı ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c509c-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>

| <span data-ttu-id="c509c-106">Name</span><span class="sxs-lookup"><span data-stu-id="c509c-106">Name</span></span>    | <span data-ttu-id="c509c-107">Değer</span><span class="sxs-lookup"><span data-stu-id="c509c-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c509c-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c509c-108">Scope</span></span>   |<span data-ttu-id="c509c-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="c509c-109">Minor</span></span>|
|<span data-ttu-id="c509c-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c509c-110">Version</span></span>|<span data-ttu-id="c509c-111">4,5</span><span class="sxs-lookup"><span data-stu-id="c509c-111">4.5</span></span>|
|<span data-ttu-id="c509c-112">Tür</span><span class="sxs-lookup"><span data-stu-id="c509c-112">Type</span></span>|<span data-ttu-id="c509c-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="c509c-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c509c-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c509c-114">Affected APIs</span></span>

-<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
