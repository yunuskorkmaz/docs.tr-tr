---
ms.openlocfilehash: b648aee35ff44730f545f0fa06f4e0a86615dece
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606771"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="b4e5b-101">HttpUtility. JavaScriptStringEncode kaçış ve amperde</span><span class="sxs-lookup"><span data-stu-id="b4e5b-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

#### <a name="details"></a><span data-ttu-id="b4e5b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b4e5b-102">Details</span></span>

<span data-ttu-id="b4e5b-103">4,5 .NET Framework başlayarak, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> ve işareti ( &amp; ) karakteri çıkar.</span><span class="sxs-lookup"><span data-stu-id="b4e5b-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> escapes the ampersand (&amp;) character.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b4e5b-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="b4e5b-104">Suggestion</span></span>

<span data-ttu-id="b4e5b-105">Uygulamanız bu yöntemin önceki davranışına bağımlıysa, yapılandırma dosyanızdaki [ASP.net appSettings öğesine](/previous-versions/aspnet/hh975440(v=vs.120)) bir ASPNET: Javascriptdonotencodeamperu ayarı ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4e5b-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>

| <span data-ttu-id="b4e5b-106">Name</span><span class="sxs-lookup"><span data-stu-id="b4e5b-106">Name</span></span>    | <span data-ttu-id="b4e5b-107">Değer</span><span class="sxs-lookup"><span data-stu-id="b4e5b-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b4e5b-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b4e5b-108">Scope</span></span>   |<span data-ttu-id="b4e5b-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="b4e5b-109">Minor</span></span>|
|<span data-ttu-id="b4e5b-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b4e5b-110">Version</span></span>|<span data-ttu-id="b4e5b-111">4,5</span><span class="sxs-lookup"><span data-stu-id="b4e5b-111">4.5</span></span>|
|<span data-ttu-id="b4e5b-112">Tür</span><span class="sxs-lookup"><span data-stu-id="b4e5b-112">Type</span></span>|<span data-ttu-id="b4e5b-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="b4e5b-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="b4e5b-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b4e5b-114">Affected APIs</span></span>

- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String)`
- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)`

-->
