---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunlar için Sıralama Modlarını Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 08d90bb45006af798b629f58821cbf50ee9ef089
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535737"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e686d-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunlar için Sıralama Modlarını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="e686d-102">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e686d-103">İçinde <xref:System.Windows.Forms.DataGridView> denetimi, metin kutusu sütunları kullanma diğer sütun türleri otomatik olarak sıralanan değil sırasında varsayılan olarak, Otomatik sıralama.</span><span class="sxs-lookup"><span data-stu-id="e686d-103">In the <xref:System.Windows.Forms.DataGridView> control, text box columns use automatic sorting by default, while other column types are not sorted automatically.</span></span> <span data-ttu-id="e686d-104">Bazen bu varsayılanlarını geçersiz kıl isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="e686d-104">Sometimes you will want to override these defaults.</span></span> <span data-ttu-id="e686d-105">Örneğin, metin, sayılar veya numaralandırma hücre değerlerinin yerine görüntüleri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e686d-105">For example, you can display images in place of text, numbers, or enumeration cell values.</span></span> <span data-ttu-id="e686d-106">Görüntüleri sıralanamaz olsa da, bunlar temsil eden temel değerleri sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="e686d-106">While the images cannot be sorted, the underlying values that they represent can be sorted.</span></span>  
  
 <span data-ttu-id="e686d-107">İçinde <xref:System.Windows.Forms.DataGridView> denetimi <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özellik değeri bir sütunun sıralama davranışını belirler.</span><span class="sxs-lookup"><span data-stu-id="e686d-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property value of a column determines its sorting behavior.</span></span>  
  
 <span data-ttu-id="e686d-108">Aşağıdaki yordamda gösterildiği `Priority` sütundan [nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="e686d-108">The following procedure shows the `Priority` column from [How to: Customize Data Formatting in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="e686d-109">Bu sütun bir görüntü sütunu ve varsayılan olarak sıralanabilir değil.</span><span class="sxs-lookup"><span data-stu-id="e686d-109">This column is an image column and is not sortable by default.</span></span> <span data-ttu-id="e686d-110">Otomatik olarak sıralanabilir şekilde, ancak dizelerdir gerçek hücre değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="e686d-110">It contains actual cell values that are strings, however, so it can be sorted automatically.</span></span>  
  
### <a name="to-set-the-sort-mode-for-a-column"></a><span data-ttu-id="e686d-111">Bir sütunun sıralama modu ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e686d-111">To set the sort mode for a column</span></span>  
  
-   <span data-ttu-id="e686d-112">Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e686d-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e686d-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e686d-113">Compiling the Code</span></span>  
 <span data-ttu-id="e686d-114">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e686d-114">This example requires:</span></span>  
  
-   <span data-ttu-id="e686d-115">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `Priority`.</span><span class="sxs-lookup"><span data-stu-id="e686d-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Priority`.</span></span>  
  
-   <span data-ttu-id="e686d-116">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="e686d-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e686d-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e686d-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="e686d-118">Windows Forms DataGridView Denetimindeki Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="e686d-118">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="e686d-119">Windows Forms DataGridView Denetiminde Sütun Sıralama Modları</span><span class="sxs-lookup"><span data-stu-id="e686d-119">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="e686d-120">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e686d-120">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
