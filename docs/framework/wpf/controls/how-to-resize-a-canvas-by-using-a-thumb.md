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
ms.openlocfilehash: 14942157429b029147d47e2f88428c56e66523d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979959"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a><span data-ttu-id="2d15b-102">Nasıl yapılır: Parmak Kullanarak Tuvali Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="2d15b-102">How to: Resize a Canvas by Using a Thumb</span></span>
<span data-ttu-id="2d15b-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Controls.Primitives.Thumb> yeniden boyutlandırmak için denetimi bir <xref:System.Windows.Controls.Canvas> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2d15b-103">This example shows how to use a <xref:System.Windows.Controls.Primitives.Thumb> control to resize a <xref:System.Windows.Controls.Canvas> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d15b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="2d15b-104">Example</span></span>  
 <span data-ttu-id="2d15b-105"><xref:System.Windows.Controls.Primitives.Thumb> Denetimi taşımak veya izleyerek yeniden boyutlandırmak için kullanılan Sürükle işlevselliği sağlar <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> ve <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> olayları <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="2d15b-105">The <xref:System.Windows.Controls.Primitives.Thumb> control provides drag functionality that can be used to move or resize controls by monitoring the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> events of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="2d15b-106">Kullanıcı, fare işaretçisi üzerinde duraklatıldığında farenin sol düğmesine basarak bir sürükleme işlemi başlar <xref:System.Windows.Controls.Primitives.Thumb> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2d15b-106">The user begins a drag operation by pressing the left mouse button when the mouse pointer is paused on the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="2d15b-107">Sol fare düğmesini basılı kaldığı sürece sürükleme işlemi devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="2d15b-107">The drag operation continues as long as the left mouse button remains pressed.</span></span> <span data-ttu-id="2d15b-108">Sürükleme işlemi sırasında <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> birden çok kez gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="2d15b-108">During the drag operation, the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> can occur more than once.</span></span> <span data-ttu-id="2d15b-109">Oluşur, her zaman <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> fare konumu değişikliği karşılık gelen konum değişikliği sınıfı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d15b-109">Each time it occurs, the <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> class provides the change in position that corresponds to the change in mouse position.</span></span> <span data-ttu-id="2d15b-110">Kullanıcının sol fare düğmesini bıraktığında sürükleme işlemi tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="2d15b-110">When the user releases the left mouse button, the drag operation is finished.</span></span> <span data-ttu-id="2d15b-111">Sürükleme işlemi yalnızca yeni koordinatları sağlar. değil otomatik olarak yeniden konumlandırdığınız <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="2d15b-111">The drag operation only provides new coordinates; it does not automatically reposition the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="2d15b-112">Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.Primitives.Thumb> denetim alt öğesi olan bir <xref:System.Windows.Controls.Canvas> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2d15b-112">The following example shows a <xref:System.Windows.Controls.Primitives.Thumb> control that is the child element of a <xref:System.Windows.Controls.Canvas> control.</span></span> <span data-ttu-id="2d15b-113">Olay işleyicisi için kendi <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> olay taşımak için mantığı sağlar <xref:System.Windows.Controls.Primitives.Thumb> ve yeniden boyutlandırma <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="2d15b-113">The event handler for its <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event provides the logic to move the <xref:System.Windows.Controls.Primitives.Thumb> and resize the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="2d15b-114">Olay işleyicileri <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> ve <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> olayı rengini değiştirmek <xref:System.Windows.Controls.Primitives.Thumb> bir sürükleme işlemi sırasında.</span><span class="sxs-lookup"><span data-stu-id="2d15b-114">The event handlers for the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event change the color of the <xref:System.Windows.Controls.Primitives.Thumb> during a drag operation.</span></span> <span data-ttu-id="2d15b-115">Aşağıdaki örnek tanımlar <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="2d15b-115">The following example defines the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 <span data-ttu-id="2d15b-116">Aşağıdaki örnekte gösterildiği <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> taşıyan olay işleyicisi <xref:System.Windows.Controls.Primitives.Thumb> ve yeniden boyutlandırır <xref:System.Windows.Controls.Canvas> yanıt olarak bir fare hareketi.</span><span class="sxs-lookup"><span data-stu-id="2d15b-116">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event handler that moves the <xref:System.Windows.Controls.Primitives.Thumb> and resizes the <xref:System.Windows.Controls.Canvas> in response to a mouse movement.</span></span>  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 <span data-ttu-id="2d15b-117">Aşağıdaki örnekte gösterildiği <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="2d15b-117">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 <span data-ttu-id="2d15b-118">Aşağıdaki örnekte gösterildiği <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="2d15b-118">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 <span data-ttu-id="2d15b-119">Tam bir örnek için bkz. [Thumb Sürükle işlevselliği örnek](https://go.microsoft.com/fwlink/?LinkID=160042).</span><span class="sxs-lookup"><span data-stu-id="2d15b-119">For the complete sample, see [Thumb Drag Functionality Sample](https://go.microsoft.com/fwlink/?LinkID=160042).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d15b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d15b-120">See also</span></span>

- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
