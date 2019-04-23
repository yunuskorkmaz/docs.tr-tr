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
ms.openlocfilehash: b3cfcc6c2873dfb0eb95cf7950adc6b2bb73e74c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977619"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a><span data-ttu-id="2ab2e-102">Nasıl yapılır: Windows Forms ListView Denetiminde Öğe Seçme</span><span class="sxs-lookup"><span data-stu-id="2ab2e-102">How to: Select an Item in the Windows Forms ListView Control</span></span>
<span data-ttu-id="2ab2e-103">Bu örnek program aracılığıyla bir Windows Formları öğeyi seçmek nasıl gösterir <xref:System.Windows.Forms.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2ab2e-103">This example demonstrates how to programmatically select an item in a Windows Forms <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="2ab2e-104">Program aracılığıyla bir öğe seçtiğinizde otomatik olarak değişmez odağı <xref:System.Windows.Forms.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2ab2e-104">Selecting an item programmatically does not automatically change the focus to the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="2ab2e-105">Bu nedenle, genellikle de öğesi bir öğeyi seçerken odaklı olarak ayarlamak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="2ab2e-105">For this reason, you will typically also want to set the item as focused when selecting an item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ab2e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ab2e-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2ab2e-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2ab2e-107">Compiling the Code</span></span>  
 <span data-ttu-id="2ab2e-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="2ab2e-108">This example requires:</span></span>  
  
-   <span data-ttu-id="2ab2e-109">A <xref:System.Windows.Forms.ListView> adlı Denetim `listView1` , en az bir öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="2ab2e-109">A <xref:System.Windows.Forms.ListView> control named `listView1` that contains at least one item.</span></span>  
  
-   <span data-ttu-id="2ab2e-110">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="2ab2e-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ab2e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ab2e-111">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
