---
title: "Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Biçimlendirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 49d5172b2638a7ac3a6a7bf005932ba4b3f9aba3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b276e-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="b276e-102">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b276e-103">Aşağıdaki yordamları kullanarak hücre değerlerini temel biçimlendirme göstermek <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> özelliği bir <xref:System.Windows.Forms.DataGridView> denetim ve bir denetiminde belirli sütunların.</span><span class="sxs-lookup"><span data-stu-id="b276e-103">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="b276e-104">Gelişmiş veri biçimlendirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b276e-104">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="b276e-105">Biçim para birimi ve tarih değerleri</span><span class="sxs-lookup"><span data-stu-id="b276e-105">To format currency and date values</span></span>  
  
-   <span data-ttu-id="b276e-106">Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="b276e-106">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="b276e-107">Aşağıdaki kod örneğinde biçimini kullanarak belirli sütunlar için ayarlar <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> sütunların özellik.</span><span class="sxs-lookup"><span data-stu-id="b276e-107">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="b276e-108">Değerler `UnitPrice` sütun ayraç içinde kullanılması negatif değerler ile geçerli kültüre özgü para birimi biçiminde görünür.</span><span class="sxs-lookup"><span data-stu-id="b276e-108">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="b276e-109">Değerler `ShipDate` sütun geçerli kültüre özgü kısa tarih biçiminde görünür.</span><span class="sxs-lookup"><span data-stu-id="b276e-109">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="b276e-110">Hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> değerler, bakın [biçimlendirme türleri](../../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="b276e-110">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="b276e-111">Null veritabanı değerlerini görüntüsünü özelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="b276e-111">To customize the display of null database values</span></span>  
  
-   <span data-ttu-id="b276e-112">Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="b276e-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="b276e-113">Aşağıdaki kod örneğinde <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> eşit değerlerini içeren tüm hücrelerdeki "Giriş" görüntülenecek özellik <xref:System.DBNull.Value?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b276e-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="b276e-114">Hücrelerde metin tabanlı wordWrap etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="b276e-114">To enable wordwrap in text-based cells</span></span>  
  
-   <span data-ttu-id="b276e-115">Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle> birine <xref:System.Windows.Forms.DataGridViewTriState> numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="b276e-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="b276e-116">Aşağıdaki kod örneğinde <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> tüm denetim kaydırma modu ayarlamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="b276e-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="b276e-117">DataGridView hücrelerinde metin hizalamasını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="b276e-117">To specify the text alignment of DataGridView cells</span></span>  
  
-   <span data-ttu-id="b276e-118">Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle> birine <xref:System.Windows.Forms.DataGridViewContentAlignment> numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="b276e-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="b276e-119">Aşağıdaki kod örneği kullanarak bir özel sütun için hizalama ayarlar <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> sütunun özelliği.</span><span class="sxs-lookup"><span data-stu-id="b276e-119">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="b276e-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="b276e-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b276e-121">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b276e-121">Compiling the Code</span></span>  
 <span data-ttu-id="b276e-122">Bu örnekler gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b276e-122">These examples require:</span></span>  
  
-   <span data-ttu-id="b276e-123">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `UnitPrice`, adlı bir sütun `ShipDate`ve adlı bir sütun `CustomerName`.</span><span class="sxs-lookup"><span data-stu-id="b276e-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
-   <span data-ttu-id="b276e-124">Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="b276e-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b276e-125">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="b276e-125">Robust Programming</span></span>  
 <span data-ttu-id="b276e-126">En yüksek ölçeklenebilirlik için paylaşması gerekir <xref:System.Windows.Forms.DataGridViewCellStyle> birden çok satırları, sütunları veya ayrı ayrı her öğe için stil özelliklerini ayarlama yerine aynı stilleri kullanın hücreleri nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b276e-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="b276e-127">Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b276e-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b276e-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b276e-128">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [<span data-ttu-id="b276e-129">Temel biçimlendirme ve stil oluşturma Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="b276e-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="b276e-130">Windows Forms DataGridView denetimindeki hücre stilleri</span><span class="sxs-lookup"><span data-stu-id="b276e-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="b276e-131">Veri biçimlendirmeyi Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="b276e-131">Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="b276e-132">Nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b276e-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="b276e-133">Biçimlendirme türleri</span><span class="sxs-lookup"><span data-stu-id="b276e-133">Formatting Types</span></span>](../../../../docs/standard/base-types/formatting-types.md)
