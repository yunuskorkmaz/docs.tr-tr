---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e35e340b786e078b5b1264d3f321ff952d52b439
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9c657-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="9c657-102">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9c657-103"><xref:System.Windows.Forms.DataGridView> Denetimi sağlar Otomatik sıralama ancak gereksinimlerinize bağlı olarak, sıralama işlemi özelleştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="9c657-103">The <xref:System.Windows.Forms.DataGridView> control provides automatic sorting but, depending on your needs, you might need to customize sort operations.</span></span> <span data-ttu-id="9c657-104">Örneğin, bir alternatif kullanıcı arabirimi (UI) oluşturmak için programlı sıralama kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c657-104">For example, you can use programmatic sorting to create an alternate user interface (UI).</span></span> <span data-ttu-id="9c657-105">Alternatif olarak, işleyebilir <xref:System.Windows.Forms.DataGridView.SortCompare> olay veya çağrı `Sort(IComparer)` , aşırı <xref:System.Windows.Forms.DataGridView.Sort%2A> birden çok sütun sıralama gibi sıralama esneklik için yöntem.</span><span class="sxs-lookup"><span data-stu-id="9c657-105">Alternatively, you can handle the <xref:System.Windows.Forms.DataGridView.SortCompare> event or call the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method for greater sorting flexibility, such as sorting multiple columns.</span></span>  
  
 <span data-ttu-id="9c657-106">Aşağıdaki kod örneğinde özel sıralama için bu üç yaklaşım gösterilir.</span><span class="sxs-lookup"><span data-stu-id="9c657-106">The following code examples demonstrate these three approaches to custom sorting.</span></span> <span data-ttu-id="9c657-107">Daha fazla bilgi için bkz: [Windows Forms DataGridView denetiminde Sütun sıralama modları](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9c657-107">For more information, see [Column Sort Modes in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="programmatic-sorting"></a><span data-ttu-id="9c657-108">Programsal sıralama</span><span class="sxs-lookup"><span data-stu-id="9c657-108">Programmatic Sorting</span></span>  
 <span data-ttu-id="9c657-109">Aşağıdaki kod örneğinde kullanarak programlı bir sıralama gösterilmektedir <xref:System.Windows.Forms.DataGridView.SortOrder%2A> ve <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> sıralama yönünü belirlemek için özellikler ve <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> sıralama karakter el ile ayarlamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="9c657-109">The following code example demonstrates a programmatic sort using the <xref:System.Windows.Forms.DataGridView.SortOrder%2A> and <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> properties to determine the direction of the sort, and the <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> property to manually set the sort glyph.</span></span> <span data-ttu-id="9c657-110">`Sort(DataGridViewColumn,ListSortDirection)` , Aşırı <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi yalnızca tek bir sütundaki verileri sıralamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9c657-110">The `Sort(DataGridViewColumn,ListSortDirection)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method is used to sort data only in a single column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a><span data-ttu-id="9c657-111">Özel SortCompare olayını kullanarak sıralama</span><span class="sxs-lookup"><span data-stu-id="9c657-111">Custom Sorting Using the SortCompare Event</span></span>  
 <span data-ttu-id="9c657-112">Aşağıdaki kod örneğinde özel kullanarak sıralama gösterilmektedir bir <xref:System.Windows.Forms.DataGridView.SortCompare> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="9c657-112">The following code example demonstrates custom sorting using a <xref:System.Windows.Forms.DataGridView.SortCompare> event handler.</span></span> <span data-ttu-id="9c657-113">Seçili <xref:System.Windows.Forms.DataGridViewColumn> sıralanır ve sütunda yinelenen değerler varsa, kimlik sütunu son sırayı belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9c657-113">The selected <xref:System.Windows.Forms.DataGridViewColumn> is sorted and, if there are duplicate values in the column, the ID column is used to determine the final order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a><span data-ttu-id="9c657-114">Özel IComparer arabirimini kullanarak sıralama</span><span class="sxs-lookup"><span data-stu-id="9c657-114">Custom Sorting Using the IComparer Interface</span></span>  
 <span data-ttu-id="9c657-115">Aşağıdaki kod örneğinde özel kullanarak sıralama gösterilmektedir `Sort(IComparer)` , aşırı <xref:System.Windows.Forms.DataGridView.Sort%2A> uygulaması gereken yöntemi <xref:System.Collections.IComparer> birden çok sütun sıralama gerçekleştirmek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="9c657-115">The following code example demonstrates custom sorting using the `Sort(IComparer)` overload of the <xref:System.Windows.Forms.DataGridView.Sort%2A> method, which takes an implementation of the <xref:System.Collections.IComparer> interface to perform a multiple-column sort.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9c657-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="9c657-116">Compiling the Code</span></span>  
 <span data-ttu-id="9c657-117">Bu örnekler gerektirir:</span><span class="sxs-lookup"><span data-stu-id="9c657-117">These examples require:</span></span>  
  
-   <span data-ttu-id="9c657-118">Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="9c657-118">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="9c657-119">Visual Basic veya Visual C# için bu örnekler komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9c657-119">For information about building these examples from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="9c657-120">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="9c657-120">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="9c657-121">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="9c657-121">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c657-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9c657-122">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="9c657-123">Windows Forms DataGridView Denetimindeki Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="9c657-123">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="9c657-124">Windows Forms DataGridView Denetiminde Sütun Sıralama Modları</span><span class="sxs-lookup"><span data-stu-id="9c657-124">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="9c657-125">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunlar için Sıralama Modlarını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="9c657-125">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)
