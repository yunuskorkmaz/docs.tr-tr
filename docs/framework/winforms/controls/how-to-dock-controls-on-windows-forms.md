---
title: Denetimleri Yerleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 02f1c26dcb322a39c41781c83d8c820bd2fd27e0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745514"
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="36cc1-102">Nasıl yapılır: Windows Forms denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="36cc1-102">How to: Dock controls on Windows Forms</span></span>

<span data-ttu-id="36cc1-103">Denetimleri formunuzun kenarlarına yerleştirebilirsiniz veya denetimin kapsayıcısını (form veya kapsayıcı denetimi) doldurmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36cc1-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="36cc1-104">Örneğin, Windows Gezgini <xref:System.Windows.Forms.TreeView> denetimini pencerenin sol tarafına ve <xref:System.Windows.Forms.ListView> denetimini pencerenin sağ tarafına kadar denetler.</span><span class="sxs-lookup"><span data-stu-id="36cc1-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="36cc1-105">Yerleştirme modunu tanımlamak için tüm görünür Windows Forms denetimleri için <xref:System.Windows.Forms.Control.Dock%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="36cc1-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>

> [!NOTE]
> <span data-ttu-id="36cc1-106">Denetimler ters z düzeninde yerleşiktir.</span><span class="sxs-lookup"><span data-stu-id="36cc1-106">Controls are docked in reverse z-order.</span></span>

<span data-ttu-id="36cc1-107"><xref:System.Windows.Forms.Control.Dock%2A> özelliği <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği ile etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="36cc1-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="36cc1-108">Daha fazla bilgi için bkz. [AutoSize özelliğine genel bakış](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="36cc1-108">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>

## <a name="to-dock-a-control"></a><span data-ttu-id="36cc1-109">Bir denetimi sabitlemek için</span><span class="sxs-lookup"><span data-stu-id="36cc1-109">To dock a control</span></span>

1. <span data-ttu-id="36cc1-110">Visual Studio 'da, sabitlemek istediğiniz denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="36cc1-110">In Visual Studio, select the control that you want to dock.</span></span>

2. <span data-ttu-id="36cc1-111">**Özellikler** penceresinde <xref:System.Windows.Forms.Control.Dock%2A> özelliğinin sağ tarafındaki oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="36cc1-111">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>

   <span data-ttu-id="36cc1-112">Bir düzenleyici görüntülenir ve bu, formun kenarlarını ve merkezini temsil eden bir kutu dizisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="36cc1-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>

3. <span data-ttu-id="36cc1-113">Denetimin sabitlemek istediğiniz yerdeki formun kenarını temsil eden düğmeye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="36cc1-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="36cc1-114">Denetimin formunun veya kapsayıcı denetiminin içeriğini dolduracak Merkez kutusuna tıklayın.</span><span class="sxs-lookup"><span data-stu-id="36cc1-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="36cc1-115">Yerleştirmeyi devre dışı bırakmak için **(yok)** seçeneğine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="36cc1-115">Click **(none)** to disable docking.</span></span>

   <span data-ttu-id="36cc1-116">Denetim, yerleşik kenarın sınırlarına uyacak şekilde otomatik olarak yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="36cc1-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>

   > [!NOTE]
   > <span data-ttu-id="36cc1-117">Devralınan denetimlerin sabitlenebilir olması için `Protected` olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="36cc1-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="36cc1-118">Bir denetimin erişim düzeyini değiştirmek için, **Özellikler** penceresinde **değiştirici** özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="36cc1-118">To change the access level of a control, set its **Modifier** property in the **Properties** window.</span></span>

## <a name="see-also"></a><span data-ttu-id="36cc1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36cc1-119">See also</span></span>

- [<span data-ttu-id="36cc1-120">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="36cc1-120">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="36cc1-121">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="36cc1-121">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="36cc1-122">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="36cc1-122">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="36cc1-123">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="36cc1-123">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- [<span data-ttu-id="36cc1-124">Nasıl yapılır: FlowLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="36cc1-124">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="36cc1-125">Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="36cc1-125">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="36cc1-126">AutoSize Özelliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="36cc1-126">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="36cc1-127">Nasıl yapılır: Windows Forms’da Denetimleri Bağlama</span><span class="sxs-lookup"><span data-stu-id="36cc1-127">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
