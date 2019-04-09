---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütun Başlıklarını Gizleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], hiding column headers
- column headers [Windows Forms], hiding
- DataGridView control [Windows Forms], column headers
ms.assetid: e4ad5f68-50d2-4b9e-93ee-9d622423a8ab
ms.openlocfilehash: 85332bfdbb80e4c49bab1ff208228a88337fbb43
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115251"
---
# <a name="how-to-hide-column-headers-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="3b024-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütun Başlıklarını Gizleme</span><span class="sxs-lookup"><span data-stu-id="3b024-102">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3b024-103">Bazen görüntülemek istediğiniz bir <xref:System.Windows.Forms.DataGridView> sütun üst bilgileri olmadan.</span><span class="sxs-lookup"><span data-stu-id="3b024-103">Sometimes you will want to display a <xref:System.Windows.Forms.DataGridView> without column headers.</span></span> <span data-ttu-id="3b024-104">İçinde <xref:System.Windows.Forms.DataGridView> denetimi <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> özellik değeri, sütun başlıklarına görüntülenip görüntülenmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="3b024-104">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> property value determines whether the column headers are displayed.</span></span>  
  
### <a name="to-hide-the-column-headers"></a><span data-ttu-id="3b024-105">Sütun üst bilgilerini gizlemek için</span><span class="sxs-lookup"><span data-stu-id="3b024-105">To hide the column headers</span></span>  
  
-   <span data-ttu-id="3b024-106">Ayarlama <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="3b024-106">Set the <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#062](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#062)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#062](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#062)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3b024-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3b024-107">Compiling the Code</span></span>  
 <span data-ttu-id="3b024-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3b024-108">This example requires:</span></span>  
  
-   <span data-ttu-id="3b024-109">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="3b024-109">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="3b024-110">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="3b024-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b024-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b024-111">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3b024-112">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="3b024-112">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
