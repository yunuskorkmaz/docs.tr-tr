---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Veri Biçimlendirmeyi Özelleştirme'
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
ms.openlocfilehash: 948e9bf485b42b445491a4da9f8de7ae7974075c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592830"
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f16f2-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Veri Biçimlendirmeyi Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="f16f2-102">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f16f2-103">Aşağıdaki kod örneği için bir işleyici uygulamak gösterilmiştir <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> hücreler, sütunlar ve değerler bağlı olarak nasıl görüntüleneceğini değiştiren olay.</span><span class="sxs-lookup"><span data-stu-id="f16f2-103">The following code example demonstrates how to implement a handler for the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event that changes how cells are displayed depending on their columns and values.</span></span>  
  
 <span data-ttu-id="f16f2-104">İçinde hücreleri `Balance` negatif sayıları içeren sütun, kırmızı bir arka plan verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f16f2-104">Cells in the `Balance` column that contain negative numbers are given a red background.</span></span> <span data-ttu-id="f16f2-105">Bu hücre parantezler negatif değerleri görüntülemek için para birimi olarak da biçimlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f16f2-105">You can also format these cells as currency to display parentheses around negative values.</span></span> <span data-ttu-id="f16f2-106">Daha fazla bilgi için [nasıl yapılır: Verileri biçimlendirme Windows Forms DataGridView denetiminde](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f16f2-106">For more information, see [How to: Format Data in the Windows Forms DataGridView Control](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="f16f2-107">İçinde hücreleri `Priority` metinsel karşılık gelen yerine sütun ekran görüntüleri hücre değerleri.</span><span class="sxs-lookup"><span data-stu-id="f16f2-107">Cells in the `Priority` column display images in place of corresponding textual cell values.</span></span> <span data-ttu-id="f16f2-108"><xref:System.Windows.Forms.ConvertEventArgs.Value%2A> Özelliği <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> metinsel hücre değerini alın ve karşılık gelen görüntü görüntüleme değeri ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f16f2-108">The <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property of the <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> is used both to get the textual cell value and to set the corresponding image display value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f16f2-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="f16f2-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f16f2-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f16f2-110">Compiling the Code</span></span>  
 <span data-ttu-id="f16f2-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f16f2-111">This example requires:</span></span>  
  
- <span data-ttu-id="f16f2-112">Sistem, System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="f16f2-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="f16f2-113"><xref:System.Drawing.Bitmap> Adlandırılmış resimler `highPri.bmp`, `mediumPri.bmp`, ve `lowPri.bmp` yürütülebilir dosyayla aynı dizinde bulunan.</span><span class="sxs-lookup"><span data-stu-id="f16f2-113"><xref:System.Drawing.Bitmap> images named `highPri.bmp`, `mediumPri.bmp`, and `lowPri.bmp` residing in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f16f2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f16f2-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [<span data-ttu-id="f16f2-115">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f16f2-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f16f2-116">Nasıl yapılır: Verileri biçimlendirme Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="f16f2-116">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f16f2-117">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="f16f2-117">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f16f2-118">Windows Forms DataGridView Denetiminde Veri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="f16f2-118">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
