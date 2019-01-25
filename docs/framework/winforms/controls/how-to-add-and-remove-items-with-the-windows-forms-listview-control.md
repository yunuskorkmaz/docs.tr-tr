---
title: 'Nasıl yapılır: Windows Forms ListView denetimi ile öğe ekleyip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: 7a4083d54ea85ff7a2e18f7e448f2b967317ac25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544529"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a><span data-ttu-id="18bb1-102">Nasıl yapılır: Windows Forms ListView denetimi ile öğe ekleyip</span><span class="sxs-lookup"><span data-stu-id="18bb1-102">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>
<span data-ttu-id="18bb1-103">Bir Windows Forms için bir öğe ekleme işlemini <xref:System.Windows.Forms.ListView> öncelikle, bulunan öğeyi belirten ve Özellikler atayarak denetimi oluşur.</span><span class="sxs-lookup"><span data-stu-id="18bb1-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="18bb1-104">Liste öğe ekleme veya kaldırma herhangi bir zamanda gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="18bb1-104">Adding or removing list items can be done at any time.</span></span>  
  
### <a name="to-add-items-programmatically"></a><span data-ttu-id="18bb1-105">Program aracılığıyla öğeleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="18bb1-105">To add items programmatically</span></span>  
  
1.  <span data-ttu-id="18bb1-106">Kullanım <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> yöntemi <xref:System.Windows.Forms.ListView.Items%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="18bb1-106">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a><span data-ttu-id="18bb1-107">Program aracılığıyla öğeleri kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="18bb1-107">To remove items programmatically</span></span>  
  
1.  <span data-ttu-id="18bb1-108">Kullanım <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> veya <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> yöntemi <xref:System.Windows.Forms.ListView.Items%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="18bb1-108">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span> <span data-ttu-id="18bb1-109"><xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> Yöntemi, tek bir öğe kaldırır; <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> yöntemi listesinden tüm öğeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="18bb1-109">The <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> method removes a single item; the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method removes all items from the list.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="18bb1-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18bb1-110">See also</span></span>
- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="18bb1-111">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="18bb1-111">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [<span data-ttu-id="18bb1-112">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="18bb1-112">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
