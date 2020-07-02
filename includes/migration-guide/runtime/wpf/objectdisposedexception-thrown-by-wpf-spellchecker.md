---
ms.openlocfilehash: b836b26f3f52e9d0cc78feb764629bd2fa306657
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621835"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="450c7-101">WPF yazım denetleyicisi tarafından oluşturulan ObjectDisposedException</span><span class="sxs-lookup"><span data-stu-id="450c7-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

#### <a name="details"></a><span data-ttu-id="450c7-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="450c7-102">Details</span></span>

<span data-ttu-id="450c7-103">WPF uygulamaları <xref:System.ObjectDisposedException?displayProperty=fullName> , yazım denetleyicisi tarafından oluşturulan uygulama kapatılırken zaman zaman kilitleniyor.</span><span class="sxs-lookup"><span data-stu-id="450c7-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=fullName> thrown by the spellchecker.</span></span> <span data-ttu-id="450c7-104">Bu, özel durumu düzgün şekilde işleyerek ve bu nedenle uygulamaların artık etkilenmemesi sağlanarak .NET Framework 4,7 WPF 'de düzeltilir.</span><span class="sxs-lookup"><span data-stu-id="450c7-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="450c7-105">Bu, zaman bir hata ayıklayıcı altında çalışan uygulamalarda devam eden ilk şans özel durumların gözlemlendiği unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="450c7-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="450c7-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="450c7-106">Suggestion</span></span>

<span data-ttu-id="450c7-107">.NET Framework 4,7 ' ye yükseltin</span><span class="sxs-lookup"><span data-stu-id="450c7-107">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="450c7-108">Name</span><span class="sxs-lookup"><span data-stu-id="450c7-108">Name</span></span>    | <span data-ttu-id="450c7-109">Değer</span><span class="sxs-lookup"><span data-stu-id="450c7-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="450c7-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="450c7-110">Scope</span></span>   |<span data-ttu-id="450c7-111">Edge</span><span class="sxs-lookup"><span data-stu-id="450c7-111">Edge</span></span>|
|<span data-ttu-id="450c7-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="450c7-112">Version</span></span>|<span data-ttu-id="450c7-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="450c7-113">4.6.1</span></span>|
|<span data-ttu-id="450c7-114">Tür</span><span class="sxs-lookup"><span data-stu-id="450c7-114">Type</span></span>|<span data-ttu-id="450c7-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="450c7-115">Runtime</span></span>|
