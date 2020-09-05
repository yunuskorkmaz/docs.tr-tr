---
ms.openlocfilehash: e42bce91afab68e509cb35a8992fa3ca2f096872
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497743"
---
### <a name="wpf-printing-stack-update"></a><span data-ttu-id="50944-101">WPF yazdırma yığını güncelleştirmesi</span><span class="sxs-lookup"><span data-stu-id="50944-101">WPF Printing Stack Update</span></span>

#### <a name="details"></a><span data-ttu-id="50944-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="50944-102">Details</span></span>

<span data-ttu-id="50944-103">WPF 'nin yazdırma API 'Leri <xref:System.Printing.PrintQueue?displayProperty=fullName> Şu anda kullanım dışı olan XPS yazdırma API 'sini tercih eden Windows 'un yazdırma belgesi paketi API 'sini çağırır.</span><span class="sxs-lookup"><span data-stu-id="50944-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=fullName> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="50944-104">Değişiklik, akılda bakım yapılmıştı. Kullanıcı veya geliştiricilerin davranış veya API kullanımında hiçbir değişiklik görmemelidir.</span><span class="sxs-lookup"><span data-stu-id="50944-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="50944-105">Yeni yazdırma yığını, Windows 10 Creators Update 'te çalışırken varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="50944-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="50944-106">Eski yazdırma yığını, eski Windows sürümlerinde olduğu gibi çalışmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="50944-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="50944-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="50944-107">Suggestion</span></span>

<span data-ttu-id="50944-108">Windows 10 Creators Update 'te eski yığını kullanmak için <code>UseXpsOMPrinting</code> <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> kayıt defteri anahtarının REG_DWORD değerini olarak ayarlayın <code>1</code> .</span><span class="sxs-lookup"><span data-stu-id="50944-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>

| <span data-ttu-id="50944-109">Name</span><span class="sxs-lookup"><span data-stu-id="50944-109">Name</span></span>    | <span data-ttu-id="50944-110">Değer</span><span class="sxs-lookup"><span data-stu-id="50944-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="50944-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="50944-111">Scope</span></span>   |<span data-ttu-id="50944-112">Edge</span><span class="sxs-lookup"><span data-stu-id="50944-112">Edge</span></span>|
|<span data-ttu-id="50944-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="50944-113">Version</span></span>|<span data-ttu-id="50944-114">4,7</span><span class="sxs-lookup"><span data-stu-id="50944-114">4.7</span></span>|
|<span data-ttu-id="50944-115">Tür</span><span class="sxs-lookup"><span data-stu-id="50944-115">Type</span></span>|<span data-ttu-id="50944-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="50944-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="50944-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="50944-117">Affected APIs</span></span>

<span data-ttu-id="50944-118">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="50944-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
