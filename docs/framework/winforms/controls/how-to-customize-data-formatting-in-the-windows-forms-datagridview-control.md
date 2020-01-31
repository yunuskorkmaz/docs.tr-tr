---
title: DataGridView Denetiminde Veri biçimlendirmeyi özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], changing colors in DataGridView control [Windows Forms]
- colors [Windows Forms], changing in DataGridView control [Windows Forms]
- data [Windows Forms], formatting in DataGridView control
- DataGridView control [Windows Forms], cell customization
- DataGridView control [Windows Forms], changing cell colors
- Windows Forms, changing colors of DataGridView cells
- DataGridView control [Windows Forms], substituting cell values for display
- data grids [Windows Forms], formatting data
ms.assetid: a6e72c70-ce18-425f-828d-d57be6f96ab6
ms.openlocfilehash: 6bc1a65b876df842df322db165dc08fcc0c931dc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746783"
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="97b09-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Veri Biçimlendirmeyi Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="97b09-102">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="97b09-103">Aşağıdaki kod örneği, sütunlarının ve değerlerine göre hücrelerin nasıl görüntülendiğini değiştiren <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olayı için bir işleyicinin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="97b09-103">The following code example demonstrates how to implement a handler for the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event that changes how cells are displayed depending on their columns and values.</span></span>  
  
 <span data-ttu-id="97b09-104">Negatif sayılar içeren `Balance` sütununda bulunan hücrelere kırmızı bir arka plan verilir.</span><span class="sxs-lookup"><span data-stu-id="97b09-104">Cells in the `Balance` column that contain negative numbers are given a red background.</span></span> <span data-ttu-id="97b09-105">Bu hücreleri negatif değerlerin etrafında parantez göstermek için para birimi olarak da biçimlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97b09-105">You can also format these cells as currency to display parentheses around negative values.</span></span> <span data-ttu-id="97b09-106">Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki verileri biçimlendirme](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="97b09-106">For more information, see [How to: Format Data in the Windows Forms DataGridView Control](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="97b09-107">`Priority` sütunundaki hücreler, ilgili metin hücresi değerlerinin yerine görüntüleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="97b09-107">Cells in the `Priority` column display images in place of corresponding textual cell values.</span></span> <span data-ttu-id="97b09-108"><xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> özelliği, her ikisi de metin hücresi değerini almak ve ilgili görüntü görüntüleme değerini ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97b09-108">The <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property of the <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> is used both to get the textual cell value and to set the corresponding image display value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97b09-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="97b09-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="97b09-110">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="97b09-110">Compiling the Code</span></span>  
 <span data-ttu-id="97b09-111">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="97b09-111">This example requires:</span></span>  
  
- <span data-ttu-id="97b09-112">System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="97b09-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="97b09-113">yürütülebilir dosya ile aynı dizinde bulunan `highPri.bmp`, `mediumPri.bmp`ve `lowPri.bmp` adlı görüntüleri <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="97b09-113"><xref:System.Drawing.Bitmap> images named `highPri.bmp`, `mediumPri.bmp`, and `lowPri.bmp` residing in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97b09-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97b09-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [<span data-ttu-id="97b09-115">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="97b09-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="97b09-116">Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="97b09-116">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="97b09-117">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="97b09-117">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="97b09-118">Windows Forms DataGridView Denetiminde Veri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="97b09-118">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
