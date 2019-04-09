---
title: 'Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme'
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
ms.openlocfilehash: e01035a356c0293959676cd5907d2234bbf79f16
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151391"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a><span data-ttu-id="1f9ac-102">Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1f9ac-102">How to: Display Icons for the Windows Forms ListView Control</span></span>
<span data-ttu-id="1f9ac-103">Windows Forms <xref:System.Windows.Forms.ListView> denetim, üç görüntü listeleri simgelerden görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f9ac-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display icons from three image lists.</span></span> <span data-ttu-id="1f9ac-104">Belirtilen görüntü listesinden görüntü listesi, Ayrıntılar ve SmallIcon görünümleri görüntüler <xref:System.Windows.Forms.ListView.SmallImageList%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1f9ac-104">The List, Details, and SmallIcon views display images from the image list specified in the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property.</span></span> <span data-ttu-id="1f9ac-105">Belirtilen görüntü listesinden görüntü LargeIcon görüntüleyen <xref:System.Windows.Forms.ListView.LargeImageList%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1f9ac-105">The LargeIcon view displays images from the image list specified in the <xref:System.Windows.Forms.ListView.LargeImageList%2A> property.</span></span> <span data-ttu-id="1f9ac-106">Bir liste görünümü de kümesinde simgeler, ek bir kümesini görüntüleyebilirsiniz <xref:System.Windows.Forms.ListView.StateImageList%2A> büyük veya küçük simgeleri yanındaki özelliği.</span><span class="sxs-lookup"><span data-stu-id="1f9ac-106">A list view can also display an additional set of icons, set in the <xref:System.Windows.Forms.ListView.StateImageList%2A> property, next to the large or small icons.</span></span> <span data-ttu-id="1f9ac-107">Görüntü listeleri hakkında daha fazla bilgi için bkz: [ImageList bileşeni](imagelist-component-windows-forms.md) ve [nasıl yapılır: Ekle veya Kaldır görüntülerle Windows Forms ImageList bileşeni](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="1f9ac-107">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
### <a name="to-display-images-in-a-list-view"></a><span data-ttu-id="1f9ac-108">Görüntüleri bir liste görünümünde görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="1f9ac-108">To display images in a list view</span></span>  
  
1.  <span data-ttu-id="1f9ac-109">Uygun özelliğini ayarlayın —<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, veya <xref:System.Windows.Forms.ListView.StateImageList%2A>— varolan <xref:System.Windows.Forms.ImageList> kullanmak istediğiniz bileşeni.</span><span class="sxs-lookup"><span data-stu-id="1f9ac-109">Set the appropriate property—<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, or <xref:System.Windows.Forms.ListView.StateImageList%2A>—to the existing <xref:System.Windows.Forms.ImageList> component you wish to use.</span></span>  
  
     <span data-ttu-id="1f9ac-110">Bu özellikleri Özellikler penceresi ile Tasarımcısı'nda veya kod içinde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f9ac-110">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2.  <span data-ttu-id="1f9ac-111">Ayarlama <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> veya <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> ilişkili bir simge içeren her bir liste öğesi için özelliği.</span><span class="sxs-lookup"><span data-stu-id="1f9ac-111">Set the <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> or <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> property for each list item that has an associated icon.</span></span>  
  
     <span data-ttu-id="1f9ac-112">Kod veya içinde bu özellikleri ayarlanabilir **ListViewItem Koleksiyonu Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="1f9ac-112">These properties can be set in code, or within the **ListViewItem Collection Editor**.</span></span> <span data-ttu-id="1f9ac-113">Açmak için **ListViewItem Koleksiyonu Düzenleyicisi**, üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki<xref:System.Windows.Forms.ListView.Items%2A>özellikte **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="1f9ac-113">To open the **ListViewItem Collection Editor**, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.ListView.Items%2A> property on the **Properties** window.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="1f9ac-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f9ac-114">See also</span></span>

- [<span data-ttu-id="1f9ac-115">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1f9ac-115">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="1f9ac-116">Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="1f9ac-116">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="1f9ac-117">Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="1f9ac-117">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="1f9ac-118">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1f9ac-118">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="1f9ac-119">ImageList Bileşeni</span><span class="sxs-lookup"><span data-stu-id="1f9ac-119">ImageList Component</span></span>](imagelist-component-windows-forms.md)
