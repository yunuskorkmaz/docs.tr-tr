---
ms.openlocfilehash: 3244913e06a744dafc4440f824ebe6bed25b8dd1
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496299"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="b332c-101">WPF yazım denetleyicisi tarafından oluşturulan ObjectDisposedException</span><span class="sxs-lookup"><span data-stu-id="b332c-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

#### <a name="details"></a><span data-ttu-id="b332c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b332c-102">Details</span></span>

<span data-ttu-id="b332c-103">WPF uygulamaları <xref:System.ObjectDisposedException?displayProperty=fullName> , yazım denetleyicisi tarafından oluşturulan uygulama kapatılırken zaman zaman kilitleniyor.</span><span class="sxs-lookup"><span data-stu-id="b332c-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=fullName> thrown by the spellchecker.</span></span> <span data-ttu-id="b332c-104">Bu, özel durumu düzgün şekilde işleyerek ve bu nedenle uygulamaların artık etkilenmemesi sağlanarak .NET Framework 4,7 WPF 'de düzeltilir.</span><span class="sxs-lookup"><span data-stu-id="b332c-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="b332c-105">Bu, zaman bir hata ayıklayıcı altında çalışan uygulamalarda devam eden ilk şans özel durumların gözlemlendiği unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b332c-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b332c-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="b332c-106">Suggestion</span></span>

<span data-ttu-id="b332c-107">.NET Framework 4,7 ' ye yükseltin</span><span class="sxs-lookup"><span data-stu-id="b332c-107">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="b332c-108">Name</span><span class="sxs-lookup"><span data-stu-id="b332c-108">Name</span></span>    | <span data-ttu-id="b332c-109">Değer</span><span class="sxs-lookup"><span data-stu-id="b332c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b332c-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b332c-110">Scope</span></span>   |<span data-ttu-id="b332c-111">Edge</span><span class="sxs-lookup"><span data-stu-id="b332c-111">Edge</span></span>|
|<span data-ttu-id="b332c-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b332c-112">Version</span></span>|<span data-ttu-id="b332c-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="b332c-113">4.6.1</span></span>|
|<span data-ttu-id="b332c-114">Tür</span><span class="sxs-lookup"><span data-stu-id="b332c-114">Type</span></span>|<span data-ttu-id="b332c-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="b332c-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="b332c-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b332c-116">Affected APIs</span></span>

<span data-ttu-id="b332c-117">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="b332c-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
