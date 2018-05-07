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
ms.openlocfilehash: c3e7176b0578c8fdc5f4331ad8f3b464f3a88b51
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a>Nasıl yapılır: Parmak Kullanarak Tuvali Yeniden Boyutlandırma
Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Controls.Primitives.Thumb> yeniden boyutlandırmak için denetim bir <xref:System.Windows.Controls.Canvas> denetim.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.Primitives.Thumb> Denetim taşıma veya izleyerek denetimleri yeniden boyutlandırma için kullanılan sürükleme işlevleri sağlayan <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> ve <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> olayları <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 Fare işaretçisini üzerinde duraklatıldığında sol fare düğmesini tıklatarak bir sürükleme işlemi kullanıcı başlar <xref:System.Windows.Controls.Primitives.Thumb> denetim. Sol fare düğmesini basılı kaldığı sürece sürükleme işlemi devam eder. Sürükleme işlemi sırasında <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> birden çok kez oluşabilir. Bu, her defasında <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> sınıfı, fare konumuna değişikliği karşılık gelen konum değişikliği sağlar. Kullanıcı sol fare düğmesini bıraktığında sürükleme işlemi tamamlandı. Sürükleme işlemi yalnızca yeni koordinatlar sağlar; Bunu değil otomatik olarak yeniden konumlandırmak <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.Primitives.Thumb> denetiminin alt öğesi olan bir <xref:System.Windows.Controls.Canvas> denetim. Olay işleyicisi için kendi <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> taşımak için mantığı sağlayan olay <xref:System.Windows.Controls.Primitives.Thumb> ve yeniden boyutlandırma <xref:System.Windows.Controls.Canvas>. Olay işleyicileri <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> ve <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> olayı rengini değiştirmek <xref:System.Windows.Controls.Primitives.Thumb> sürükleme işlemi sırasında. Aşağıdaki örnek tanımlar <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 [!code-xaml[Thumb#thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> taşır olay işleyicisi <xref:System.Windows.Controls.Primitives.Thumb> ve yeniden boyutlandırır <xref:System.Windows.Controls.Canvas> yanıt fare hareketini olarak.  
  
 [!code-csharp[Thumb#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> olay işleyicisi.  
  
 [!code-csharp[Thumb#DragStartedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> olay işleyicisi.  
  
 [!code-csharp[Thumb#DragCompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 Tam bir örnek için bkz: [Flash sürükleme işlevselliği örnek](http://go.microsoft.com/fwlink/?LinkID=160042).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Primitives.Thumb>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
