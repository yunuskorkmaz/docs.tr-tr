---
title: Kullanıcıların DataGridView denetiminden panoya birden fazla hücre kopyalamasını sağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], copying to Clipboard
- DataGridView control [Windows Forms], copying multiple cells
- data grids [Windows Forms], copying multiple cells
- Clipboard [Windows Forms], copying multiple cells
ms.assetid: fd0403b2-d0e3-4ae0-839c-0f737e1eb4a9
ms.openlocfilehash: 2bb74a1f0c59b28ab496ce9c89c1c1b5f9d8147b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745775"
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a><span data-ttu-id="c3614-102">Nasıl yapılır: Kullanıcıların Windows Forms DataGridView Denetiminden Panoya Birden Fazla Hücre Kopyalamasına Olanak Tanıma</span><span class="sxs-lookup"><span data-stu-id="c3614-102">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c3614-103">Hücre kopyalamayı etkinleştirdiğinizde, <xref:System.Windows.Forms.DataGridView> denetimindeki verileri, <xref:System.Windows.Forms.Clipboard>üzerinden diğer uygulamalar için kolayca erişilebilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3614-103">When you enable cell copying, you make the data in your <xref:System.Windows.Forms.DataGridView> control easily accessible to other applications through the <xref:System.Windows.Forms.Clipboard>.</span></span> <span data-ttu-id="c3614-104">Seçilen hücrelerin değerleri dizelere dönüştürülür ve Not defteri ve Excel gibi uygulamalara yapıştırılmasına yönelik sekmeyle ayrılmış metin değerleri olarak panoya ve Word gibi uygulamalara yapıştırılmasına yönelik HTML biçimli bir tablo olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="c3614-104">The values of the selected cells are converted to strings and added to the Clipboard as tab-delimited text values for pasting into applications like Notepad and Excel, and as an HTML-formatted table for pasting into applications like Word.</span></span>  
  
 <span data-ttu-id="c3614-105">Hücre kopyalamayı yalnızca hücre değerlerini kopyalamak, pano verilerine satır ve sütun üst bilgi metnini dahil etmek veya yalnızca kullanıcılar tüm satırları veya sütunları seçerken başlık metnini eklemek için yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3614-105">You can configure cell copying to copy cell values only, to include row and column header text in the Clipboard data, or to include header text only when users select entire rows or columns.</span></span>  
  
 <span data-ttu-id="c3614-106">Kullanıcılar seçim moduna bağlı olarak, birden fazla bağlantısı kesilmiş hücre grubunu seçebilir.</span><span class="sxs-lookup"><span data-stu-id="c3614-106">Depending on the selection mode, users can select multiple disconnected groups of cells.</span></span> <span data-ttu-id="c3614-107">Bir Kullanıcı panoya hücre kopyadığında, seçili hücreleri olmayan satırlar ve sütunlar kopyalanmaz.</span><span class="sxs-lookup"><span data-stu-id="c3614-107">When a user copies cells to the Clipboard, rows and columns with no selected cells are not copied.</span></span> <span data-ttu-id="c3614-108">Diğer tüm satırlar veya sütunlar, panoya kopyalanmış veri tablosunda satır ve sütun haline gelir.</span><span class="sxs-lookup"><span data-stu-id="c3614-108">All other rows or columns become rows and columns in the table of data copied to the Clipboard.</span></span> <span data-ttu-id="c3614-109">Bu satırlardaki veya sütunlardaki seçilmemiş hücreler, panoya boş yer tutucular olarak kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="c3614-109">Unselected cells in these rows or columns are copied as blank placeholders to the Clipboard.</span></span>  
  
### <a name="to-enable-cell-copying"></a><span data-ttu-id="c3614-110">Hücre kopyalamayı etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="c3614-110">To enable cell copying</span></span>  
  
- <span data-ttu-id="c3614-111"><xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c3614-111">Set the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a><span data-ttu-id="c3614-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3614-112">Example</span></span>  
 <span data-ttu-id="c3614-113">Aşağıdaki kod örneğinde, hücrelerin Pano 'ya nasıl kopyalandığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c3614-113">The following complete code example demonstrates how cells are copied to the Clipboard.</span></span> <span data-ttu-id="c3614-114">Bu örnek, <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> yöntemini kullanarak seçili hücreleri panoya kopyalayan ve Pano içeriğini bir metin kutusunda görüntüleyen bir düğme içerir.</span><span class="sxs-lookup"><span data-stu-id="c3614-114">This example includes a button that copies the selected cells to the Clipboard using the <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> method and displays the Clipboard contents in a text box.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c3614-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c3614-115">Compiling the Code</span></span>  
 <span data-ttu-id="c3614-116">Bu kod şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c3614-116">This code requires:</span></span>  
  
- <span data-ttu-id="c3614-117">N:System ve N:System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="c3614-117">References to the N:System and N:System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3614-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3614-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>
- <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>
- [<span data-ttu-id="c3614-119">Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı</span><span class="sxs-lookup"><span data-stu-id="c3614-119">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
