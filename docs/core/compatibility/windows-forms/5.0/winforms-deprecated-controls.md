---
title: 'Son değişiklik: durum çubuğu denetimleri kaldırıldı'
description: Bazı Windows Forms denetimlerinin artık kullanılamadığı .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 07/18/2020
ms.openlocfilehash: 70aaa20f3fee1f4c342c4d9e547b0658aaf533b1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761609"
---
# <a name="removed-status-bar-controls"></a><span data-ttu-id="97f5d-103">Durum çubuğu denetimleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="97f5d-103">Removed status bar controls</span></span>

<span data-ttu-id="97f5d-104">.NET 5,0 ' den başlayarak bazı Windows Forms denetimleri artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="97f5d-104">Starting in .NET 5.0, some Windows Forms controls are no longer available.</span></span>

## <a name="change-description"></a><span data-ttu-id="97f5d-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="97f5d-105">Change description</span></span>

<span data-ttu-id="97f5d-106">.NET 5,0 ile başlayarak, durum çubuğu ile ilgili Windows Forms denetimlerinin bazıları artık kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="97f5d-106">Starting with .NET 5.0, some of the status bar-related Windows Forms controls are no longer available.</span></span> <span data-ttu-id="97f5d-107">Daha iyi tasarım ve destek içeren değiştirme denetimleri .NET Framework 2,0 ' de sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="97f5d-107">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="97f5d-108">Kullanım dışı bırakılan denetimler daha önce Tasarımcı araç kutularından kaldırılmıştır ancak yine de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97f5d-108">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span> <span data-ttu-id="97f5d-109">Şimdi tamamen kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="97f5d-109">Now, they have been completely removed.</span></span>

<span data-ttu-id="97f5d-110">Aşağıdaki türler artık kullanılamaz:</span><span class="sxs-lookup"><span data-stu-id="97f5d-110">The following types are no longer available:</span></span>

* `StatusBar`
* `StatusBarDrawItemEventArgs`
* `StatusBarDrawItemEventHandler`
* `StatusBarPanel`
* `StatusBarPanelAutoSize`
* `StatusBarPanelBorderStyle`
* `StatusBarPanelClickEventArgs`
* `StatusBarPanelClickEventHandler`
* `StatusBarPanelStyle`

## <a name="version-introduced"></a><span data-ttu-id="97f5d-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="97f5d-111">Version introduced</span></span>

<span data-ttu-id="97f5d-112">5.0</span><span class="sxs-lookup"><span data-stu-id="97f5d-112">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="97f5d-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="97f5d-113">Recommended action</span></span>

<span data-ttu-id="97f5d-114">Bu denetimler ve bunların senaryoları için değiştirme API 'Lerine geçin:</span><span class="sxs-lookup"><span data-stu-id="97f5d-114">Move to the replacement APIs for these controls and their scenarios:</span></span>

| <span data-ttu-id="97f5d-115">Eski denetim (API)</span><span class="sxs-lookup"><span data-stu-id="97f5d-115">Old Control (API)</span></span> | <span data-ttu-id="97f5d-116">Önerilen değiştirme</span><span class="sxs-lookup"><span data-stu-id="97f5d-116">Recommended Replacement</span></span>                          |
|-------------------|--------------------------------------------------|
| <span data-ttu-id="97f5d-117">StatusBar</span><span class="sxs-lookup"><span data-stu-id="97f5d-117">StatusBar</span></span>         | <xref:System.Windows.Forms.StatusStrip>          |
| <span data-ttu-id="97f5d-118">StatusBarPanel</span><span class="sxs-lookup"><span data-stu-id="97f5d-118">StatusBarPanel</span></span>    | <xref:System.Windows.Forms.ToolStripStatusLabel> |

## <a name="affected-apis"></a><span data-ttu-id="97f5d-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="97f5d-119">Affected APIs</span></span>

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

### Affected APIs

- `T:System.Windows.Forms.StatusBar`
- `T:System.Windows.Forms.StatusBarDrawItemEventArgs`
- `T:System.Windows.Forms.StatusBarDrawItemEventHandler`
- `T:System.Windows.Forms.StatusBarPanel`
- `T:System.Windows.Forms.StatusBarPanelAutoSize`
- `T:System.Windows.Forms.StatusBarPanelBorderStyle`
- `T:System.Windows.Forms.StatusBarPanelClickEventArgs`
- `T:System.Windows.Forms.StatusBarPanelClickEventHandler`
- `T:System.Windows.Forms.StatusBarPanelStyle`

### Category

Windows Forms

-->
