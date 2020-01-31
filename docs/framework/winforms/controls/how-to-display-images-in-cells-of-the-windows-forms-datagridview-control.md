---
title: DataGridView denetiminin hücrelerinde görüntü görüntüleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
ms.openlocfilehash: e0e125c816877875b80e0f20887d9beee443577a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740280"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="b9c1e-102">Nasıl yapılır: Windows Forms DataGridView Denetiminin Hücrelerinde Resim Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="b9c1e-102">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b9c1e-103">Bir resim veya grafik, bir veri satırında görüntülenebilecek değerlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="b9c1e-103">A picture or graphic is one of the values that you can display in a row of data.</span></span> <span data-ttu-id="b9c1e-104">Genellikle, bu grafikler bir çalışanın fotoğrafı veya şirket logosu biçimini alır.</span><span class="sxs-lookup"><span data-stu-id="b9c1e-104">Frequently, these graphics take the form of an employee's photograph or a company logo.</span></span>  
  
 <span data-ttu-id="b9c1e-105"><xref:System.Windows.Forms.DataGridView> denetimi içinde veri görüntülediğinizde resimleri eklemek basittir.</span><span class="sxs-lookup"><span data-stu-id="b9c1e-105">Incorporating pictures is simple when you display data within the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="b9c1e-106"><xref:System.Windows.Forms.DataGridView> denetimi, <xref:System.Drawing.Image> sınıfının desteklediği tüm görüntü biçimlerini ve bazı veritabanları tarafından kullanılan OLE resim biçimini yerel olarak işler.</span><span class="sxs-lookup"><span data-stu-id="b9c1e-106">The <xref:System.Windows.Forms.DataGridView> control natively handles any image format supported by the <xref:System.Drawing.Image> class, as well as the OLE picture format used by some databases.</span></span>  
  
 <span data-ttu-id="b9c1e-107"><xref:System.Windows.Forms.DataGridView> denetimin veri kaynağında bir görüntü sütunu varsa, bu, <xref:System.Windows.Forms.DataGridView> denetimi tarafından otomatik olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b9c1e-107">If the <xref:System.Windows.Forms.DataGridView> control's data source has a column of images, they will be displayed automatically by the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="b9c1e-108">Aşağıdaki kod örneği, gömülü bir kaynaktan bir simgenin nasıl ayıklanacağını ve bir görüntü sütununun her hücresinde görüntülenmek üzere bir bit eşlem 'e nasıl dönüştürüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b9c1e-108">The following code example demonstrates how to extract an icon from an embedded resource and convert it to a bitmap for display in every cell of an image column.</span></span> <span data-ttu-id="b9c1e-109">Metin hücresi değerlerini karşılık gelen görüntülerle değiştiren başka bir örnek için, bkz. [nasıl yapılır: veri biçimlendirmeyi özelleştirme Windows Forms DataGridView denetiminde](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b9c1e-109">For another example that replaces textual cell values with corresponding images, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9c1e-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9c1e-110">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b9c1e-111">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="b9c1e-111">Compiling the Code</span></span>  
 <span data-ttu-id="b9c1e-112">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b9c1e-112">This example requires:</span></span>  
  
- <span data-ttu-id="b9c1e-113">`dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="b9c1e-113">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="b9c1e-114">`tree.ico`adlı gömülü bir simge kaynağı.</span><span class="sxs-lookup"><span data-stu-id="b9c1e-114">An embedded icon resource named `tree.ico`.</span></span>  
  
- <span data-ttu-id="b9c1e-115"><xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>ve <xref:System.Drawing?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="b9c1e-115">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9c1e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9c1e-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="b9c1e-117">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="b9c1e-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="b9c1e-118">Nasıl yapılır: Windows Forms DataGridView Denetiminde Veri Biçimlendirmeyi Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b9c1e-118">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
