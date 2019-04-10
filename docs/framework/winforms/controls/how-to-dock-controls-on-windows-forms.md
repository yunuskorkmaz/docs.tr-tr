---
title: "Nasıl yapılır: Windows Forms'a Denetimler Yerleştirme"
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: d015dce7307bec092f6da1dc5ee31691a6baf1f0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317265"
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="17ddc-102">Nasıl yapılır: Windows Forms'a Denetimler Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="17ddc-102">How to: Dock Controls on Windows Forms</span></span>
<span data-ttu-id="17ddc-103">Formunuza kenarlarına denetimleri yerleştirme veya onlara denetimin kapsayıcı (bir form veya bir kapsayıcı denetimi) doldurun.</span><span class="sxs-lookup"><span data-stu-id="17ddc-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="17ddc-104">Örneğin, Windows Gezgini noktaları kendi <xref:System.Windows.Forms.TreeView> pencerenin sol tarafındaki denetim ve kendi <xref:System.Windows.Forms.ListView> penceresinin sağ tarafındaki denetimi.</span><span class="sxs-lookup"><span data-stu-id="17ddc-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="17ddc-105">Kullanım <xref:System.Windows.Forms.Control.Dock%2A> yerleştirme modu tanımlamak, tüm görünür Windows Forms denetimleri için özellik.</span><span class="sxs-lookup"><span data-stu-id="17ddc-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17ddc-106">Denetimleri ters z düzeninde sabitlenir.</span><span class="sxs-lookup"><span data-stu-id="17ddc-106">Controls are docked in reverse z-order.</span></span>  
  
 <span data-ttu-id="17ddc-107"><xref:System.Windows.Forms.Control.Dock%2A> Özelliği etkileşim <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="17ddc-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="17ddc-108">Daha fazla bilgi için [AutoSize özelliğine genel bakış](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="17ddc-108">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>  
  
### <a name="to-dock-a-control"></a><span data-ttu-id="17ddc-109">Bir denetim sabitlemek için</span><span class="sxs-lookup"><span data-stu-id="17ddc-109">To dock a control</span></span>  
  
1. <span data-ttu-id="17ddc-110">Sabitlemek istediğiniz denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="17ddc-110">Select the control that you want to dock.</span></span>  
  
2. <span data-ttu-id="17ddc-111">Özellikler penceresinde sağındaki oku <xref:System.Windows.Forms.Control.Dock%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="17ddc-111">In the Properties window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="17ddc-112">Bir düzenleyici gösteren bir dizi kenarları ve form merkezini temsil eden kutu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="17ddc-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>  
  
3. <span data-ttu-id="17ddc-113">Edge denetim sabitlemek istediğiniz formun temsil eden düğmeye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="17ddc-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="17ddc-114">Denetimin form veya denetim kapsayıcı içeriğini doldurmak için merkezi kutusuna tıklayın.</span><span class="sxs-lookup"><span data-stu-id="17ddc-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="17ddc-115">Tıklayın **(hiçbiri)** yerleştirme devre dışı bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="17ddc-115">Click **(none)** to disable docking.</span></span>  
  
     <span data-ttu-id="17ddc-116">Denetim, yerleşik uç sınırlarına uyacak şekilde otomatik olarak boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="17ddc-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="17ddc-117">Devralınan denetimler olmalıdır `Protected` sabitlenebilir yapabilmek için.</span><span class="sxs-lookup"><span data-stu-id="17ddc-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="17ddc-118">Bir denetim erişim düzeyini değiştirmek için Ayarla kendi **değiştiricisi** Özellikler penceresindeki özellik.</span><span class="sxs-lookup"><span data-stu-id="17ddc-118">To change the access level of a control, set its **Modifier** property in the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17ddc-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17ddc-119">See also</span></span>

- [<span data-ttu-id="17ddc-120">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="17ddc-120">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="17ddc-121">Windows Formlarında Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="17ddc-121">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="17ddc-122">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="17ddc-122">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="17ddc-123">Windows Forms'ta Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="17ddc-123">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="17ddc-124">İşlevlere Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="17ddc-124">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- [<span data-ttu-id="17ddc-125">Nasıl yapılır: FlowLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="17ddc-125">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="17ddc-126">Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="17ddc-126">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="17ddc-127">AutoSize Özelliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="17ddc-127">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="17ddc-128">Nasıl yapılır: Windows Forms’da Denetimleri Bağlama</span><span class="sxs-lookup"><span data-stu-id="17ddc-128">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
