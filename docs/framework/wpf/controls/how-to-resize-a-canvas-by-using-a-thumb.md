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
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a>Nasıl yapılır: Parmak Kullanarak Tuvali Yeniden Boyutlandırma
Bu örnek, bir <xref:System.Windows.Controls.Canvas> denetimini yeniden boyutlandırmak için <xref:System.Windows.Controls.Primitives.Thumb> denetimini nasıl kullanacağınızı gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.Primitives.Thumb> denetimi, <xref:System.Windows.Controls.Primitives.Thumb><xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> ve <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> olaylarını izleyerek denetimleri taşımak veya yeniden boyutlandırmak için kullanılabilen sürükle işlevlerini sağlar.  
  
 Kullanıcı, <xref:System.Windows.Controls.Primitives.Thumb> denetiminde fare işaretçisi duraklatıldığında sol fare düğmesine basarak bir sürükleme işlemi başlatır. Sol fare düğmesi basılı kaldığı sürece sürükleme işlemi devam eder. Sürükleme işlemi sırasında <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> birden çok kez gerçekleşebilir. Her gerçekleştiğinde <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> sınıfı, fare konumundaki değişikliğe karşılık gelen konumdaki değişikliği sağlar. Kullanıcı sol fare düğmesini bıraktığında, sürükleme işlemi tamamlanır. Sürükleme işlemi yalnızca yeni koordinatlar sağlar; <xref:System.Windows.Controls.Primitives.Thumb>otomatik olarak yeniden konumlandırır.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.Canvas> denetiminin alt öğesi olan bir <xref:System.Windows.Controls.Primitives.Thumb> denetimini gösterir. <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> olayının olay işleyicisi, <xref:System.Windows.Controls.Primitives.Thumb> taşıma ve <xref:System.Windows.Controls.Canvas>yeniden boyutlandırma mantığını sağlar. <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> ve <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> olayının olay işleyicileri, bir sürükleme işlemi sırasında <xref:System.Windows.Controls.Primitives.Thumb> rengini değiştirir. Aşağıdaki örnek <xref:System.Windows.Controls.Primitives.Thumb>tanımlar.  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.Primitives.Thumb> taşınan <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> olay işleyicisini gösterir ve bir fare hareketine yanıt olarak <xref:System.Windows.Controls.Canvas> yeniden boyutlandırır.  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 Aşağıdaki örnekte <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> olay işleyicisi gösterilmektedir.  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 Aşağıdaki örnekte <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> olay işleyicisi gösterilmektedir.  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 Tüm örnek için bkz. [Thumb sürükle Işlevi örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
