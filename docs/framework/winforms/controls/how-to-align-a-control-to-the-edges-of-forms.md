---
title: 'Nasıl yapılır: Bir denetimi formların kenarlarına hizalama'
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
ms.openlocfilehash: 33a3b2e996bdab280eb7a4cd8ad7c59ccb1a1bd2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713897"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a><span data-ttu-id="edfcd-102">Nasıl yapılır: Bir denetimi formların kenarlarına hizalama</span><span class="sxs-lookup"><span data-stu-id="edfcd-102">How to: Align a Control to the Edges of Forms</span></span>
<span data-ttu-id="edfcd-103">Denetiminiz ayarlayarak formlarınızı kenarına hizalama yapabileceğiniz <xref:System.Windows.Forms.Control.Dock%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="edfcd-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="edfcd-104">Bu özellik, denetimi forma bulunduğu belirler.</span><span class="sxs-lookup"><span data-stu-id="edfcd-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="edfcd-105"><xref:System.Windows.Forms.Control.Dock%2A> Özelliği aşağıdaki değerlere ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="edfcd-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="edfcd-106">Ayar</span><span class="sxs-lookup"><span data-stu-id="edfcd-106">Setting</span></span>|<span data-ttu-id="edfcd-107">Denetiminiz etkisi</span><span class="sxs-lookup"><span data-stu-id="edfcd-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="edfcd-108">Formun altına noktaları.</span><span class="sxs-lookup"><span data-stu-id="edfcd-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="edfcd-109">Formdaki tüm kalan alanı doldurur.</span><span class="sxs-lookup"><span data-stu-id="edfcd-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="edfcd-110">Formun sol tarafına noktaları.</span><span class="sxs-lookup"><span data-stu-id="edfcd-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="edfcd-111">Her yerden ve bunu görünür tarafından belirtilen konumda dock yoksa kendi <xref:System.Windows.Forms.Control.Location%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="edfcd-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="edfcd-112">Formun sağ tarafına noktaları.</span><span class="sxs-lookup"><span data-stu-id="edfcd-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="edfcd-113">Üst formun noktaları.</span><span class="sxs-lookup"><span data-stu-id="edfcd-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="edfcd-114">Visual Studio'da bu özellik için tasarım zamanı desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="edfcd-114">There is design-time support for this feature in Visual Studio.</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-run-time"></a><span data-ttu-id="edfcd-115">Çalışma zamanında denetiminizi Dock özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="edfcd-115">To set the Dock property for your control at run time</span></span>  
  
1.  <span data-ttu-id="edfcd-116">Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> kodunda uygun değere özelliği.</span><span class="sxs-lookup"><span data-stu-id="edfcd-116">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to the appropriate value in code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="edfcd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edfcd-117">See also</span></span>
- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="edfcd-118">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="edfcd-118">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="edfcd-119">Nasıl yapılır: Sabitleme ve FlowLayoutPanel denetiminde alt denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="edfcd-119">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="edfcd-120">Nasıl yapılır: Sabitleme ve TableLayoutPanel denetiminde alt denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="edfcd-120">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="edfcd-121">AutoSize Özelliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="edfcd-121">AutoSize Property Overview</span></span>](autosize-property-overview.md)
