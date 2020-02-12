---
title: 'Nasıl yapılır: Parmak Kullanarak Tuvali Yeniden Boyutlandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resizing Canvas control [WPF]
- controls [WPF], Thumb
- controls [WPF], Canvas
- Thumb control [WPF]
- Canvas control [WPF]
ms.assetid: 7dc9f435-726c-4d4d-be41-eb24cfe17bef
ms.openlocfilehash: 84f5ac2b53124b7f4d7c15741e94b40e7ee81526
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124305"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a><span data-ttu-id="d30fb-102">Nasıl yapılır: Parmak Kullanarak Tuvali Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="d30fb-102">How to: Resize a Canvas by Using a Thumb</span></span>
<span data-ttu-id="d30fb-103">Bu örnek, bir <xref:System.Windows.Controls.Canvas> denetimini yeniden boyutlandırmak için <xref:System.Windows.Controls.Primitives.Thumb> denetimini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d30fb-103">This example shows how to use a <xref:System.Windows.Controls.Primitives.Thumb> control to resize a <xref:System.Windows.Controls.Canvas> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d30fb-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d30fb-104">Example</span></span>  
 <span data-ttu-id="d30fb-105"><xref:System.Windows.Controls.Primitives.Thumb> denetimi, <xref:System.Windows.Controls.Primitives.Thumb><xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> ve <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> olaylarını izleyerek denetimleri taşımak veya yeniden boyutlandırmak için kullanılabilen sürükle işlevlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d30fb-105">The <xref:System.Windows.Controls.Primitives.Thumb> control provides drag functionality that can be used to move or resize controls by monitoring the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> events of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="d30fb-106">Kullanıcı, <xref:System.Windows.Controls.Primitives.Thumb> denetiminde fare işaretçisi duraklatıldığında sol fare düğmesine basarak bir sürükleme işlemi başlatır.</span><span class="sxs-lookup"><span data-stu-id="d30fb-106">The user begins a drag operation by pressing the left mouse button when the mouse pointer is paused on the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="d30fb-107">Sol fare düğmesi basılı kaldığı sürece sürükleme işlemi devam eder.</span><span class="sxs-lookup"><span data-stu-id="d30fb-107">The drag operation continues as long as the left mouse button remains pressed.</span></span> <span data-ttu-id="d30fb-108">Sürükleme işlemi sırasında <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> birden çok kez gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="d30fb-108">During the drag operation, the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> can occur more than once.</span></span> <span data-ttu-id="d30fb-109">Her gerçekleştiğinde <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> sınıfı, fare konumundaki değişikliğe karşılık gelen konumdaki değişikliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="d30fb-109">Each time it occurs, the <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> class provides the change in position that corresponds to the change in mouse position.</span></span> <span data-ttu-id="d30fb-110">Kullanıcı sol fare düğmesini bıraktığında, sürükleme işlemi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="d30fb-110">When the user releases the left mouse button, the drag operation is finished.</span></span> <span data-ttu-id="d30fb-111">Sürükleme işlemi yalnızca yeni koordinatlar sağlar; <xref:System.Windows.Controls.Primitives.Thumb>otomatik olarak yeniden konumlandırır.</span><span class="sxs-lookup"><span data-stu-id="d30fb-111">The drag operation only provides new coordinates; it does not automatically reposition the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="d30fb-112">Aşağıdaki örnek, bir <xref:System.Windows.Controls.Canvas> denetiminin alt öğesi olan bir <xref:System.Windows.Controls.Primitives.Thumb> denetimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d30fb-112">The following example shows a <xref:System.Windows.Controls.Primitives.Thumb> control that is the child element of a <xref:System.Windows.Controls.Canvas> control.</span></span> <span data-ttu-id="d30fb-113"><xref:System.Windows.Controls.Primitives.Thumb.DragDelta> olayının olay işleyicisi, <xref:System.Windows.Controls.Primitives.Thumb> taşıma ve <xref:System.Windows.Controls.Canvas>yeniden boyutlandırma mantığını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d30fb-113">The event handler for its <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event provides the logic to move the <xref:System.Windows.Controls.Primitives.Thumb> and resize the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="d30fb-114"><xref:System.Windows.Controls.Primitives.Thumb.DragStarted> ve <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> olayının olay işleyicileri, bir sürükleme işlemi sırasında <xref:System.Windows.Controls.Primitives.Thumb> rengini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d30fb-114">The event handlers for the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event change the color of the <xref:System.Windows.Controls.Primitives.Thumb> during a drag operation.</span></span> <span data-ttu-id="d30fb-115">Aşağıdaki örnek <xref:System.Windows.Controls.Primitives.Thumb>tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d30fb-115">The following example defines the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 <span data-ttu-id="d30fb-116">Aşağıdaki örnek, <xref:System.Windows.Controls.Primitives.Thumb> taşınan <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> olay işleyicisini gösterir ve bir fare hareketine yanıt olarak <xref:System.Windows.Controls.Canvas> yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="d30fb-116">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event handler that moves the <xref:System.Windows.Controls.Primitives.Thumb> and resizes the <xref:System.Windows.Controls.Canvas> in response to a mouse movement.</span></span>  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 <span data-ttu-id="d30fb-117">Aşağıdaki örnekte <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> olay işleyicisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d30fb-117">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 <span data-ttu-id="d30fb-118">Aşağıdaki örnekte <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> olay işleyicisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d30fb-118">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 <span data-ttu-id="d30fb-119">Tüm örnek için bkz. [Thumb sürükle Işlevi örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps).</span><span class="sxs-lookup"><span data-stu-id="d30fb-119">For the complete sample, see [Thumb Drag Functionality Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d30fb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d30fb-120">See also</span></span>

- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
