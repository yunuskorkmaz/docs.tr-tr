---
title: ListView denetimiyle öğe ekleme ve kaldırma
description: Öğeyi belirterek ve içine özellikler atayarak Windows Forms ListView denetimiyle bir öğe ekleme ve kaldırma hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: db374ded69bcbd93527381d75a8ff751a1c9abe6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618096"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a><span data-ttu-id="2d89c-103">Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="2d89c-103">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>
<span data-ttu-id="2d89c-104">Bir Windows Forms denetimine öğe ekleme işlemi, <xref:System.Windows.Forms.ListView> öncelikle öğeyi belirtmektir ve bu öğeye özellikler atamaktan oluşur.</span><span class="sxs-lookup"><span data-stu-id="2d89c-104">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="2d89c-105">Liste öğelerini ekleme veya kaldırma işlemi herhangi bir zamanda yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="2d89c-105">Adding or removing list items can be done at any time.</span></span>  
  
### <a name="to-add-items-programmatically"></a><span data-ttu-id="2d89c-106">Program aracılığıyla öğe eklemek için</span><span class="sxs-lookup"><span data-stu-id="2d89c-106">To add items programmatically</span></span>  
  
1. <span data-ttu-id="2d89c-107"><xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A>Özelliğin yöntemini kullanın <xref:System.Windows.Forms.ListView.Items%2A> .</span><span class="sxs-lookup"><span data-stu-id="2d89c-107">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a><span data-ttu-id="2d89c-108">Öğeleri programlı olarak kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="2d89c-108">To remove items programmatically</span></span>  
  
1. <span data-ttu-id="2d89c-109"><xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> Özelliğinin veya yöntemini kullanın <xref:System.Windows.Forms.ListView.Items%2A> .</span><span class="sxs-lookup"><span data-stu-id="2d89c-109">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span> <span data-ttu-id="2d89c-110"><xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A>Yöntemi tek bir öğeyi kaldırır; <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> yöntemi listedeki tüm öğeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2d89c-110">The <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> method removes a single item; the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method removes all items from the list.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="2d89c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d89c-111">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="2d89c-112">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="2d89c-112">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="2d89c-113">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2d89c-113">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
