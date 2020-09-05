---
ms.openlocfilehash: 1487b5f47966cfcae0e47848dae99b39b42db18d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497318"
---
### <a name="keytips-behavior-improved-in-wpf"></a><span data-ttu-id="28292-101">WPF 'de geliştirilmiş KeyTips davranışı</span><span class="sxs-lookup"><span data-stu-id="28292-101">Keytips behavior improved in WPF</span></span>

#### <a name="details"></a><span data-ttu-id="28292-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="28292-102">Details</span></span>

<span data-ttu-id="28292-103">KeyTips davranışı, Microsoft Word ve Windows Gezgini 'ndeki davranışa eşlik eden şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="28292-103">Keytips behavior has been modified to bring parity with behavior on Microsoft Word and Windows Explorer.</span></span> <span data-ttu-id="28292-104">Anahtar ipucu durumunun etkin olup olmadığını kontrol ederek <xref:System.Windows.Input.KeyEventArgs.SystemKey> (özellikle <xref:System.Windows.Input.Key> veya <xref:System.Windows.Input.Key.F11> ) basıldığında, WPF KeyTip tuşlarını uygun şekilde işler.</span><span class="sxs-lookup"><span data-stu-id="28292-104">By checking whether keytip state is enabled or not in the case of a <xref:System.Windows.Input.KeyEventArgs.SystemKey> (in particular, <xref:System.Windows.Input.Key> or <xref:System.Windows.Input.Key.F11>) being pressed, WPF handles keytip keys appropriately.</span></span> <span data-ttu-id="28292-105">KeyTips artık fare tarafından açılsa bile menüyü kapatabilir.</span><span class="sxs-lookup"><span data-stu-id="28292-105">Keytips now dismiss a menu even when it is opened by mouse.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="28292-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="28292-106">Suggestion</span></span>

<span data-ttu-id="28292-107">YOK</span><span class="sxs-lookup"><span data-stu-id="28292-107">N/A</span></span>

| <span data-ttu-id="28292-108">Name</span><span class="sxs-lookup"><span data-stu-id="28292-108">Name</span></span>    | <span data-ttu-id="28292-109">Değer</span><span class="sxs-lookup"><span data-stu-id="28292-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="28292-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="28292-110">Scope</span></span>   |<span data-ttu-id="28292-111">Edge</span><span class="sxs-lookup"><span data-stu-id="28292-111">Edge</span></span>|
|<span data-ttu-id="28292-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="28292-112">Version</span></span>|<span data-ttu-id="28292-113">4.7.2</span><span class="sxs-lookup"><span data-stu-id="28292-113">4.7.2</span></span>|
|<span data-ttu-id="28292-114">Tür</span><span class="sxs-lookup"><span data-stu-id="28292-114">Type</span></span>|<span data-ttu-id="28292-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="28292-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="28292-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="28292-116">Affected APIs</span></span>

<span data-ttu-id="28292-117">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="28292-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
