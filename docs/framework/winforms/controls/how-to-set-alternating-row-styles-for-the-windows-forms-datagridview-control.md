---
title: "Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a31e8eb02949c0f6db487e3cd1a6976f2ed37222
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="84bad-102">Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="84bad-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="84bad-103">Tablo verisi genellikle defter benzeri biçimde kullanıcılara değişik satırların farklı arka plan renklerini sahip olduğu sunulur.</span><span class="sxs-lookup"><span data-stu-id="84bad-103">Tabular data is often presented to users in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="84bad-104">Bu biçim, kullanıcıların her satırda, özellikle çok sayıda sütuna sahip geniş tablolar ile hangi hücrelerin olduğunu bildirir kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="84bad-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>  
  
 <span data-ttu-id="84bad-105">İle <xref:System.Windows.Forms.DataGridView> denetimi satırların değişerek için tam stil bilgilerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84bad-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="84bad-106">Stil özelliklerini kullanmak bu etkinleştirir, ön plan rengini ve değişen satırları ayırt etmek için yazı tipi, arka plan rengi, ek olarak gibi.</span><span class="sxs-lookup"><span data-stu-id="84bad-106">This enables you use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span>  
  
 <span data-ttu-id="84bad-107">Visual Studio'da bu görev için desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="84bad-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="84bad-108">Ayrıca bkz. [nasıl yapılır: ayarlama Alternatif satır stillerini Windows Forms DataGridView denetimi kullanan bir tasarımcı](http://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="84bad-108">Also see [How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).</span></span>  
  
### <a name="to-set-alternating-row-styles-programmatically"></a><span data-ttu-id="84bad-109">Ayarlamak için alternatif satır stillerini program aracılığıyla</span><span class="sxs-lookup"><span data-stu-id="84bad-109">To set alternating row styles programmatically</span></span>  
  
-   <span data-ttu-id="84bad-110">Özellik kümesinin <xref:System.Windows.Forms.DataGridViewCellStyle> tarafından döndürülen nesne <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> özelliklerini <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="84bad-110">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> objects returned by the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties of the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    >  <span data-ttu-id="84bad-111">Kullanarak belirtilen stillerini <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> özellikler sütunu belirtilen stillerini geçersiz kılar ve <xref:System.Windows.Forms.DataGridView> düzey, ancak tek tek satır ve hücre düzeyinde ayarlanan stilleri tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="84bad-111">The styles specified using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties override the styles specified on the column and <xref:System.Windows.Forms.DataGridView> level, but are overridden by the styles set on the individual row and cell level.</span></span> <span data-ttu-id="84bad-112">Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="84bad-112">For more information, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="84bad-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="84bad-113">Compiling the Code</span></span>  
 <span data-ttu-id="84bad-114">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="84bad-114">This example requires:</span></span>  
  
-   <span data-ttu-id="84bad-115">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="84bad-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="84bad-116">Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="84bad-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="84bad-117">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="84bad-117">Robust Programming</span></span>  
 <span data-ttu-id="84bad-118">En yüksek ölçeklenebilirlik için paylaşması gerekir <xref:System.Windows.Forms.DataGridViewCellStyle> birden çok satırları, sütunları veya ayrı ayrı her öğe için stil özelliklerini ayarlama yerine aynı stilleri kullanın hücreleri nesneleri.</span><span class="sxs-lookup"><span data-stu-id="84bad-118">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="84bad-119">Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="84bad-119">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84bad-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84bad-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [<span data-ttu-id="84bad-121">Temel biçimlendirme ve stil oluşturma Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="84bad-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="84bad-122">Windows Forms DataGridView denetimindeki hücre stilleri</span><span class="sxs-lookup"><span data-stu-id="84bad-122">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="84bad-123">Windows Forms DataGridView denetimini ölçeklendirme için en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="84bad-123">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="84bad-124">Nasıl yapılır: Windows Forms DataGridView denetiminde yazı tipi ve renk stillerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="84bad-124">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
