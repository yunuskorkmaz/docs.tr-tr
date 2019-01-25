---
title: Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], basic features
- columns [Windows Forms], DataGridView control
- data grids [Windows Forms], examples
- DataGridView control [Windows Forms], examples
ms.assetid: 78085f26-d5d2-4b75-813e-e932b72fd06f
ms.openlocfilehash: af8dcaf8b6d32f03c2f2f46312d1290a99381c43
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611507"
---
# <a name="basic-column-row-and-cell-features-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="191c3-102">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="191c3-102">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="191c3-103">Birçok temel davranışlarını `DataGridView` hücreler, satırlar ve sütunlarla tek özelliklerini ayarlayarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="191c3-103">Many basic behaviors of `DataGridView` cells, rows, and columns can be modified by setting single properties.</span></span> <span data-ttu-id="191c3-104">Bu bölümdeki konularda en yaygın olarak kullanılan bu özelliklerin bazıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="191c3-104">The topics in this section describe several of the most commonly used of these features.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="191c3-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="191c3-105">In This Section</span></span>  
 [<span data-ttu-id="191c3-106">Nasıl yapılır: Windows Forms DataGridView denetiminde sütunları gizleme</span><span class="sxs-lookup"><span data-stu-id="191c3-106">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="191c3-107">Belirli sütunları denetiminde görünmesini engellemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="191c3-107">Describes how to prevent specific columns from appearing in the control.</span></span>  
  
 [<span data-ttu-id="191c3-108">Nasıl yapılır: Windows Forms DataGridView denetiminde sütun başlıklarını gizleme</span><span class="sxs-lookup"><span data-stu-id="191c3-108">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-column-headers-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="191c3-109">Sütun başlıklarını denetiminde görünmesini engellemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="191c3-109">Describes how to prevent the column headers from appearing in the control.</span></span>  
  
 [<span data-ttu-id="191c3-110">Nasıl yapılır: Windows Forms DataGridView denetiminde sütunları yeniden sıralamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="191c3-110">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="191c3-111">Kullanıcıların denetiminde sütunları yeniden etkinleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="191c3-111">Describes how to enable users to rearrange columns in the control.</span></span>  
  
 [<span data-ttu-id="191c3-112">Nasıl yapılır: Windows Forms DataGridView denetiminde sütunları dondurma</span><span class="sxs-lookup"><span data-stu-id="191c3-112">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="191c3-113">Açıklayan nasıl bir veya daha fazla bitişik sütunlar kaymasını engellemek.</span><span class="sxs-lookup"><span data-stu-id="191c3-113">Describes how prevent one or more adjacent columns from scrolling.</span></span>  
  
 [<span data-ttu-id="191c3-114">Nasıl yapılır: Salt okunur Windows Forms DataGridView denetiminde sütunları olun</span><span class="sxs-lookup"><span data-stu-id="191c3-114">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="191c3-115">Kullanıcıların belirli sütunları denetiminde düzenlemesini önlemek nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="191c3-115">Describes how to prevent users from editing specific columns in the control.</span></span>  
  
 [<span data-ttu-id="191c3-116">Nasıl yapılır: Satır eklemeyi ve silmeyi Windows Forms DataGridView denetiminde engelle</span><span class="sxs-lookup"><span data-stu-id="191c3-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)  
 <span data-ttu-id="191c3-117">Kullanıcılar satırları eklemesini engellemek için denetim altındaki yeni kayıtlar için satır kaldırmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="191c3-117">Describes how to remove the row for new records at the bottom of the control to prevent users from adding rows.</span></span> <span data-ttu-id="191c3-118">Ayrıca kullanıcılar satırları silmesini engeller açıklar.</span><span class="sxs-lookup"><span data-stu-id="191c3-118">Also describes how to prevent users from deleting rows.</span></span>  
  
 [<span data-ttu-id="191c3-119">Nasıl yapılır: Alma ve Windows Forms DataGridView denetiminde geçerli hücreyi ayarlama</span><span class="sxs-lookup"><span data-stu-id="191c3-119">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/get-and-set-the-current-cell-wf-datagridview-control.md)  
 <span data-ttu-id="191c3-120">Erişim denetimi odağa sahip hücre açıklar.</span><span class="sxs-lookup"><span data-stu-id="191c3-120">Describes how to access the cell that currently has focus in the control.</span></span>  
  
 [<span data-ttu-id="191c3-121">Nasıl yapılır: Windows Forms DataGridView denetiminin hücrelerinde görüntü görüntüleme</span><span class="sxs-lookup"><span data-stu-id="191c3-121">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="191c3-122">Her hücre bir simge görüntüleyen bir görüntü sütunu oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="191c3-122">Describes how to create an image column that displays an icon in every cell.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="191c3-123">Başvuru</span><span class="sxs-lookup"><span data-stu-id="191c3-123">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="191c3-124">Denetim için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="191c3-124">Provides reference documentation for the control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="191c3-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="191c3-125">Related Sections</span></span>  
 [<span data-ttu-id="191c3-126">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="191c3-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="191c3-127">Denetiminin temel görünümünü ve görüntü hücre verilerin biçimlendirmesini değiştirme açıklayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="191c3-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="191c3-128">Windows Forms DataGridView Denetiminde Hücreler, Satırlar ve Sütunlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="191c3-128">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="191c3-129">Hücre, satır ve sütun nesneleri ile program açıklayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="191c3-129">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="191c3-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="191c3-130">See also</span></span>
- [<span data-ttu-id="191c3-131">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="191c3-131">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
- [<span data-ttu-id="191c3-132">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="191c3-132">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
