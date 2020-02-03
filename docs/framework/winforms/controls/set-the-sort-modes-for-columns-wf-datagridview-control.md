---
title: DataGridView Denetimindeki sütunlar için sıralama modlarını ayarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 45ee1e7d82f826cddbd3492fed0f63e7a9c2cf1d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743004"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="3e3dd-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunlar için Sıralama Modlarını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="3e3dd-102">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3e3dd-103"><xref:System.Windows.Forms.DataGridView> denetiminde metin kutusu sütunları otomatik sıralamayı varsayılan olarak kullanır, diğer sütun türleri otomatik olarak sıralanmaz.</span><span class="sxs-lookup"><span data-stu-id="3e3dd-103">In the <xref:System.Windows.Forms.DataGridView> control, text box columns use automatic sorting by default, while other column types are not sorted automatically.</span></span> <span data-ttu-id="3e3dd-104">Bazen bu Varsayılanları geçersiz kılmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="3e3dd-104">Sometimes you will want to override these defaults.</span></span> <span data-ttu-id="3e3dd-105">Örneğin, resimleri metin, sayı veya numaralandırma hücresi değerlerinin yerine görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e3dd-105">For example, you can display images in place of text, numbers, or enumeration cell values.</span></span> <span data-ttu-id="3e3dd-106">Görüntüler sıralanamadığından, temsil ettikleri temel değerler sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="3e3dd-106">While the images cannot be sorted, the underlying values that they represent can be sorted.</span></span>  
  
 <span data-ttu-id="3e3dd-107"><xref:System.Windows.Forms.DataGridView> denetiminde, bir sütunun <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliği değeri sıralama davranışını belirler.</span><span class="sxs-lookup"><span data-stu-id="3e3dd-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property value of a column determines its sorting behavior.</span></span>  
  
 <span data-ttu-id="3e3dd-108">Aşağıdaki yordamda, [Windows Forms DataGridView Denetimindeki nasıl yapılır: veri biçimlendirmesini özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)`Priority` sütunu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3e3dd-108">The following procedure shows the `Priority` column from [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="3e3dd-109">Bu sütun bir resim sütunudur ve varsayılan olarak sıralanabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="3e3dd-109">This column is an image column and is not sortable by default.</span></span> <span data-ttu-id="3e3dd-110">Ancak, dizeler olan gerçek hücre değerlerini içerir, bu nedenle otomatik olarak sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="3e3dd-110">It contains actual cell values that are strings, however, so it can be sorted automatically.</span></span>  
  
### <a name="to-set-the-sort-mode-for-a-column"></a><span data-ttu-id="3e3dd-111">Bir sütunun sıralama modunu ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="3e3dd-111">To set the sort mode for a column</span></span>  
  
- <span data-ttu-id="3e3dd-112"><xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3e3dd-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3e3dd-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3e3dd-113">Compiling the Code</span></span>  
 <span data-ttu-id="3e3dd-114">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3e3dd-114">This example requires:</span></span>  
  
- <span data-ttu-id="3e3dd-115">`Priority`adlı bir sütun içeren `dataGridView1` adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="3e3dd-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Priority`.</span></span>  
  
- <span data-ttu-id="3e3dd-116"><xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="3e3dd-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e3dd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e3dd-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3e3dd-118">Windows Forms DataGridView Denetimindeki Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="3e3dd-118">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3e3dd-119">Windows Forms DataGridView Denetiminde Sütun Sıralama Modları</span><span class="sxs-lookup"><span data-stu-id="3e3dd-119">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3e3dd-120">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="3e3dd-120">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
