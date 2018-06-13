---
title: 'Nasıl yapılır: Windows Forms ListView Denetiminde Öğe Seçme'
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
ms.openlocfilehash: 8256eaeddf98c5a0dd80357bcd562e8f66db85b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532827"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a><span data-ttu-id="23b37-102">Nasıl yapılır: Windows Forms ListView Denetiminde Öğe Seçme</span><span class="sxs-lookup"><span data-stu-id="23b37-102">How to: Select an Item in the Windows Forms ListView Control</span></span>
<span data-ttu-id="23b37-103">Bu örnek program aracılığıyla bir Windows Forms öğeyi seçmek gösterilmiştir <xref:System.Windows.Forms.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="23b37-103">This example demonstrates how to programmatically select an item in a Windows Forms <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="23b37-104">Bir öğe program aracılığıyla seçme otomatik olarak değişmez odağı <xref:System.Windows.Forms.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="23b37-104">Selecting an item programmatically does not automatically change the focus to the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="23b37-105">Bu nedenle, genellikle aynı zamanda öğesi bir öğeyi seçerken odaklanmış olarak ayarlamak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="23b37-105">For this reason, you will typically also want to set the item as focused when selecting an item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23b37-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="23b37-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="23b37-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="23b37-107">Compiling the Code</span></span>  
 <span data-ttu-id="23b37-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="23b37-108">This example requires:</span></span>  
  
-   <span data-ttu-id="23b37-109">A <xref:System.Windows.Forms.ListView> adlı Denetim `listView1` en az bir öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="23b37-109">A <xref:System.Windows.Forms.ListView> control named `listView1` that contains at least one item.</span></span>  
  
-   <span data-ttu-id="23b37-110">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="23b37-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23b37-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23b37-111">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
