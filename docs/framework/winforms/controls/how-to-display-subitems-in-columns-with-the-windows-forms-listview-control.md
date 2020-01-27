---
title: ListView denetimiyle alt öğeleri sütunlarda görüntüleme
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
ms.openlocfilehash: 5c6d807410ad4ee0198d6334844bd65b148edff4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745551"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a><span data-ttu-id="a1479-102">Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a1479-102">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>
<span data-ttu-id="a1479-103">Windows Forms <xref:System.Windows.Forms.ListView> denetimi, Ayrıntılar görünümündeki her öğe için ek metin veya alt öğeleri görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a1479-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display additional text, or subitems, for each item in the Details view.</span></span> <span data-ttu-id="a1479-104">İlk sütunda öğe metni, örneğin bir çalışan numarası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a1479-104">The first column displays the item text, for example an employee number.</span></span> <span data-ttu-id="a1479-105">İkinci, üçüncü ve sonraki sütunlar birinci, ikinci ve sonraki ilişkili alt öğeleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a1479-105">The second, third, and subsequent columns display the first, second, and subsequent associated subitems.</span></span>  
  
### <a name="to-add-subitems-to-a-list-item"></a><span data-ttu-id="a1479-106">Bir liste öğesine alt öğeleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="a1479-106">To add subitems to a list item</span></span>  
  
1. <span data-ttu-id="a1479-107">Gereken sütunları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a1479-107">Add any columns needed.</span></span> <span data-ttu-id="a1479-108">İlk sütunda öğenin <xref:System.Windows.Forms.ListView.Text%2A> özelliği görüntülendiği için, alt öğeleri olan bir sütundan daha fazla olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1479-108">Because the first column will display the item's <xref:System.Windows.Forms.ListView.Text%2A> property, you need one more column than there are subitems.</span></span> <span data-ttu-id="a1479-109">Sütun ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: sütunları Windows Forms ListView denetimine ekleme](how-to-add-columns-to-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="a1479-109">For more information on adding columns, see [How to: Add Columns to the Windows Forms ListView Control](how-to-add-columns-to-the-windows-forms-listview-control.md).</span></span>  
  
2. <span data-ttu-id="a1479-110">Bir öğenin <xref:System.Windows.Forms.ListViewItem.SubItems%2A> özelliği tarafından döndürülen koleksiyonun <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="a1479-110">Call the <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.ListViewItem.SubItems%2A> property of an item.</span></span> <span data-ttu-id="a1479-111">Aşağıdaki kod örneği, bir liste öğesi için çalışan adı ve departmanı belirler.</span><span class="sxs-lookup"><span data-stu-id="a1479-111">The code example below sets the employee name and department for a list item.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="a1479-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1479-112">See also</span></span>

- [<span data-ttu-id="a1479-113">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a1479-113">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="a1479-114">Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="a1479-114">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="a1479-115">Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="a1479-115">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="a1479-116">Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a1479-116">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="a1479-117">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a1479-117">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
