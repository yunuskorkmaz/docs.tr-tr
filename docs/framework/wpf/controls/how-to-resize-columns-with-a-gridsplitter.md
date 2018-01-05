---
title: "Nasıl yapılır: GridSplitter ile Sütunları Yeniden Boyutlandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d68d829e5543b1c299668493c11b62ccb11d81af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a><span data-ttu-id="a5ced-102">Nasıl yapılır: GridSplitter ile Sütunları Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="a5ced-102">How to: Resize Columns with a GridSplitter</span></span>
<span data-ttu-id="a5ced-103">Bu örnek dikey oluşturulacağını gösterir <xref:System.Windows.Controls.GridSplitter> iki sütun arasındaki boşluğu yeniden dağıtmak için bir <xref:System.Windows.Controls.Grid> boyutlarını değiştirmeden <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="a5ced-103">This example shows how to create a vertical <xref:System.Windows.Controls.GridSplitter> in order to redistribute the space between two columns in a <xref:System.Windows.Controls.Grid> without changing the dimensions of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5ced-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5ced-104">Example</span></span>  
 <span data-ttu-id="a5ced-105">**Bu yer GridSplitter nasıl sütunun kenarına**</span><span class="sxs-lookup"><span data-stu-id="a5ced-105">**How to create a GridSplitter that overlays the edge of a column**</span></span>  
  
 <span data-ttu-id="a5ced-106">Belirtmek için bir <xref:System.Windows.Controls.GridSplitter> içinde bitişik sütunları yeniden boyutlandırır bir <xref:System.Windows.Controls.Grid>ayarlayın <xref:System.Windows.Controls.Grid.Column%2A> özelliği yeniden boyutlandırmak istediğiniz sütunlardan biri için eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="a5ced-106">To specify a <xref:System.Windows.Controls.GridSplitter> that resizes adjacent columns in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Column%2A> attached property to one of the columns that you want to resize.</span></span> <span data-ttu-id="a5ced-107">Varsa, <xref:System.Windows.Controls.Grid> birden fazla satır içeriyorsa ayarlamak <xref:System.Windows.Controls.Grid.RowSpan%2A> satır sayısı özelliği eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="a5ced-107">If your <xref:System.Windows.Controls.Grid> has more than one row, set the <xref:System.Windows.Controls.Grid.RowSpan%2A> attached property to the number of rows.</span></span> <span data-ttu-id="a5ced-108">Ardından <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliğine <xref:System.Windows.HorizontalAlignment.Left> veya <xref:System.Windows.HorizontalAlignment.Right> (hangi hizalamayı ayarlayacağınız yeniden boyutlandırmak istediğiniz iki sütuna bağlıdır).</span><span class="sxs-lookup"><span data-stu-id="a5ced-108">Then set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Left> or <xref:System.Windows.HorizontalAlignment.Right> (which alignment you set depends on which two columns you want to resize).</span></span> <span data-ttu-id="a5ced-109">Son olarak, ayarlamak <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özelliğine <xref:System.Windows.VerticalAlignment.Stretch>.</span><span class="sxs-lookup"><span data-stu-id="a5ced-109">Finally, set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> property to <xref:System.Windows.VerticalAlignment.Stretch>.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 <span data-ttu-id="a5ced-110">A <xref:System.Windows.Controls.GridSplitter> kendi sütun yok'deki diğer denetimler tarafından görünmeyebilir <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="a5ced-110">A <xref:System.Windows.Controls.GridSplitter> that does not have its own column may be obscured by other controls in the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="a5ced-111">Bu sorunu önlemek nasıl hakkında daha fazla bilgi için bkz: [GridSplitter görünür olduğundan emin olun](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span><span class="sxs-lookup"><span data-stu-id="a5ced-111">For more information about how to prevent this issue, see [Make Sure That a GridSplitter Is Visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span></span>  
  
 <span data-ttu-id="a5ced-112">**Bir sütun kaplayan GridSplitter nasıl oluşturulur**</span><span class="sxs-lookup"><span data-stu-id="a5ced-112">**How to create a GridSplitter that occupies a column**</span></span>  
  
 <span data-ttu-id="a5ced-113">Belirtmek için bir <xref:System.Windows.Controls.GridSplitter> içinde bir sütun kaplayan bir <xref:System.Windows.Controls.Grid>ayarlayın <xref:System.Windows.Controls.Grid.Column%2A> özelliği yeniden boyutlandırmak istediğiniz sütunlardan biri için eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="a5ced-113">To specify a <xref:System.Windows.Controls.GridSplitter> that occupies a column in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Column%2A> attached property to one of the columns that you want to resize.</span></span> <span data-ttu-id="a5ced-114">Kılavuzunuzun birden fazla satır varsa ayarlamak <xref:System.Windows.Controls.Grid.RowSpan%2A> satır sayısı özelliği eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="a5ced-114">If your Grid has more than one row, set the <xref:System.Windows.Controls.Grid.RowSpan%2A> attached property to the number of rows.</span></span> <span data-ttu-id="a5ced-115">Ardından <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> için <xref:System.Windows.HorizontalAlignment.Center>ayarlayın <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özelliğine <xref:System.Windows.VerticalAlignment.Stretch>ve <xref:System.Windows.Controls.ColumnDefinition.Width%2A> içeren sütunun <xref:System.Windows.Controls.GridSplitter> için <xref:System.Windows.GridLength.Auto%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5ced-115">Then set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> to <xref:System.Windows.HorizontalAlignment.Center>, set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> property to <xref:System.Windows.VerticalAlignment.Stretch>, and set the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of the column that contains the <xref:System.Windows.Controls.GridSplitter> to <xref:System.Windows.GridLength.Auto%2A>.</span></span>  
  
 <span data-ttu-id="a5ced-116">Aşağıdaki örnek, dikey tanımlamak gösterilmiştir <xref:System.Windows.Controls.GridSplitter> , bir sütun kaplayan ve her iki tarafında sütunları yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="a5ced-116">The following example shows how to define a vertical <xref:System.Windows.Controls.GridSplitter> that occupies a column and resizes the columns on either side of it.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a><span data-ttu-id="a5ced-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5ced-117">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="a5ced-118">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="a5ced-118">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
