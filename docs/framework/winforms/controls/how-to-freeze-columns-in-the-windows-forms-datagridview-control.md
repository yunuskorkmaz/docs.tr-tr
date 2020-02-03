---
title: DataGridView Denetimindeki sütunları dondurma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: 6d1a98e5c4332078c6012cb7c9ed836108abd86c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736747"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="c7f59-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Dondurma</span><span class="sxs-lookup"><span data-stu-id="c7f59-102">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c7f59-103">Kullanıcılar bir Windows Forms <xref:System.Windows.Forms.DataGridView> denetiminde görüntülendiklerinde verileri görüntülerken bazen tek bir sütuna veya sütun kümesine sıklıkla başvurmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7f59-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="c7f59-104">Örneğin, çok sayıda sütun içeren bir müşteri bilgileri tablosu görüntülenirken, diğer sütunların görünür bölgenin dışına kaymasını sağlayan müşteri adını her zaman görüntülemek yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="c7f59-104">For example, when displaying a table of customer information that contains many columns, it is useful to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="c7f59-105">Bu davranışı başarmak için denetimdeki sütunları dondurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7f59-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="c7f59-106">Bir sütunu dondurduktan sonra, sol tarafında (veya sağdan sola dil betiklerine ait olan) tüm sütunlar da dondurulur.</span><span class="sxs-lookup"><span data-stu-id="c7f59-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="c7f59-107">Dondurulmuş sütunlar, diğer tüm sütunlar kaydırılarken yerinde kalır.</span><span class="sxs-lookup"><span data-stu-id="c7f59-107">Frozen columns remain in place while all other columns can scroll.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7f59-108">Sütun yeniden sıralama etkinse, Dondurulmuş sütunlar dondurulmamış sütunlardan farklı bir grup olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c7f59-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="c7f59-109">Kullanıcılar her iki gruptaki sütunları yeniden konumlandırabilirsiniz, ancak bir sütunu bir gruptan diğerine taşıyamaz.</span><span class="sxs-lookup"><span data-stu-id="c7f59-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="c7f59-110">Sütunun <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> özelliği, sütunun kılavuz içinde her zaman görünür olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="c7f59-110">The <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property of a column determines whether the column is always visible within the grid.</span></span>  
  
 <span data-ttu-id="c7f59-111">Visual Studio 'da bu görev için destek vardır.</span><span class="sxs-lookup"><span data-stu-id="c7f59-111">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="c7f59-112">Ayrıca bkz. [nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView Denetimindeki sütunları dondurma](freeze-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="c7f59-112">Also see [How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer](freeze-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-freeze-a-column-programmatically"></a><span data-ttu-id="c7f59-113">Bir sütunu programlı bir şekilde dondurmak için</span><span class="sxs-lookup"><span data-stu-id="c7f59-113">To freeze a column programmatically</span></span>  
  
- <span data-ttu-id="c7f59-114"><xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c7f59-114">Set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c7f59-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c7f59-115">Compiling the Code</span></span>  
 <span data-ttu-id="c7f59-116">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c7f59-116">This example requires:</span></span>  
  
- <span data-ttu-id="c7f59-117">`AddToCartButton`adlı bir sütun içeren `dataGridView1` adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="c7f59-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `AddToCartButton`.</span></span>  
  
- <span data-ttu-id="c7f59-118"><xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="c7f59-118">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f59-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7f59-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="c7f59-120">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="c7f59-120">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="c7f59-121">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Yeniden Sıralamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="c7f59-121">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
