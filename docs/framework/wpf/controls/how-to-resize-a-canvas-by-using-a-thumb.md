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
ms.openlocfilehash: 80b873e81acc243ff61257bc305c4f782b5bf867
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351835"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a>Nasıl yapılır: Parmak Kullanarak Tuvali Yeniden Boyutlandırma
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Controls.Primitives.Thumb> yeniden boyutlandırmak için denetimi bir <xref:System.Windows.Controls.Canvas> denetimi.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.Primitives.Thumb> Denetimi taşımak veya izleyerek yeniden boyutlandırmak için kullanılan Sürükle işlevselliği sağlar <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> ve <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> olayları <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 Kullanıcı, fare işaretçisi üzerinde duraklatıldığında farenin sol düğmesine basarak bir sürükleme işlemi başlar <xref:System.Windows.Controls.Primitives.Thumb> denetimi. Sol fare düğmesini basılı kaldığı sürece sürükleme işlemi devam ediyor. Sürükleme işlemi sırasında <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> birden çok kez gerçekleşebilir. Oluşur, her zaman <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> fare konumu değişikliği karşılık gelen konum değişikliği sınıfı sağlar. Kullanıcının sol fare düğmesini bıraktığında sürükleme işlemi tamamlandı. Sürükleme işlemi yalnızca yeni koordinatları sağlar. değil otomatik olarak yeniden konumlandırdığınız <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.Primitives.Thumb> denetim alt öğesi olan bir <xref:System.Windows.Controls.Canvas> denetimi. Olay işleyicisi için kendi <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> olay taşımak için mantığı sağlar <xref:System.Windows.Controls.Primitives.Thumb> ve yeniden boyutlandırma <xref:System.Windows.Controls.Canvas>. Olay işleyicileri <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> ve <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> olayı rengini değiştirmek <xref:System.Windows.Controls.Primitives.Thumb> bir sürükleme işlemi sırasında. Aşağıdaki örnek tanımlar <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> taşıyan olay işleyicisi <xref:System.Windows.Controls.Primitives.Thumb> ve yeniden boyutlandırır <xref:System.Windows.Controls.Canvas> yanıt olarak bir fare hareketi.  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> olay işleyicisi.  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> olay işleyicisi.  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 Tam bir örnek için bkz. [Thumb Sürükle işlevselliği örnek](https://go.microsoft.com/fwlink/?LinkID=160042).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
