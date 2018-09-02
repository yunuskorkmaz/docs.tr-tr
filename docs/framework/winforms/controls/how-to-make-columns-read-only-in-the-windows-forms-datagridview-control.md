---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Salt Okunur Yapma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: a8b5c0f9492941cf0e01e016d9fb097e1df44d2e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389721"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="208b1-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Salt Okunur Yapma</span><span class="sxs-lookup"><span data-stu-id="208b1-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="208b1-103">Tüm veri düzenleme amacıyla yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="208b1-103">Not all data is meant for editing.</span></span> <span data-ttu-id="208b1-104">İçinde <xref:System.Windows.Forms.DataGridView> denetimindeki sütun <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> özellik değeri, kullanıcılar söz konusu sütundaki hücrelerin düzenleyip düzenleyemeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="208b1-104">In the <xref:System.Windows.Forms.DataGridView> control, the column <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property value determines whether users can edit cells in that column.</span></span> <span data-ttu-id="208b1-105">Salt okunur tamamen denetimi yapma hakkında daha fazla bilgi için bkz: [nasıl yapılır: önlemek satır eklemeyi ve silmeyi Windows Forms DataGridView denetiminde](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="208b1-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md).</span></span>  
  
 <span data-ttu-id="208b1-106">Visual Studio'da bu görevi için desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="208b1-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="208b1-107">Ayrıca bkz: [nasıl yapılır: Windows Forms DataGridView denetimi kullanarak Tasarımcı içinde sütunları salt okunur hale](https://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="208b1-107">Also see [How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer](https://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\)).</span></span>  
  
### <a name="to-make-a-column-read-only-programmatically"></a><span data-ttu-id="208b1-108">Salt okunur bir sütunu programlı bir şekilde yapmak için</span><span class="sxs-lookup"><span data-stu-id="208b1-108">To make a column read-only programmatically</span></span>  
  
-   <span data-ttu-id="208b1-109">Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="208b1-109">Set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="208b1-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="208b1-110">Compiling the Code</span></span>  
 <span data-ttu-id="208b1-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="208b1-111">This example requires:</span></span>  
  
-   <span data-ttu-id="208b1-112">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütunun `CompanyName`.</span><span class="sxs-lookup"><span data-stu-id="208b1-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a column named `CompanyName`.</span></span>  
  
-   <span data-ttu-id="208b1-113">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="208b1-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="208b1-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="208b1-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="208b1-115">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="208b1-115">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="208b1-116">Nasıl yapılır: Windows Forms DataGridView Denetiminde Satır Eklemeyi ve Silmeyi Engelleme</span><span class="sxs-lookup"><span data-stu-id="208b1-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)
