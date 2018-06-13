---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
ms.openlocfilehash: b7206d2896ad391f8a45e1fbb612cdb49004182d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539714"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="f7b1d-102">Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="f7b1d-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f7b1d-103">Tablo verisi genellikle defter benzeri biçimde kullanıcılara değişik satırların farklı arka plan renklerini sahip olduğu sunulur.</span><span class="sxs-lookup"><span data-stu-id="f7b1d-103">Tabular data is often presented to users in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="f7b1d-104">Bu biçim, kullanıcıların her satırda, özellikle çok sayıda sütuna sahip geniş tablolar ile hangi hücrelerin olduğunu bildirir kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="f7b1d-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>  
  
 <span data-ttu-id="f7b1d-105">İle <xref:System.Windows.Forms.DataGridView> denetimi satırların değişerek için tam stil bilgilerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7b1d-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="f7b1d-106">Stil özelliklerini kullanmak bu etkinleştirir, ön plan rengini ve değişen satırları ayırt etmek için yazı tipi, arka plan rengi, ek olarak gibi.</span><span class="sxs-lookup"><span data-stu-id="f7b1d-106">This enables you use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span>  
  
 <span data-ttu-id="f7b1d-107">Visual Studio'da bu görev için desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="f7b1d-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="f7b1d-108">Ayrıca bkz. [nasıl yapılır: ayarlama Alternatif satır stillerini Windows Forms DataGridView denetimi kullanan bir tasarımcı](http://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f7b1d-108">Also see [How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).</span></span>  
  
### <a name="to-set-alternating-row-styles-programmatically"></a><span data-ttu-id="f7b1d-109">Ayarlamak için alternatif satır stillerini program aracılığıyla</span><span class="sxs-lookup"><span data-stu-id="f7b1d-109">To set alternating row styles programmatically</span></span>  
  
-   <span data-ttu-id="f7b1d-110">Özellik kümesinin <xref:System.Windows.Forms.DataGridViewCellStyle> tarafından döndürülen nesne <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> özelliklerini <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="f7b1d-110">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> objects returned by the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties of the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    >  <span data-ttu-id="f7b1d-111">Kullanarak belirtilen stillerini <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> özellikler sütunu belirtilen stillerini geçersiz kılar ve <xref:System.Windows.Forms.DataGridView> düzey, ancak tek tek satır ve hücre düzeyinde ayarlanan stilleri tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="f7b1d-111">The styles specified using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties override the styles specified on the column and <xref:System.Windows.Forms.DataGridView> level, but are overridden by the styles set on the individual row and cell level.</span></span> <span data-ttu-id="f7b1d-112">Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f7b1d-112">For more information, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f7b1d-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f7b1d-113">Compiling the Code</span></span>  
 <span data-ttu-id="f7b1d-114">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f7b1d-114">This example requires:</span></span>  
  
-   <span data-ttu-id="f7b1d-115">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="f7b1d-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="f7b1d-116">Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="f7b1d-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f7b1d-117">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="f7b1d-117">Robust Programming</span></span>  
 <span data-ttu-id="f7b1d-118">En yüksek ölçeklenebilirlik için paylaşması gerekir <xref:System.Windows.Forms.DataGridViewCellStyle> birden çok satırları, sütunları veya ayrı ayrı her öğe için stil özelliklerini ayarlama yerine aynı stilleri kullanın hücreleri nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f7b1d-118">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="f7b1d-119">Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f7b1d-119">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7b1d-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f7b1d-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [<span data-ttu-id="f7b1d-121">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="f7b1d-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f7b1d-122">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="f7b1d-122">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f7b1d-123">Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f7b1d-123">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f7b1d-124">Nasıl yapılır: Windows Forms DataGridView Denetiminde Yazı Tipi ve Renk Stillerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="f7b1d-124">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
