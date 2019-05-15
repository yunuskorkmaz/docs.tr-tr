---
title: 'Nasıl yapılır: Kullanıcıların Windows Forms DataGridView Denetiminden Panoya Birden Fazla Hücre Kopyalamasına Olanak Tanıma'
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
ms.openlocfilehash: b220603adcaeae6f3380a2e3c10ea524c9a61f24
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591913"
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a><span data-ttu-id="50a15-102">Nasıl yapılır: Kullanıcıların Windows Forms DataGridView Denetiminden Panoya Birden Fazla Hücre Kopyalamasına Olanak Tanıma</span><span class="sxs-lookup"><span data-stu-id="50a15-102">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="50a15-103">Hücre kopyalama etkinleştirdiğinizde, verileri olun, <xref:System.Windows.Forms.DataGridView> denetim diğer uygulamalara kolayca erişilebilir <xref:System.Windows.Forms.Clipboard>.</span><span class="sxs-lookup"><span data-stu-id="50a15-103">When you enable cell copying, you make the data in your <xref:System.Windows.Forms.DataGridView> control easily accessible to other applications through the <xref:System.Windows.Forms.Clipboard>.</span></span> <span data-ttu-id="50a15-104">Seçili hücreleri değerleri dizelere dönüştürülür ve not defteri ve Excel gibi uygulamalara yapıştırmak için sekmeyle ayrılmış metin değerleri ve HTML biçimli bir tablo Word gibi uygulamalarda yapıştırma olarak panoya eklendi.</span><span class="sxs-lookup"><span data-stu-id="50a15-104">The values of the selected cells are converted to strings and added to the Clipboard as tab-delimited text values for pasting into applications like Notepad and Excel, and as an HTML-formatted table for pasting into applications like Word.</span></span>  
  
 <span data-ttu-id="50a15-105">Hücre değerlerini kopyalamak için satır ve sütun üst bilgi metni Pano verilerine dahil edilecek veya tüm satırları veya sütunları yalnızca belirli kullanıcılara üst bilgi metni dahil edilecek hücre kopyalama yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50a15-105">You can configure cell copying to copy cell values only, to include row and column header text in the Clipboard data, or to include header text only when users select entire rows or columns.</span></span>  
  
 <span data-ttu-id="50a15-106">Seçim moduna bağlı olarak, kullanıcıların birden fazla bağlantısı kesilen grubu hücre seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50a15-106">Depending on the selection mode, users can select multiple disconnected groups of cells.</span></span> <span data-ttu-id="50a15-107">Bir kullanıcı hücreleri panoya kopyalar, satırları ve sütunları ile seçilen hücre kopyalanmaz.</span><span class="sxs-lookup"><span data-stu-id="50a15-107">When a user copies cells to the Clipboard, rows and columns with no selected cells are not copied.</span></span> <span data-ttu-id="50a15-108">Diğer tüm satırları veya sütunları panoya kopyalandı veri tablo içindeki satırları ve sütunları haline gelir.</span><span class="sxs-lookup"><span data-stu-id="50a15-108">All other rows or columns become rows and columns in the table of data copied to the Clipboard.</span></span> <span data-ttu-id="50a15-109">Bu satırlar veya sütunlar seçili olmayan hücre boş yer tutucu olarak panoya kopyalanamadı.</span><span class="sxs-lookup"><span data-stu-id="50a15-109">Unselected cells in these rows or columns are copied as blank placeholders to the Clipboard.</span></span>  
  
### <a name="to-enable-cell-copying"></a><span data-ttu-id="50a15-110">Hücre kopyalama etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="50a15-110">To enable cell copying</span></span>  
  
- <span data-ttu-id="50a15-111">Ayarlama <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="50a15-111">Set the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a><span data-ttu-id="50a15-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="50a15-112">Example</span></span>  
 <span data-ttu-id="50a15-113">Aşağıdaki kod örneği, nasıl hücreler panoya kopyalanır gösterir.</span><span class="sxs-lookup"><span data-stu-id="50a15-113">The following complete code example demonstrates how cells are copied to the Clipboard.</span></span> <span data-ttu-id="50a15-114">Bu örnek Pano kullanarak seçili hücreleri kopyalayan bir düğme içerir <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> Pano içeriğini metin kutusunda yöntemi ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="50a15-114">This example includes a button that copies the selected cells to the Clipboard using the <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> method and displays the Clipboard contents in a text box.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="50a15-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="50a15-115">Compiling the Code</span></span>  
 <span data-ttu-id="50a15-116">Bu kod gerektirir:</span><span class="sxs-lookup"><span data-stu-id="50a15-116">This code requires:</span></span>  
  
- <span data-ttu-id="50a15-117">N: System ve N:System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="50a15-117">References to the N:System and N:System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50a15-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50a15-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>
- <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>
- [<span data-ttu-id="50a15-119">Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı</span><span class="sxs-lookup"><span data-stu-id="50a15-119">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
