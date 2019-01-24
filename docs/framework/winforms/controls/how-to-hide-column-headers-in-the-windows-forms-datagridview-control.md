---
title: 'Nasıl yapılır: Windows Forms DataGridView denetiminde sütun başlıklarını gizleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], hiding column headers
- column headers [Windows Forms], hiding
- DataGridView control [Windows Forms], column headers
ms.assetid: e4ad5f68-50d2-4b9e-93ee-9d622423a8ab
ms.openlocfilehash: 80377aa598938031f9708c4b7657594985ec0746
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717071"
---
# <a name="how-to-hide-column-headers-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9ed8d-102">Nasıl yapılır: Windows Forms DataGridView denetiminde sütun başlıklarını gizleme</span><span class="sxs-lookup"><span data-stu-id="9ed8d-102">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9ed8d-103">Bazen görüntülemek istediğiniz bir <xref:System.Windows.Forms.DataGridView> sütun üst bilgileri olmadan.</span><span class="sxs-lookup"><span data-stu-id="9ed8d-103">Sometimes you will want to display a <xref:System.Windows.Forms.DataGridView> without column headers.</span></span> <span data-ttu-id="9ed8d-104">İçinde <xref:System.Windows.Forms.DataGridView> denetimi <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> özellik değeri, sütun başlıklarına görüntülenip görüntülenmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="9ed8d-104">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> property value determines whether the column headers are displayed.</span></span>  
  
### <a name="to-hide-the-column-headers"></a><span data-ttu-id="9ed8d-105">Sütun üst bilgilerini gizlemek için</span><span class="sxs-lookup"><span data-stu-id="9ed8d-105">To hide the column headers</span></span>  
  
-   <span data-ttu-id="9ed8d-106">Ayarlama <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="9ed8d-106">Set the <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#062](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#062)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#062](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#062)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9ed8d-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="9ed8d-107">Compiling the Code</span></span>  
 <span data-ttu-id="9ed8d-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="9ed8d-108">This example requires:</span></span>  
  
-   <span data-ttu-id="9ed8d-109">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="9ed8d-109">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="9ed8d-110">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="9ed8d-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed8d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ed8d-111">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9ed8d-112">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="9ed8d-112">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
