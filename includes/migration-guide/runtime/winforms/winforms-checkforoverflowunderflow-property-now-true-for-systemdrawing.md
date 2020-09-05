---
ms.openlocfilehash: 68b0c4bb032b9744ef585eaef3d68e31afebee24
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496772"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="81d04-101">WinForm 'ın Checkforoverflowyetersizliği özelliği artık System. Drawing için doğru</span><span class="sxs-lookup"><span data-stu-id="81d04-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

#### <a name="details"></a><span data-ttu-id="81d04-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="81d04-102">Details</span></span>

<span data-ttu-id="81d04-103">System.Drawing.dll derlemesinin Checkforoverflowyetersizliği özelliği true olarak ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="81d04-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="81d04-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="81d04-104">Suggestion</span></span>

<span data-ttu-id="81d04-105">Daha önce taşmalar oluştuğunda, sonuç sessizce kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="81d04-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="81d04-106">Şimdi bir <xref:System.OverflowException?displayProperty=fullName> özel durum oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="81d04-106">Now an <xref:System.OverflowException?displayProperty=fullName> exception is thrown.</span></span>

| <span data-ttu-id="81d04-107">Name</span><span class="sxs-lookup"><span data-stu-id="81d04-107">Name</span></span>    | <span data-ttu-id="81d04-108">Değer</span><span class="sxs-lookup"><span data-stu-id="81d04-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="81d04-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="81d04-109">Scope</span></span>   |<span data-ttu-id="81d04-110">Edge</span><span class="sxs-lookup"><span data-stu-id="81d04-110">Edge</span></span>|
|<span data-ttu-id="81d04-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="81d04-111">Version</span></span>|<span data-ttu-id="81d04-112">4,5</span><span class="sxs-lookup"><span data-stu-id="81d04-112">4.5</span></span>|
|<span data-ttu-id="81d04-113">Tür</span><span class="sxs-lookup"><span data-stu-id="81d04-113">Type</span></span>|<span data-ttu-id="81d04-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="81d04-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="81d04-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="81d04-115">Affected APIs</span></span>

<span data-ttu-id="81d04-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="81d04-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
