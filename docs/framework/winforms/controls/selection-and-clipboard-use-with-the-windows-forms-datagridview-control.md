---
title: DataGridView denetimiyle seçim ve Pano kullanımı
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], Clipboard use
- cells [Windows Forms], selecting in grids
- Clipboard [Windows Forms], in DataGridView control
- selection [Windows Forms], in DataGridView control
- data grids [Windows Forms], selecting cells
- DataGridView control [Windows Forms], selecting cells
ms.assetid: 82cffcad-8b30-4897-bddb-c3a79d751b83
ms.openlocfilehash: 6993f77e8ce532d8df1bdc7e6b6abc1cc3268e49
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743069"
---
# <a name="selection-and-clipboard-use-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="c901d-102">Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı</span><span class="sxs-lookup"><span data-stu-id="c901d-102">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c901d-103">`DataGridView` denetimi, kullanıcıların hücreleri, satırları ve sütunları nasıl seçkullanılabileceğini yapılandırmaya yönelik çeşitli seçenekler sunar.</span><span class="sxs-lookup"><span data-stu-id="c901d-103">The `DataGridView` control provides you with a variety of options for configuring how users can select cells, rows, and columns.</span></span> <span data-ttu-id="c901d-104">Örneğin, kullanıcılar hücrelere tıkladığınızda tek veya birden çok seçimi, satır veya sütun seçimini etkinleştirebilir veya yalnızca kullanıcılar üst bilgilerine tıkladığınızda, hücre seçimini de etkinleştiren tüm satır veya sütunları seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c901d-104">For example, you can enable single or multiple selection, selection of whole rows or columns when users click cells, or selection of whole rows or columns only when users click their headers, which enables cell selection as well.</span></span> <span data-ttu-id="c901d-105">Seçim için kendi Kullanıcı arabiriminizi sağlamak istiyorsanız, normal seçimi devre dışı bırakabilir ve tüm seçimleri program aracılığıyla işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c901d-105">If you want to provide your own user interface for selection, you can disable ordinary selection and handle all selection programmatically.</span></span> <span data-ttu-id="c901d-106">Ayrıca, kullanıcıların seçili değerleri panoya kopyalamasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c901d-106">Additionally, you can enable users to copy the selected values to the Clipboard.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c901d-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c901d-107">In This Section</span></span>  
 [<span data-ttu-id="c901d-108">Windows Forms DataGridView Denetimindeki Seçim Modları</span><span class="sxs-lookup"><span data-stu-id="c901d-108">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c901d-109">Denetimde kullanıcı ve programlı seçim seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c901d-109">Describes the options for user and programmatic selection in the control.</span></span>  
  
 [<span data-ttu-id="c901d-110">Nasıl yapılır: Windows Forms DataGridView Denetiminin Seçim Modunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="c901d-110">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c901d-111">Kullanıcı bir hücreye tıkladığında, tek satırlık seçim için denetimin nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c901d-111">Describes how to configure the control for single-row selection when a user clicks a cell.</span></span>  
  
 [<span data-ttu-id="c901d-112">Nasıl yapılır: Windows Forms DataGridView Denetiminde Seçili Hücre, Satır ve Sütunları Alma</span><span class="sxs-lookup"><span data-stu-id="c901d-112">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](selected-cells-rows-and-columns-datagridview.md)  
 <span data-ttu-id="c901d-113">Seçilen hücre, satır ve sütun koleksiyonlarıyla nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c901d-113">Describes how to work with the selected cell, row, and column collections.</span></span>  
  
 [<span data-ttu-id="c901d-114">Nasıl yapılır: Kullanıcıların Windows Forms DataGridView Denetiminden Panoya Birden Fazla Hücre Kopyalamasına Olanak Tanıma</span><span class="sxs-lookup"><span data-stu-id="c901d-114">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>](enable-users-to-copy-multiple-cells-to-the-clipboard-datagridview.md)  
 <span data-ttu-id="c901d-115">Denetimde Pano desteğinin nasıl etkinleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c901d-115">Describes how to enable Clipboard support in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c901d-116">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c901d-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="c901d-117"><xref:System.Windows.Forms.DataGridView> denetimi için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c901d-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="c901d-118"><xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliği için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c901d-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <span data-ttu-id="c901d-119"><xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> özelliği için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c901d-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>  
 <span data-ttu-id="c901d-120"><xref:System.Windows.Forms.DataGridViewSelectedCellCollection> sınıfı için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c901d-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>  
 <span data-ttu-id="c901d-121"><xref:System.Windows.Forms.DataGridViewSelectedRowCollection> sınıfı için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c901d-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>  
 <span data-ttu-id="c901d-122"><xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> sınıfı için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c901d-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c901d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c901d-123">See also</span></span>

- [<span data-ttu-id="c901d-124">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="c901d-124">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="c901d-125">Windows Forms DataGridView Denetiminde Varsayılan Klavye ve Fare Kullanımı</span><span class="sxs-lookup"><span data-stu-id="c901d-125">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
