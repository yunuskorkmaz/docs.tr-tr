---
title: "Nasıl yapılır: Windows Forms'a Denetimler Yerleştirme"
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: dc514fd8b9b7a17bf07a878e42729db4187d2b82
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963622"
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="eed04-102">Nasıl yapılır: Windows Forms'a Denetimler Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="eed04-102">How to: Dock Controls on Windows Forms</span></span>
<span data-ttu-id="eed04-103">Denetimleri formunuzun kenarlarına yerleştirebilirsiniz veya denetimin kapsayıcısını (form veya kapsayıcı denetimi) doldurmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eed04-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="eed04-104">Örneğin, Windows Gezgini <xref:System.Windows.Forms.TreeView> , denetimini pencerenin sol tarafına <xref:System.Windows.Forms.ListView> ve denetimini pencerenin sağ tarafına göre denetler.</span><span class="sxs-lookup"><span data-stu-id="eed04-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="eed04-105">Yerleştirme modunu tanımlamak için tüm görünür Windows Forms denetimlerinin özelliğinikullanın.<xref:System.Windows.Forms.Control.Dock%2A></span><span class="sxs-lookup"><span data-stu-id="eed04-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eed04-106">Denetimler ters z düzeninde yerleşiktir.</span><span class="sxs-lookup"><span data-stu-id="eed04-106">Controls are docked in reverse z-order.</span></span>  
  
 <span data-ttu-id="eed04-107"><xref:System.Windows.Forms.Control.Dock%2A> Özelliği özelliği<xref:System.Windows.Forms.Control.AutoSize%2A> ile etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="eed04-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="eed04-108">Daha fazla bilgi için bkz. [AutoSize özelliğine genel bakış](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="eed04-108">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>  
  
### <a name="to-dock-a-control"></a><span data-ttu-id="eed04-109">Bir denetimi sabitlemek için</span><span class="sxs-lookup"><span data-stu-id="eed04-109">To dock a control</span></span>  
  
1. <span data-ttu-id="eed04-110">Sabitlemek istediğiniz denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="eed04-110">Select the control that you want to dock.</span></span>  
  
2. <span data-ttu-id="eed04-111">Özellikler penceresi, <xref:System.Windows.Forms.Control.Dock%2A> özelliğin sağ tarafındaki oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="eed04-111">In the Properties window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="eed04-112">Bir düzenleyici görüntülenir ve bu, formun kenarlarını ve merkezini temsil eden bir kutu dizisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eed04-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>  
  
3. <span data-ttu-id="eed04-113">Denetimin sabitlemek istediğiniz yerdeki formun kenarını temsil eden düğmeye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="eed04-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="eed04-114">Denetimin formunun veya kapsayıcı denetiminin içeriğini dolduracak Merkez kutusuna tıklayın.</span><span class="sxs-lookup"><span data-stu-id="eed04-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="eed04-115">Yerleştirmeyi devre dışı bırakmak için **(yok)** seçeneğine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="eed04-115">Click **(none)** to disable docking.</span></span>  
  
     <span data-ttu-id="eed04-116">Denetim, yerleşik kenarın sınırlarına uyacak şekilde otomatik olarak yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="eed04-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="eed04-117">Devralınan denetimlerin yerleştirilamayacak `Protected` olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="eed04-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="eed04-118">Bir denetimin erişim düzeyini değiştirmek için Özellikler penceresi **değiştirici** özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eed04-118">To change the access level of a control, set its **Modifier** property in the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed04-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eed04-119">See also</span></span>

- [<span data-ttu-id="eed04-120">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="eed04-120">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="eed04-121">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="eed04-121">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="eed04-122">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="eed04-122">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="eed04-123">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="eed04-123">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="eed04-124">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="eed04-124">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- [<span data-ttu-id="eed04-125">Nasıl yapılır: FlowLayoutPanel denetiminde alt denetimleri sabitleme ve yerleştirme</span><span class="sxs-lookup"><span data-stu-id="eed04-125">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="eed04-126">Nasıl yapılır: TableLayoutPanel denetiminde alt denetimleri sabitleme ve yerleştirme</span><span class="sxs-lookup"><span data-stu-id="eed04-126">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="eed04-127">AutoSize Özelliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="eed04-127">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="eed04-128">Nasıl yapılır: Windows Forms üzerinde geçiş denetimleri</span><span class="sxs-lookup"><span data-stu-id="eed04-128">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
