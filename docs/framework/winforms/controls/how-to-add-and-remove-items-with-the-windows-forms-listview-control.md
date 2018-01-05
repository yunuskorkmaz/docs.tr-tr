---
title: "Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma"
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
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a66d0da6e010efbad77e9544267d1b6af9d1233
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a><span data-ttu-id="2dfa4-102">Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="2dfa4-102">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>
<span data-ttu-id="2dfa4-103">Windows Forms için bir öğe ekleme işlemini <xref:System.Windows.Forms.ListView> denetim oluşur öncelikle öğesi belirtme ve Özellikler atayarak.</span><span class="sxs-lookup"><span data-stu-id="2dfa4-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="2dfa4-104">Liste öğe ekleme veya kaldırma herhangi bir zamanda yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="2dfa4-104">Adding or removing list items can be done at any time.</span></span>  
  
### <a name="to-add-items-programmatically"></a><span data-ttu-id="2dfa4-105">Öğeleri programlı olarak eklemek için</span><span class="sxs-lookup"><span data-stu-id="2dfa4-105">To add items programmatically</span></span>  
  
1.  <span data-ttu-id="2dfa4-106">Kullanım <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> yöntemi <xref:System.Windows.Forms.ListView.Items%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2dfa4-106">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a><span data-ttu-id="2dfa4-107">Program aracılığıyla öğeleri kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="2dfa4-107">To remove items programmatically</span></span>  
  
1.  <span data-ttu-id="2dfa4-108">Kullanım <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> veya <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> yöntemi <xref:System.Windows.Forms.ListView.Items%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2dfa4-108">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span> <span data-ttu-id="2dfa4-109"><xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> Yöntemi, tek bir öğe kaldırır; <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> yöntemi listeden tüm öğeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2dfa4-109">The <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> method removes a single item; the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method removes all items from the list.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="2dfa4-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2dfa4-110">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 [<span data-ttu-id="2dfa4-111">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="2dfa4-111">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="2dfa4-112">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2dfa4-112">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
