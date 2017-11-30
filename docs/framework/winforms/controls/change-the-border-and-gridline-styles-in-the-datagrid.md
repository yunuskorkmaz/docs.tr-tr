---
title: "Nasıl yapılır: Windows Forms DataGridView Denetiminde Kenarlık ve Kılavuz Çizgi Stillerini Değiştirme"
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
- gridlines [Windows Forms], changing styles
- data grids [Windows Forms], changing gridline styles
- DataGridView control [Windows Forms], border styles
- data grids [Windows Forms], changing border styles
- DataGridView control [Windows Forms], gridline styles
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ebe73e0c29a211e3319998ef7acd14e78e4eb14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="2401e-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Kenarlık ve Kılavuz Çizgi Stillerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="2401e-102">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="2401e-103">İle <xref:System.Windows.Forms.DataGridView> denetim, denetimin kenarlık ve kullanıcı deneyimini geliştirmek için kılavuz çizgilerini görünümünü özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2401e-103">With the <xref:System.Windows.Forms.DataGridView> control, you can customize the appearance of the control's border and gridlines to improve the user experience.</span></span> <span data-ttu-id="2401e-104">Kılavuz çizgisi rengi ve denetim hücrelerde kenarlık stilleri yanı sıra Denetim kenarlık stili değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2401e-104">You can modify the gridline color and the control border style in addition to the border styles for the cells within the control.</span></span> <span data-ttu-id="2401e-105">Ayrıca, farklı bir hücre kenarlık stilleri sıradan hücre, Satır üstbilgisi hücreleri ve sütun başlığı hücreleri uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2401e-105">You can also apply different cell border styles for ordinary cells, row header cells, and column header cells.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2401e-106">Kılavuz çizgisi rengi yalnızca kullanılan <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, ve <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> değerlerini <xref:System.Windows.Forms.DataGridViewCellBorderStyle> numaralandırma ve <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> değerini <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="2401e-106">The gridline color is used only with the <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, and <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> values of the <xref:System.Windows.Forms.DataGridViewCellBorderStyle> enumeration and the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> value of the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> enumeration.</span></span> <span data-ttu-id="2401e-107">Bu numaralandırma, diğer değerler işletim sistemi tarafından belirtilen renkleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="2401e-107">The other values of these enumerations use colors specified by the operating system.</span></span> <span data-ttu-id="2401e-108">Ayrıca, ne zaman görsel stiller Windows XP ve Windows Server 2003 ailesinde aracılığıyla etkinleştirilir <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi, <xref:System.Windows.Forms.DataGridView.GridColor%2A> özellik değeri kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="2401e-108">Additionally, when visual styles are enabled on Windows XP and the Windows Server 2003 family through the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method, the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property value is not used.</span></span>  
  
### <a name="to-change-the-gridline-color-programmatically"></a><span data-ttu-id="2401e-109">Kılavuz çizgisi rengi programlı olarak değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="2401e-109">To change the gridline color programmatically</span></span>  
  
-   <span data-ttu-id="2401e-110">Ayarlama <xref:System.Windows.Forms.DataGridView.GridColor%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2401e-110">Set the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a><span data-ttu-id="2401e-111">Tüm DataGridView denetiminin kenarlık stili programlı olarak değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="2401e-111">To change the border style of the entire DataGridView control programmatically</span></span>  
  
-   <span data-ttu-id="2401e-112">Ayarlama <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> özelliğini birine <xref:System.Windows.Forms.BorderStyle> numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="2401e-112">Set the <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> property to one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a><span data-ttu-id="2401e-113">DataGridView hücrelerinde kenarlık stilleri programlı olarak değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="2401e-113">To change the border styles for DataGridView cells programmatically</span></span>  
  
-   <span data-ttu-id="2401e-114">Ayarlama <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, ve <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="2401e-114">Set the <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, and <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a><span data-ttu-id="2401e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="2401e-115">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2401e-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2401e-116">Compiling the Code</span></span>  
 <span data-ttu-id="2401e-117">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="2401e-117">This example requires:</span></span>  
  
-   <span data-ttu-id="2401e-118">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="2401e-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="2401e-119">Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, ve <xref:System.Drawing?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="2401e-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2401e-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2401e-120">See Also</span></span>  
 <xref:System.Windows.Forms.BorderStyle>  
 <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellBorderStyle>  
 <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>  
 [<span data-ttu-id="2401e-121">Temel biçimlendirme ve stil oluşturma Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="2401e-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
