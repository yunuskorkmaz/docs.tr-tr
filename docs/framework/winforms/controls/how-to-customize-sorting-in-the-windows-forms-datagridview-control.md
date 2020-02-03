---
title: DataGridView Denetiminde Sıralamayı Özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: 20f581b2df6fd172a0a1998aed60c56b0306f2eb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743185"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="38d01-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="38d01-102">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="38d01-103"><xref:System.Windows.Forms.DataGridView> denetimi otomatik sıralama sağlar, ancak gereksinimlerinize bağlı olarak sıralama işlemlerini özelleştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="38d01-103">The <xref:System.Windows.Forms.DataGridView> control provides automatic sorting but, depending on your needs, you might need to customize sort operations.</span></span> <span data-ttu-id="38d01-104">Örneğin, alternatif bir kullanıcı arabirimi (UI) oluşturmak için programlı sıralama kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38d01-104">For example, you can use programmatic sorting to create an alternate user interface (UI).</span></span> <span data-ttu-id="38d01-105">Alternatif olarak, <xref:System.Windows.Forms.DataGridView.SortCompare> olayını işleyebilir veya birden çok sütunu sıralama gibi daha fazla sıralama esnekliği için <xref:System.Windows.Forms.DataGridView.Sort%2A> yönteminin `Sort(IComparer)` aşırı yüklemesini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38d01-105">Alternatively, you can handle the <xref:System.Windows.Forms.DataGridView.SortCompare> event or call the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method for greater sorting flexibility, such as sorting multiple columns.</span></span>  
  
 <span data-ttu-id="38d01-106">Aşağıdaki kod örneklerinde özel sıralamaya yönelik bu üç yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="38d01-106">The following code examples demonstrate these three approaches to custom sorting.</span></span> <span data-ttu-id="38d01-107">Daha fazla bilgi için, [Windows Forms DataGridView Denetimindeki sütun sıralama modları](column-sort-modes-in-the-windows-forms-datagridview-control.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="38d01-107">For more information, see [Column Sort Modes in the Windows Forms DataGridView Control](column-sort-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="programmatic-sorting"></a><span data-ttu-id="38d01-108">Programlı sıralama</span><span class="sxs-lookup"><span data-stu-id="38d01-108">Programmatic Sorting</span></span>  
 <span data-ttu-id="38d01-109">Aşağıdaki kod örneği, sıralamayı ve sıralama karakterini el ile ayarlamak için <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> özelliğini kullanarak <xref:System.Windows.Forms.DataGridView.SortOrder%2A> ve <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> özellikleri kullanılarak programlı bir sıralama gösterir.</span><span class="sxs-lookup"><span data-stu-id="38d01-109">The following code example demonstrates a programmatic sort using the <xref:System.Windows.Forms.DataGridView.SortOrder%2A> and <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> properties to determine the direction of the sort, and the <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> property to manually set the sort glyph.</span></span> <span data-ttu-id="38d01-110"><xref:System.Windows.Forms.DataGridView.Sort%2A> yönteminin `Sort(DataGridViewColumn,ListSortDirection)` aşırı yüklemesi, verileri yalnızca tek bir sütunda sıralamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38d01-110">The `Sort(DataGridViewColumn,ListSortDirection)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method is used to sort data only in a single column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a><span data-ttu-id="38d01-111">SortCompare olayını kullanarak özel sıralama</span><span class="sxs-lookup"><span data-stu-id="38d01-111">Custom Sorting Using the SortCompare Event</span></span>  
 <span data-ttu-id="38d01-112">Aşağıdaki kod örneği, bir <xref:System.Windows.Forms.DataGridView.SortCompare> olay işleyicisi kullanarak özel sıralamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="38d01-112">The following code example demonstrates custom sorting using a <xref:System.Windows.Forms.DataGridView.SortCompare> event handler.</span></span> <span data-ttu-id="38d01-113">Seçilen <xref:System.Windows.Forms.DataGridViewColumn> sıralanır ve sütunda yinelenen değerler varsa, son sırayı belirlemede KIMLIK sütunu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38d01-113">The selected <xref:System.Windows.Forms.DataGridViewColumn> is sorted and, if there are duplicate values in the column, the ID column is used to determine the final order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a><span data-ttu-id="38d01-114">IComparer arabirimini kullanarak özel sıralama</span><span class="sxs-lookup"><span data-stu-id="38d01-114">Custom Sorting Using the IComparer Interface</span></span>  
 <span data-ttu-id="38d01-115">Aşağıdaki kod örneği, birden çok sütunlu sıralama gerçekleştirmek için <xref:System.Collections.IComparer> arabiriminin bir uygulamasını Alan <xref:System.Windows.Forms.DataGridView.Sort%2A> yönteminin `Sort(IComparer)` aşırı yüklemesini kullanarak özel sıralamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="38d01-115">The following code example demonstrates custom sorting using the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method, which takes an implementation of the <xref:System.Collections.IComparer> interface to perform a multiple-column sort.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="38d01-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="38d01-116">Compiling the Code</span></span>  
 <span data-ttu-id="38d01-117">Bu örneklerde şunlar gerekir:</span><span class="sxs-lookup"><span data-stu-id="38d01-117">These examples require:</span></span>  
  
- <span data-ttu-id="38d01-118">System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="38d01-118">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d01-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38d01-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="38d01-120">Windows Forms DataGridView Denetimindeki Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="38d01-120">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="38d01-121">Windows Forms DataGridView Denetiminde Sütun Sıralama Modları</span><span class="sxs-lookup"><span data-stu-id="38d01-121">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="38d01-122">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunlar için Sıralama Modlarını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="38d01-122">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](set-the-sort-modes-for-columns-wf-datagridview-control.md)
