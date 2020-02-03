---
title: ListView denetimindeki bir öğe seçin
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lists [Windows Forms], selecting items
- ListView control [Windows Forms], selecting items
- selection [Windows Forms], in list views
- list views [Windows Forms], selecting items
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
ms.openlocfilehash: 57e985af9d0347510d7d7782f68d5b414d36e077
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743238"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a><span data-ttu-id="241d6-102">Nasıl yapılır: Windows Forms ListView Denetiminde Öğe Seçme</span><span class="sxs-lookup"><span data-stu-id="241d6-102">How to: Select an Item in the Windows Forms ListView Control</span></span>
<span data-ttu-id="241d6-103">Bu örnek, Windows Forms <xref:System.Windows.Forms.ListView> denetimindeki bir öğeyi programlı olarak nasıl seçeceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="241d6-103">This example demonstrates how to programmatically select an item in a Windows Forms <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="241d6-104">Program aracılığıyla bir öğe seçildiğinde odak <xref:System.Windows.Forms.ListView> denetimine otomatik olarak değişmez.</span><span class="sxs-lookup"><span data-stu-id="241d6-104">Selecting an item programmatically does not automatically change the focus to the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="241d6-105">Bu nedenle, öğe seçerken genellikle öğeyi odaklanmış olarak ayarlamak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="241d6-105">For this reason, you will typically also want to set the item as focused when selecting an item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="241d6-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="241d6-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="241d6-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="241d6-107">Compiling the Code</span></span>  
 <span data-ttu-id="241d6-108">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="241d6-108">This example requires:</span></span>  
  
- <span data-ttu-id="241d6-109">En az bir öğe içeren `listView1` adlı <xref:System.Windows.Forms.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="241d6-109">A <xref:System.Windows.Forms.ListView> control named `listView1` that contains at least one item.</span></span>  
  
- <span data-ttu-id="241d6-110"><xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanlarına başvurular.</span><span class="sxs-lookup"><span data-stu-id="241d6-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="241d6-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="241d6-111">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
