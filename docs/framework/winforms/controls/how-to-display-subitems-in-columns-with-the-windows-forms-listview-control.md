---
title: "Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be1b055c8ea0e7a7c6466033735431a17ecc32f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a><span data-ttu-id="ccbd3-102">Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="ccbd3-102">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>
<span data-ttu-id="ccbd3-103">Windows Forms <xref:System.Windows.Forms.ListView> denetim ek metin ya da Ayrıntılar görünümünde her öğe için alt öğeler görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ccbd3-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display additional text, or subitems, for each item in the Details view.</span></span> <span data-ttu-id="ccbd3-104">İlk sütun öğesi metin, örneğin çalışan sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ccbd3-104">The first column displays the item text, for example an employee number.</span></span> <span data-ttu-id="ccbd3-105">İkinci, üçüncü ve sonraki sütunları görüntülemek birinci, ikinci ve sonraki ilişkili alt öğeler.</span><span class="sxs-lookup"><span data-stu-id="ccbd3-105">The second, third, and subsequent columns display the first, second, and subsequent associated subitems.</span></span>  
  
### <a name="to-add-subitems-to-a-list-item"></a><span data-ttu-id="ccbd3-106">Alt öğeler için bir liste öğesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="ccbd3-106">To add subitems to a list item</span></span>  
  
1.  <span data-ttu-id="ccbd3-107">Gerekli tüm sütunları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ccbd3-107">Add any columns needed.</span></span> <span data-ttu-id="ccbd3-108">İlk sütun öğesi'nin görüntüler olduğundan <xref:System.Windows.Forms.ListView.Text%2A> özelliği, bir alt öğesi sayısından daha fazla sütun gerekir.</span><span class="sxs-lookup"><span data-stu-id="ccbd3-108">Because the first column will display the item's <xref:System.Windows.Forms.ListView.Text%2A> property, you need one more column than there are subitems.</span></span> <span data-ttu-id="ccbd3-109">Sütunlar ekleme ile ilgili daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms ListView denetimine Sütun Ekle](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="ccbd3-109">For more information on adding columns, see [How to: Add Columns to the Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).</span></span>  
  
2.  <span data-ttu-id="ccbd3-110">Çağrı <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> yöntemi tarafından döndürülen koleksiyonunun <xref:System.Windows.Forms.ListViewItem.SubItems%2A> öğenin özellik.</span><span class="sxs-lookup"><span data-stu-id="ccbd3-110">Call the <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.ListViewItem.SubItems%2A> property of an item.</span></span> <span data-ttu-id="ccbd3-111">Aşağıdaki kod örneği, bir liste öğesi için bölüm ve çalışan adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ccbd3-111">The code example below sets the employee name and department for a list item.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="ccbd3-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ccbd3-112">See Also</span></span>  
 [<span data-ttu-id="ccbd3-113">ListView denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="ccbd3-113">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="ccbd3-114">Nasıl yapılır: ekleme ve kaldırma öğeleri Windows Forms ListView denetimi</span><span class="sxs-lookup"><span data-stu-id="ccbd3-114">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="ccbd3-115">Nasıl yapılır: sütunları Windows Forms ListView denetimine ekleme</span><span class="sxs-lookup"><span data-stu-id="ccbd3-115">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="ccbd3-116">Nasıl yapılır: Windows Forms ListView denetimi için simgeler görüntüleme</span><span class="sxs-lookup"><span data-stu-id="ccbd3-116">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="ccbd3-117">Nasıl yapılır: bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme</span><span class="sxs-lookup"><span data-stu-id="ccbd3-117">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
