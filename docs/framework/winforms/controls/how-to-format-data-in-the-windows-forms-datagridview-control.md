---
title: DataGridView denetiminde verileri biçimlendirme
description: Windows Forms DataGridView denetiminin DefaultCellStyle özelliğini kullanarak hücre değerlerini biçimlendirmeyi ve denetimdeki belirli sütunları kullanmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
ms.openlocfilehash: d6105c1d1120876f854332e7a10106cc1caf6276
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622815"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="2ef8e-103">Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="2ef8e-103">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="2ef8e-104">Aşağıdaki yordamlarda, <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> bir denetimin özelliğini <xref:System.Windows.Forms.DataGridView> ve bir denetimdeki belirli sütunları kullanarak hücre değerlerinin temel biçimlendirmesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2ef8e-104">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="2ef8e-105">Gelişmiş veri biçimlendirme hakkında daha fazla bilgi için, bkz. [nasıl yapılır: veri biçimlendirmeyi özelleştirme Windows Forms DataGridView denetiminde](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="2ef8e-105">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="2ef8e-106">Para birimi ve tarih değerlerini biçimlendirmek için</span><span class="sxs-lookup"><span data-stu-id="2ef8e-106">To format currency and date values</span></span>  
  
- <span data-ttu-id="2ef8e-107"><xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>Öğesinin özelliğini ayarlayın <xref:System.Windows.Forms.DataGridViewCellStyle> .</span><span class="sxs-lookup"><span data-stu-id="2ef8e-107">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="2ef8e-108">Aşağıdaki kod örneği, sütunların özelliğini kullanarak belirli sütunların biçimini ayarlar <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> .</span><span class="sxs-lookup"><span data-stu-id="2ef8e-108">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="2ef8e-109">`UnitPrice`Sütundaki değerler, parantez içine alınmış negatif değerlerle birlikte geçerli kültüre özgü para birimi biçiminde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2ef8e-109">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="2ef8e-110">`ShipDate`Sütundaki değerler geçerli kültüre özgü kısa tarih biçiminde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2ef8e-110">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="2ef8e-111">Değerler hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> bkz. [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="2ef8e-111">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="2ef8e-112">Null veritabanı değerlerinin görüntülenmesini özelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="2ef8e-112">To customize the display of null database values</span></span>  
  
- <span data-ttu-id="2ef8e-113"><xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A>Öğesinin özelliğini ayarlayın <xref:System.Windows.Forms.DataGridViewCellStyle> .</span><span class="sxs-lookup"><span data-stu-id="2ef8e-113">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="2ef8e-114">Aşağıdaki kod örneği, <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> değerine eşit değer içeren tüm hücrelerde "giriş yok" göstermek için özelliğini kullanır <xref:System.DBNull.Value?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2ef8e-114">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="2ef8e-115">Metin tabanlı hücrelerde WordWrap özelliğini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="2ef8e-115">To enable wordwrap in text-based cells</span></span>  
  
- <span data-ttu-id="2ef8e-116"><xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>Öğesinin özelliğini <xref:System.Windows.Forms.DataGridViewCellStyle> <xref:System.Windows.Forms.DataGridViewTriState> sabit listesi değerlerinden birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2ef8e-116">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="2ef8e-117">Aşağıdaki kod örneği, <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> tüm denetim için Wrap modunu ayarlamak için özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2ef8e-117">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="2ef8e-118">DataGridView hücrelerinin metin hizalamasını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="2ef8e-118">To specify the text alignment of DataGridView cells</span></span>  
  
- <span data-ttu-id="2ef8e-119"><xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>Öğesinin özelliğini <xref:System.Windows.Forms.DataGridViewCellStyle> <xref:System.Windows.Forms.DataGridViewContentAlignment> sabit listesi değerlerinden birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2ef8e-119">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="2ef8e-120">Aşağıdaki kod örneği, sütununun özelliğini kullanarak belirli bir sütunun hizalamasını ayarlar <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> .</span><span class="sxs-lookup"><span data-stu-id="2ef8e-120">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="2ef8e-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ef8e-121">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2ef8e-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2ef8e-122">Compiling the Code</span></span>  
 <span data-ttu-id="2ef8e-123">Bu örneklerde şunlar gerekir:</span><span class="sxs-lookup"><span data-stu-id="2ef8e-123">These examples require:</span></span>  
  
- <span data-ttu-id="2ef8e-124">Adında bir sütun, adlı bir sütun ve adlı bir sütun <xref:System.Windows.Forms.DataGridView> içeren adlı bir denetim `dataGridView1` `UnitPrice` `ShipDate` `CustomerName` .</span><span class="sxs-lookup"><span data-stu-id="2ef8e-124">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
- <span data-ttu-id="2ef8e-125"><xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType> Ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerinin başvuruları.</span><span class="sxs-lookup"><span data-stu-id="2ef8e-125">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2ef8e-126">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="2ef8e-126">Robust Programming</span></span>  
 <span data-ttu-id="2ef8e-127">En yüksek ölçeklenebilirlik için, <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri her öğe için stil özelliklerini ayrı ayrı ayarlamak yerine, aynı stilleri kullanan birden çok satır, sütun veya hücrede paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ef8e-127">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="2ef8e-128">Daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirme Için En Iyi uygulamalar](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="2ef8e-128">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ef8e-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ef8e-129">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="2ef8e-130">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="2ef8e-130">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="2ef8e-131">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="2ef8e-131">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="2ef8e-132">Windows Forms DataGridView Denetiminde Veri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="2ef8e-132">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="2ef8e-133">Nasıl yapılır: Windows Forms DataGridView Denetiminde Veri Biçimlendirmeyi Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="2ef8e-133">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="2ef8e-134">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="2ef8e-134">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
