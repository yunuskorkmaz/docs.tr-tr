---
title: Windows Forms DataGridView Denetiminde Hücreler, Satırlar ve Sütunlarla Programlama
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], elements
- columns [Windows Forms], data grids
- cells [Windows Forms], data grids
- DataGridView control [Windows Forms], programming with grid elements
- rows [Windows Forms], data grids
ms.assetid: 0d76f7e4-4149-42c6-9118-bb37d6669dc5
ms.openlocfilehash: f87d1e2744ffcd81f5711991880deb1fe5edd2a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538547"
---
# <a name="programming-with-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a546d-102">Windows Forms DataGridView Denetiminde Hücreler, Satırlar ve Sütunlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="a546d-102">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a546d-103">Bu bölümde hücre, satır ve sütun nesneleri içeren çeşitli programlama görevleri gösteren konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="a546d-103">This section provides topics that demonstrate various programming tasks involving cell, row, and column objects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a546d-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a546d-104">In This Section</span></span>  
 [<span data-ttu-id="a546d-105">Nasıl yapılır: Bir Windows Forms DataGridView Denetiminde Ayrı Hücrelere ToolTips Ekleme</span><span class="sxs-lookup"><span data-stu-id="a546d-105">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/add-tooltips-to-individual-cells-in-a-wf-datagridview-control.md)  
 <span data-ttu-id="a546d-106">Nasıl yapılacağını açıklar <xref:System.Windows.Forms.DataGridView.CellFormatting> farklı araç ipuçları için tek tek hücreler sağlamak için olay.</span><span class="sxs-lookup"><span data-stu-id="a546d-106">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting> event to provide different ToolTips for individual cells.</span></span>  
  
 [<span data-ttu-id="a546d-107">Nasıl yapılır: Bir Windows Forms DataGridView Denetiminin Bir Hücresindeki Değişikliklere Dayalı Olarak Özel Eylem Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="a546d-107">How to: Perform a Custom Action Based on Changes in a Cell of a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/perform-a-custom-action-based-on-changes-in-a-cell-of-a-datagrid.md)  
 <span data-ttu-id="a546d-108">Nasıl yapılacağını açıklar <xref:System.Windows.Forms.DataGridView.CellValueChanged> ve <xref:System.Windows.Forms.DataGridView.CellStateChanged> olaylar.</span><span class="sxs-lookup"><span data-stu-id="a546d-108">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellValueChanged> and <xref:System.Windows.Forms.DataGridView.CellStateChanged> events.</span></span>  
  
 [<span data-ttu-id="a546d-109">Nasıl yapılır: Windows Forms DataGridView Denetiminde Bantları Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="a546d-109">How to: Manipulate Bands in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-manipulate-bands-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a546d-110">Türündeki nesnelerle program açıklar <xref:System.Windows.Forms.DataGridViewBand>, satırları ve sütunları için temel tür değil.</span><span class="sxs-lookup"><span data-stu-id="a546d-110">Describes how to program with objects of type <xref:System.Windows.Forms.DataGridViewBand>, which is the base type for rows and columns.</span></span>  
  
 [<span data-ttu-id="a546d-111">Nasıl yapılır: Windows Forms DataGridView Denetiminde Satırları Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="a546d-111">How to: Manipulate Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-manipulate-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a546d-112">Türündeki nesnelerle program açıklar `DataGridViewRow`.</span><span class="sxs-lookup"><span data-stu-id="a546d-112">Describes how to program with objects of type `DataGridViewRow`.</span></span>  
  
 [<span data-ttu-id="a546d-113">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="a546d-113">How to: Manipulate Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-manipulate-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a546d-114">Türündeki nesnelerle program açıklar `DataGridViewColumn`.</span><span class="sxs-lookup"><span data-stu-id="a546d-114">Describes how to program with objects of type `DataGridViewColumn`.</span></span>  
  
 [<span data-ttu-id="a546d-115">Nasıl yapılır: Windows Forms DataGridView Denetiminde Görüntü Sütunlarıyla Çalışma</span><span class="sxs-lookup"><span data-stu-id="a546d-115">How to: Work with Image Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="a546d-116">İle programlamayı açıklamaktadır `DataGridViewImageColumn` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a546d-116">Describes how to program with the `DataGridViewImageColumn` class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a546d-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a546d-117">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="a546d-118">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="a546d-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="a546d-119">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewCell> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a546d-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="a546d-120">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewRow> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a546d-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="a546d-121">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewColumn> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a546d-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a546d-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a546d-122">Related Sections</span></span>  
 [<span data-ttu-id="a546d-123">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="a546d-123">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="a546d-124">Yaygın olarak açıklayan konulara hücre, satır ve sütun özelliklerinin kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a546d-124">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a546d-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a546d-125">See Also</span></span>  
 [<span data-ttu-id="a546d-126">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="a546d-126">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="a546d-127">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="a546d-127">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
