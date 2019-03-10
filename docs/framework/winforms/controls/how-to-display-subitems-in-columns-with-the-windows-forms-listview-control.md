---
title: 'Nasıl yapılır: Windows Forms ListView denetimiyle sütunlardaki alt öğeleri görüntüleme'
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
ms.openlocfilehash: ecdb16087ff5788723b7d562cebd08551df87deb
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713078"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a><span data-ttu-id="7c06c-102">Nasıl yapılır: Windows Forms ListView denetimiyle sütunlardaki alt öğeleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="7c06c-102">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>
<span data-ttu-id="7c06c-103">Windows Forms <xref:System.Windows.Forms.ListView> denetim ek metin ya da Ayrıntılar görünümünde her öğenin alt öğelerini görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7c06c-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display additional text, or subitems, for each item in the Details view.</span></span> <span data-ttu-id="7c06c-104">İlk sütun öğesi metni, örneğin çalışan sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7c06c-104">The first column displays the item text, for example an employee number.</span></span> <span data-ttu-id="7c06c-105">İkinci, üçüncü ve sonraki sütunları görüntülemek birinci, ikinci ve sonraki ilişkili alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="7c06c-105">The second, third, and subsequent columns display the first, second, and subsequent associated subitems.</span></span>  
  
### <a name="to-add-subitems-to-a-list-item"></a><span data-ttu-id="7c06c-106">Liste öğesi alt öğesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="7c06c-106">To add subitems to a list item</span></span>  
  
1.  <span data-ttu-id="7c06c-107">Gerekli tüm sütunları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7c06c-107">Add any columns needed.</span></span> <span data-ttu-id="7c06c-108">İlk sütun öğenin görüntüleyeceği için <xref:System.Windows.Forms.ListView.Text%2A> özelliği, bir alt öğesi sayısından daha fazla sütun gerekir.</span><span class="sxs-lookup"><span data-stu-id="7c06c-108">Because the first column will display the item's <xref:System.Windows.Forms.ListView.Text%2A> property, you need one more column than there are subitems.</span></span> <span data-ttu-id="7c06c-109">Sütunlar ekleme ile ilgili daha fazla bilgi için bkz: [nasıl yapılır: Sütunları Windows Forms ListView denetiminde ekleme](how-to-add-columns-to-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7c06c-109">For more information on adding columns, see [How to: Add Columns to the Windows Forms ListView Control](how-to-add-columns-to-the-windows-forms-listview-control.md).</span></span>  
  
2.  <span data-ttu-id="7c06c-110">Çağrı <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> yöntemi tarafından döndürülen koleksiyon <xref:System.Windows.Forms.ListViewItem.SubItems%2A> öğenin özellik.</span><span class="sxs-lookup"><span data-stu-id="7c06c-110">Call the <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.ListViewItem.SubItems%2A> property of an item.</span></span> <span data-ttu-id="7c06c-111">Aşağıdaki kod örneği, bir liste öğesi için bölüm ve çalışan adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7c06c-111">The code example below sets the employee name and department for a list item.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="7c06c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c06c-112">See also</span></span>
- [<span data-ttu-id="7c06c-113">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7c06c-113">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="7c06c-114">Nasıl yapılır: Windows Forms ListView denetimi ile öğe ekleyip</span><span class="sxs-lookup"><span data-stu-id="7c06c-114">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="7c06c-115">Nasıl yapılır: Windows Forms ListView denetimine sütun ekleme</span><span class="sxs-lookup"><span data-stu-id="7c06c-115">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="7c06c-116">Nasıl yapılır: Windows Forms ListView denetimi için simgeler görüntüleme</span><span class="sxs-lookup"><span data-stu-id="7c06c-116">How to: Display Icons for the Windows Forms ListView Control</span></span>](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [<span data-ttu-id="7c06c-117">Nasıl yapılır: Bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme</span><span class="sxs-lookup"><span data-stu-id="7c06c-117">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
