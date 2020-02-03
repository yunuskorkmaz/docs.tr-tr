---
title: DataGridView denetiminde satır eklemeyi ve silmeyi engelleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
ms.openlocfilehash: de8e0412faf8c3731f9356771b35a4a5d31b6ec7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728726"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="98453-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Satır Ekleme ve Silmeyi Engelleme</span><span class="sxs-lookup"><span data-stu-id="98453-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="98453-103">Bazen, kullanıcıların <xref:System.Windows.Forms.DataGridView> denetiinizden yeni veri satırları girmesini veya mevcut satırları silmelerini engellemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98453-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="98453-104"><xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> özelliği, denetimin alt kısmında yeni kayıtların satırının mevcut olup olmadığını gösterir, ancak <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> özelliği satırların kaldırılıp kaldırılamayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="98453-104">The <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property indicates whether the row for new records is present at the bottom of the control, while the <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> property indicates whether rows can be removed.</span></span> <span data-ttu-id="98453-105">Aşağıdaki kod örneği bu özellikleri kullanır ve ayrıca denetimi tamamen Salt okunabilir hale getirmek için <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> özelliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="98453-105">The following code example uses these properties and also sets the <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> property to make the control entirely read-only.</span></span>  
  
 <span data-ttu-id="98453-106">Visual Studio 'da bu görev için destek vardır.</span><span class="sxs-lookup"><span data-stu-id="98453-106">There is support for this task in Visual Studio.</span></span> <span data-ttu-id="98453-107">Ayrıca bkz. [nasıl yapılır: tasarımcı kullanarak Windows Forms DataGridView denetiminde satır eklemeyi ve silmeyi engelleme](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="98453-107">Also see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="98453-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="98453-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="98453-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="98453-109">Compiling the Code</span></span>  
 <span data-ttu-id="98453-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="98453-110">This example requires:</span></span>  
  
- <span data-ttu-id="98453-111">`dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="98453-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="98453-112"><xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="98453-112">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98453-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98453-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="98453-114">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="98453-114">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
