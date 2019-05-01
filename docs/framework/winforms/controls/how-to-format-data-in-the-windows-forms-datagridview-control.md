---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Biçimlendirme'
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
ms.openlocfilehash: 62701edfdb3cf2729cb401ad12a12ee4f524287b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941420"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ef520-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="ef520-102">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ef520-103">Aşağıdaki yordamlar temel kullanarak hücre değerlerinin biçimlendirilmesi göstermektedir <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> özelliği bir <xref:System.Windows.Forms.DataGridView> denetimi ve belirli bir denetim sütun.</span><span class="sxs-lookup"><span data-stu-id="ef520-103">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="ef520-104">Gelişmiş veri biçimlendirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="ef520-104">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="ef520-105">Biçimi para birimi ve tarih değerleri</span><span class="sxs-lookup"><span data-stu-id="ef520-105">To format currency and date values</span></span>  
  
- <span data-ttu-id="ef520-106">Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="ef520-106">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="ef520-107">Aşağıdaki kod örneği kullanarak belirli sütunları biçimini ayarlar <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> özellik sütunları.</span><span class="sxs-lookup"><span data-stu-id="ef520-107">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="ef520-108">Değerler `UnitPrice` sütunu parantez içine negatif değerler içeren geçerli kültüre özgü para birimi biçiminde görünür.</span><span class="sxs-lookup"><span data-stu-id="ef520-108">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="ef520-109">Değerler `ShipDate` sütun geçerli kültüre özgü kısa tarih biçiminde görünür.</span><span class="sxs-lookup"><span data-stu-id="ef520-109">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="ef520-110">Hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> değerleri, görmek [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="ef520-110">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="ef520-111">Boş veritabanı değerlerini görüntüsünü özelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="ef520-111">To customize the display of null database values</span></span>  
  
- <span data-ttu-id="ef520-112">Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="ef520-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="ef520-113">Aşağıdaki kod örneğinde <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> "giriş materyali" eşit olan değerleri içeren tüm hücreleri görüntülenecek özelliği <xref:System.DBNull.Value?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ef520-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="ef520-114">Hücrelerde metin tabanlı sözcük kaydırmayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="ef520-114">To enable wordwrap in text-based cells</span></span>  
  
- <span data-ttu-id="ef520-115">Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle> birine <xref:System.Windows.Forms.DataGridViewTriState> sabit listesi değerleri.</span><span class="sxs-lookup"><span data-stu-id="ef520-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="ef520-116">Aşağıdaki kod örneğinde <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> eksiksiz bir denetim için kaydırma modu ayarlamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="ef520-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="ef520-117">DataGridView hücrelerinin metin hizalaması belirtmek için</span><span class="sxs-lookup"><span data-stu-id="ef520-117">To specify the text alignment of DataGridView cells</span></span>  
  
- <span data-ttu-id="ef520-118">Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle> birine <xref:System.Windows.Forms.DataGridViewContentAlignment> sabit listesi değerleri.</span><span class="sxs-lookup"><span data-stu-id="ef520-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="ef520-119">Aşağıdaki kod örneği kullanarak belirli bir sütun için hizalamasını ayarlar <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> sütunun özelliği.</span><span class="sxs-lookup"><span data-stu-id="ef520-119">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="ef520-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef520-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ef520-121">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ef520-121">Compiling the Code</span></span>  
 <span data-ttu-id="ef520-122">Bu örneği gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ef520-122">These examples require:</span></span>  
  
- <span data-ttu-id="ef520-123">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `UnitPrice`, adlı bir sütun `ShipDate`, adlı bir sütun `CustomerName`.</span><span class="sxs-lookup"><span data-stu-id="ef520-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
- <span data-ttu-id="ef520-124">Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="ef520-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ef520-125">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="ef520-125">Robust Programming</span></span>  
 <span data-ttu-id="ef520-126">En yüksek ölçeklenebilirlik için paylaşmalıdır <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri birden çok satırları, sütunları veya hücreleri stil özellikleri her öğe için ayrı olarak ayarlamak yerine aynı stili kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef520-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="ef520-127">Daha fazla bilgi için [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="ef520-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef520-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef520-128">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="ef520-129">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="ef520-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ef520-130">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="ef520-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ef520-131">Windows Forms DataGridView Denetiminde Veri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="ef520-131">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ef520-132">Nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="ef520-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ef520-133">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="ef520-133">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
