---
title: 'Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
ms.openlocfilehash: efee926301bc358bb7645ba67826f412c0d0dbbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532513"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a><span data-ttu-id="d462e-102">Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d462e-102">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>
<span data-ttu-id="d462e-103">Windows Forms <xref:System.Windows.Forms.ListView> denetim ek metin ya da Ayrıntılar görünümünde her öğe için alt öğeler görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="d462e-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display additional text, or subitems, for each item in the Details view.</span></span> <span data-ttu-id="d462e-104">İlk sütun öğesi metin, örneğin çalışan sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d462e-104">The first column displays the item text, for example an employee number.</span></span> <span data-ttu-id="d462e-105">İkinci, üçüncü ve sonraki sütunları görüntülemek birinci, ikinci ve sonraki ilişkili alt öğeler.</span><span class="sxs-lookup"><span data-stu-id="d462e-105">The second, third, and subsequent columns display the first, second, and subsequent associated subitems.</span></span>  
  
### <a name="to-add-subitems-to-a-list-item"></a><span data-ttu-id="d462e-106">Alt öğeler için bir liste öğesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="d462e-106">To add subitems to a list item</span></span>  
  
1.  <span data-ttu-id="d462e-107">Gerekli tüm sütunları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d462e-107">Add any columns needed.</span></span> <span data-ttu-id="d462e-108">İlk sütun öğesi'nin görüntüler olduğundan <xref:System.Windows.Forms.ListView.Text%2A> özelliği, bir alt öğesi sayısından daha fazla sütun gerekir.</span><span class="sxs-lookup"><span data-stu-id="d462e-108">Because the first column will display the item's <xref:System.Windows.Forms.ListView.Text%2A> property, you need one more column than there are subitems.</span></span> <span data-ttu-id="d462e-109">Sütunlar ekleme ile ilgili daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms ListView denetimine Sütun Ekle](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="d462e-109">For more information on adding columns, see [How to: Add Columns to the Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).</span></span>  
  
2.  <span data-ttu-id="d462e-110">Çağrı <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> yöntemi tarafından döndürülen koleksiyonunun <xref:System.Windows.Forms.ListViewItem.SubItems%2A> öğenin özellik.</span><span class="sxs-lookup"><span data-stu-id="d462e-110">Call the <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.ListViewItem.SubItems%2A> property of an item.</span></span> <span data-ttu-id="d462e-111">Aşağıdaki kod örneği, bir liste öğesi için bölüm ve çalışan adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d462e-111">The code example below sets the employee name and department for a list item.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="d462e-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d462e-112">See Also</span></span>  
 [<span data-ttu-id="d462e-113">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d462e-113">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="d462e-114">Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="d462e-114">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="d462e-115">Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="d462e-115">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="d462e-116">Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d462e-116">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="d462e-117">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d462e-117">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
