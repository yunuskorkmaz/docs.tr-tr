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
ms.openlocfilehash: 5ce43054130db88792acab852b1e886285ff34d7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116057"
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d0780-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Veri Biçimlendirmeyi Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d0780-102">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d0780-103">Aşağıdaki kod örneği için bir işleyici uygulamak gösterilmiştir <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> hücreler, sütunlar ve değerler bağlı olarak nasıl görüntüleneceğini değiştiren olay.</span><span class="sxs-lookup"><span data-stu-id="d0780-103">The following code example demonstrates how to implement a handler for the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event that changes how cells are displayed depending on their columns and values.</span></span>  
  
 <span data-ttu-id="d0780-104">İçinde hücreleri `Balance` negatif sayıları içeren sütun, kırmızı bir arka plan verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d0780-104">Cells in the `Balance` column that contain negative numbers are given a red background.</span></span> <span data-ttu-id="d0780-105">Bu hücre parantezler negatif değerleri görüntülemek için para birimi olarak da biçimlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0780-105">You can also format these cells as currency to display parentheses around negative values.</span></span> <span data-ttu-id="d0780-106">Daha fazla bilgi için [nasıl yapılır: Verileri biçimlendirme Windows Forms DataGridView denetiminde](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="d0780-106">For more information, see [How to: Format Data in the Windows Forms DataGridView Control](how-to-format-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="d0780-107">İçinde hücreleri `Priority` metinsel karşılık gelen yerine sütun ekran görüntüleri hücre değerleri.</span><span class="sxs-lookup"><span data-stu-id="d0780-107">Cells in the `Priority` column display images in place of corresponding textual cell values.</span></span> <span data-ttu-id="d0780-108"><xref:System.Windows.Forms.ConvertEventArgs.Value%2A> Özelliği <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> metinsel hücre değerini alın ve karşılık gelen görüntü görüntüleme değeri ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0780-108">The <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property of the <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> is used both to get the textual cell value and to set the corresponding image display value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0780-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0780-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d0780-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d0780-110">Compiling the Code</span></span>  
 <span data-ttu-id="d0780-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="d0780-111">This example requires:</span></span>  
  
-   <span data-ttu-id="d0780-112">Sistem, System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="d0780-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
-   <xref:System.Drawing.Bitmap> <span data-ttu-id="d0780-113">Adlandırılmış resimler `highPri.bmp`, `mediumPri.bmp`, ve `lowPri.bmp` yürütülebilir dosyayla aynı dizinde bulunan.</span><span class="sxs-lookup"><span data-stu-id="d0780-113">images named `highPri.bmp`, `mediumPri.bmp`, and `lowPri.bmp` residing in the same directory as the executable file.</span></span>  
  
 <span data-ttu-id="d0780-114">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d0780-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="d0780-115">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0780-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0780-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0780-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [<span data-ttu-id="d0780-117">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d0780-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d0780-118">Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="d0780-118">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d0780-119">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="d0780-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d0780-120">Windows Forms DataGridView Denetimindeki Veri Biçimleri</span><span class="sxs-lookup"><span data-stu-id="d0780-120">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
