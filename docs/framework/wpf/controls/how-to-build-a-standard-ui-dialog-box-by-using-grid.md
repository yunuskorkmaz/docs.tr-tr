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
ms.openlocfilehash: 68c9653e616388374aad2ad33ac7dab68446241d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923415"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a><span data-ttu-id="895fd-102">Nasıl yapılır: Kılavuz Kullanarak Standart UI İletişim Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="895fd-102">How to: Build a Standard UI Dialog Box by Using Grid</span></span>
<span data-ttu-id="895fd-103">Bu örnek, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] <xref:System.Windows.Controls.Grid> öğesini kullanarak bir standart iletişim kutusu oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="895fd-103">This example shows how to create a standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialog box by using the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="895fd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="895fd-104">Example</span></span>  
 <span data-ttu-id="895fd-105">Aşağıdaki örnek, Windows işletim sistemindeki **Çalıştır** iletişim kutusu gibi bir iletişim kutusu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="895fd-105">The following example creates a dialog box like the **Run** dialog box in the Windows operating system.</span></span>  
  
 <span data-ttu-id="895fd-106">Örnek bir <xref:System.Windows.Controls.Grid> oluşturur ve beş sütun ve dört <xref:System.Windows.Controls.RowDefinition> satır tanımlamak için <xref:System.Windows.Controls.ColumnDefinition> ve sınıflarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="895fd-106">The example creates a <xref:System.Windows.Controls.Grid> and uses the <xref:System.Windows.Controls.ColumnDefinition> and <xref:System.Windows.Controls.RowDefinition> classes to define five columns and four rows.</span></span>  
  
 <span data-ttu-id="895fd-107">Daha sonra bu örnek, iletişim kutusunda <xref:System.Windows.Controls.Image>bulunan `RunIcon.png`görüntüyü göstermek için bir, ekler ve konumlandırır.</span><span class="sxs-lookup"><span data-stu-id="895fd-107">The example then adds and positions an <xref:System.Windows.Controls.Image>, `RunIcon.png`, to represent the image that is found in the dialog box.</span></span> <span data-ttu-id="895fd-108">Görüntü, <xref:System.Windows.Controls.Grid> (sol üst köşenin) ilk sütununa ve satırına yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="895fd-108">The image is placed in the first column and row of the <xref:System.Windows.Controls.Grid> (the upper-left corner).</span></span>  
  
 <span data-ttu-id="895fd-109">Sonra, örnek ilk sütuna bir <xref:System.Windows.Controls.TextBlock> öğe ekler ve ilk satırın kalan sütunlarını kapsar.</span><span class="sxs-lookup"><span data-stu-id="895fd-109">Next, the example adds a <xref:System.Windows.Controls.TextBlock> element to the first column, which spans the remaining columns of the first row.</span></span> <span data-ttu-id="895fd-110">**Açık** metin kutusunu <xref:System.Windows.Controls.TextBlock> göstermek için ilk sütundaki ikinci satıra bir öğe ekler.</span><span class="sxs-lookup"><span data-stu-id="895fd-110">It adds another <xref:System.Windows.Controls.TextBlock> element to the second row in the first column, to represent the **Open** text box.</span></span> <span data-ttu-id="895fd-111">Veri <xref:System.Windows.Controls.TextBlock> girişi alanını temsil eden aşağıdaki bir.</span><span class="sxs-lookup"><span data-stu-id="895fd-111">A <xref:System.Windows.Controls.TextBlock> follows, which represents the data entry area.</span></span>  
  
 <span data-ttu-id="895fd-112">Son olarak, örnek, son <xref:System.Windows.Controls.Button> satıra, **Tamam**, **iptal**ve **Gözden** geçirme olaylarını temsil eden üç öğe ekler.</span><span class="sxs-lookup"><span data-stu-id="895fd-112">Finally, the example adds three <xref:System.Windows.Controls.Button> elements to the final row, which represent the **OK**, **Cancel**, and **Browse** events.</span></span>  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="895fd-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="895fd-113">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [<span data-ttu-id="895fd-114">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="895fd-114">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="895fd-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="895fd-115">How-to Topics</span></span>](grid-how-to-topics.md)
