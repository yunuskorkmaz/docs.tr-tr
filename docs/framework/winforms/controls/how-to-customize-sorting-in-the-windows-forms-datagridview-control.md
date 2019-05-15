---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: 85ca27bf2ef738dce86c6e88037da00e4992a4b2
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592788"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6322f-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6322f-102">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6322f-103"><xref:System.Windows.Forms.DataGridView> Denetimi, Otomatik sıralama sağlar ancak gereksinimlerinize bağlı olarak, sıralama işlemlerinde özelleştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="6322f-103">The <xref:System.Windows.Forms.DataGridView> control provides automatic sorting but, depending on your needs, you might need to customize sort operations.</span></span> <span data-ttu-id="6322f-104">Örneğin, bir diğer kullanıcı arabirimi (UI) oluşturmak için programlı sıralama kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6322f-104">For example, you can use programmatic sorting to create an alternate user interface (UI).</span></span> <span data-ttu-id="6322f-105">Alternatif olarak, işleyebileceği <xref:System.Windows.Forms.DataGridView.SortCompare> olay veya çağrı `Sort(IComparer)` aşırı yükünü <xref:System.Windows.Forms.DataGridView.Sort%2A> birden çok sütunu sıralama gibi sıralama esneklik için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6322f-105">Alternatively, you can handle the <xref:System.Windows.Forms.DataGridView.SortCompare> event or call the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method for greater sorting flexibility, such as sorting multiple columns.</span></span>  
  
 <span data-ttu-id="6322f-106">Aşağıdaki kod örnekleri, özel sıralamak için üç bu yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6322f-106">The following code examples demonstrate these three approaches to custom sorting.</span></span> <span data-ttu-id="6322f-107">Daha fazla bilgi için [Windows Forms DataGridView denetiminde Sütun sıralama modları](column-sort-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="6322f-107">For more information, see [Column Sort Modes in the Windows Forms DataGridView Control](column-sort-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="programmatic-sorting"></a><span data-ttu-id="6322f-108">Programlı sıralama</span><span class="sxs-lookup"><span data-stu-id="6322f-108">Programmatic Sorting</span></span>  
 <span data-ttu-id="6322f-109">Aşağıdaki kod örneği kullanılarak programlı bir sıralama gösterir <xref:System.Windows.Forms.DataGridView.SortOrder%2A> ve <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> sıralama yönünü belirlemek için özellikleri ve <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> karakter Sırala el ile ayarlamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="6322f-109">The following code example demonstrates a programmatic sort using the <xref:System.Windows.Forms.DataGridView.SortOrder%2A> and <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> properties to determine the direction of the sort, and the <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> property to manually set the sort glyph.</span></span> <span data-ttu-id="6322f-110">`Sort(DataGridViewColumn,ListSortDirection)` Aşırı yükünü <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi yalnızca tek bir sütunda verileri sıralamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6322f-110">The `Sort(DataGridViewColumn,ListSortDirection)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method is used to sort data only in a single column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a><span data-ttu-id="6322f-111">Özel SortCompare olayını kullanarak sıralama</span><span class="sxs-lookup"><span data-stu-id="6322f-111">Custom Sorting Using the SortCompare Event</span></span>  
 <span data-ttu-id="6322f-112">Aşağıdaki kod örneği kullanarak özel sıralama gösterir bir <xref:System.Windows.Forms.DataGridView.SortCompare> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="6322f-112">The following code example demonstrates custom sorting using a <xref:System.Windows.Forms.DataGridView.SortCompare> event handler.</span></span> <span data-ttu-id="6322f-113">Seçili <xref:System.Windows.Forms.DataGridViewColumn> sıralanır ve sütundaki yinelenen değerler varsa, kimlik sütunu son sırasını belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6322f-113">The selected <xref:System.Windows.Forms.DataGridViewColumn> is sorted and, if there are duplicate values in the column, the ID column is used to determine the final order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a><span data-ttu-id="6322f-114">Özel IComparer arabirimini kullanarak sıralama</span><span class="sxs-lookup"><span data-stu-id="6322f-114">Custom Sorting Using the IComparer Interface</span></span>  
 <span data-ttu-id="6322f-115">Aşağıdaki kod örneği kullanarak özel sıralama gösterir `Sort(IComparer)` aşırı yükünü <xref:System.Windows.Forms.DataGridView.Sort%2A> uygulaması gereken yöntemini <xref:System.Collections.IComparer> birden çok sütunu sıralamayı gerçekleştirmek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="6322f-115">The following code example demonstrates custom sorting using the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method, which takes an implementation of the <xref:System.Collections.IComparer> interface to perform a multiple-column sort.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6322f-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="6322f-116">Compiling the Code</span></span>  
 <span data-ttu-id="6322f-117">Bu örneği gerektirir:</span><span class="sxs-lookup"><span data-stu-id="6322f-117">These examples require:</span></span>  
  
- <span data-ttu-id="6322f-118">Sistem, System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="6322f-118">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6322f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6322f-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="6322f-120">Windows Forms DataGridView Denetimindeki Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="6322f-120">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6322f-121">Windows Forms DataGridView Denetiminde Sütun Sıralama Modları</span><span class="sxs-lookup"><span data-stu-id="6322f-121">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6322f-122">Nasıl yapılır: Windows Forms DataGridView denetiminde sütunlar için sıralama modlarını ayarlama</span><span class="sxs-lookup"><span data-stu-id="6322f-122">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](set-the-sort-modes-for-columns-wf-datagridview-control.md)
