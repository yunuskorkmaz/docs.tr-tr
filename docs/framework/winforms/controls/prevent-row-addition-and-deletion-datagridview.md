---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Satır Ekleme ve Silmeyi Engelleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
ms.openlocfilehash: d361b0791691fa6a3e1720538c7bf22b14397579
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654475"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a35d8-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Satır Ekleme ve Silmeyi Engelleme</span><span class="sxs-lookup"><span data-stu-id="a35d8-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a35d8-103">Bazen kullanıcıların yeni veri satırı girme veya var olan satır silme önlemek istersiniz, <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="a35d8-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="a35d8-104"><xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> Özelliği gösteren yeni kayıtlar için satır denetimi altındaki mevcut olup olmadığını, while <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> özelliği satırları kaldırılıp kaldırılamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a35d8-104">The <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property indicates whether the row for new records is present at the bottom of the control, while the <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> property indicates whether rows can be removed.</span></span> <span data-ttu-id="a35d8-105">Aşağıdaki kod örneği, bu özellikleri kullanan ve ayrıca ayarlar <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> salt okunur tamamen denetimi yapma özelliği.</span><span class="sxs-lookup"><span data-stu-id="a35d8-105">The following code example uses these properties and also sets the <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> property to make the control entirely read-only.</span></span>  
  
 <span data-ttu-id="a35d8-106">Visual Studio'da bu görevi için desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="a35d8-106">There is support for this task in Visual Studio.</span></span> <span data-ttu-id="a35d8-107">Ayrıca bkz: [nasıl yapılır: Engelleme satır eklemeyi ve silmeyi Windows Forms DataGridView denetiminde Tasarımcısı'nı kullanarak](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="a35d8-107">Also see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a35d8-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="a35d8-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a35d8-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a35d8-109">Compiling the Code</span></span>  
 <span data-ttu-id="a35d8-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a35d8-110">This example requires:</span></span>  
  
- <span data-ttu-id="a35d8-111">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="a35d8-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="a35d8-112">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="a35d8-112">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a35d8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a35d8-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a35d8-114">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="a35d8-114">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
