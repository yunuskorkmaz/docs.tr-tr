---
title: "Nasıl yapılır: GridSplitter ile Satırları Yeniden Boyutlandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d4cf06a86a1da7bb34074623f8f19f4bda7a724
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a><span data-ttu-id="8c8e1-102">Nasıl yapılır: GridSplitter ile Satırları Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="8c8e1-102">How to: Resize Rows with a GridSplitter</span></span>
<span data-ttu-id="8c8e1-103">Bu örnek yatay kullanmayı gösterir <xref:System.Windows.Controls.GridSplitter> iki satır arasındaki boşluğu yeniden dağıtmak için bir <xref:System.Windows.Controls.Grid> boyutlarını değiştirmeden <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="8c8e1-103">This example shows how to use a horizontal <xref:System.Windows.Controls.GridSplitter> to redistribute the space between two rows in a <xref:System.Windows.Controls.Grid> without changing the dimensions of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c8e1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c8e1-104">Example</span></span>  
 <span data-ttu-id="8c8e1-105">**Bu yer GridSplitter nasıl kenarın satır**</span><span class="sxs-lookup"><span data-stu-id="8c8e1-105">**How to create a GridSplitter that overlays the edge of a row**</span></span>  
  
 <span data-ttu-id="8c8e1-106">Belirtmek için bir <xref:System.Windows.Controls.GridSplitter> içinde bitişik satırları yeniden boyutlandırır bir <xref:System.Windows.Controls.Grid>ayarlayın <xref:System.Windows.Controls.Grid.Row%2A> özelliği yeniden boyutlandırmak istediğiniz satırları birine eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="8c8e1-106">To specify a <xref:System.Windows.Controls.GridSplitter> that resizes adjacent rows in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Row%2A> attached property to one of the rows that you want to resize.</span></span> <span data-ttu-id="8c8e1-107">Varsa, <xref:System.Windows.Controls.Grid> birden fazla sütun var. ayarlamak <xref:System.Windows.Controls.Grid.ColumnSpan%2A> iliştirilmiş özelliği sütun sayısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="8c8e1-107">If your <xref:System.Windows.Controls.Grid> has more than one column, set the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> attached property to specify the number of columns.</span></span> <span data-ttu-id="8c8e1-108">Ardından <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> için <xref:System.Windows.VerticalAlignment.Top> veya <xref:System.Windows.VerticalAlignment.Bottom> (hangi hizalamayı ayarlayacağınız yeniden boyutlandırmak istediğiniz iki satıra bağlıdır).</span><span class="sxs-lookup"><span data-stu-id="8c8e1-108">Then set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> to <xref:System.Windows.VerticalAlignment.Top> or <xref:System.Windows.VerticalAlignment.Bottom> (which alignment you set depends on which two rows you want to resize).</span></span> <span data-ttu-id="8c8e1-109">Son olarak, ayarlamak <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliğine <xref:System.Windows.HorizontalAlignment.Stretch>.</span><span class="sxs-lookup"><span data-stu-id="8c8e1-109">Finally, set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Stretch>.</span></span>  
  
 <span data-ttu-id="8c8e1-110">Aşağıdaki örnek, yatay tanımlamak gösterilmiştir <xref:System.Windows.Controls.GridSplitter> bitişik satırlara göre yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="8c8e1-110">The following example shows how to define a horizontal <xref:System.Windows.Controls.GridSplitter> that resizes adjacent rows.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 <span data-ttu-id="8c8e1-111">A <xref:System.Windows.Controls.GridSplitter> kendi satırında kaplar değil diğer denetimler tarafından görünmeyebilir <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="8c8e1-111">A <xref:System.Windows.Controls.GridSplitter> that does not occupy its own row may be obscured by other controls in the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="8c8e1-112">Bu sorunu önlemek nasıl hakkında daha fazla bilgi için bkz: [GridSplitter görünür olduğundan emin olun](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span><span class="sxs-lookup"><span data-stu-id="8c8e1-112">For more information about how to prevent this issue, see [Make Sure That a GridSplitter Is Visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span></span>  
  
 <span data-ttu-id="8c8e1-113">**Bir satır kaplayan GridSplitter nasıl oluşturulur**</span><span class="sxs-lookup"><span data-stu-id="8c8e1-113">**How to create a GridSplitter that occupies a row**</span></span>  
  
 <span data-ttu-id="8c8e1-114">Belirtmek için bir <xref:System.Windows.Controls.GridSplitter> içinde bir satır kaplayan bir <xref:System.Windows.Controls.Grid>ayarlayın <xref:System.Windows.Controls.Grid.Row%2A> özelliği yeniden boyutlandırmak istediğiniz satırları birine eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="8c8e1-114">To specify a <xref:System.Windows.Controls.GridSplitter> that occupies a row in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Row%2A> attached property to one of the rows that you want to resize.</span></span> <span data-ttu-id="8c8e1-115">Varsa, <xref:System.Windows.Controls.Grid> birden fazla sütun var. ayarlamak <xref:System.Windows.Controls.Grid.ColumnSpan%2A> sütun sayısı özelliği eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="8c8e1-115">If your <xref:System.Windows.Controls.Grid> has more than one column, set the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> attached property to the number of columns.</span></span> <span data-ttu-id="8c8e1-116">Ardından <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> için <xref:System.Windows.VerticalAlignment.Center>ayarlayın <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliğine <xref:System.Windows.HorizontalAlignment.Stretch>ve <xref:System.Windows.Controls.RowDefinition.Height%2A> içeren satırın <xref:System.Windows.Controls.GridSplitter> için <xref:System.Windows.GridLength.Auto%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c8e1-116">Then set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> to <xref:System.Windows.VerticalAlignment.Center>, set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Stretch>, and set the <xref:System.Windows.Controls.RowDefinition.Height%2A> of the row that contains the <xref:System.Windows.Controls.GridSplitter> to <xref:System.Windows.GridLength.Auto%2A>.</span></span>  
  
 <span data-ttu-id="8c8e1-117">Aşağıdaki örnek, yatay tanımlamak gösterilmiştir <xref:System.Windows.Controls.GridSplitter> , bir satır kaplayan ve her iki tarafında satırları yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="8c8e1-117">The following example shows how to define a horizontal <xref:System.Windows.Controls.GridSplitter> that occupies a row and resizes the rows on either side of it.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a><span data-ttu-id="8c8e1-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c8e1-118">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="8c8e1-119">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="8c8e1-119">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
