---
title: "Windows Forms DataGridView Denetiminde Hücreler, Satırlar ve Sütunlarla Programlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], elements
- columns [Windows Forms], data grids
- cells [Windows Forms], data grids
- DataGridView control [Windows Forms], programming with grid elements
- rows [Windows Forms], data grids
ms.assetid: 0d76f7e4-4149-42c6-9118-bb37d6669dc5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 313867b76d569fb98b1bd5d46c658763d0020726
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="programming-with-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b89f2-102">Windows Forms DataGridView Denetiminde Hücreler, Satırlar ve Sütunlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="b89f2-102">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b89f2-103">Bu bölümde hücre, satır ve sütun nesneleri içeren çeşitli programlama görevleri gösteren konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="b89f2-103">This section provides topics that demonstrate various programming tasks involving cell, row, and column objects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b89f2-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b89f2-104">In This Section</span></span>  
 [<span data-ttu-id="b89f2-105">Nasıl yapılır: araç ipuçlarını ayrı hücrelere bir Windows Forms DataGridView denetiminde ekleme</span><span class="sxs-lookup"><span data-stu-id="b89f2-105">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/add-tooltips-to-individual-cells-in-a-wf-datagridview-control.md)  
 <span data-ttu-id="b89f2-106">Nasıl yapılacağını açıklar <xref:System.Windows.Forms.DataGridView.CellFormatting> farklı araç ipuçları için tek tek hücreler sağlamak için olay.</span><span class="sxs-lookup"><span data-stu-id="b89f2-106">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting> event to provide different ToolTips for individual cells.</span></span>  
  
 [<span data-ttu-id="b89f2-107">Nasıl yapılır: Windows Forms DataGridView denetiminin bir hücresindeki değişikliklere dayalı olarak özel eylem gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="b89f2-107">How to: Perform a Custom Action Based on Changes in a Cell of a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/perform-a-custom-action-based-on-changes-in-a-cell-of-a-datagrid.md)  
 <span data-ttu-id="b89f2-108">Nasıl yapılacağını açıklar <xref:System.Windows.Forms.DataGridView.CellValueChanged> ve <xref:System.Windows.Forms.DataGridView.CellStateChanged> olaylar.</span><span class="sxs-lookup"><span data-stu-id="b89f2-108">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellValueChanged> and <xref:System.Windows.Forms.DataGridView.CellStateChanged> events.</span></span>  
  
 [<span data-ttu-id="b89f2-109">Nasıl yapılır: Windows Forms DataGridView denetiminde bantları yönlendirme</span><span class="sxs-lookup"><span data-stu-id="b89f2-109">How to: Manipulate Bands in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-manipulate-bands-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b89f2-110">Türündeki nesnelerle program açıklar <xref:System.Windows.Forms.DataGridViewBand>, satırları ve sütunları için temel tür değil.</span><span class="sxs-lookup"><span data-stu-id="b89f2-110">Describes how to program with objects of type <xref:System.Windows.Forms.DataGridViewBand>, which is the base type for rows and columns.</span></span>  
  
 [<span data-ttu-id="b89f2-111">Nasıl yapılır: Windows Forms DataGridView denetiminde satırları yönlendirme</span><span class="sxs-lookup"><span data-stu-id="b89f2-111">How to: Manipulate Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-manipulate-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b89f2-112">Türündeki nesnelerle program açıklar `DataGridViewRow`.</span><span class="sxs-lookup"><span data-stu-id="b89f2-112">Describes how to program with objects of type `DataGridViewRow`.</span></span>  
  
 [<span data-ttu-id="b89f2-113">Nasıl yapılır: Windows Forms DataGridView denetiminde sütunları yönlendirme</span><span class="sxs-lookup"><span data-stu-id="b89f2-113">How to: Manipulate Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-manipulate-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b89f2-114">Türündeki nesnelerle program açıklar `DataGridViewColumn`.</span><span class="sxs-lookup"><span data-stu-id="b89f2-114">Describes how to program with objects of type `DataGridViewColumn`.</span></span>  
  
 [<span data-ttu-id="b89f2-115">Nasıl yapılır: Windows Forms DataGridView denetiminde görüntü sütunlarıyla çalışma</span><span class="sxs-lookup"><span data-stu-id="b89f2-115">How to: Work with Image Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b89f2-116">İle programlamayı açıklamaktadır `DataGridViewImageColumn` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b89f2-116">Describes how to program with the `DataGridViewImageColumn` class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b89f2-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="b89f2-117">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="b89f2-118">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="b89f2-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="b89f2-119">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewCell> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b89f2-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="b89f2-120">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewRow> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b89f2-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="b89f2-121">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewColumn> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b89f2-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b89f2-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b89f2-122">Related Sections</span></span>  
 [<span data-ttu-id="b89f2-123">Temel sütun, satır ve hücre özellikleri Windows Forms DataGridView denetiminde</span><span class="sxs-lookup"><span data-stu-id="b89f2-123">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="b89f2-124">Yaygın olarak açıklayan konulara hücre, satır ve sütun özelliklerinin kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b89f2-124">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b89f2-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b89f2-125">See Also</span></span>  
 [<span data-ttu-id="b89f2-126">DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="b89f2-126">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="b89f2-127">Windows Forms DataGridView denetiminde sütun türleri</span><span class="sxs-lookup"><span data-stu-id="b89f2-127">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
