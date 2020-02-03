---
title: Veriye bağlı bir DataGridView denetimine Ilişkisiz sütun ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: 807bbc121f33c35d70068571e76637c078ecb3da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747069"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="56ac8-102">Nasıl yapılır: Veri Bağlantılı Windows Forms DataGridView Denetimine Bağlantısız Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="56ac8-102">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="56ac8-103"><xref:System.Windows.Forms.DataGridView> denetiminde görüntülenen veriler normalde bazı tür bir veri kaynağından gelir, ancak veri kaynağından gelmeyen veri sütununu göstermek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56ac8-103">The data you display in the <xref:System.Windows.Forms.DataGridView> control will normally come from a data source of some kind, but you might want to display a column of data that does not come from the data source.</span></span> <span data-ttu-id="56ac8-104">Bu tür bir sütuna ilişkisiz sütun denir.</span><span class="sxs-lookup"><span data-stu-id="56ac8-104">This kind of column is called an unbound column.</span></span> <span data-ttu-id="56ac8-105">İlişkisiz sütunlar birçok form alabilir.</span><span class="sxs-lookup"><span data-stu-id="56ac8-105">Unbound columns can take many forms.</span></span> <span data-ttu-id="56ac8-106">Genellikle, bir veri satırının ayrıntılarına erişim sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="56ac8-106">Frequently, they are used to provide access to the details of a data row.</span></span>  
  
 <span data-ttu-id="56ac8-107">Aşağıdaki kod örneği, ana/ayrıntı senaryosunu uyguladığınızda üst tablodaki belirli bir satırla ilgili bir alt tablo göstermek için ilişkisiz bir **ayrıntı** düğmesi sütununun nasıl oluşturulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="56ac8-107">The following code example demonstrates how to create an unbound column of **Details** buttons to display a child table related to a particular row in a parent table when you implement a master/detail scenario.</span></span> <span data-ttu-id="56ac8-108">Düğme tıklamalarına yanıt vermek için, alt tabloyu içeren bir form görüntüleyen <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> olay işleyicisi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="56ac8-108">To respond to button clicks, implement a <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> event handler that displays a form containing the child table.</span></span>  
  
 <span data-ttu-id="56ac8-109">Visual Studio 'da bu görev için destek vardır.</span><span class="sxs-lookup"><span data-stu-id="56ac8-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="56ac8-110">Ayrıca bkz. [nasıl yapılır: tasarımcı kullanarak Windows Forms DataGridView denetiminde sütun ekleme ve kaldırma](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="56ac8-110">Also see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="56ac8-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="56ac8-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="56ac8-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="56ac8-112">Compiling the Code</span></span>  
 <span data-ttu-id="56ac8-113">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="56ac8-113">This example requires:</span></span>  
  
- <span data-ttu-id="56ac8-114">`dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="56ac8-114">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="56ac8-115"><xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="56ac8-115">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ac8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56ac8-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="56ac8-117">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="56ac8-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="56ac8-118">Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları</span><span class="sxs-lookup"><span data-stu-id="56ac8-118">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
