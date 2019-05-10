---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminin Hücrelerinde Resim Görüntüleme'
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
ms.openlocfilehash: e3a4c395e86e4091d8344bebcf99ee04474f3295
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609924"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="1532a-102">Nasıl yapılır: Windows Forms DataGridView Denetiminin Hücrelerinde Resim Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="1532a-102">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1532a-103">Bir resim veya grafik veri satırında görüntüleyebilen değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="1532a-103">A picture or graphic is one of the values that you can display in a row of data.</span></span> <span data-ttu-id="1532a-104">Genellikle, bu grafik bir çalışanın fotoğraf veya bir şirket logosu biçiminde.</span><span class="sxs-lookup"><span data-stu-id="1532a-104">Frequently, these graphics take the form of an employee's photograph or a company logo.</span></span>  
  
 <span data-ttu-id="1532a-105">Resim ekleme basit veri içinde görüntülediğinizde <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="1532a-105">Incorporating pictures is simple when you display data within the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1532a-106"><xref:System.Windows.Forms.DataGridView> Denetimi tarafından desteklenen herhangi bir resim biçimi yerel olarak işleme <xref:System.Drawing.Image> OLE yanı sıra, sınıf resim bazı veritabanları tarafından kullanılan biçimi.</span><span class="sxs-lookup"><span data-stu-id="1532a-106">The <xref:System.Windows.Forms.DataGridView> control natively handles any image format supported by the <xref:System.Drawing.Image> class, as well as the OLE picture format used by some databases.</span></span>  
  
 <span data-ttu-id="1532a-107">Varsa <xref:System.Windows.Forms.DataGridView> tarafından otomatik olarak görüntülenir, denetiminin veri kaynağına sahip bir sütun görüntülerin <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="1532a-107">If the <xref:System.Windows.Forms.DataGridView> control's data source has a column of images, they will be displayed automatically by the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="1532a-108">Aşağıdaki kod örneği, katıştırılmış bir kaynaktan bir simgeyi çıkarma ve bir bit eşlem görüntülenmek üzere her bir hücresinde göreceğiniz bir görüntü sütunu Dönüştür gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1532a-108">The following code example demonstrates how to extract an icon from an embedded resource and convert it to a bitmap for display in every cell of an image column.</span></span> <span data-ttu-id="1532a-109">Metinsel hücre değerlerine karşılık gelen görüntülerle değiştiren başka bir örnek için bkz [nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1532a-109">For another example that replaces textual cell values with corresponding images, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1532a-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="1532a-110">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1532a-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1532a-111">Compiling the Code</span></span>  
 <span data-ttu-id="1532a-112">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1532a-112">This example requires:</span></span>  
  
- <span data-ttu-id="1532a-113">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="1532a-113">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="1532a-114">Adlı bir katıştırılmış simge kaynağı `tree.ico`.</span><span class="sxs-lookup"><span data-stu-id="1532a-114">An embedded icon resource named `tree.ico`.</span></span>  
  
- <span data-ttu-id="1532a-115">Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, ve <xref:System.Drawing?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="1532a-115">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1532a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1532a-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="1532a-117">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="1532a-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="1532a-118">Nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="1532a-118">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
