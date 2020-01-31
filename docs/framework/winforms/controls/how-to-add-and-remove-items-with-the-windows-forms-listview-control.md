---
title: ListView denetimiyle öğe ekleme ve kaldırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: bbfe99db857ebe3a80bf99926f3ce0bec38a1f3f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743144"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a><span data-ttu-id="aea16-102">Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="aea16-102">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>
<span data-ttu-id="aea16-103">Bir Windows Forms <xref:System.Windows.Forms.ListView> denetimine öğe ekleme işlemi, öncelikle öğeyi belirtmesinin ve bu öğeye özellikler atamaktan oluşur.</span><span class="sxs-lookup"><span data-stu-id="aea16-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="aea16-104">Liste öğelerini ekleme veya kaldırma işlemi herhangi bir zamanda yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="aea16-104">Adding or removing list items can be done at any time.</span></span>  
  
### <a name="to-add-items-programmatically"></a><span data-ttu-id="aea16-105">Program aracılığıyla öğe eklemek için</span><span class="sxs-lookup"><span data-stu-id="aea16-105">To add items programmatically</span></span>  
  
1. <span data-ttu-id="aea16-106"><xref:System.Windows.Forms.ListView.Items%2A> özelliğinin <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="aea16-106">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a><span data-ttu-id="aea16-107">Öğeleri programlı olarak kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="aea16-107">To remove items programmatically</span></span>  
  
1. <span data-ttu-id="aea16-108"><xref:System.Windows.Forms.ListView.Items%2A> özelliğinin <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> veya <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="aea16-108">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span> <span data-ttu-id="aea16-109"><xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> yöntemi tek bir öğeyi kaldırır; <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> yöntemi listedeki tüm öğeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="aea16-109">The <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> method removes a single item; the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method removes all items from the list.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="aea16-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aea16-110">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="aea16-111">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="aea16-111">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="aea16-112">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="aea16-112">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
