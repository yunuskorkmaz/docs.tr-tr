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
ms.openlocfilehash: d113c45469f6a78c94b9489bd82f9e55b5b96bba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962272"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="20148-102">Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="20148-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="20148-103">Tablo verileri genellikle, değişen satırlarda farklı arka plan rengine sahip olan bir defter benzeri biçimde kullanıcılara sunulur.</span><span class="sxs-lookup"><span data-stu-id="20148-103">Tabular data is often presented to users in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="20148-104">Bu biçim, özellikle çok sayıda sütunu olan geniş tablolar ile, kullanıcıların her satırda hangi hücrelerin olduğunu söylemesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="20148-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>  
  
 <span data-ttu-id="20148-105"><xref:System.Windows.Forms.DataGridView> Denetimiyle, alternatif satırlar için tüm stil bilgilerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20148-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="20148-106">Bu, alternatif satırları ayırt etmek için arka plan rengine ek olarak, ön plan rengi ve yazı tipi gibi stil özellikleri kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="20148-106">This enables you use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span>  
  
 <span data-ttu-id="20148-107">Visual Studio 'da bu görev için destek vardır.</span><span class="sxs-lookup"><span data-stu-id="20148-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="20148-108">Ayrıca bkz [. nasıl yapılır: Tasarımcıyı](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)kullanarak Windows Forms DataGridView denetimi Için alternatif satır stillerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="20148-108">Also see [How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer](set-alternating-row-styles-for-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-set-alternating-row-styles-programmatically"></a><span data-ttu-id="20148-109">Alternatif satır stillerini programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="20148-109">To set alternating row styles programmatically</span></span>  
  
- <span data-ttu-id="20148-110"><xref:System.Windows.Forms.DataGridViewCellStyle> <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> Öğesinin ve<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> özellikleri tarafından döndürülen nesnelerinin özelliklerini ayarlayın. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="20148-110">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> objects returned by the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties of the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    > <span data-ttu-id="20148-111"><xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> Ve <xref:System.Windows.Forms.DataGridView> özellikleri kullanılarak belirtilen stiller, sütun ve düzeyde belirtilen stilleri geçersiz kılar, ancak tek satır ve hücre düzeyinde ayarlanan stiller tarafından geçersiz kılınır. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A></span><span class="sxs-lookup"><span data-stu-id="20148-111">The styles specified using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties override the styles specified on the column and <xref:System.Windows.Forms.DataGridView> level, but are overridden by the styles set on the individual row and cell level.</span></span> <span data-ttu-id="20148-112">Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki Hücre stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="20148-112">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="20148-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="20148-113">Compiling the Code</span></span>  
 <span data-ttu-id="20148-114">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="20148-114">This example requires:</span></span>  
  
- <span data-ttu-id="20148-115"><xref:System.Windows.Forms.DataGridView> Adlı`dataGridView1`bir denetim.</span><span class="sxs-lookup"><span data-stu-id="20148-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="20148-116"><xref:System?displayProperty=nameWithType> ,<xref:System.Drawing?displayProperty=nameWithType>Ve derlemelerinin<xref:System.Windows.Forms?displayProperty=nameWithType> başvuruları.</span><span class="sxs-lookup"><span data-stu-id="20148-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="20148-117">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="20148-117">Robust Programming</span></span>  
 <span data-ttu-id="20148-118">En yüksek ölçeklenebilirlik için, nesneleri her <xref:System.Windows.Forms.DataGridViewCellStyle> öğe için stil özelliklerini ayrı ayrı ayarlamak yerine, aynı stilleri kullanan birden çok satır, sütun veya hücrede paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20148-118">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="20148-119">Daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirme Için En Iyi uygulamalar](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="20148-119">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20148-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20148-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="20148-121">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="20148-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="20148-122">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="20148-122">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="20148-123">Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="20148-123">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="20148-124">Nasıl yapılır: Windows Forms DataGridView denetiminde yazı tipi ve renk stillerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="20148-124">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
