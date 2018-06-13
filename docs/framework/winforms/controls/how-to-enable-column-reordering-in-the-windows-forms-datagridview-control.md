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
ms.openlocfilehash: fbcafae2cb4e4cc320c31794269355d6312b95b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532590"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a2ced-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Yeniden Sıralamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="a2ced-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a2ced-103">Sütun yeniden sıralamayı etkinleştirdiğinizde <xref:System.Windows.Forms.DataGridView> denetim, kullanıcıların taşıyabilirsiniz bir sütun yeni bir konuma fareyle sütun başlığını sürükleyerek.</span><span class="sxs-lookup"><span data-stu-id="a2ced-103">When you enable column reordering in the <xref:System.Windows.Forms.DataGridView> control, users can move a column to a new position by dragging the column header with the mouse.</span></span> <span data-ttu-id="a2ced-104">İçinde <xref:System.Windows.Forms.DataGridView> denetimi <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> özellik değeri kullanıcıları sütunları farklı konumlara taşıyın olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="a2ced-104">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> property value determines whether users can move columns to different positions.</span></span>  
  
 <span data-ttu-id="a2ced-105">Visual Studio'da bu görev için desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="a2ced-105">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="a2ced-106">Ayrıca bkz. [nasıl yapılır: Windows Forms DataGridView denetimi kullanarak Tasarımcı içindeki sütun yeniden sıralamayı](http://msdn.microsoft.com/library/8xwtyc86\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="a2ced-106">Also see [How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/8xwtyc86\(v=vs.110\))</span></span>  
  
### <a name="to-enable-column-reordering-programmatically"></a><span data-ttu-id="a2ced-107">Program aracılığıyla yeniden sıralama sütunu etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="a2ced-107">To enable column reordering programmatically</span></span>  
  
-   <span data-ttu-id="a2ced-108">Ayarlama <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="a2ced-108">Set the <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#060](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#060)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#060](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#060)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a2ced-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a2ced-109">Compiling the Code</span></span>  
 <span data-ttu-id="a2ced-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a2ced-110">This example requires:</span></span>  
  
-   <span data-ttu-id="a2ced-111">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="a2ced-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="a2ced-112">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="a2ced-112">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2ced-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2ced-113">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="a2ced-114">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="a2ced-114">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="a2ced-115">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Dondurma</span><span class="sxs-lookup"><span data-stu-id="a2ced-115">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)
