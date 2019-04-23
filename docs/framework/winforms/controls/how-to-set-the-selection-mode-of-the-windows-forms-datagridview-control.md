---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminin Seçim Modunu Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
- data grids [Windows Forms], selection mode
ms.assetid: 2f241643-7f82-4583-8757-03494f63b465
ms.openlocfilehash: 2e430dfb170943178f6db27c0bd2c1ef0f972882
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200564"
---
# <a name="how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="5c4b9-102">Nasıl yapılır: Windows Forms DataGridView Denetiminin Seçim Modunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="5c4b9-102">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5c4b9-103">Aşağıdaki kod örneğinde nasıl yapılandırılacağını gösteren bir <xref:System.Windows.Forms.DataGridView> denetim böylece satır içinde otomatik olarak herhangi bir yere tıklayarak tüm satırı seçer ve bu nedenle aynı anda yalnızca bir satır seçilebilir.</span><span class="sxs-lookup"><span data-stu-id="5c4b9-103">The following code example demonstrates how to configure a <xref:System.Windows.Forms.DataGridView> control so that clicking anywhere within a row automatically selects the entire row, and so that only one row at a time can be selected.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c4b9-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c4b9-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#065](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#065)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#065](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#065)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5c4b9-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5c4b9-105">Compiling the Code</span></span>  
 <span data-ttu-id="5c4b9-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="5c4b9-106">This example requires:</span></span>  
  
-   <span data-ttu-id="5c4b9-107">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="5c4b9-107">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="5c4b9-108">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="5c4b9-108">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c4b9-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c4b9-109">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [<span data-ttu-id="5c4b9-110">Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı</span><span class="sxs-lookup"><span data-stu-id="5c4b9-110">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="5c4b9-111">Windows Forms DataGridView Denetimindeki Seçim Modları</span><span class="sxs-lookup"><span data-stu-id="5c4b9-111">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
