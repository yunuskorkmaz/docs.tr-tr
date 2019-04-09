---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Yeniden Sıralamayı Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], reordering columns
- columns [Windows Forms], reordering
ms.assetid: cc20eae3-e4db-493f-95ce-a4215e29472a
ms.openlocfilehash: 625c4987a45ed3749284e7abc7b6cde6d24821ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161479"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e0a47-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Yeniden Sıralamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="e0a47-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e0a47-103">Sütun yeniden sıralamayı etkinleştirdiğinizde <xref:System.Windows.Forms.DataGridView> denetimi, kullanıcıların taşıyabilirsiniz bir sütunu yeni bir konuma fare ile sütun üst bilgisini sürükleyerek.</span><span class="sxs-lookup"><span data-stu-id="e0a47-103">When you enable column reordering in the <xref:System.Windows.Forms.DataGridView> control, users can move a column to a new position by dragging the column header with the mouse.</span></span> <span data-ttu-id="e0a47-104">İçinde <xref:System.Windows.Forms.DataGridView> denetimi <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> özellik değeri, kullanıcıların sütunları farklı konumlara taşıyabilirsiniz olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="e0a47-104">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> property value determines whether users can move columns to different positions.</span></span>  
  
 <span data-ttu-id="e0a47-105">Visual Studio'da bu görevi için desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="e0a47-105">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="e0a47-106">Ayrıca bkz: [nasıl yapılır: Forms DataGridView denetimi Tasarımcısı'nı kullanarak etkinleştir içinde Windows sütun yeniden sıralamayı](enable-column-reordering-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="e0a47-106">Also see [How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer](enable-column-reordering-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-enable-column-reordering-programmatically"></a><span data-ttu-id="e0a47-107">Programlı olarak yeniden sıralama sütunu etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e0a47-107">To enable column reordering programmatically</span></span>  
  
-   <span data-ttu-id="e0a47-108">Ayarlama <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="e0a47-108">Set the <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#060)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#060)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e0a47-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e0a47-109">Compiling the Code</span></span>  
 <span data-ttu-id="e0a47-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e0a47-110">This example requires:</span></span>  
  
-   <span data-ttu-id="e0a47-111">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="e0a47-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="e0a47-112">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="e0a47-112">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a47-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0a47-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e0a47-114">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="e0a47-114">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="e0a47-115">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Dondurma</span><span class="sxs-lookup"><span data-stu-id="e0a47-115">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)
