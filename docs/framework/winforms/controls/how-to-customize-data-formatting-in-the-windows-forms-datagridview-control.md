---
title: 'Nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme'
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
ms.openlocfilehash: 4a7e74afa985d36281994078bd0ea464f084cfa9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714911"
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a9f5f-102">Nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="a9f5f-102">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a9f5f-103">Aşağıdaki kod örneği için bir işleyici uygulamak gösterilmiştir <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> hücreler, sütunlar ve değerler bağlı olarak nasıl görüntüleneceğini değiştiren olay.</span><span class="sxs-lookup"><span data-stu-id="a9f5f-103">The following code example demonstrates how to implement a handler for the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event that changes how cells are displayed depending on their columns and values.</span></span>  
  
 <span data-ttu-id="a9f5f-104">İçinde hücreleri `Balance` negatif sayıları içeren sütun, kırmızı bir arka plan verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a9f5f-104">Cells in the `Balance` column that contain negative numbers are given a red background.</span></span> <span data-ttu-id="a9f5f-105">Bu hücre parantezler negatif değerleri görüntülemek için para birimi olarak da biçimlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9f5f-105">You can also format these cells as currency to display parentheses around negative values.</span></span> <span data-ttu-id="a9f5f-106">Daha fazla bilgi için [nasıl yapılır: Verileri biçimlendirme Windows Forms DataGridView denetiminde](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="a9f5f-106">For more information, see [How to: Format Data in the Windows Forms DataGridView Control](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="a9f5f-107">İçinde hücreleri `Priority` metinsel karşılık gelen yerine sütun ekran görüntüleri hücre değerleri.</span><span class="sxs-lookup"><span data-stu-id="a9f5f-107">Cells in the `Priority` column display images in place of corresponding textual cell values.</span></span> <span data-ttu-id="a9f5f-108"><xref:System.Windows.Forms.ConvertEventArgs.Value%2A> Özelliği <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> metinsel hücre değerini alın ve karşılık gelen görüntü görüntüleme değeri ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a9f5f-108">The <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property of the <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> is used both to get the textual cell value and to set the corresponding image display value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9f5f-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9f5f-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a9f5f-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a9f5f-110">Compiling the Code</span></span>  
 <span data-ttu-id="a9f5f-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a9f5f-111">This example requires:</span></span>  
  
-   <span data-ttu-id="a9f5f-112">Sistem, System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="a9f5f-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="a9f5f-113"><xref:System.Drawing.Bitmap> Adlandırılmış resimler `highPri.bmp`, `mediumPri.bmp`, ve `lowPri.bmp` yürütülebilir dosyayla aynı dizinde bulunan.</span><span class="sxs-lookup"><span data-stu-id="a9f5f-113"><xref:System.Drawing.Bitmap> images named `highPri.bmp`, `mediumPri.bmp`, and `lowPri.bmp` residing in the same directory as the executable file.</span></span>  
  
 <span data-ttu-id="a9f5f-114">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a9f5f-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="a9f5f-115">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9f5f-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9f5f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9f5f-116">See also</span></span>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [<span data-ttu-id="a9f5f-117">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a9f5f-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a9f5f-118">Nasıl yapılır: Verileri biçimlendirme Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="a9f5f-118">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a9f5f-119">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="a9f5f-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a9f5f-120">Windows Forms DataGridView Denetiminde Veri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="a9f5f-120">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
