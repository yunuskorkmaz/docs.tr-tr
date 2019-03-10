---
title: 'Nasıl yapılır: Tasarım zamanında denetimi formların kenarlarına hizalama'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
ms.openlocfilehash: b81cb839664499d69710d81b7b0c8a479966d569
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724953"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a><span data-ttu-id="931e5-102">Nasıl yapılır: Tasarım zamanında denetimi formların kenarlarına hizalama</span><span class="sxs-lookup"><span data-stu-id="931e5-102">How to: Align a Control to the Edges of Forms at Design Time</span></span>
<span data-ttu-id="931e5-103">Denetiminiz ayarlayarak formlarınızı kenarına hizalama yapabileceğiniz <xref:System.Windows.Forms.Control.Dock%2A>.</span><span class="sxs-lookup"><span data-stu-id="931e5-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A>.</span></span> <span data-ttu-id="931e5-104">Bu özellik, denetimi forma bulunduğu belirler.</span><span class="sxs-lookup"><span data-stu-id="931e5-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="931e5-105"><xref:System.Windows.Forms.Control.Dock%2A> Özelliği aşağıdaki değerlere ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="931e5-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="931e5-106">Ayar</span><span class="sxs-lookup"><span data-stu-id="931e5-106">Setting</span></span>|<span data-ttu-id="931e5-107">Denetiminiz etkisi</span><span class="sxs-lookup"><span data-stu-id="931e5-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="931e5-108">Formun altına noktaları.</span><span class="sxs-lookup"><span data-stu-id="931e5-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="931e5-109">Formdaki tüm kalan alanı doldurur.</span><span class="sxs-lookup"><span data-stu-id="931e5-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="931e5-110">Formun sol tarafına noktaları.</span><span class="sxs-lookup"><span data-stu-id="931e5-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="931e5-111">Her yerden ve bunu görünür tarafından belirtilen konumda dock yoksa kendi <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="931e5-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A>.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="931e5-112">Formun sağ tarafına noktaları.</span><span class="sxs-lookup"><span data-stu-id="931e5-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="931e5-113">Üst formun noktaları.</span><span class="sxs-lookup"><span data-stu-id="931e5-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="931e5-114">Bu değerleri de kod içinde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="931e5-114">These values can also be set in code.</span></span> <span data-ttu-id="931e5-115">Daha fazla bilgi için [nasıl yapılır: Bir denetimi formların kenarlarına hizalama](how-to-align-a-control-to-the-edges-of-forms.md).</span><span class="sxs-lookup"><span data-stu-id="931e5-115">For more information, see [How to: Align a Control to the Edges of Forms](how-to-align-a-control-to-the-edges-of-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="931e5-116">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="931e5-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="931e5-117">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="931e5-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="931e5-118">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="931e5-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-design-time"></a><span data-ttu-id="931e5-119">Tasarım zamanında denetiminizi Dock özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="931e5-119">To set the Dock property for your control at design time</span></span>  
  
1.  <span data-ttu-id="931e5-120">Windows Form Tasarımcısı'nda denetiminizi seçin.</span><span class="sxs-lookup"><span data-stu-id="931e5-120">In the Windows Forms Designer, select your control.</span></span>  
  
2.  <span data-ttu-id="931e5-121">İçinde **özellikleri** penceresinde, aşağı açılan kutusunda sonraki tıklatın <xref:System.Windows.Forms.Control.Dock%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="931e5-121">In the **Properties** window, click the drop-down box next to the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="931e5-122">Altı olası temsil eden bir grafik arabirim <xref:System.Windows.Forms.Control.Dock%2A> ayarları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="931e5-122">A graphical interface representing the six possible <xref:System.Windows.Forms.Control.Dock%2A> settings is displayed.</span></span>  
  
3.  <span data-ttu-id="931e5-123">Uygun ayarı seçin.</span><span class="sxs-lookup"><span data-stu-id="931e5-123">Choose the appropriate setting.</span></span>  
  
4.  <span data-ttu-id="931e5-124">Denetiminiz artık ayarı tarafından belirlenen şekilde dock.</span><span class="sxs-lookup"><span data-stu-id="931e5-124">Your control will now dock in the manner specified by the setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="931e5-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="931e5-125">See also</span></span>
- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="931e5-126">Nasıl yapılır: Bir denetimi formların kenarlarına hizalama</span><span class="sxs-lookup"><span data-stu-id="931e5-126">How to: Align a Control to the Edges of Forms</span></span>](how-to-align-a-control-to-the-edges-of-forms.md)
- [<span data-ttu-id="931e5-127">İzlenecek yol: Dayama çizgileri kullanarak Windows Forms'da denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="931e5-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="931e5-128">Nasıl yapılır: Windows Forms'da denetimleri</span><span class="sxs-lookup"><span data-stu-id="931e5-128">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
- [<span data-ttu-id="931e5-129">Nasıl yapılır: Sabitleme ve TableLayoutPanel denetiminde alt denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="931e5-129">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="931e5-130">Nasıl yapılır: Sabitleme ve FlowLayoutPanel denetiminde alt denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="931e5-130">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="931e5-131">İzlenecek yol: TableLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="931e5-131">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="931e5-132">İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="931e5-132">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="931e5-133">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="931e5-133">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
