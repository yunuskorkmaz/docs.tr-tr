---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Dondurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: a83c5078d67be40fda2ae3382b8124594ee78103
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966653"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6b824-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Dondurma</span><span class="sxs-lookup"><span data-stu-id="6b824-102">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6b824-103">Kullanıcılar bir Windows Forms <xref:System.Windows.Forms.DataGridView> denetiminde görüntülendiklerinde verileri görüntülerken, bazen tek bir sütuna veya sütun kümesine sıklıkla başvurmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b824-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="6b824-104">Örneğin, çok sayıda sütun içeren bir müşteri bilgileri tablosu görüntülenirken, diğer sütunların görünür bölgenin dışına kaymasını sağlayan müşteri adını her zaman görüntülemek yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="6b824-104">For example, when displaying a table of customer information that contains many columns, it is useful to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="6b824-105">Bu davranışı başarmak için denetimdeki sütunları dondurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b824-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="6b824-106">Bir sütunu dondurduktan sonra, sol tarafında (veya sağdan sola dil betiklerine ait olan) tüm sütunlar da dondurulur.</span><span class="sxs-lookup"><span data-stu-id="6b824-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="6b824-107">Dondurulmuş sütunlar, diğer tüm sütunlar kaydırılarken yerinde kalır.</span><span class="sxs-lookup"><span data-stu-id="6b824-107">Frozen columns remain in place while all other columns can scroll.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b824-108">Sütun yeniden sıralama etkinse, Dondurulmuş sütunlar dondurulmamış sütunlardan farklı bir grup olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6b824-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="6b824-109">Kullanıcılar her iki gruptaki sütunları yeniden konumlandırabilirsiniz, ancak bir sütunu bir gruptan diğerine taşıyamaz.</span><span class="sxs-lookup"><span data-stu-id="6b824-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="6b824-110">Bir <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> sütunun özelliği, sütunun kılavuz içinde her zaman görünür olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="6b824-110">The <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property of a column determines whether the column is always visible within the grid.</span></span>  
  
 <span data-ttu-id="6b824-111">Visual Studio 'da bu görev için destek vardır.</span><span class="sxs-lookup"><span data-stu-id="6b824-111">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="6b824-112">Ayrıca bkz [. nasıl yapılır: Tasarımcıyı](freeze-columns-in-the-datagrid-using-the-designer.md)kullanarak Windows Forms DataGridView Denetimindeki sütunları dondurma.</span><span class="sxs-lookup"><span data-stu-id="6b824-112">Also see [How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer](freeze-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-freeze-a-column-programmatically"></a><span data-ttu-id="6b824-113">Bir sütunu programlı bir şekilde dondurmak için</span><span class="sxs-lookup"><span data-stu-id="6b824-113">To freeze a column programmatically</span></span>  
  
- <span data-ttu-id="6b824-114">Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="6b824-114">Set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6b824-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="6b824-115">Compiling the Code</span></span>  
 <span data-ttu-id="6b824-116">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="6b824-116">This example requires:</span></span>  
  
- <span data-ttu-id="6b824-117">Adında <xref:System.Windows.Forms.DataGridView> bir sütun içerenadlı`dataGridView1` bir denetim. `AddToCartButton`</span><span class="sxs-lookup"><span data-stu-id="6b824-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `AddToCartButton`.</span></span>  
  
- <span data-ttu-id="6b824-118"><xref:System?displayProperty=nameWithType> Ve<xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="6b824-118">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b824-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b824-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="6b824-120">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="6b824-120">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="6b824-121">Nasıl yapılır: Windows Forms DataGridView denetiminde sütun yeniden sıralamayı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="6b824-121">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
