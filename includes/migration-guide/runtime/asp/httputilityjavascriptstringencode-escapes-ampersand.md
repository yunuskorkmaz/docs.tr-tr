---
ms.openlocfilehash: 12fb72d5ee9fc0d6c57899589cb2b0da7db41f4a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497084"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="54a24-101">HttpUtility. JavaScriptStringEncode kaçış ve amperde</span><span class="sxs-lookup"><span data-stu-id="54a24-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

#### <a name="details"></a><span data-ttu-id="54a24-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="54a24-102">Details</span></span>

<span data-ttu-id="54a24-103">4,5 .NET Framework başlayarak, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> ve işareti ( &amp; ) karakteri çıkar.</span><span class="sxs-lookup"><span data-stu-id="54a24-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> escapes the ampersand (&amp;) character.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="54a24-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="54a24-104">Suggestion</span></span>

<span data-ttu-id="54a24-105">Uygulamanız bu yöntemin önceki davranışına bağımlıysa, yapılandırma dosyanızdaki [ASP.net appSettings öğesine](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) bir ASPNET: Javascriptdonotencodeamperu ayarı ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54a24-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>

| <span data-ttu-id="54a24-106">Name</span><span class="sxs-lookup"><span data-stu-id="54a24-106">Name</span></span>    | <span data-ttu-id="54a24-107">Değer</span><span class="sxs-lookup"><span data-stu-id="54a24-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="54a24-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="54a24-108">Scope</span></span>   |<span data-ttu-id="54a24-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="54a24-109">Minor</span></span>|
|<span data-ttu-id="54a24-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="54a24-110">Version</span></span>|<span data-ttu-id="54a24-111">4,5</span><span class="sxs-lookup"><span data-stu-id="54a24-111">4.5</span></span>|
|<span data-ttu-id="54a24-112">Tür</span><span class="sxs-lookup"><span data-stu-id="54a24-112">Type</span></span>|<span data-ttu-id="54a24-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="54a24-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="54a24-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="54a24-114">Affected APIs</span></span>

- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String)`
- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)`

-->
