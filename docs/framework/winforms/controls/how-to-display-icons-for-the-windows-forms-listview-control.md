---
title: ListView denetimi için simgeler görüntüleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], displaying icons
- icons [Windows Forms], displaying for ListView controls
- lists [Windows Forms], displaying icons
- ImageList component [Windows Forms], with ListView control
- list views [Windows Forms], displaying icons
ms.assetid: 9d577542-8595-429b-99e5-078770ec9d35
ms.openlocfilehash: 5fc54c448dae95cab50cdafa8403769fb421dffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744512"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a><span data-ttu-id="d0c1b-102">Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d0c1b-102">How to: Display Icons for the Windows Forms ListView Control</span></span>
<span data-ttu-id="d0c1b-103">Windows Forms <xref:System.Windows.Forms.ListView> denetimi üç görüntü listesinden simgeleri görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="d0c1b-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display icons from three image lists.</span></span> <span data-ttu-id="d0c1b-104">Liste, Ayrıntılar ve Smallıon görünümleri, <xref:System.Windows.Forms.ListView.SmallImageList%2A> özelliğinde belirtilen görüntü listesindeki görüntüleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d0c1b-104">The List, Details, and SmallIcon views display images from the image list specified in the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property.</span></span> <span data-ttu-id="d0c1b-105">LargeIcon görünümü, <xref:System.Windows.Forms.ListView.LargeImageList%2A> özelliğinde belirtilen görüntü listesindeki görüntüleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d0c1b-105">The LargeIcon view displays images from the image list specified in the <xref:System.Windows.Forms.ListView.LargeImageList%2A> property.</span></span> <span data-ttu-id="d0c1b-106">Liste görünümü, büyük veya küçük simgelerin yanında <xref:System.Windows.Forms.ListView.StateImageList%2A> özelliğinde ayarlanan ek bir simge kümesi de gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="d0c1b-106">A list view can also display an additional set of icons, set in the <xref:System.Windows.Forms.ListView.StateImageList%2A> property, next to the large or small icons.</span></span> <span data-ttu-id="d0c1b-107">Görüntü listeleri hakkında daha fazla bilgi için bkz. [ImageList bileşeni](imagelist-component-windows-forms.md) ve [nasıl yapılır: Windows Forms ImageList bileşeni ile görüntü ekleme veya kaldırma](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="d0c1b-107">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
### <a name="to-display-images-in-a-list-view"></a><span data-ttu-id="d0c1b-108">Resimleri bir liste görünümünde görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="d0c1b-108">To display images in a list view</span></span>  
  
1. <span data-ttu-id="d0c1b-109">Uygun özelliği (<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>veya <xref:System.Windows.Forms.ListView.StateImageList%2A>) kullanmak istediğiniz varolan <xref:System.Windows.Forms.ImageList> bileşenine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d0c1b-109">Set the appropriate property—<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, or <xref:System.Windows.Forms.ListView.StateImageList%2A>—to the existing <xref:System.Windows.Forms.ImageList> component you wish to use.</span></span>  
  
     <span data-ttu-id="d0c1b-110">Bu özellikler, Özellikler penceresi veya kod ile tasarımcıda ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d0c1b-110">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2. <span data-ttu-id="d0c1b-111">İlişkili simgesi olan her liste öğesi için <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> veya <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d0c1b-111">Set the <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> or <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> property for each list item that has an associated icon.</span></span>  
  
     <span data-ttu-id="d0c1b-112">Bu özellikler kod içinde veya **ListViewItem koleksiyon Düzenleyicisi**içinde ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d0c1b-112">These properties can be set in code, or within the **ListViewItem Collection Editor**.</span></span> <span data-ttu-id="d0c1b-113">**ListViewItem koleksiyon düzenleyicisini**açmak Için, **Özellikler** penceresindeki <xref:System.Windows.Forms.ListView.Items%2A> özelliğinin yanındaki üç nokta düğmesini (...) ve Visual Studio 'nun Özellikler penceresi![.](./media/visual-studio-ellipsis-button.png)) tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d0c1b-113">To open the **ListViewItem Collection Editor**, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ListView.Items%2A> property on the **Properties** window.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="d0c1b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0c1b-114">See also</span></span>

- [<span data-ttu-id="d0c1b-115">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d0c1b-115">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="d0c1b-116">Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="d0c1b-116">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="d0c1b-117">Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="d0c1b-117">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="d0c1b-118">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d0c1b-118">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="d0c1b-119">ImageList Bileşeni</span><span class="sxs-lookup"><span data-stu-id="d0c1b-119">ImageList Component</span></span>](imagelist-component-windows-forms.md)
