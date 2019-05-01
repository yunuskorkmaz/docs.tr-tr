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
ms.openlocfilehash: 1836fbc1887082ca685c49bef2bc42bdb167578f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902258"
---
# <a name="selection-and-clipboard-use-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="dcdf8-102">Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı</span><span class="sxs-lookup"><span data-stu-id="dcdf8-102">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="dcdf8-103">`DataGridView` Denetim çeşitli kullanıcılar hücreler, satırlar ve sütunlarla nasıl seçebilir yapılandırma seçenekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="dcdf8-103">The `DataGridView` control provides you with a variety of options for configuring how users can select cells, rows, and columns.</span></span> <span data-ttu-id="dcdf8-104">Kullanıcılar kendi üst bilgileri tıkladığınızda gibi tek veya birden çok seçim, tüm satırları veya kullanıcılar hücreleri tıkladığınızda sütun seçimi ya da tüm satırları veya sütunları seçimi hücre seçimi sağlayan etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dcdf8-104">For example, you can enable single or multiple selection, selection of whole rows or columns when users click cells, or selection of whole rows or columns only when users click their headers, which enables cell selection as well.</span></span> <span data-ttu-id="dcdf8-105">Seçimi için kendi kullanıcı arabirimini sağlamak istiyorsanız, sıradan seçimi devre dışı bırakabilir ve tüm seçimi programlı olarak işleme.</span><span class="sxs-lookup"><span data-stu-id="dcdf8-105">If you want to provide your own user interface for selection, you can disable ordinary selection and handle all selection programmatically.</span></span> <span data-ttu-id="dcdf8-106">Ayrıca, kullanıcıların seçilen değerleri panoya kopyalamak etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dcdf8-106">Additionally, you can enable users to copy the selected values to the Clipboard.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dcdf8-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="dcdf8-107">In This Section</span></span>  
 [<span data-ttu-id="dcdf8-108">Windows Forms DataGridView Denetimindeki Seçim Modları</span><span class="sxs-lookup"><span data-stu-id="dcdf8-108">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="dcdf8-109">Kullanıcı ve programlı seçiminde denetim seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="dcdf8-109">Describes the options for user and programmatic selection in the control.</span></span>  
  
 [<span data-ttu-id="dcdf8-110">Nasıl yapılır: Windows Forms DataGridView denetiminin seçim modunu ayarlama</span><span class="sxs-lookup"><span data-stu-id="dcdf8-110">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="dcdf8-111">Bir kullanıcı bir hücreye tıkladığında denetim tek satır seçimi için yapılandırılması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dcdf8-111">Describes how to configure the control for single-row selection when a user clicks a cell.</span></span>  
  
 [<span data-ttu-id="dcdf8-112">Nasıl yapılır: Windows Forms DataGridView denetiminde seçili hücre, satır ve sütunları alma</span><span class="sxs-lookup"><span data-stu-id="dcdf8-112">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](selected-cells-rows-and-columns-datagridview.md)  
 <span data-ttu-id="dcdf8-113">Seçili hücre, satır ve sütun koleksiyonlarla çalışma açıklar.</span><span class="sxs-lookup"><span data-stu-id="dcdf8-113">Describes how to work with the selected cell, row, and column collections.</span></span>  
  
 [<span data-ttu-id="dcdf8-114">Nasıl yapılır: Kullanıcıların Windows Forms DataGridView denetiminden panoya birden fazla hücre kopyalamasına olanak</span><span class="sxs-lookup"><span data-stu-id="dcdf8-114">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>](enable-users-to-copy-multiple-cells-to-the-clipboard-datagridview.md)  
 <span data-ttu-id="dcdf8-115">Denetimdeki Pano desteğini nasıl etkinleştireceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="dcdf8-115">Describes how to enable Clipboard support in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="dcdf8-116">Başvuru</span><span class="sxs-lookup"><span data-stu-id="dcdf8-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="dcdf8-117">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="dcdf8-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="dcdf8-118">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="dcdf8-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <span data-ttu-id="dcdf8-119">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="dcdf8-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>  
 <span data-ttu-id="dcdf8-120">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dcdf8-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>  
 <span data-ttu-id="dcdf8-121">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dcdf8-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>  
 <span data-ttu-id="dcdf8-122">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dcdf8-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcdf8-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dcdf8-123">See also</span></span>

- [<span data-ttu-id="dcdf8-124">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="dcdf8-124">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="dcdf8-125">Windows Forms DataGridView Denetiminde Varsayılan Klavye ve Fare Kullanımı</span><span class="sxs-lookup"><span data-stu-id="dcdf8-125">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
