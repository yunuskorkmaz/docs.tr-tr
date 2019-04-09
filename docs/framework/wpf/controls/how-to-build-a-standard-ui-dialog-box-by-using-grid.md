---
title: 'Nasıl yapılır: Kılavuz Kullanarak Standart UI İletişim Kutusu Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: 0ade908e92e552017acb9ba242ccba2c28c3c995
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149532"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a><span data-ttu-id="d2b44-102">Nasıl yapılır: Kılavuz Kullanarak Standart UI İletişim Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2b44-102">How to: Build a Standard UI Dialog Box by Using Grid</span></span>
<span data-ttu-id="d2b44-103">Bu örnek, standart bir oluşturma işlemi gösterilmektedir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] iletişim kutusunu kullanarak <xref:System.Windows.Controls.Grid> öğesi.</span><span class="sxs-lookup"><span data-stu-id="d2b44-103">This example shows how to create a standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialog box by using the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2b44-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2b44-104">Example</span></span>  
 <span data-ttu-id="d2b44-105">Aşağıdaki örnek gibi bir iletişim kutusu oluşturur **çalıştırma** iletişim kutusunda [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] işletim sistemi.</span><span class="sxs-lookup"><span data-stu-id="d2b44-105">The following example creates a dialog box like the **Run** dialog box in the [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="d2b44-106">Örnek bir <xref:System.Windows.Controls.Grid> ve kullandığı <xref:System.Windows.Controls.ColumnDefinition> ve <xref:System.Windows.Controls.RowDefinition> beş sütun ve dört satır tanımlamak için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="d2b44-106">The example creates a <xref:System.Windows.Controls.Grid> and uses the <xref:System.Windows.Controls.ColumnDefinition> and <xref:System.Windows.Controls.RowDefinition> classes to define five columns and four rows.</span></span>  
  
 <span data-ttu-id="d2b44-107">Bu örnek, ardından ekler ve yerleştirir bir <xref:System.Windows.Controls.Image>, `RunIcon.png`, iletişim kutusunda bulunan resmi temsil edecek.</span><span class="sxs-lookup"><span data-stu-id="d2b44-107">The example then adds and positions an <xref:System.Windows.Controls.Image>, `RunIcon.png`, to represent the image that is found in the dialog box.</span></span> <span data-ttu-id="d2b44-108">Görüntünün ilk sütun ve satır yerleştirilir <xref:System.Windows.Controls.Grid> (sol üst köşede).</span><span class="sxs-lookup"><span data-stu-id="d2b44-108">The image is placed in the first column and row of the <xref:System.Windows.Controls.Grid> (the upper-left corner).</span></span>  
  
 <span data-ttu-id="d2b44-109">Ardından, örnek ekler bir <xref:System.Windows.Controls.TextBlock> kalan sütunlarını ilk satırın kapsayan ilk sütuna öğesi.</span><span class="sxs-lookup"><span data-stu-id="d2b44-109">Next, the example adds a <xref:System.Windows.Controls.TextBlock> element to the first column, which spans the remaining columns of the first row.</span></span> <span data-ttu-id="d2b44-110">Başka bir ekler <xref:System.Windows.Controls.TextBlock> temsil etmek için ilk sütunda, ikinci satır öğesi **açık** metin kutusu.</span><span class="sxs-lookup"><span data-stu-id="d2b44-110">It adds another <xref:System.Windows.Controls.TextBlock> element to the second row in the first column, to represent the **Open** text box.</span></span> <span data-ttu-id="d2b44-111">A <xref:System.Windows.Controls.TextBlock> aşağıdaki gibi veri giriş alanı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d2b44-111">A <xref:System.Windows.Controls.TextBlock> follows, which represents the data entry area.</span></span>  
  
 <span data-ttu-id="d2b44-112">Son olarak, üç örnek ekler <xref:System.Windows.Controls.Button> temsil eden son satırın öğelerine **Tamam**, **iptal**, ve **Gözat** olayları.</span><span class="sxs-lookup"><span data-stu-id="d2b44-112">Finally, the example adds three <xref:System.Windows.Controls.Button> elements to the final row, which represent the **OK**, **Cancel**, and **Browse** events.</span></span>  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d2b44-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2b44-113">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [<span data-ttu-id="d2b44-114">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d2b44-114">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="d2b44-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="d2b44-115">How-to Topics</span></span>](grid-how-to-topics.md)
