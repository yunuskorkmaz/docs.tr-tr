---
title: DataGridView denetiminde sütunları salt okuma yapın
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: 11d008d47ec5edb594d3d862c68ff3b9920e0e25
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736189"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8b893-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Salt Okunur Yapma</span><span class="sxs-lookup"><span data-stu-id="8b893-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8b893-103">Verilerin hepsi düzenlenmez.</span><span class="sxs-lookup"><span data-stu-id="8b893-103">Not all data is meant for editing.</span></span> <span data-ttu-id="8b893-104"><xref:System.Windows.Forms.DataGridView> denetiminde, sütun <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> Özellik değeri, kullanıcıların söz konusu sütundaki hücreleri düzenleyip düzenleyemeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="8b893-104">In the <xref:System.Windows.Forms.DataGridView> control, the column <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property value determines whether users can edit cells in that column.</span></span> <span data-ttu-id="8b893-105">Denetimi tamamen salt okuma yapma hakkında daha fazla bilgi için, bkz. [nasıl yapılır: satır ekleme ve silmeyi engelleme Windows Forms DataGridView denetiminde](prevent-row-addition-and-deletion-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="8b893-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md).</span></span>  
  
 <span data-ttu-id="8b893-106">Visual Studio 'da bu görev için destek vardır.</span><span class="sxs-lookup"><span data-stu-id="8b893-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="8b893-107">Ayrıca bkz. [nasıl yapılır: tasarımcı kullanarak sütunları salt okuma yapma Windows Forms DataGridView denetiminde](make-columns-read-only-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="8b893-107">Also see [How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer](make-columns-read-only-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-make-a-column-read-only-programmatically"></a><span data-ttu-id="8b893-108">Sütunu programlı olarak salt okunabilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="8b893-108">To make a column read-only programmatically</span></span>  
  
- <span data-ttu-id="8b893-109">Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="8b893-109">Set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8b893-110">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="8b893-110">Compiling the Code</span></span>  
 <span data-ttu-id="8b893-111">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8b893-111">This example requires:</span></span>  
  
- <span data-ttu-id="8b893-112">`CompanyName`adlı bir sütunla `dataGridView1` adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="8b893-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a column named `CompanyName`.</span></span>  
  
- <span data-ttu-id="8b893-113"><xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="8b893-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b893-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b893-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8b893-115">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="8b893-115">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="8b893-116">Nasıl yapılır: Windows Forms DataGridView Denetiminde Satır Eklemeyi ve Silmeyi Engelleme</span><span class="sxs-lookup"><span data-stu-id="8b893-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](prevent-row-addition-and-deletion-datagridview.md)
