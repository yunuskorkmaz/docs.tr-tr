---
ms.openlocfilehash: c9720f51e40ada4cd2cf6997ba7006a232893553
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702474"
---
### <a name="removed-status-bar-controls"></a><span data-ttu-id="38c85-101">Durum çubuğu denetimleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="38c85-101">Removed status bar controls</span></span>

<span data-ttu-id="38c85-102">.NET 5,0 Preview 1 ' den başlayarak bazı Windows Forms denetimleri artık kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="38c85-102">Starting in .NET 5.0 Preview 1, some Windows Forms controls are no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="38c85-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="38c85-103">Change description</span></span>

<span data-ttu-id="38c85-104">.NET 5,0 Preview 1 ' den itibaren, durum çubuğu ile ilgili Windows Forms denetimlerinin bazıları artık kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="38c85-104">Starting with .NET 5.0 Preview 1, some of the status bar-related Windows Forms controls are no longer available.</span></span> <span data-ttu-id="38c85-105">Daha iyi tasarım ve destek içeren değiştirme denetimleri .NET Framework 2,0 ' de sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="38c85-105">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="38c85-106">Kullanım dışı bırakılan denetimler daha önce Tasarımcı araç kutularından kaldırılmıştır ancak yine de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="38c85-106">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span> <span data-ttu-id="38c85-107">Şimdi tamamen kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="38c85-107">Now, they have been completely removed.</span></span>

<span data-ttu-id="38c85-108">Aşağıdaki türler artık kullanılamaz:</span><span class="sxs-lookup"><span data-stu-id="38c85-108">The following types are no longer available:</span></span>

* `StatusBar`
* `StatusBarDrawItemEventArgs`
* `StatusBarDrawItemEventHandler`
* `StatusBarPanel`
* `StatusBarPanelAutoSize`
* `StatusBarPanelBorderStyle`
* `StatusBarPanelClickEventArgs`
* `StatusBarPanelClickEventHandler`
* `StatusBarPanelStyle`

#### <a name="version-introduced"></a><span data-ttu-id="38c85-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="38c85-109">Version introduced</span></span>

<span data-ttu-id="38c85-110">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="38c85-110">5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="38c85-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="38c85-111">Recommended action</span></span>

<span data-ttu-id="38c85-112">Bu denetimler ve bunların senaryoları için değiştirme API 'Lerine geçin:</span><span class="sxs-lookup"><span data-stu-id="38c85-112">Move to the replacement APIs for these controls and their scenarios:</span></span>

| <span data-ttu-id="38c85-113">Eski denetim (API)</span><span class="sxs-lookup"><span data-stu-id="38c85-113">Old Control (API)</span></span> | <span data-ttu-id="38c85-114">Önerilen değiştirme</span><span class="sxs-lookup"><span data-stu-id="38c85-114">Recommended Replacement</span></span>                          |
|-------------------|--------------------------------------------------|
| <span data-ttu-id="38c85-115">StatusBar</span><span class="sxs-lookup"><span data-stu-id="38c85-115">StatusBar</span></span>         | <xref:System.Windows.Forms.StatusStrip>          |
| <span data-ttu-id="38c85-116">StatusBarPanel</span><span class="sxs-lookup"><span data-stu-id="38c85-116">StatusBarPanel</span></span>    | <xref:System.Windows.Forms.ToolStripStatusLabel> |

#### <a name="category"></a><span data-ttu-id="38c85-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="38c85-117">Category</span></span>

<span data-ttu-id="38c85-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="38c85-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="38c85-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="38c85-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.StatusBar?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanel?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelAutoSize?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelBorderStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelStyle?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:System.Windows.Forms.StatusBar`
- `T:System.Windows.Forms.StatusBarDrawItemEventArgs`
- `T:System.Windows.Forms.StatusBarDrawItemEventHandler`
- `T:System.Windows.Forms.StatusBarPanel`
- `T:System.Windows.Forms.StatusBarPanelAutoSize`
- `T:System.Windows.Forms.StatusBarPanelBorderStyle`
- `T:System.Windows.Forms.StatusBarPanelClickEventArgs`
- `T:System.Windows.Forms.StatusBarPanelClickEventHandler`
- `T:System.Windows.Forms.StatusBarPanelStyle` 

-->
