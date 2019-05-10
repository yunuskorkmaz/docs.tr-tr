---
title: 'Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
ms.openlocfilehash: b08e01eb9adb984a32a8fc435cf1f3b93b159a14
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210377"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a><span data-ttu-id="6928b-102">Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama</span><span class="sxs-lookup"><span data-stu-id="6928b-102">How to: Align a Control to the Edges of Forms at Design Time</span></span>

<span data-ttu-id="6928b-103">Denetiminiz değerini ayarlayarak formlarınızı kenarına hizalama yapabileceğiniz <xref:System.Windows.Forms.Control.Dock%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="6928b-103">You can make your control align to the edge of your forms by setting the value of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="6928b-104">Bu özellik, denetimi forma bulunduğu belirler.</span><span class="sxs-lookup"><span data-stu-id="6928b-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="6928b-105"><xref:System.Windows.Forms.Control.Dock%2A> Özelliği aşağıdaki değerlere ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="6928b-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>

|<span data-ttu-id="6928b-106">Ayar</span><span class="sxs-lookup"><span data-stu-id="6928b-106">Setting</span></span>|<span data-ttu-id="6928b-107">Denetiminiz etkisi</span><span class="sxs-lookup"><span data-stu-id="6928b-107">Effect on your control</span></span>|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="6928b-108">Formun altına noktaları.</span><span class="sxs-lookup"><span data-stu-id="6928b-108">Docks to the bottom of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="6928b-109">Formdaki tüm kalan alanı doldurur.</span><span class="sxs-lookup"><span data-stu-id="6928b-109">Fills all remaining space in the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="6928b-110">Formun sol tarafına noktaları.</span><span class="sxs-lookup"><span data-stu-id="6928b-110">Docks to the left side of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="6928b-111">Her yerden ve bunu görünür tarafından belirtilen konumda dock yoksa kendi <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="6928b-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A>.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="6928b-112">Formun sağ tarafına noktaları.</span><span class="sxs-lookup"><span data-stu-id="6928b-112">Docks to the right side of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="6928b-113">Üst formun noktaları.</span><span class="sxs-lookup"><span data-stu-id="6928b-113">Docks to the top of the form.</span></span>|

<span data-ttu-id="6928b-114">Bu değerleri de kod içinde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6928b-114">These values can also be set in code.</span></span> <span data-ttu-id="6928b-115">Daha fazla bilgi için [nasıl yapılır: Bir denetimi formların kenarlarına hizalama](how-to-align-a-control-to-the-edges-of-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6928b-115">For more information, see [How to: Align a Control to the Edges of Forms](how-to-align-a-control-to-the-edges-of-forms.md).</span></span>

## <a name="set-the-dock-property-for-your-control-at-design-time"></a><span data-ttu-id="6928b-116">Tasarım zamanında denetiminizi Dock özelliğini ayarlama</span><span class="sxs-lookup"><span data-stu-id="6928b-116">Set the Dock property for your control at design time</span></span>

1. <span data-ttu-id="6928b-117">Windows Form Tasarımcısı'nda Visual Studio'da denetiminizi seçin.</span><span class="sxs-lookup"><span data-stu-id="6928b-117">In the Windows Forms Designer in Visual Studio, select your control.</span></span>

2. <span data-ttu-id="6928b-118">İçinde **özellikleri** penceresinde, aşağı açılan kutusunda sonraki tıklatın <xref:System.Windows.Forms.Control.Dock%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="6928b-118">In the **Properties** window, click the drop-down box next to the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>

     <span data-ttu-id="6928b-119">Altı olası temsil eden bir grafik arabirim <xref:System.Windows.Forms.Control.Dock%2A> ayarları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6928b-119">A graphical interface representing the six possible <xref:System.Windows.Forms.Control.Dock%2A> settings is displayed.</span></span>

3. <span data-ttu-id="6928b-120">Uygun ayarı seçin.</span><span class="sxs-lookup"><span data-stu-id="6928b-120">Choose the appropriate setting.</span></span>

4. <span data-ttu-id="6928b-121">Denetiminiz artık ayarı tarafından belirlenen şekilde dock.</span><span class="sxs-lookup"><span data-stu-id="6928b-121">Your control will now dock in the manner specified by the setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="6928b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6928b-122">See also</span></span>

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6928b-123">Nasıl yapılır: Bir denetimi formların kenarlarına hizalama</span><span class="sxs-lookup"><span data-stu-id="6928b-123">How to: Align a Control to the Edges of Forms</span></span>](how-to-align-a-control-to-the-edges-of-forms.md)
- [<span data-ttu-id="6928b-124">İzlenecek yol: Dayama çizgileri kullanarak Windows Forms'da denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="6928b-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="6928b-125">Nasıl yapılır: Windows Forms'da denetimleri</span><span class="sxs-lookup"><span data-stu-id="6928b-125">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
- [<span data-ttu-id="6928b-126">Nasıl yapılır: Sabitleme ve TableLayoutPanel denetiminde alt denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="6928b-126">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="6928b-127">Nasıl yapılır: Sabitleme ve FlowLayoutPanel denetiminde alt denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="6928b-127">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="6928b-128">İzlenecek yol: TableLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="6928b-128">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="6928b-129">İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="6928b-129">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="6928b-130">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="6928b-130">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
