---
title: Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], Clipboard use
- cells [Windows Forms], selecting in grids
- Clipboard [Windows Forms], in DataGridView control
- selection [Windows Forms], in DataGridView control
- data grids [Windows Forms], selecting cells
- DataGridView control [Windows Forms], selecting cells
ms.assetid: 82cffcad-8b30-4897-bddb-c3a79d751b83
ms.openlocfilehash: dd7dca483b05e52ea3932bc59e3c5b98de1a0667
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659442"
---
# <a name="selection-and-clipboard-use-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="7dda0-102">Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı</span><span class="sxs-lookup"><span data-stu-id="7dda0-102">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7dda0-103">`DataGridView` Denetim çeşitli kullanıcılar hücreler, satırlar ve sütunlarla nasıl seçebilir yapılandırma seçenekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7dda0-103">The `DataGridView` control provides you with a variety of options for configuring how users can select cells, rows, and columns.</span></span> <span data-ttu-id="7dda0-104">Kullanıcılar kendi üst bilgileri tıkladığınızda gibi tek veya birden çok seçim, tüm satırları veya kullanıcılar hücreleri tıkladığınızda sütun seçimi ya da tüm satırları veya sütunları seçimi hücre seçimi sağlayan etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7dda0-104">For example, you can enable single or multiple selection, selection of whole rows or columns when users click cells, or selection of whole rows or columns only when users click their headers, which enables cell selection as well.</span></span> <span data-ttu-id="7dda0-105">Seçimi için kendi kullanıcı arabirimini sağlamak istiyorsanız, sıradan seçimi devre dışı bırakabilir ve tüm seçimi programlı olarak işleme.</span><span class="sxs-lookup"><span data-stu-id="7dda0-105">If you want to provide your own user interface for selection, you can disable ordinary selection and handle all selection programmatically.</span></span> <span data-ttu-id="7dda0-106">Ayrıca, kullanıcıların seçilen değerleri panoya kopyalamak etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7dda0-106">Additionally, you can enable users to copy the selected values to the Clipboard.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7dda0-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7dda0-107">In This Section</span></span>  
 [<span data-ttu-id="7dda0-108">Windows Forms DataGridView Denetimindeki Seçim Modları</span><span class="sxs-lookup"><span data-stu-id="7dda0-108">Selection Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="7dda0-109">Kullanıcı ve programlı seçiminde denetim seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="7dda0-109">Describes the options for user and programmatic selection in the control.</span></span>  
  
 [<span data-ttu-id="7dda0-110">Nasıl yapılır: Windows Forms DataGridView denetiminin seçim modunu ayarlama</span><span class="sxs-lookup"><span data-stu-id="7dda0-110">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="7dda0-111">Bir kullanıcı bir hücreye tıkladığında denetim tek satır seçimi için yapılandırılması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7dda0-111">Describes how to configure the control for single-row selection when a user clicks a cell.</span></span>  
  
 [<span data-ttu-id="7dda0-112">Nasıl yapılır: Windows Forms DataGridView denetiminde seçili hücre, satır ve sütunları alma</span><span class="sxs-lookup"><span data-stu-id="7dda0-112">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selected-cells-rows-and-columns-datagridview.md)  
 <span data-ttu-id="7dda0-113">Seçili hücre, satır ve sütun koleksiyonlarla çalışma açıklar.</span><span class="sxs-lookup"><span data-stu-id="7dda0-113">Describes how to work with the selected cell, row, and column collections.</span></span>  
  
 [<span data-ttu-id="7dda0-114">Nasıl yapılır: Kullanıcıların Windows Forms DataGridView denetiminden panoya birden fazla hücre kopyalamasına olanak</span><span class="sxs-lookup"><span data-stu-id="7dda0-114">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/enable-users-to-copy-multiple-cells-to-the-clipboard-datagridview.md)  
 <span data-ttu-id="7dda0-115">Denetimdeki Pano desteğini nasıl etkinleştireceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="7dda0-115">Describes how to enable Clipboard support in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7dda0-116">Başvuru</span><span class="sxs-lookup"><span data-stu-id="7dda0-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="7dda0-117">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7dda0-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="7dda0-118">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7dda0-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <span data-ttu-id="7dda0-119">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7dda0-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>  
 <span data-ttu-id="7dda0-120">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7dda0-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>  
 <span data-ttu-id="7dda0-121">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7dda0-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>  
 <span data-ttu-id="7dda0-122">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7dda0-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dda0-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7dda0-123">See also</span></span>
- [<span data-ttu-id="7dda0-124">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="7dda0-124">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
- [<span data-ttu-id="7dda0-125">Windows Forms DataGridView Denetiminde Varsayılan Klavye ve Fare Kullanımı</span><span class="sxs-lookup"><span data-stu-id="7dda0-125">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
