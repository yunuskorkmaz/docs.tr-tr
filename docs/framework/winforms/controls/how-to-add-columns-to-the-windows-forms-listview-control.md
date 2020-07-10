---
title: ListView Denetimine sütun ekleme
description: Her liste öğesi hakkında çeşitli bilgi türlerini göstermek için Windows Forms ListView denetimine nasıl sütun ekleneceğini öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: 7ca4e86ca3a9679876f2525c49596534f175096a
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174568"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a><span data-ttu-id="04ea7-103">Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="04ea7-103">How to: Add Columns to the Windows Forms ListView Control</span></span>
<span data-ttu-id="04ea7-104">Ayrıntılar görünümünde, <xref:System.Windows.Forms.ListView> Denetim her liste öğesi için birden çok sütun görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="04ea7-104">In the Details view, the <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item.</span></span> <span data-ttu-id="04ea7-105">Sütunları, her liste öğesiyle ilgili birkaç tür bilgiyi kullanıcıya göstermek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04ea7-105">You can use the columns to display to the user several types of information about each list item.</span></span> <span data-ttu-id="04ea7-106">Örneğin bir dosya listesi, dosyanın son değiştirilme dosya adını, dosya türünü, boyutunu ve tarihini görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="04ea7-106">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="04ea7-107">Sütunları oluşturulduktan sonra doldurma hakkında daha fazla bilgi için bkz. [nasıl yapılır: alt öğeleri Windows Forms ListView denetimiyle sütunlarda görüntüleme](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="04ea7-107">For information about populating the columns after they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>  
  
### <a name="to-add-columns-programmatically"></a><span data-ttu-id="04ea7-108">Program aracılığıyla sütun eklemek için</span><span class="sxs-lookup"><span data-stu-id="04ea7-108">To add columns programmatically</span></span>  
  
1. <span data-ttu-id="04ea7-109">Denetimin <xref:System.Windows.Forms.ListView.View%2A> özelliğini olarak ayarlayın <xref:System.Windows.Forms.View.Details> .</span><span class="sxs-lookup"><span data-stu-id="04ea7-109">Set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
2. <span data-ttu-id="04ea7-110"><xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A>Liste görünümü özelliğinin yöntemini kullanın <xref:System.Windows.Forms.ListView.Columns%2A> .</span><span class="sxs-lookup"><span data-stu-id="04ea7-110">Use the <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> method of the list view's <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="04ea7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04ea7-111">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="04ea7-112">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="04ea7-112">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="04ea7-113">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="04ea7-113">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
