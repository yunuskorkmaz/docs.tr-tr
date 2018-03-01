---
title: "Nasıl yapılır: Tuval Konumlandırma Özelliklerini Alma veya Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Canvas control [WPF], setting positioning properties
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d2b01657088c388ad09037716278dc0788de2abb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-or-set-canvas-positioning-properties"></a>Nasıl yapılır: Tuval Konumlandırma Özelliklerini Alma veya Ayarlama
Bu örnek konumlandırma yöntemlerini kullanmayı gösterir <xref:System.Windows.Controls.Canvas> alt konumlandırmak için öğesi. Bu örnek içeriği kullanan bir <xref:System.Windows.Controls.ListBoxItem> temsil etmek için konumlandırma değerler ve değerlerin örneğine dönüştürür <xref:System.Double>, konumlandırma için gerekli bir bağımsız değişken olduğu. Değerler sonra dizelere geri dönüştürülür ve metin olarak görüntülenen bir <xref:System.Windows.Controls.TextBlock> kullanarak öğesi <xref:System.Windows.Controls.Canvas.GetLeft%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.ListBox> seçilebilir on sahip öğe <xref:System.Windows.Controls.ListBoxItem> öğeleri. <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> Olay tetikleyicileri `ChangeLeft` izleyen kod bloğunun tanımladığı özel yöntem.  
  
 Her <xref:System.Windows.Controls.ListBoxItem> temsil eden bir <xref:System.Double> bir bağımsız değişken değeri, <xref:System.Windows.Controls.Canvas.SetLeft%2A> yöntemi <xref:System.Windows.Controls.Canvas> kabul eder. Kullanmak için bir <xref:System.Windows.Controls.ListBoxItem> örneğini temsil etmek için <xref:System.Double>, dönüştürmeniz gerekir <xref:System.Windows.Controls.ListBoxItem> doğru veri türü.  
  
 [!code-xaml[CanvasPositioningProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 Bir kullanıcı değiştiğinde <xref:System.Windows.Controls.ListBox> seçimi çağırılır `ChangeLeft` özel yöntem. Bu yöntem geçirir <xref:System.Windows.Controls.ListBoxItem> için bir <xref:System.Windows.LengthConverter> dönüştürür Nesne <xref:System.Windows.Controls.ContentControl.Content%2A> , bir <xref:System.Windows.Controls.ListBoxItem> örneğine <xref:System.Double> (Bu değer için zaten dönüştürülmüş bildirimi bir <xref:System.String> kullanarak <xref:System.Windows.Controls.Control.ToString%2A> yöntem). Bu değer daha sonra geri geçirilir <xref:System.Windows.Controls.Canvas.SetLeft%2A> ve <xref:System.Windows.Controls.Canvas.GetLeft%2A> yöntemlerinin <xref:System.Windows.Controls.Canvas> konumunu değiştirmek için `text1` nesnesi.  
  
 [!code-csharp[CanvasPositioningProperties#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.ListBoxItem>  
 <xref:System.Windows.LengthConverter>  
 [Panellere Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)
