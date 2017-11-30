---
title: "Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], basic features
- columns [Windows Forms], DataGridView control
- data grids [Windows Forms], examples
- DataGridView control [Windows Forms], examples
ms.assetid: 78085f26-d5d2-4b75-813e-e932b72fd06f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eebd0f36fbf1bf3bfc37b8fa836d318a9b8ac007
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="basic-column-row-and-cell-features-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="c315c-102">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="c315c-102">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c315c-103">Birçok temel davranışlarını `DataGridView` hücrelerini, satırları ve sütunları tek özelliklerini ayarlayarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c315c-103">Many basic behaviors of `DataGridView` cells, rows, and columns can be modified by setting single properties.</span></span> <span data-ttu-id="c315c-104">Bu bölümdeki konular, en yaygın olarak kullanılan bu özelliklerin bazıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c315c-104">The topics in this section describe several of the most commonly used of these features.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c315c-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c315c-105">In This Section</span></span>  
 [<span data-ttu-id="c315c-106">Nasıl yapılır: Gizle sütunları Windows Forms DataGridView denetiminde</span><span class="sxs-lookup"><span data-stu-id="c315c-106">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c315c-107">Belirli sütunları denetiminde görünmesini engellemek üzere açıklar.</span><span class="sxs-lookup"><span data-stu-id="c315c-107">Describes how to prevent specific columns from appearing in the control.</span></span>  
  
 [<span data-ttu-id="c315c-108">Nasıl yapılır: sütun başlıklarını gizleme Windows Forms DataGridView denetiminde</span><span class="sxs-lookup"><span data-stu-id="c315c-108">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-column-headers-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c315c-109">Sütun üstbilgileri denetiminde görünmesini engellemek üzere açıklar.</span><span class="sxs-lookup"><span data-stu-id="c315c-109">Describes how to prevent the column headers from appearing in the control.</span></span>  
  
 [<span data-ttu-id="c315c-110">Nasıl yapılır: Windows Forms DataGridView denetiminde sütun yeniden sıralamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="c315c-110">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c315c-111">Kullanıcıların denetiminde sütunları yeniden etkinleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c315c-111">Describes how to enable users to rearrange columns in the control.</span></span>  
  
 [<span data-ttu-id="c315c-112">Nasıl yapılır: sütunları dondurma Windows Forms DataGridView denetiminde</span><span class="sxs-lookup"><span data-stu-id="c315c-112">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c315c-113">Açıklar nasıl bir veya birden çok bitişik sütunlar kaymasını engellemek.</span><span class="sxs-lookup"><span data-stu-id="c315c-113">Describes how prevent one or more adjacent columns from scrolling.</span></span>  
  
 [<span data-ttu-id="c315c-114">Nasıl yapılır: yapma sütunları salt okunur Windows Forms DataGridView denetiminde</span><span class="sxs-lookup"><span data-stu-id="c315c-114">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c315c-115">Kullanıcıların belirli sütunlardaki denetimi düzenlemesini önlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="c315c-115">Describes how to prevent users from editing specific columns in the control.</span></span>  
  
 [<span data-ttu-id="c315c-116">Nasıl yapılır: satır ekleme ve engelleme silme Windows Forms DataGridView denetiminde</span><span class="sxs-lookup"><span data-stu-id="c315c-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)  
 <span data-ttu-id="c315c-117">Kullanıcıların satırları eklenmesini önlemek için denetim altındaki yeni kayıtlar için satır kaldırmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c315c-117">Describes how to remove the row for new records at the bottom of the control to prevent users from adding rows.</span></span> <span data-ttu-id="c315c-118">Ayrıca kullanıcıların satırları silmesini önlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="c315c-118">Also describes how to prevent users from deleting rows.</span></span>  
  
 [<span data-ttu-id="c315c-119">Nasıl yapılır: alma ve Windows Forms DataGridView denetiminde geçerli hücreyi ayarlama</span><span class="sxs-lookup"><span data-stu-id="c315c-119">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/get-and-set-the-current-cell-wf-datagridview-control.md)  
 <span data-ttu-id="c315c-120">Erişim denetimi odağa sahip hücre açıklar.</span><span class="sxs-lookup"><span data-stu-id="c315c-120">Describes how to access the cell that currently has focus in the control.</span></span>  
  
 [<span data-ttu-id="c315c-121">Nasıl yapılır: Windows hücrelerinde görüntü görüntüleme Forms DataGridView denetiminde</span><span class="sxs-lookup"><span data-stu-id="c315c-121">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c315c-122">Bir simge her hücre görüntüler bir görüntü sütunu oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c315c-122">Describes how to create an image column that displays an icon in every cell.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c315c-123">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c315c-123">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="c315c-124">Başvuru belgeleri denetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c315c-124">Provides reference documentation for the control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c315c-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c315c-125">Related Sections</span></span>  
 [<span data-ttu-id="c315c-126">Temel biçimlendirme ve stil oluşturma Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="c315c-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c315c-127">Temel denetimin görünümünü ve görüntü hücre verilerin biçimlendirmesini değiştirme açıklayan konulara sağlar.</span><span class="sxs-lookup"><span data-stu-id="c315c-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="c315c-128">Hücrelerini, satırları ve sütunları Windows Forms DataGridView denetiminde ile programlama</span><span class="sxs-lookup"><span data-stu-id="c315c-128">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="c315c-129">Hücre, satır ve sütun nesneleri ile programlamayı açıklayan konulara sağlar.</span><span class="sxs-lookup"><span data-stu-id="c315c-129">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c315c-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c315c-130">See Also</span></span>  
 [<span data-ttu-id="c315c-131">DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="c315c-131">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="c315c-132">Windows Forms DataGridView denetiminde sütun türleri</span><span class="sxs-lookup"><span data-stu-id="c315c-132">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
