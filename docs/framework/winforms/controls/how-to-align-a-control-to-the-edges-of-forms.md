---
title: 'Nasıl yapılır: Denetimi Formların Kenarlarına Hizalama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock property [Windows Forms], aligning controls (using code)
- forms [Windows Forms], aligning controls
- controls [Windows Forms], aligning on forms
- custom controls [Windows Forms], docking using code
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
ms.openlocfilehash: 5d662489b7e31f391bbd508409e69c091a25592c
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015940"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a><span data-ttu-id="96571-102">Nasıl yapılır: Denetimi Formların Kenarlarına Hizalama</span><span class="sxs-lookup"><span data-stu-id="96571-102">How to: Align a Control to the Edges of Forms</span></span>

<span data-ttu-id="96571-103"><xref:System.Windows.Forms.Control.Dock%2A> Özelliğini ayarlayarak denetiminizi formlarınızın kenarına hizalayın.</span><span class="sxs-lookup"><span data-stu-id="96571-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="96571-104">Bu özellik, denetiminizin formda nerede olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="96571-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="96571-105"><xref:System.Windows.Forms.Control.Dock%2A> Özelliği aşağıdaki değerlere ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="96571-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>

|<span data-ttu-id="96571-106">Ayar</span><span class="sxs-lookup"><span data-stu-id="96571-106">Setting</span></span>|<span data-ttu-id="96571-107">Denetiminizin etkisi</span><span class="sxs-lookup"><span data-stu-id="96571-107">Effect on your control</span></span>|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="96571-108">Formun altına noktaları.</span><span class="sxs-lookup"><span data-stu-id="96571-108">Docks to the bottom of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="96571-109">Formdaki kalan tüm alanı doldurur.</span><span class="sxs-lookup"><span data-stu-id="96571-109">Fills all remaining space in the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="96571-110">Formun sol tarafına noktaları.</span><span class="sxs-lookup"><span data-stu-id="96571-110">Docks to the left side of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="96571-111">Herhangi bir yere sabitlemez ve <xref:System.Windows.Forms.Control.Location%2A> özelliği tarafından belirtilen konumda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="96571-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="96571-112">Formun sağ tarafına noktaları.</span><span class="sxs-lookup"><span data-stu-id="96571-112">Docks to the right side of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="96571-113">Formun üst kısmına noktaları.</span><span class="sxs-lookup"><span data-stu-id="96571-113">Docks to the top of the form.</span></span>|

<span data-ttu-id="96571-114">Visual Studio 'da bu özellik için tasarım zamanı desteği vardır.</span><span class="sxs-lookup"><span data-stu-id="96571-114">There is design-time support for this feature in Visual Studio.</span></span>

## <a name="set-the-dock-property-for-your-control-at-run-time"></a><span data-ttu-id="96571-115">Çalışma zamanında denetiminizin Dock özelliğini ayarlayın</span><span class="sxs-lookup"><span data-stu-id="96571-115">Set the Dock property for your control at run time</span></span>

<span data-ttu-id="96571-116">Özelliği, <xref:System.Windows.Forms.Control.Dock%2A> koddaki uygun değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="96571-116">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to the appropriate value in code.</span></span>

```vb
' To set the Dock property internally.
Me.Dock = DockStyle.Top
' To set the Dock property from another object.
UserControl1.Dock = DockStyle.Top
```

```csharp
// To set the Dock property internally.
this.Dock = DockStyle.Top;
// To set the Dock property from another object.
UserControl1.Dock = DockStyle.Top;
```

## <a name="see-also"></a><span data-ttu-id="96571-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96571-117">See also</span></span>

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="96571-118">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="96571-118">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="96571-119">Nasıl yapılır: FlowLayoutPanel denetiminde alt denetimleri sabitleme ve yerleştirme</span><span class="sxs-lookup"><span data-stu-id="96571-119">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="96571-120">Nasıl yapılır: TableLayoutPanel denetiminde alt denetimleri sabitleme ve yerleştirme</span><span class="sxs-lookup"><span data-stu-id="96571-120">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="96571-121">AutoSize Özelliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="96571-121">AutoSize Property Overview</span></span>](autosize-property-overview.md)
